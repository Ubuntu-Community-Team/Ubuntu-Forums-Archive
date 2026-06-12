---
title: "Install Error"
date: 2006-12-12
forum: General Help
---

### Post by diezora on 2006-12-12
](*,) i put v6.10 on... and it wouldn't show disks... as posted earlier...

now i've tried to put dappy drake on... and it won't create a file system?? stops at 15% install...
what am i doing wrong?

---

### Post by Sef on 2006-12-12
1) What are your computer specs?

2) Did you md5sum the downloads?

3) Did you burn the iso at 4x or less?

4) If using the Live CD, did you try the alternate cd?

5) If you have the Live CD, is there another computer you can check it on?

---

### Post by diezora on 2006-12-12
okay... got it to install... that's all good. thank god for fiddling. :p 

now... er... it recognises my 300gb drive... but it won't let me access it... saying i have unsufficient privileges... and that it's owned by root... now, i tried logging on as root... but sorta guessed that wouldn't work... and i can't change the permissions to let me in.

HELPPP... i need my drivers and music. lol.

is it because it's NTFS??? please don't tell me i have to reformat. :(

jack

---

### Post by Sef on 2006-12-13
> is it because it's NTFS??? please don't tell me i have to reformat.

What file system did you use on the install?

Ubuntu's default is ext3.  If you used NTFS as your file system, then you will have to reformat the partition.  NTFS is a Microsoft proprietary file system.

---

### Post by diezora on 2006-12-13
so does that mean i can't access my music. :( coz it shows the contents but not anything else... i really dont want to lose it all... is there any way to get it all off???

oh bugger.

jack

---

### Post by namelessone on 2006-12-13
Are you saying that you didn't completely wipe your hd when you installed?

Did you just install ubuntu on a seperate partition?

If so, you can rescue your music files using CaptiveNTFS, either by installing it on ubuntu, or using a live cd something like [SystemRescueCD]("http://www.sysrescd.org").

---

### Post by diezora on 2006-12-13
i have 2 HD's it's installed on My C.. and all my stuff is on D.

---

### Post by namelessone on 2006-12-14
> i have 2 HD's it's installed on My C.. and all my stuff is on D.

Here's a proposed solution:

Use a program such as captiventfs to take all the files on hdb(D) and transfer them to hda(C).

Next, reformat hdb to ext3 format

Finally, move all your stuff back onto hdb.

NOTE: I'm not an expert on ntfs stuff. I only know what I've read, so there may be another program that would work just as well as captiventfs, or maybe you don't even need captiventfs.

---

### Post by diezora on 2006-12-15
er... yeah, my C is 20 and my D is 300... problem. lol.

120gb is used up on my D... that's a lot of cd's. 

suggestions?

---

### Post by Sef on 2006-12-15
Check out [Trinity Rescue Disk]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").  You can use that to pull your files off that partition.    Have you thought about making another partition and saving the files to there?

---

