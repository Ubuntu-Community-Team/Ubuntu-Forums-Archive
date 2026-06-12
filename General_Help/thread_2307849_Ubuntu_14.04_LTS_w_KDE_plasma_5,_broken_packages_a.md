---
title: "Ubuntu 14.04 LTS w/ KDE plasma 5, broken packages and blackscreen"
date: 2015-12-28
forum: General Help
---

### Post by Javaisnom on 2015-12-28
After completing a security update, I had to hard reboot due to my keyboard input and mouse button presses not doing anything.  Specs: Dell Inspiron 7548 (laptop) - Intel(r) core i7-5500U cpu 2.40 ghz, came with Win 8.1.

After the hard reboot, my PC blackscreens shortly after the Kubuntu splash screen pops up. 

I've checked other posts, and I can get as far as the TTY1-6 terminal screens (using 'nomodeset' and 'nosplash',/however, when I run 'sudo apt-get update', the output was 'W: failed to fetch (ppa links)'. If anyone could help, I would greatly appreciate it.

 - Java (my first posts after months of lurking and using Ubuntu'

**please excuse some noobiness**

---

### Post by Vladlenin5000 on 2015-12-28
Hi and welcome.

The 'failed to fetch...' regarding one or more PPAs doesn't stop you from doing the next steps:
```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post errors, if any. The not working PPAs can be tackled later.

---

### Post by Javaisnom on 2015-12-28
Vladlenin5000, 
 After running both commands, I got an 'E: Unmet dependencies. Try using -f.' Error.

I ran both with the -f flag, and got more 'Failed to fetch (link)' errors, what could I do from here?

Thanks for the help!
-Java

---

### Post by Vladlenin5000 on 2015-12-28
Run
```
sudo apt-get install -f
```

---

### Post by Javaisnom on 2015-12-28
After running that command, it outputted 

'Failed to fetch..." As well as ```
 unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
``` Do you know what else I could do now? Thanks for your time.

---

### Post by Vladlenin5000 on 2015-12-29
Please post the entire error messages. Use code tags or the Go Advanced button, click "#" and paste inside. Thank you.

---

### Post by Javaisnom on 2015-12-29
```
 E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.7+1ubuntu8.1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.7+1ubuntu8.1_amd64.deb). Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
```

I can't directly copy-paste the rest of the output, since the PC can't access any browsers/GUI's, sorry. 

-Java

---

### Post by ajgreeny on 2015-12-29
That .deb package is in the standard repos for trusty so you should have no problem finding and downloading it.

You could perhaps try a different server for your updates and upgrades to see if the US archive site is down at the moment, or otherwise just wait for a few days or hours and try again.

---

### Post by Javaisnom on 2015-12-30
Sorry for the late reply, but how would I go about changing the server?

---

### Post by claracc on 2015-12-30
You go to software updates, then click on settings button, in the windows appearing, select ubuntu software tab (see attched image), and there you can select what server to download the software and updates.

---

### Post by Javaisnom on 2015-12-30
Claracc, I can't access my desktop at all, TTY7 lacks any graphics, and is just a blackscreen. This is the primary issue.

---

### Post by claracc on 2015-12-30
Perhaps you have a malformed sources.list file.

Could you post, between code tags, your /etc/apt/sources.list file ?

Sorry, I didn't take into account you didn't have a gui

---

### Post by Javaisnom on 2015-12-30
Claracc, I apologize for my noobiness, but by code tags do you mean the commented areas after sharps/hash's??

Edit:: I may not have made the lack of a GUI clear in earlier posts, my bad. Thank you for your help, though. 

Also, I've fixed the sudo apt-get update issue, and can now access the internet on my PC.

---

### Post by claracc on 2015-12-30
Please see: [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by Javaisnom on 2015-12-30
Thank you, Claracc, checking the post now. :)

Edit: One second please, painstakingly writing it on my phone :P

---

### Post by claracc on 2015-12-30
Glad you got fixed your problem with updates. Any other problem remaining?

Can you now access to the gui too?.

---

### Post by Javaisnom on 2015-12-30
Claracc, I still cannot access my GUI, is there a quicker way to get the text on my phone? I'm stuck with just that right now, as I lack a GUI and don't have a CLI browser.

---

### Post by claracc on 2015-12-30
I have found this guide: [https://journalxtra.com/es/linux/desktop-recovery/the-definitive-guide-to-getting-your-linux-desktop-back/](https://journalxtra.com/es/linux/desktop-recovery/the-definitive-guide-to-getting-your-linux-desktop-back/), perhaps you can read it in your phone and try some of the fixes.

---

### Post by Javaisnom on 2015-12-30
Thank you for the link, Claracc, I'm checking it out now. :D

---

### Post by Javaisnom on 2015-12-30
Okay, after running ```
 egrep '\(EE\)|\(WW\)' /var/log/Xorg.0* | less 
```
 , the first part of the output reads

 ```
 /var/log/Xorg.0.log: [ 75756.129] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.]

``` 

along with a few other WW tagged lines relating to nonexistent DPI directories, in /usr/share/X11/.  Is this of any particular importance/urgently needed fix?

---

### Post by Javaisnom on 2015-12-30
Fixed it!
 Thank you, Vladlenin5000, ajgreeny, and Claracc for your time and assistance!

[https://bbs.archlinux.org/viewtopic.php?id=173808](https://bbs.archlinux.org/viewtopic.php?id=173808)

After running the command in maxarsys response, ```
 sudo rm /dev/rfkill 
```


, I was able to boot into my desktop normally. Thank you all for helping out with my issue, as well as making my first post on Ubuntu Forums a helpful one!

 -Java

---

### Post by claracc on 2015-12-30
You are very welcome. Glad you fixed it.

---

### Post by Javaisnom on 2015-12-31
*** After rebooting a second time after "fixing" my PC, I yet again boot into a black screen immediately after the splash. 

Since the first post, I installed XFCE and was yet again rebooting to apply Ubuntu security updates. I'm still able to access the internet in the tty1-6 terminals, but I lack a TTY7 GUI as was the issue before. 

I'm hoping for more replies on this thread, although I'll post another if I can't find a solution that will remain after a reboot. 

-Java

***

Edit: I also added 2 commands to my bashrc file to launch on startup, 
```

cowsay | fortune #or fortune | cowsay
Archey 
```

If that information helps.

---

