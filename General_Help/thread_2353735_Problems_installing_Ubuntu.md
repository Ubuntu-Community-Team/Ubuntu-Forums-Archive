---
title: "Problems installing Ubuntu"
date: 2017-02-24
forum: General Help
---

### Post by A Traveller on 2017-02-24
Hi all.

Sorry the subject should read 'Problems booting Ubuntu'.

I recently tried to install ubuntu-16.04.1-desktop-amd64.iso but ran into all kinds of trouble. At first install, it seemed to load fine. At the next boot, I tried loading a video but it was very jittery and caused a mess of everything and the third boot, would only get past the grub screen and then nothing.

I have an nvidia card and for some reason, Ubuntu still hasn't been friendly with these, so I reformatted the whole hard drive and re-intalled Ubuntu. I left the option to install updates at the time of installation unchecked just in case it was something that was installed that caused the problem first time round, but still nothing! I have also tried editing the nomodeset thing which seems to have worked for a lot of users on the web but this didn't work either.

The MD5SUM and SHA256SUM match for the image on my hard drive, but the SHA256SUM does not match for the actual DVD. I haven't yet checked the MD5SUM for the actual DVD as it seems a longer, more complicated process. I followed the instructions found at the two links below.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)

The instructions for checking the SHA256SUM are simply 'sha256sum /dev/cdrom', but for MD5SUM, they say that it's not as simple as 'md5sum /dev/cdrom' because:-

"this will almost NEVER be the same hash as the iso image that was burned to the disk, because this command includes the empty space at the end of the disk, which changes the hash. So you must check only the part of the disk that was on the iso."

Are the instructions to check the SHA256 of the DVD correct? Is it simply 'sha256sum /dev/cdrom' or is it a longer process like it is with the MD5SUM?

Anyway, if the MD5SUM and SHA256SUM match for the image on my hard drive and I have re-installed Ubuntu and it's still isn't working, where would the problem lie? Do I need to burn a new DVD with the same image?

Any suggestions would be appreciated!

Thanks.

---

### Post by Impavidus on 2017-02-24
When you boot from your dvd, you should get a menu where you can choose "try before installing", "install ubuntu" and some other options. One of the options should be "check the disc for errors" (or something like that). Run that check.

---

### Post by A Traveller on 2017-02-26
Thanks for your reply, Impavidus.

I did as you suggested but there wasn't any option to check the disc for errors. The Desktop and everything worked fine in the try before installing mode. Does this narrow down what the problem could be at all?

Thanks.

Edit - Just found the following link. Didn't know that you had to hit Enter for newer Ubuntu versions. Will try that and post back.

---

### Post by A Traveller on 2017-02-26
Managed to do the check and the results were:-

Check finished: no errors found.

Have I done the SHA256SUM correctly?

Thanks.

---

### Post by mörgæs on 2017-02-26
> **A Traveller said:**
> 
I recently tried to install ubuntu-16.04.1-desktop-amd64.iso but ran into all kinds of trouble.

If you want the 16.04 family then installing 16.04.2 is a better idea. It contains all bug fixes which have been released for 16.04.1.

---

### Post by A Traveller on 2017-02-26
Hi morgaes (sorry for the incorrect characters in your name).

Thanks for your advice, which I have followed. Unfortunately, I am having the same problem.

I re-formatted the whole disk again and did a new clean install of 16.04.2, but the problem is exactly the same.

I am stuck on a screen which says New_Volume: Clean, 190224/1313760 files, 1164043/5253173 blocks.

I have tried searching for an answer and have looked at the suggestions at the two links below, but in both cases, it seems that the problem for those users is that it took a little longer than normal to get past that screen. My problem is that I'm stuck at that screen forever. On the 16.04.1 install, I left it for over an hour but still nothing happened.

[http://askubuntu.com/questions/761653/startup-problem-in-16-04?noredirect=1&lq=1](http://askubuntu.com/questions/761653/startup-problem-in-16-04?noredirect=1&lq=1)
[http://askubuntu.com/questions/383114/my-ubuntu-is-running-fsck-on-every-bootup](http://askubuntu.com/questions/383114/my-ubuntu-is-running-fsck-on-every-bootup)

Is there anything else I could try? I am confused about why it booted fine on the very first occasion and then would not boot at all even after a re-format and clean install!

---

### Post by mörgæs on 2017-02-27
On which hardware are you installing?

---

### Post by A Traveller on 2017-02-27
Desktop PC
GA-890GPA-UD3H Motherboard
4 x 2Gb G Skill RAM
NVIDIA GeForce GTX 460 Graphics Card
Old Seagate 30Gb hard disk

I have Ubuntu 10.04 and 12.04 installed on other hard drives and both are able to boot.

Thanks.

---

### Post by mörgæs on 2017-02-27
Have you tried installing from USB?

---

### Post by A Traveller on 2017-02-27
Thanks for the suggestion.

Yes, I tried that but it did not work. I cannot remember exactly what happened but it didn't boot at all. The only thing I was able to do was see the files on the USB drive in the file manager. I had to end up buying DVDs specially to install Ubuntu, which as you know, hasn't worked but at least I've gotten to the GRUB screen! I have been installing Ubuntu since 6.06 and have never come across anything like this before!

---

### Post by mörgæs on 2017-02-28
This is getting difficult... The [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by mörgæs on 2017-02-28
This is getting difficult... The [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by A Traveller on 2017-03-04
Thanks for the suggestion. Before trying that, I still wish to solve the problem with Ubuntu.

I am thinking it has something to do with graphics and NVIDIA. Which drivers does Ubuntu 16.04 install during the installation process for computers with an NVIDIA card?

---

### Post by mörgæs on 2017-03-04
By default it installs open source Nouveau drivers. Often there is an option to add closed-source Nvidia drivers during install but I don't know which version of them.

---

