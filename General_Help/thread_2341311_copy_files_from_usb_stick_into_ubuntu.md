---
title: "copy files from usb stick into ubuntu"
date: 2016-10-26
forum: General Help
---

### Post by seaboss67 on 2016-10-26
Firstly, I am new to Ubuntu so please go easy. I have a lot of mp3 files on a 64gb usb stick. These files were put on the usb stick in windows 10. Can someone please tell me how to get these files (or some of them) into Ubuntu. I have googled this question but amazingly, I have found no answer which is suitable for a person who is brand new to Ubuntu. Thanks for any info.

---

### Post by gsahli on 2016-10-26
You haven't told us what you tried. Did you insert the stick and did it show up on the desktop or the file browser?
Then open it up and highlight files, right-click and copy, then paste where you want.

---

### Post by seaboss67 on 2016-10-27
Thank you for your reply gsahli. When I insert the usb stick. I get a notice on the desktop saying. Unable to mount UUI, followed by a lot of info that a newbie would not understand.

---

### Post by mastablasta on 2016-10-27
1. does the stick work well in windows?
2. what is the file format used (FAT32 or NTFS maybe?)

unable to mount usually means something is wrong with file system on the USB drive ,but it could also mean that stick is (for some reason) incompatible with linux.

---

### Post by coffeecat on 2016-10-27
> **seaboss67 said:**
> When I insert the usb stick. I get a notice on the desktop saying. Unable to mount UUI, followed by a lot of info that a newbie would not understand.

Ah, but many forum members would be able to understand. :wink:

Please take a screenshot of the error notice and post that so that we can see what the problem is. You can take a screenshot with the PrtScn key, one of these ways:

PrtScn = screenshot of whole desktop
PrtScn + Alt - screenshot of active window
PrtScn + Shift - screenshot of a selection. Press that key combination and a cropping tool in the shape of a cross replaces the cursor. Hold the left mouse button down and make your selection. A window pops up for you to save the selection as an image file.

You can attach your screenshot to your post either with the paperclip icon or the "manage attachments" button below the advanced reply editor.

One possible cause of your problem could be that the USB stick is formatted ExFAT, which can't be read out of the box in Ubuntu. If that's the case, the fix is straightforward - installing a couple of packages - but let's see what the error message says before making any assumptions.

---

### Post by lisati on 2016-10-27
Did you "safely remove" the stick from Windows?

---

### Post by Bucky Ball on 2016-10-27
UUI  = Univeral USB Installer???

> Unable to mount UUI

Do you mean UUID? I can find no info anywhere that matches the error 'unable to mount uui'. 

I know this sounds obvious, but you are absolutely positive this is the 64Gb stick with the MP3s on it? It would help a lot if you take a screenshot of that error window, paste it to a post here using 'Adv Reply' and attach with the paperclip icon in the taskbar there. Thanks.

---

### Post by SeijiSensei on 2016-10-27
> **lisati said:**
> Did you "safely remove" the stick from Windows?

I'm guessing this is the culprit, too.  If you reinsert the stick into the Windows machine, does it still work properly?  It's also possible that the filesystem on the stick is marked as faulty.  In Windows, go to Control Panel > Administrative Tools > Computer Management > Storage, and see if the partition on the USB stick appears.  If so, right-click on it, pick Properties, then go to the Tools tab.  You'll see a button that will check the drive for errors and fix them if possible.

(You might need to right click on Administrative Tools and choose "Run as Administrator".)

---

### Post by seaboss67 on 2016-10-27
[ATTACH=CONFIG]271813[/ATTACH]

---

### Post by Bucky Ball on 2016-10-27
Exactly what lisati and SeijiSensei suspected by the looks of it. Have you read their posts and taken their advice?

---

### Post by seaboss67 on 2016-10-27
If you give me a chance I'll explain. I've already told you I am new to ubuntu. The UUI can be ignored. For some reason, Windows 10 decided to call the USB stick - UUI.  I am now trying to load a screenshot into the forum. Thank you to those who have a little patience with newcomers.

---

### Post by Bucky Ball on 2016-10-27
What we're trying to advise is if you put this in a Windows machine, right click it and eject it safely, your problem will probably be fixed. Do that before you do anything else, including posting here, if you haven't already.

Let us know what happens when you put this in a Win machine. Does it show normally and can it be ejected without issue? After that, should work.

---

