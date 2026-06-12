---
title: "Ubuntu 14.04 - No Sound - What files to delete for space?"
date: 2015-09-12
forum: General Help
---

### Post by dr13 on 2015-09-12
Hi Guys,

I have no sound on ubuntu 14.04.

Scrrenshot of messages attached.

My question is which files do I delete? Will this solve my no sound situation.

Thanking you in advance for your assistance.

---

### Post by mörgæs on 2015-09-12
```
sudo apt-get clean
sudo apt-get autoremove 

```are a good beginning.

Let's hope it's possible to save the system. A hard disk running full can make a lot of damage.

---

### Post by dr13 on 2015-09-12
Thanks for the response mörgæs.

I've tried your suggestion which has given me +500mb more free space but still no sound sir.

Anything else I can try?

---

### Post by mörgæs on 2015-09-12
Have you emptied the trash can?

Most of the space is used by your own files in /home according to the screen shot. I guess you are better than me to know which to delete.

---

### Post by dr13 on 2015-09-13
Trash is empty

Not sure which to delete mörgæs.

---

### Post by v3.xx on 2015-09-13
This command will list all files over 500M, may help figure this out.

```
sudo find / -name '*' -size +500M
```

---

### Post by dr13 on 2015-09-14
Hi  v3.xx

Thanks for replying.

Ran the command and comes up with "no such file or directory"

---

### Post by v3.xx on 2015-09-14
I believe that there was more output than that; those lines probably started with /proc.

At the bottom of that output it should of list any other files.  So lets go smaller and see what pops up.

```
sudo find / -name '*' -size +50M
```

Please post the output using code tags.

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by dr13 on 2015-09-19
Hi  v3.xx

I moved and deleted all video files from pc and sound is back:D

Thanks for all the assistance guys.

---

### Post by dr13 on 2015-09-19
Ok guys it can't be a space issue coz I moved all video files and audio was back.
Put the pc off and after a while on again and no sound again.
what should i check for now.

I have not added any files so space shouldn't be an issue

---

### Post by mörgæs on 2015-09-21
Have you tried the [Sound Troubleshooting Guide]("http://ubuntuforums.org/showthread.php?t=1885240")?

---

