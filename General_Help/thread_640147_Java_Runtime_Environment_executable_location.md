---
title: "Java Runtime Environment executable location?"
date: 2007-12-13
forum: General Help
---

### Post by yaknowwat on 2007-12-13
I need to know where the the executable location so that I can install it.

A program for my school work was coded in java for cross platform compatibility.

I've been using the synaptic manager log files to see if I can locate it but I'm not sure if I'm finding the right ones.

I have.

Java Sun runtime 5,6 (both independant/dependant sets)


I really don't want to install window to run a single program as ubuntu is suiting me quite well.

---

### Post by luisromangz on 2007-12-14
In a terminal, write:

whereis java

It is probably a simlink located in /usr/bin, you can check what real file is the simlink pointing to easly, for example using ls:

ls -l /usr/bin/java

That's a standard procedure for finding executables.

---

### Post by yaknowwat on 2007-12-22
I tried the directories that pulled up and about every other one none of them worked out right...

i think it might be the program as it'll crash when pointed at a directory and says everything else is not a jre executable.

i'm most likely going to vmware for the program..,

forunately vmware is quite fast on linux and I can leave it minimized without an effect on performance .

though itd be nice if someone knew someting to do about this.

I will upload the program if i need to it was originally on a CD so I left it in ISO format and it is a 272 MB file and uploading on ADSL can take a while... (15KB/s max)

the program is 'Aplusanywhere' normally shown like this 'A+nywhere Learning System'

Kind of annoying when their site ( [http://204.97.228.57/](http://204.97.228.57/) {their domain is broken or something...} ) even says it supports Linux. Main site is [http://www.amered.com/index.php](http://www.amered.com/index.php)

---

### Post by PeterJS on 2007-12-22
Just install it with synaptic, the package name is sun-java6-bin.

---

