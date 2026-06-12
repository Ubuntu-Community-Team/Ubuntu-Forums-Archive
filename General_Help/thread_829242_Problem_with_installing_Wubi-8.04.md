---
title: "Problem with installing Wubi-8.04"
date: 2008-06-14
forum: General Help
---

### Post by ashishbond on 2008-06-14
Hi

I have IBM laptop with Intel centrino. I have downloaded "ubuntu-8.04-desktop-i386.iso" to install Ubuntu but when i wrote it on cd and ran it a got an error of "cd not accessible". 

I went to the forum and found the way to resolve it. I downloaded the Wubi-8.04.exe and put the wubi and iso in the same folder. Now whenever i try to run it i get trojan warning from AVG antivirus: **Trojan Horse Agent.VJL**. Secondly it doesn't link to the iso file and try to download the data from the net. but again give the following error and stop:
**The download was interrupted with the error:**
:mad:

Please suggest what to do about it for error free installation.

---

### Post by ashishbond on 2008-06-14
For your info i am using windows XP sp3 and have AVG 8.0.100.

---

### Post by ago on 2008-06-16
There have been reports of antivirus comany marking wubi as suspect all have been confirmed to be false alarms. As for the download it might have been that the server was down when you tried, just try again. Otherwise download the iso manually and place it in the same folder as wubi.exe

---

### Post by ashishbond on 2008-06-19
Thank you for your reply AGO but i don't understand what would an AV company has a problem in this??? They can generate revenues by making an AV for linux too.

I have downloaded the iso as i mentioned in my main thread. But still the Wubi file starts downloading and shows me the error. It is not able to catch the iso file nor it is able to download. I am in a difficult glitch.
:confused:

---

### Post by ago on 2008-06-19
That is because the ISO is wrong or corrupt, if you look into the wubi log in your user temp folder there will be an explanation

---

### Post by ashishbond on 2008-07-05
instead of downloadin again i installed it on a seperate partition along with xp. the other reason of doing it is i want the hibernation facility too on my comp.
thanks for your help.

---

### Post by Geckosquad on 2008-07-06
I am having a similar problem on Windows XP SP3, with Wubi 8.04.1.  I get the same "The download was interrupted with the error:" message.

I think it has something to do with the md5 sums - I checked the log file as ago suggested, and I attached the relevant snippet.

I got the same errors with Ubuntu and Xubuntu (I'm currently downloading the Xubuntu ISO separately to see if that works).  Any thoughts / suggestions?  Is this a server issue, or is it something else?

---

### Post by ago on 2008-07-06
Yes the problem is that [http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/MD5SUMS-metalink](http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/MD5SUMS-metalink) does not mention any desktop image file.

I will notify the ubuntu release manager to have it fixed.

As a workaround try to pre-download the DESKTOP ISO form [http://cdimages.ubuntu.com/xubuntu/releases/hardy/release](http://cdimages.ubuntu.com/xubuntu/releases/hardy/release) and place it in the same folder as wubi.exe then run wubi with --skipmd5check

---

### Post by ashishbond on 2008-07-06
how to skip the md5sum check. i don't see that option while installing wubi.

---

### Post by ago on 2008-07-06
run wubi from command line and append it to the command

---

### Post by Ljubo on 2008-07-06
I had an ISO file on my hard disk which I accidently found it (it was hidden file).
version 8.04

and no luck installing it.

in that ISO file was already a file wubi.exe.

So, I extracted that wubi.exe file and put it along the original ISO file, tried to start it... but dos shell window opens for a second, closes down and nothing happens.
When I tried to run it from a dos prompt window, message turns back `Program too big to fit in memory`.

I have a laptop FCS Intel Celeron with over 700mb of RAM.

Where am I doing wrong?

---

### Post by Ljubo on 2008-07-06
ok, I had a non functioning wubi file.
I have downloaded the coresponding one to the ISO file (dates criteria), have run it, virus...
disabled virus check...
it went on but with error message `The download was interrupted with the error:`.

thanks for any info

---

### Post by ago on 2008-07-06
you have to use wubi rev 501 with 8.04, rev 505 will not work (requires 8.04.1)

---

### Post by Geckosquad on 2008-07-07
I tried downloading the .iso separately and then using Wubi.  I didn't skip the md5 check, but it still installed correctly (I'm posting this from Xubuntu).  Thanks for all your help!

---

### Post by Ljubo on 2008-07-07
> **ago said:**
> you have to use wubi rev 501 with 8.04, rev 505 will not work (requires 8.04.1)

Yes, I did use rev 501, the problem is like the previos guy had... wubi doesn`t look for iso file on hard disk, it tries to download and unsuccessfully.

Please have a look at log files attached.

thanks...

---

### Post by catfished on 2008-07-07
This is really too bad. I was lured to the wubi site from a post on WHT and got really excited when I read things like: 
"**Wubi is Simple**
No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you." 
I've been playing around with this all morning and was just told about this forum on WHT. I guess I won't be installing Ubuntu anytime soon.:(

---

### Post by ago on 2008-07-07
can you post also the wubi.log please?

---

### Post by thomas576 on 2008-07-07
ok this isn't working im have same problems as guy above. ive tried manual download of iso several actually and several verson combo/disto.. here is log file

---

### Post by ago on 2008-07-07
The signature of the metalink MD%SUMS file cannot be verified for some reason, can you please attach a zipped /ubuntu/install dir?

---

### Post by catfished on 2008-07-15
Well, it turns out that the Wubi Installer does not support Windows ME, it supports Win 98, 2000, XP and Vista. It doesn't specifically say that on the Wubi download page so I had to dig around quite a bit on these forums before discovering that I'd been wasting my time. :mad:

I just tried the Wubi today on my XP laptop and it installed without a hitch. Now if I can figure out how to get my wireless internet connection working on it, I'll be all set.:popcorn:

---

### Post by Ljubo on 2008-07-18
Installation failed on Win XP s.p.2.

Please find in attachment installation logs.

Thank you!

---

### Post by temp1029 on 2008-07-29
Having the same problem here, anything on this?

---

### Post by ago on 2008-07-29
There seem to be disk read errors:

Jul 17 14:03:38 ubuntu kernel: [ 1150.456200] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0

Might be hardware related. Try first to detach any USB device, also do some HD testing.

---

### Post by Ljubo on 2008-07-29
It was HD problem.

After several tries, it went through the installation process completely.

---

