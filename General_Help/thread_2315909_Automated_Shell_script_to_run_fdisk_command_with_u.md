---
title: "Automated Shell script to run fdisk command with user input"
date: 2016-03-03
forum: General Help
---

### Post by Bowei_Zhao on 2016-03-03
I'd like to create a bash shell script that can run commands and provide input as if I was typing it on the  terminal.


I have written bash shell scripts before and understand how to but I'm a bit confused on how it 'interfaces'.


Currently, I'm required to run fdisk and other terminal commands and then go through their option panel providing a set/specified input. It is taking too long and since it is constant, I was  wondering then how I would go about it.


I get that a shell script is like if you were to type that command into the terminal. Thus, can I just literally write a script that says something like:


sudo fdisk /dev/sda


d


1


d


2


n


p


1


As an example where the single string entries are what I type on my keyboard as fdisk waits for commands. This doesn't seem valid but it may be.


Also, something I have to do after those commands run is unplug the drive and then continue running it. Am I able to implement that into my program to wait for me to unplug, and replug and then continue running automated script?


I appreciate  all the help.

---

### Post by TheFu on 2016-03-03
fdisk is dangerous. Use parted instead.  For filling in answers to terminal questions, use **expect**.  But, if you want to just repartition a disk, I'd create a machine-readable partition file and use that with parted to re-partition as desired.
Try:
```
sudo parted  -m 
```
to see the output.

Use the 'read' command in bash.  The ABSG has examples for most of this stuff.  Websearch "bash ABSG" to find it.

---

### Post by Bowei_Zhao on 2016-03-31
Thank you!

We are specified by the industry instruction manual to run that command however. But I appreciate it.

---

### Post by TheFu on 2016-03-31
fdisk support for GPT partitioned disks may not exist. It depends on the exact version.  All versions of **parted** handle both GPT and MBR partitioned disks.  **gparted** also works with both.  Both fdisk and parted have "machine readable" input and output capabilities so that would be the most exact way to do this, provided the physical geometry of the drive is understood.  parted also handles alignment issues that fdisk doesn't.

<rant>
It would have been much easier if the team that wrote parted/gparted just forked the fdisk/sfdisk/cfdisk code and kept the name.  But then we would probably end up with something like the grub mess - where grub v2 isn't actually v2.xx, but 1.98g something (don't quote me) is grub2. What a mess.  Should have used "2.00.00.00 alpha" for all the non-production versions.  Devs shouldn't try to be cute with their versioning.  Code names are fun, but confusing - why should I have to memorize **any** f*cking code names at all? Numbers are clear.  Sorry Ubuntu  and Android - I don't like your release code names.  They all blend together and don't convey anything useful like a release number.  I **KNOW** that 6.06 was before 8.04. Further, 8.04 was released in April 2008. THAT is useful.  16.04 is clear. Computers know how to parse it. People can understand it. It is useful. "trusty" isn't useful at all as a name. Geez.
Look here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - what good is the "code name" column?  It doesn't convey **anything** more than the version number. Nothing. Nada. Worthless. </rant> 

There was 1 code name that I liked - "beefy miracle" [https://beefymiracle.org/history.html](https://beefymiracle.org/history.html)
Ubuntu is coming up on the Zeds ... what's next?  After the huge party, of course.

Ok - I'll go and find my happy place now. ;) Thanks for supporting my need to rant today.

---

