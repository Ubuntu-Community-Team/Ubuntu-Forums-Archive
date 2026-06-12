---
title: "fsck dies with error code 1"
date: 2007-05-01
forum: General Help
---

### Post by ShirishAg75 on 2007-05-01
Hi all,
    I have consistently had fsck die on me with error status 1. This has been going for the past few days. So today i looked up it up finally & came up with the following explanation :-

[http://adminschoice.com/docs/fsck.htm](http://adminschoice.com/docs/fsck.htm)

> **[FONT=Times New Roman][SIZE=4]Error messages & Corrective action :[/SIZE][/FONT]**
 **[FONT=Times New Roman]1.Corrupted superblock[/FONT]**[FONT=Times New Roman] - fsck fails to run [/FONT]
 [FONT=Times New Roman]If the superblock is corrupted the file system still can be repaired using alternate superblock which are formed while making new file system .[/FONT]
 [FONT=Times New Roman]the first alternate superblock number is 32 and others superblock numbers can be found using the following command :[/FONT]
 **[FONT=Times New Roman]newfs -N /dev/rdsk/c0t0d0s6[/FONT]**
 [FONT=Times New Roman]for example to run fsck using first alternate superblock following command is used [/FONT]
 **[FONT=Times New Roman]fsck -F ufs -o b=32 /dev/rdsk/c0t0d0s6[/FONT]**


  Now this one doesn't look easy to fix. I do know I would have to use the Live CD to boot go to the command prompt somehow, somehow mount the hdd do the above comamnd/s . But I am stumped how to do the same? I looked both at W.U.C as well as H.U.C. but didn't come any wiser. Can anybody help me fix this issue, thanx in advance.

---

### Post by psusi on 2007-05-01
Could you be more specific?  What is the fsck command you are trying to run, and what exactly does it say?  The documentation you found is for solaris, not linux.

---

### Post by ShirishAg75 on 2007-05-01
fsck as in file-system consistency check. I got that link from [http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck) 

 I'm running ubuntu 7.04 . I have 2 partitions a / & /home (both are primary partitions) , after checking the file-system every time it says fsck died with error status 1. This is fsck 1.49 version. I wouldn't want my filesytem to fail at any point in time. Don't know whether its a bug or is my system has some issue which needs to be fixed? 
        If it needs to be fixed or to be run from the Live CD to make sure what the issue is then how do I go about doing that? What procedure should I do so that the correct partitions are identifed & checked. (I have NTFS partitions also). 

Thanx in advance. Cheers !

---

### Post by ShirishAg75 on 2007-05-02
The actual scenario which happens is :-

[FONT=Tahoma]dev/sda10 has gone **49710 days** without being checked,check forced

and then [/FONT][FONT=Tahoma]fsck exited with error status 1 [/FONT]

---

### Post by psusi on 2007-05-02
Sounds like your sda10 partition is fubar.  Why do you have so many partitions anyhow?  Try to manually fsck it:

sudo fsck -f /dev/sda10

---

### Post by ShirishAg75 on 2007-05-04
its actually sdb1 , sorry that was another partition. But this partition is / how can I do fsck to a mounted partition? and what do u mean by fubar?

---

### Post by psusi on 2007-05-04
Boot from the livecd and fsck it from there.  

[http://en.wikipedia.org/wiki/Fubar](http://en.wikipedia.org/wiki/Fubar)

---

### Post by ShirishAg75 on 2007-05-05
> **psusi said:**
> Boot from the livecd and fsck it from there.  

[http://en.wikipedia.org/wiki/Fubar](http://en.wikipedia.org/wiki/Fubar)

ok, I surrender ;)

---

### Post by niceguy123 on 2008-01-06
When I try turning on the the computer instead of the Ubuntu screen I get a linux run of script that basically say the fsck in not functioning and that I must run it manually. 

What comand should I write inorder to get past this and back to good old Ubuntu.

Thanks

---

