# wenzel_database_parser
Programatically parse a Wenzel CMM Access database.

# Overview

The class herein exposes routines to interact programatically with the access database produced by a Wenzel CMM and allows the user to convert between the machine coordinate system (MCS) and part coordinate systems (PCS). It works by processing "measurements" in a Quartis CMM database. Each measurement contains a group of "elements"; these are circles, spheres, lines etc. 
      
The Quartis CMM database has two pertinent tables to record the information taken by the CMM: tbCoordSys and tbElement. The former table contains the matrix elements of a transform that can be used to convert the raw CMM table positions e.g. _tbElement.elAct* into a desired PCS. The two tables can be joined on \_tbElement.elMsRecNr --> \_tbCoordSys.csMsRecNr, giving each element within a measurement a PCS (many elements will thus have the same PCS).
      
There may also exist several PCSs for each measurement. In this case, the user is required to specify a "csId", which uniquely identifies a PCS in the database. The default for this is 1.
      
For each element in a measurement, there will be a unique "elRecNr".
