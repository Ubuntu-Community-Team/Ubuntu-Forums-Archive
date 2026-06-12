---
title: "DDRescue help please"
date: 2015-12-10
forum: General Help
---

### Post by juan54 on 2015-12-10
[COLOR=#000000][FONT=verdana]Hello guys![/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I'm trying to copy data from a failing 3TB seagate drive (yes one of those defective seagate drives), using the following comand from a rescue disk:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]sudo ddrescue -v -r 3 /dev/sda /dev/sdb logfile[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]1: Where is the logfile being created / stored ? ( i didn't specify a 3rd drive as destination)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2: If I were to stop, how could I resume ? I actually had to add --force to the beginning of the command in order to proceed[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]3:I see a line where it says that 1834 GB have been rescued[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]then a 2nd line that says 1958 GB have been rescued (is that the 2nd pass)[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]4: What happens if I stop this right now? will I have access to what has been rescued ?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Or will I just lose everything[/FONT][/COLOR]



[COLOR=#000000][FONT=verdana]Thanks![/FONT][/COLOR]

---

### Post by sudodus on 2015-12-10
Welcome to the Ubuntu Forums :-)

> **juan54 said:**
> [COLOR=#000000][FONT=verdana]Hello guys![/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I'm trying to copy data from a failing 3TB seagate drive (yes one of those defective seagate drives), using the following comand from a rescue disk:[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]sudo ddrescue -v -r 3 /dev/sda /dev/sdb logfile[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]1: Where is the logfile being created / stored ? ( i didn't specify a 3rd drive as destination)[/FONT][/COLOR]

In the local directory, where you are running the command (in the terminal window). Beware, if you are running a live session, you must save the logfile to some place, where is survives a reboot. You can do that when ddrescue has finished. Simply copy the logfile for example to a pendrive or other media.
> 
[COLOR=#000000][FONT=verdana]2: If I were to stop, how could I resume ? I actually had to add --force to the beginning of the command in order to proceed[/FONT][/COLOR]

I'm not sure, but I think what is documented in the logfile will be saved, so that you need not re-do it.
> 
[COLOR=#000000][FONT=verdana]3:I see a line where it says that 1834 GB have been rescued[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]then a 2nd line that says 1958 GB have been rescued (is that the 2nd pass)[/FONT][/COLOR]

I think the latter number is the current value.
> 
[COLOR=#000000][FONT=verdana]4: What happens if I stop this right now? will I have access to what has been rescued ?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Or will I just lose everything[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thanks![/FONT][/COLOR]

Try to have patience and let ddresue finish its work. 1958 GB is about 2/3 of the 3 TB drive :-)

-o-

Some parts might be slower to clone, if they are almost failing and therefore difficult to read (so that many attempts are necessary). But a crude estimate is to consider 2/3 of the work done.

---

### Post by juan54 on 2015-12-10
Thank you for taking the time to reply
I'm happy over 2TB's have been recovered, but it appears that this is it for the drive
Since yesterday, only about 40GB have been recovered and at this rate, it will be a couple of weeks :(
Problem is, I'm afraid that stopping the drive right now will not save what's been rescued so far :(

---

### Post by sudodus on 2015-12-11
As I wrote before: I'm not sure, but I think what is documented in the logfile will be saved, so that you need not re-do it. That amount of data is already cloned to the target drive. I don't know which part of the drive that is bad and difficult (impossible?) to read. If some early part is bad, the partition table and or the file system infrastructure is bad, but at least all the 2 TB data that are cloned should be available for PhotoRec to recover. And with some luck you might be able to repair the partition table and file system.

---

