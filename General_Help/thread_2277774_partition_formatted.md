---
title: "partition formatted"
date: 2015-05-11
forum: General Help
---

### Post by amr-elfiky on 2015-05-11
[TABLE]
[TR]
[TD="class: votecell"]         0         down vote          [favorite]("http://askubuntu.com/questions/622322/partition-formatted?noredirect=1#")            
              [/TD]
              [TD="class: postcell"]        a couple of days ago i was downloading a torrent overnight on   windows  and the following day when i opened the laptop, bittorrent   showed that it was working for only 3 hours though i left it for more  than 9 hours .i restarted to  ubuntu  and i couldn't open the D drive  and it told me to run  "chkdsk/f"  on windows .i thought it was this  thing that happens when windows 8 hibernates and you have to disable  this feature to open the drives on ubuntu .i thought it might happed  with windows 7 too .so i typed  "chkdsk/f"  on run on windows .i didn't  see a change .i don't use windows a lot .but when i went to "my computer  " the D drive was  formatted  .i went back to ubuntu and it was really  formatted .i googled a little and knew that "chkdsk/f"  has nothing to  do with formating drives .and some people said there was something wrong  with  "mbr". i tried using "boot-repair" to repair my  "mbr"  but the option is not  available there .my guess is that the data is still there but both  ubuntu and windows can't read it .i lost more that 250 GB of data .i  don't want to use data recovery software yet .can anbody please help me ?
     

[/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2015-05-11
Post link to summary report from Boot-Repair, so we can see details.

---

### Post by amr-elfiky on 2015-05-11
i'm so sorry , but how can i do that ?

---

### Post by amr-elfiky on 2015-05-11
is this the one ?
[http://paste.ubuntu.com/11080684/](http://paste.ubuntu.com/11080684/)

---

### Post by oldfred on 2015-05-11
Is sda3 your d: "drive"?
It shows as NTFS, did the chkdsk work on it?

 Chkdsk
[http://technet.microsoft.com/en-us/library/cc730714.aspx](http://technet.microsoft.com/en-us/library/cc730714.aspx)

chkdsk d: /b
You may want to use /b instead of /f and often have to rerun it until no errors shown.

---

### Post by amr-elfiky on 2015-05-11
yes , sda3 is indeed my d drive .
well, there is a file named "bootsqm.dat" in there and some people in windows forums said whenever there's this file ,a chkdsk must have worked .
i did use "chkdsk/f" on the run menu on windows ,but i don't think anything happened and i didn't type d: in the command .
i am googling how to run chkdsk right now :p

---

### Post by amr-elfiky on 2015-05-11
yes , sda3 is indeed my d drive .
well, there is a file named "bootsqm.dat" in there and some people in windows forums said whenever there's this file ,a chkdsk must have worked .
i did use "chkdsk/f" on the run menu on windows ,but i don't think anything happened and i didn't type d: in the command .
i am googling how to run chkdsk right now :p

---

### Post by amr-elfiky on 2015-05-11
i just remembered ,windows did run chkdsk when i started it before i found out that the d drive was formatted .at the time i thought it was normal.

---

### Post by Mark Phelps on 2015-05-11
Your best bet, to recover lost files and folders, is to use Windows data recovery apps.  

Do the following:
1) Boot into Windows
2) Download and install "recuva" This is a free Windows data recovery app
3) Run recuva and select Partition Recovery
4) If that works, then you should check the partition to see if the files and folders you need are OK
5) If that doesn't work, then try Lost File Recovery.
6) If that works, then you should check to see ifn the files and folders you need are OK
7) If that doesn't work, then download and install RecoverMyFiles.  This is free to download and try out.
8) Run that in deepest discovery mode -- probably overnight
9) If that finds the files and folders you want, you will need to go online and purchase a license to do the actual data recovery.

Note that you can NOT recover files/folders to the same drive that is being examined, so you will need an external drive or a USB stick to hold the recovered files/folders.
Good Luck

---

### Post by amr-elfiky on 2015-05-11
thanks,**Mar****k **for your great and well organized answer ,but i don't want to use data recovery apps just yet .i feel like there is  an easy way out there to restore the partition as a whole .if i can't find this easy method ,i'll have to use recuva and recover my files .[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=311399")

---

### Post by amr-elfiky on 2015-05-17
guys , any help ?

---

### Post by oldfred on 2015-05-17
Did you run chkdsk on d: drive?
If you do not specify it just runs on c:. And you may have to run multiple times as it only fixes one issue per pass.

---

### Post by amr-elfiky on 2015-05-19
i ran chkdsk d: /B   ... it found nothing though..

---

### Post by oldfred on 2015-05-19
Is /B the same as /b as shown in the Microsoft instructions?

Did it show it ran?

---

### Post by amr-elfiky on 2015-05-21
i was a little confused about this too .i googled it and [COLOR=#000000] /B mostly showed up .yes ,it did run .it took like 45 minutes .found nothing though .[/COLOR]

---

### Post by sudodus on 2015-05-21
The command line syntax of DOS and Windows does not make a difference between upper case and lower case, so /B and /b are interpreted in the same way. The only exception that I know is within text strings (for obvious reasons).

---

