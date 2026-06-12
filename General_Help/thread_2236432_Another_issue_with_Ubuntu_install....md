---
title: "Another issue with Ubuntu install..."
date: 2014-07-26
forum: General Help
---

### Post by mark155 on 2014-07-26
I finally got the computer to boot from the DVD drive after making some changes to BIOS. After clicking install from the menu everything went well until the very last of the installation when I got a error message that said "An Error Occurred 'None Type' object has no attribute". I've downloaded the file from the Ubuntu web site and from a torrent. I get the same error message with both when trying to install. I ran a MD5 checksum on both files. The MD5 calculated the same value for both downloads, and neither matches what is posted on the Ubuntu web site.

---

### Post by renanrischiotto1 on 2014-07-26
Hi!


The checksum is correct? 


Your DVD media is of good quality? 


If possible, try to install from a Pen Drive.


I think it would be interesting too check the integrity of the copy after recording in DVD or Pen Drive.


To the DVD, you can follow these instructions:


[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


For Pen Drive I do not know a command to do this, but the UNetbootin program has an option to check for disk errors (or on Pen Drive :))


Hugs!

---

### Post by slooksterpsv on 2014-07-26
He stated the MD5 was good. Just want to mention that.

Now couple of questions - what kind of a machine is it? are you installing 32-bit or 64-bit? The md5 sum will be different depending on 32-bit or 64-bit; so did you check both?

**dccff28314d9ae4ed262cfc6f35e5153 *ubuntu-14.04-desktop-amd64.iso** 14.04 (Not .1) 64-bit
**c4d4d037d7d0a05e8f526d18aa25fb5e *ubuntu-14.04-desktop-i386.iso** 14.04 (not .1) 32-bit
**119cb63b48c9a18f31f417f09655efbd *ubuntu-14.04.1-desktop-amd64.iso** 14.04.1 64-bit
**a4fc15313ef2a516bfbf83ce44281535 *ubuntu-14.04.1-desktop-i386.iso** 14.04.1 32-bit

---

