---
title: "Copy  a file extension from a folder that changes name regularly"
date: 2013-04-11
forum: General Help
---

### Post by saande on 2013-04-11
Hi all,

I tried to use the cp command when trying to copy from an ubuntu server (source) to a Windows Server (Destination), a file with a particular extension (.bam). The problem does not rely on the command itself but the fact that the location of the file is on a folder which changes name every day.

Do you know any command I could use in this case?


Here is an example of what I try to do: cp ionadminAT192.168.2.63:/results/analysis/output/Home/Auto_*/plugin_out/*_rawlib.bam AT192.168.0.174:\pgm


Thks,

---

### Post by Vaphell on 2013-04-11
scp is used to copy between computers and its syntax is roughly like you wrote it.

in case there is only 1 dir that changes its name what you did should work (using * to abstract it away that is). If there are many dirs with new one added daily, is there any rule to the naming scheme?

---

### Post by saande on 2013-04-11
Thanks for your reply. I actually tried cp or scp and I get the error message that multi-level wildcard is not supported. When I work with one folder, everything is Ok. 
What complicates it all is also the fact that the naming is done arbitrary and does not follow any naming scheme?

---

### Post by Vaphell on 2013-04-12
this issue is trivial, nothing a simple script wouldn't solve
even bigger problem is that windows sucks a** and doesn't really play ball when it comes to ssh/scp/sftp networking AND automation - 2 things needed here.

you have to either
- set up some scp capable ssh server on windows (freesshd, openssh?) - operation performed from ubuntu box, assuming some light scripting required to solve the dynamic dir name issue before pushing file to 
- figure out automation in winscp (reportedly can be done but i am not sure it is able to do this) - from win box
- create a share on windows box, mount it in ubuntu as cifs/smbfs and perform the operation via simple local cp - probably the easiest way

---

### Post by saande on 2013-04-12
Tanks a lot. I'll give it à try back to work on Monday and let you know.

---

