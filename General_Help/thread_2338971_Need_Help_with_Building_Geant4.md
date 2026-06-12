---
title: "Need Help with Building Geant4"
date: 2016-10-03
forum: General Help
---

### Post by real-solace on 2016-10-03
Hi

   I really really appreciate any help i can get with this.
I have followed the geant4 installation guide step by step but for some reason this error has me stumped:
------------------------------------------------------------------------------------
[skulmiya@localhost B1-build]$ ./exampleB1
Available UI session types: [ GAG, tcsh, csh ]

-------- EEEE ------- G4Exception-START -------- EEEE -------
*** G4Exception : PART70001
      issued by : G4NuclideTable
ENSDFSTATE.dat is not found.
*** Fatal Exception *** core dump ***
-------- EEEE -------- G4Exception-END --------- EEEE -------


*** G4Exception: Aborting execution ***
Aborted (core dumped)
------------------------------------------------------------------------------------

I have relocated my environment variables, but i dont know why its not recognising the .dat file, even though its present within the directory.

Thank you once again.

---

### Post by theokost on 2017-01-03
Hello all, 

I also have the exact same problem.
Did you found any solution about that?
Thank you in advance

---

### Post by lokithefly on 2017-01-03
[http://geant4.cern.ch/support/source/geant4/source/particles/management/src/G4NuclideTable.cc](http://geant4.cern.ch/support/source/geant4/source/particles/management/src/G4NuclideTable.cc)

{

   if ( threshold_of_half_life < minimum_threshold_of_half_life ) {

      // Need to update full list

      char* path = getenv("G4ENSDFSTATEDATA");

      if ( !path ) {
         G4Exception("G4NuclideTable", "PART70000",
                     FatalException, "G4ENSDFSTATEDATA environment variable must be set");
         return;
      }

      std::ifstream ifs;
      G4String filename(path);
      filename += "/ENSDFSTATE.dat";

      ifs.open( filename.c_str() );

      if ( !ifs.good() ) {
         G4Exception("G4NuclideTable", "PART70001",
                     FatalException, "ENSDFSTATE.dat is not found.");
         return;
      }

Are you setting the enviroment variable right?

---

### Post by hmostafa on 2017-05-14
check the data folder under your geant4 installation directory 

for example geant4 installation directory/share/Geant4-10.3.1/data/G4ENSDFSTATE2.1

If it is empty, then you need to install data files

---

