---
title: "Problem with starting FoamX"
date: 2008-01-10
forum: General Help
---

### Post by fpetit on 2008-01-10
Hi everyone,
I recently installed OpenFoam. The blockMesh . cavity and icoFoam . cavity at the end of installation are working properly but then I cannot run FoamX...

The error message is:

flo@flo-laptop:~$ FoamX
Starting NameServer with inet:flo-laptop:1234 ...
Starting FoamX Host Browser with inet:flo-laptop:1234 ...
/*---------------------------------------------------------------------------*\
| =========                 |                                                 |
| \\      /  F ield         | OpenFOAM: The Open Source CFD Toolbox           |
|  \\    /   O peration     | Version:  1.4.1                                 |
|   \\  /    A nd           | Web:      [http://www.openfoam.org](http://www.openfoam.org)               |
|    \\/     M anipulation  |                                                 |
\*---------------------------------------------------------------------------*/

Exec   : FoamXHostBrowser 
Date   : Jan 10 2008
Time   : 10:02:36
Host   : flo-laptop
PID    : 6016
Root   : 
Case   : 
Nprocs : 1
HostBrowser running.....
Setting LANG to en_EN
Using jar /home/flo/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/lib/FoamX.jar
Using jar /home/flo/OpenFOAM/OpenFOAM-1.4.1/applications/utilities/preProcessing/FoamX/lib/jlfgr-1_0.jar
/home/flo/OpenFOAM/OpenFOAM-1.4.1/bin/FoamX: 244: /home/flo/OpenFOAM/linux64/j2sdk1.4.2_05/bin/java: not found
Killed
runFoamXHB : cleanup
runFoamXHB: Killing name server nsd(pid 6012).


Anybody can help???
Thank you

---

### Post by zionpsyfer on 2008-01-10
/home/flo/OpenFOAM/linux64/j2sdk1.4.2_05/bin/java: not found


That's what's killing ya.  Does the /home/flo/OpenFOAM/linux64/j2sdk1.4.2_05/bin directory exist?  Is the java executable in there?

---

### Post by fpetit on 2008-01-11
That's also what  I thought but the java file is there:

flo@flo-laptop:~$ cd /home/flo/OpenFOAM/linux64/j2sdk1.4.2_05/bin
flo@flo-laptop:~/OpenFOAM/linux64/j2sdk1.4.2_05/bin$ ls
appletviewer   idlj       java     javah         jdb      klist         orbd        rmid         servertool
extcheck       jar        javac    javap         keytool  ktab          policytool  rmiregistry  tnameserv
HtmlConverter  jarsigner  javadoc  java-rmi.cgi  kinit    native2ascii  rmic        serialver


I'm really stuck on that...

Flo

---

### Post by erazz on 2008-01-19
Had the same problem on Xubuntu 64bit.

Install gcc and sun-java6 jre and sdk using synaptic.

You will need to modify ~/OpenFOAM/OpenFOAM-1.4.1/.bashrc

Change line 100 
```
from:
 export WM_COMPILER_DIR=$WM_PROJECT_INST_DIR/$WM_ARCH/gcc-4.2.1$WM_COMPILER_ARCH
to:
  export WM_COMPILER_DIR=/usr
```

Change line 118
```
from:
  export JAVA_HOME=$WM_PROJECT_INST_DIR/$WM_ARCH/j2sdk1.4.2_05
to:
  export JAVA_HOME=/usr
```

source ~/OpenFOAM/OpenFOAM-1.4.1/.OpenFOAM/bashrc
and you're set

Erez

---

