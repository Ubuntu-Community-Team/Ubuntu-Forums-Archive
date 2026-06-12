---
title: "Error while copying from usb flash drive"
date: 2014-04-20
forum: General Help
---

### Post by babakflame on 2014-04-20
Dear Buddies

I have got a problem with my flash drive. This usb flash drive is scanned by Kaspersky antivirus and no virus detected. Additionally I have formatted this flash drive. Unfortunately, I have faced a problem with copying files with flashdrive. Any time I try to copy files into or from this flash drive, I confront this error:


```


There was an error copying the file into /media/Local Disk/Film/Four Brothers (2005) [1080p].

[COLOR=#ff0000]Error splicing file: Input/output error[/COLOR]


```

Would somebody PLZ hint me how can I solve this problem?

  Regards
   Bobi

---

### Post by llamabr on 2014-04-20
Are you using ext4?  Try having file names with no spaces.  You should do this generally anyway.  So:

```
mv four\ brothers four_brothers
```

and try again

---

### Post by babakflame on 2014-04-20
Hi llamber

Would you PLZ hint me what is **ext4?**

I reformmated the usb flash drive (deleted every thing) and will take into account your advice (omitting space between words)

I tried to copy another file with no spaces in its name. **However the problem still exists**.:frown::frown::frown::frown::redface::redface::redface::-\"


    Regards
      Bobi

---

### Post by llamabr on 2014-04-20
If the problem still exists, you should copy/paste your input, and then the output, to give us a better idea.

When you reformatted it, how did you do it?  What filesystem did you put on it?

[https://en.wikipedia.org/wiki/Ext4](https://en.wikipedia.org/wiki/Ext4)

---

### Post by babakflame on 2014-04-20
Greetings llamber

I was trying to copy a film which had 8 GB volume on my usb drive (16 GB Volume) from a 
PC that this error happened.  My ubuntu is 11.10 and the PC has this version of ubuntu too.

This is the error:

```
[COLOR=#FF0000][FONT=Ubuntu Mono]Error splicing file: Input/output error[/FONT][/COLOR]
``` 

I did not have this error on my usb flash drive beforehand. It is the first time that I see this error.

I lent my usb to a friend for some data transfer and after she gave it back to me, I faced with this error.:confused::frown::frown::-\":-\":-\" 

I used windows system for formating the usb. And the file system is NTFS. 

Any hint is warmly appreciated.

  Regards
   Bobi

---

### Post by babakflame on 2014-04-23
Dear Buddies

I reformatted the usb flash drive by Gparted in ubuntu and modified the format to ext4. However the problem of not copying an 8 GB film still occurs.](*,)](*,)](*,)](*,)](*,)](*,)](*,)

It is very confusing. I am going the delete the film on PC to solve the problem in this way and hope to not face this problem any more.

   Regards
     Bobi

---

