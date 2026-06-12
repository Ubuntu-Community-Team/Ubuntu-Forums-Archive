---
title: "Error while running INET framework in ubuntu 12.04"
date: 2013-12-03
forum: General Help
---

### Post by mulyead on 2013-12-03
Hello everyone,

I am doing project on BGP convergence. For this i installed Ubuntu 12.04 and OMNET++ 4.3.1 version. I also installed INET framework inet-2.2.0-src. After installing when i try to run the demo from terminal i encountered following error:

:~/omnetpp-4.3.1/samples/inet/examples$ ./rundemo
< !> Warning: opp_run: Cannot check library ../../../src/inet: ../../../src//libinet.so: cannot open shared object file: No such file or directory

OMNeT++ Discrete Event Simulation  (C) 1992-2013 Andras Varga, OpenSim Ltd.
Version: 4.3.1, build: 130913-19cda8a, edition: Academic Public License -- NOT FOR COMMERCIAL USE
See the license for distribution terms and warranty disclaimer

< !> Error during startup: Cannot load library '../../../src//libinet.so': ../../../src//libinet.so: cannot open shared object file: No such file or directory.

End.

I am trying to study effect of MRAI timers on BGP cpnvergence through this OMNET ++ simulation.
Is this simulator supports the MRAI timer adjustment for different network topologies???

Thanks in advance 

ADM

---