### Post by seaboss67 on 2016-10-27
Above is a screenshot of the problem. For some reason windows decided to call my usb stick UUI, so that bit can be ignored. Thank you to those who have a little patience with a newcomer.

---

### Post by seaboss67 on 2016-10-27
This usb stick has no errors and plays perfectly in windows 10 and is ejected correctly from windows 10.

---

### Post by Bucky Ball on 2016-10-27
Above where? Just post the screen shot in the next post and please do NOT post backwards. It is totally confusing. Keep it chronological please. :)

Ejected correctly from Windows. Great. Does it now work in Ubuntu??? If you get an error, is it the same? Please include all info you can think of in one post next in line, not back, please.

---

### Post by coffeecat on 2016-10-28
@seaboss67, thank you for posting the screenshot in your post #9. It appears to be telling you what I suspected and mentioned in post #5, that the stick is formatted ExFAT, which cannot be read out of the box in Ubuntu. The last part of the error message in your screenshot says, "unknown filesystem type 'exfat'. I have no idea why no one else commenting in this thread has not noticed that. 

You need to install the packages exfat-fuse and exfat-utils. Normally I would suggest using Software Centre for newcomers, but in my 16.04 installation Software Centre is resolutely refusing to show me those two packages. SC appears to be a tad flaky. So I suggest you use a couple of simple terminal commands instead. Open a terminal with ctrl-alt-t and run these two commands exactly as I've typed them:

```
sudo apt-get update
sudo apt-get install exfat-utils exfat-fuse
```

(I'm suggesting you use apt-get rather than the newer apt because we haven't established which version of Ubuntu you are using. It probably won't matter, but for the record please tell us: 14.04, 16.04, 16.10 or something else? )

After the first command, the terminal will prompt you for your password. This is your login password - you must be logged in with the first created account which is an administrator account. As you type it in, it is not echoed to the screen - that is, nothing appears to be happening., Don't worry - it is going in. Just continue typing your password and then press enter. The system will allow you elevated privileges for a few minutes so it will run the second command without a password prompt.

Once those two packages have been installed, try your 64GB stick again and let us know what happens.

I have to say that I have never used ExFAT myself, but I'm 99% sure that those two packages will fix the problem, **if** the only problem is that your system can't read ExFAT. If not, we need to hear from someone with experience of ExFAT in Ubuntu.

---

### Post by seaboss67 on 2016-10-28
Thank you coffeecat for your helpful attitude. You have given me details that I can understand and act on. In the next day or so I will do what you say. Of course, it was never my intention to post in the wrong order. PS - I'm using 16.04

---

### Post by seaboss67 on 2016-10-28
Thank you coffeecat My usb stick is now downloading into ubuntu and although the laptop is fairly old and slow, the download is fast, probably faster than windows. Your help is much appreciated. It looks as if my old, spare laptop will be fine for ubuntu. I will now persevere with this operating system because I want to see if Audacity will run  okay on it. Of course, I will now have to learn more ubuntu.

---

### Post by Bucky Ball on 2016-10-28
Audacity should run faultlessly on it. It is in the Ubuntu repositories. When you've installed, simply go to Software Centre and install it. Done. Been using it in Ubuntu for years. It's an open-source, cross-platform app. :)

(The caveat to this is while Audacity will work fine with Ubuntu, depending on what you are doing with it, your hardware may droop a little if you're going for heavy manipulations. See how far you can push it before the machine sweats. :))

---

### Post by coffeecat on 2016-10-29
> **seaboss67 said:**
> Thank you coffeecat My usb stick is now downloading into ubuntu and although the laptop is fairly old and slow, the download is fast, probably faster than windows. Your help is much appreciated. It looks as if my old, spare laptop will be fine for ubuntu. I will now persevere with this operating system because I want to see if Audacity will run  okay on it. Of course, I will now have to learn more ubuntu.

I'm glad to hear that worked. In fact, out of curiosity, I formatted a 32GB flash drive with exFAT in Windows 10 and then plugged it into Ubuntu 16.04 and saw the same "unable to mount" message window as you. Resolved, of course, when I installed the two exfat packages.

Good luck with your further adventures with Ubuntu. If you need help with Audacity, do please start a new thread - rule of thumb, one thread per problem. Or any other problem you want help with. Members here are always glad to help.

Happy Ubuntu-ing!

---

### Post by seaboss67 on 2016-10-29
Thanks to all.

---