### Post by renanrischiotto1 on 2014-07-26
> [COLOR=#000000]He stated the MD5 was good. Just want to mention that

[/COLOR]Sorry, is that I am Brazilian, do not dominate the English '-'

---

### Post by sandyd on 2014-07-26
Is there a word after "An Error Occurred 'None Type' object has no attribute"?
If so, we can identify the error.

edit:... and I read that again,
Try downloading via torrent, it will ensure that you have a good checksum.

---

### Post by linux_dream on 2014-07-26
> **slooksterpsv said:**
> He stated the MD5 was good. Just want to mention that.

Now couple of questions - what kind of a machine is it? are you installing 32-bit or 64-bit? The md5 sum will be different depending on 32-bit or 64-bit; so did you check both?

**dccff28314d9ae4ed262cfc6f35e5153 *ubuntu-14.04-desktop-amd64.iso** 14.04 (Not .1) 64-bit
**c4d4d037d7d0a05e8f526d18aa25fb5e *ubuntu-14.04-desktop-i386.iso** 14.04 (not .1) 32-bit
**119cb63b48c9a18f31f417f09655efbd *ubuntu-14.04.1-desktop-amd64.iso** 14.04.1 64-bit
**a4fc15313ef2a516bfbf83ce44281535 *ubuntu-14.04.1-desktop-i386.iso** 14.04.1 32-bit

I think you got it wrong, the md5sum does **not** match what is on Ubuntu's website. At least according to the words of the original poster. 
Nevertheless he should indeed make sure he's checked for both 32 and 64 bits, just in case.

---

### Post by yancek on 2014-07-27
> I ran a MD5 checksum on both files. The MD5 calculated the same value  for both downloads, and neither matches what is posted on the Ubuntu web  site. 		

You need to download again if the md5sum doesn't match.

---

### Post by mark155 on 2014-07-27
> **slooksterpsv said:**
> He stated the MD5 was good. Just want to mention that.

Now couple of questions - what kind of a machine is it? are you installing 32-bit or 64-bit? The md5 sum will be different depending on 32-bit or 64-bit; so did you check both?

**dccff28314d9ae4ed262cfc6f35e5153 *ubuntu-14.04-desktop-amd64.iso** 14.04 (Not .1) 64-bit
**c4d4d037d7d0a05e8f526d18aa25fb5e *ubuntu-14.04-desktop-i386.iso** 14.04 (not .1) 32-bit
**119cb63b48c9a18f31f417f09655efbd *ubuntu-14.04.1-desktop-amd64.iso** 14.04.1 64-bit
**a4fc15313ef2a516bfbf83ce44281535 *ubuntu-14.04.1-desktop-i386.iso** 14.04.1 32-bit


The third checksum that you posted does match. There was only one calculation on the Ubuntu site. However, I still get the above error message when trying to install Ubuntu software. Surely, there is a solution. Thanks.
[COLOR=#000000]119cb63b48c9a18f31f417f09655efbd[/COLOR]

---

### Post by mc4man on 2014-07-27
Maybe ck. the integrity of your burned dvd, various methods described here in "Check Cd" section 
(either ck. from boot screen or check directly
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mark155 on 2014-07-27
Here's the entire error message that I get. It pops up just before the end of the installation process: 'None Type' object has no attribute 'get info'. For more information, please log file: c:\users\mark\appdata\local\temp\wubi-14.04-rev286.log

To even get to the install prompt, I had to move the wubi.exe file from the DVD drive(where I burned the file to) to my C drive. I found that solution after several Google attempts. However, I get the above error message just before the file has completed installing.

---

### Post by sandyd on 2014-07-27
> **mark155 said:**
> Here's the entire error message that I get. It pops up just before the end of the installation process: 'None Type' object has no attribute 'get info'. For more information, please log file: c:\users\mark\appdata\local\temp\wubi-14.04-rev286.log

To even get to the install prompt, I had to move the wubi.exe file from the DVD drive(where I burned the file to) to my C drive. I found that solution after several Google attempts. However, I get the above error message just before the file has completed installing.

Dont use Wubi to install Ubuntu.

Boot from the DVD (You may have to change the computer's boot order), you should then see a screen asking you to set the language.
Set the language and then choose Install Ubuntu.

---

### Post by mark155 on 2014-07-27
> **sandyd said:**
> Dont use Wubi to install Ubuntu.

Boot from the DVD (You may have to change the computer's boot order), you should then see a screen asking you to set the language.
Set the language and then choose Install Ubuntu.

I've already tried that. I get a screen that comes up asking for several options. I chose install Ubuntu, and then the screen goes blank. I've tried this with burning the Ubuntu file to a DVD and USB Pendrive to a flash drive. Neither works.

---

### Post by mark155 on 2014-07-27
BTW, My setup is a Asus p8z77-v motherboard, Windows 7 Professional 64 bit, and a I-5 3570K processor with Intel 4000hd graphics. I have no dedicated graphics card. I've had this setup for 1.5 years and have had no problems installing programs before.

---

### Post by mark155 on 2014-07-27
I've pretty much exhausted all of my options of trying to install Ubuntu from either the DVD or flash. I've done all the BOIS tweaks and everything else that is recommend on this forum, and what I could find after 3 days of searching on Google. My last desperate question: Is there any way to manually install the Ubuntu file that I downloaded. If so, what are the recommendations as far as partitioning the disk etc. BTW, I also tried wubi.exe and got the error message mentioned above. Thanks.

---

### Post by CharlesA on 2014-07-27
> **mark155 said:**
> I've already tried that. I get a screen that comes up asking for several options. I chose install Ubuntu, and then the screen goes blank. I've tried this with burning the Ubuntu file to a DVD and USB Pendrive to a flash drive. Neither works.

Try adding nomodset to the list of options when you go to boot the Livecd.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

