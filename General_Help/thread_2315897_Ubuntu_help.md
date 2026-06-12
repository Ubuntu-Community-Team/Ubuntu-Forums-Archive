---
title: "Ubuntu help"
date: 2016-03-03
forum: General Help
---

### Post by Firefox264 on 2016-03-03
Hi Guys, 
Can anyone please tell me what this is all about in the image below? 

My system booted fine after having to sysrq... I'm just worried whether it did any harm at all? 
[URL="http://www.pchelpforum.com/attachment.php?attachmentid=60323&stc=1"]
[/URL][IMG]http://i.imgur.com/Va4hkk8.png[/IMG]

---

### Post by grahammechanical on 2016-03-03
From your thread title I thought that you had a question about the Ubuntu Help utility. The image is too small for me to see the words.

I have found that Linux is very crash resistant. There have been times when I have had to press the hardware power button or reset button and Linux/Ubuntu has come back to usefulness without any damage.

My advice would be to shut down & restart a couple of times to establish good loading & shut down profiles. You might find that those messages disappear.

Regards.

---

### Post by oldos2er on 2016-03-03
Please give some info such as Ubuntu version, hardware specs, etc. When was your screenshot taken, on reboot, or when you entered 'sysrq'?

---

### Post by Firefox264 on 2016-03-03
Thank you for your reply. 

If you right click on the image and open it on a new tab. You can zoom in on the image and that should give you a clear image or much larger image. 

I did shutdown and restart using 'sysrq' and the system and files seems to be untouched but I'm just curious as this is the first time I'm seeing this message for the long years I have been using Ubuntu. 

Just curious that's all.

---

### Post by Firefox264 on 2016-03-04
> **oldos2er said:**
> Please give some info such as Ubuntu version, hardware specs, etc. When was your screenshot taken, on reboot, or when you entered 'sysrq'?

Thank you for your reply and the specs are,

Ubuntu 14.04 LTS
i5-4690 @ 3.5GHz
Mobo - Z97M Pro4
RAM 12GB (had 8GB in my system but got a 4GB for a really good price and now it's 12GB)**[B]**[/B]

---

### Post by Bucky Ball on 2016-03-04
> **Firefox264 said:**
> If you right click on the image and open it on a new tab.

I don't have that option. For future reference, attach pics by Go Adv or Adv Reply and using the paperclip icon rather than inserting them into the body of your post.

---

### Post by deadflowr on 2016-03-04
From the fuzziness of the image it looks like a hard drive disk error output of some sort.
Perhaps a quick fsck can clear that.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

you might also consider looking at the Hard Drives SMART status:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

For the record, Ubuntu comes with a somewhat variant of smartmontools installed in the **Disks** program.
Simply open that program and in the left pane area highlight the hard drive, and in the main window click on the cog icon in the top right corner area and select the 
*SMART Data and Self-Tests* option to view the disks SMART stats.

---

### Post by Firefox264 on 2016-03-04
> **Bucky Ball said:**
> I don't have that option. For future reference, attach pics by Go Adv or Adv Reply and using the paperclip icon rather than inserting them into the body of your post.

What do you mean "I don't have that option" ? 

Anyway the only reason the image is small because I uploaded it to imgur.com and then shared the link here. It somehow appears smaller but not hard to see...

---

### Post by Bucky Ball on 2016-03-04
> **Firefox264 said:**
> What do you mean "I don't have that option" ? 

I clearly state what option in my post. Right click and open in a new tab. Bottom line is that the majority of us have little idea what is in your screenshot because we can't see it. 

Anyway, let's get back on topic and get on with it, thanks. :)

---

### Post by Firefox264 on 2016-03-04
> **deadflowr said:**
> From the fuzziness of the image it looks like a hard drive disk error output of some sort.
Perhaps a quick fsck can clear that.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

you might also consider looking at the Hard Drives SMART status:
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

For the record, Ubuntu comes with a somewhat variant of smartmontools installed in the Disks program.
Simply open that program and in the left pane area highlight the hard drive, and in the main window click on the cog icon in the top right corner area and select the 
SMART Data and Self-Tests option to view the disks SMART stats.

The hard drives are all okay. No errors on them at all. 

Here is what happened, 

The files and folders got write protected and the system was trying writeback to those locations (refer screenshot, err -30)

Anyway what happened was, I was trying out an Ubuntu beta release on my virtual box vm and after the installtion process it freezed before it could restart. So I used systemrq without really thinking that it was the vm and it somehow might have applied it to my system instead of the vm. 

Anyway I noticed that my .vdi file was write protected on my system, and that's when I closed virtual box and logged out of the system. 

Then it got to the screen on the screenshot. 

The good thing is that after I shut-down the system and then restarted it back, the files and everything else was back to normal. 

The only difference I could notice was that my system clock settings and system clock wasn't showing on my desktop. This was also fixed after a restart.

Also I went through all of my files and folders but nothing was luckily deleted or harmed. 

There was only this one folder that was locked (had a lock sign on it). 

I'm just curious to know whether this did any harm to the files or anything else and what caused it?

---

### Post by Firefox264 on 2016-03-04
> **Bucky Ball said:**
> I clearly state what option in my post. Right click and open in a new tab. Bottom line is that the majority of us have little idea what is in your screenshot because we can't see it. 

Anyway, let's get back on topic and get on with it, thanks. :)

Well I asked you because you weren't clear. I have no problem attaching the image rather than using a link but the reason I said to "open the image in a new tab" was because then you have the option to zoom in on the image. 

I can clearly see the image and the users who replied can see the image, otherwise they wouldn't reply :D

---

