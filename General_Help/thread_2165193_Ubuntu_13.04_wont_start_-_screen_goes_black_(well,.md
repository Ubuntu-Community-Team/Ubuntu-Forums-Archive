---
title: "Ubuntu 13.04 wont start - screen goes black (well, grey actually)"
date: 2013-08-03
forum: General Help
---

### Post by stefan_bahrens on 2013-08-03
Everything has been absolutely fine. Suddenly for no apparent reason Ubuntu 13.04 refuses to start. The laptop boots OK and everything works until the "Ubuntu" splash in the centre of the screen with the 5 dots under it. At this point I do not get the correct splash, it is very distorted and flashes up for a fraction of a second. The screen then goes to a kind of 70% grey and nothing happens. I cannot face the idea of reinstalling Ubuntu again as I have spent months getting all the applications working the way I want. Is there a way of getting into the laptop and fixing this? Thanks for any help.

---

### Post by stefan_bahrens on 2013-08-03
I used Ctrl-Alt-F1 to get a tty1 screen. This asked me for Login and Password. Remembering the Login was hard. Eventually I got it. Can I fix the problem from the ~$ prompt? Should I be following Option 2 here? [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) I really don't have a clue what I'm doing> Thanks for any help.

---

### Post by zteam2 on 2013-08-03
Are you using a SDD, with Ubuntu?

If so then you are probably facing a LightDM bug.

Look at the article right here.

[http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html](http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html)

But instead of just adding sleep 2, to your 
/etc/init/lightdm.conf configuration try with these lines:


```
stop on runlevel [016]

respawn
  emits login-session-start
emits desktop-session-start
u
emits desktop-shutdown



```

And if you doing this from the terminal you have to use nano instead of gedit.

Other than that just follow the article and use solution 1

---

### Post by stefan_bahrens on 2013-08-03
If I type gksudo gedit /etc/default/grub then I get a message that says gksudo is not installed. If I type sudo gedit /etc/default/grub I get the message -

Invalid MIT-MAGIC-COOKIE-1 key
** (gedit:2042): WARNING **: Could not open X display
Cannot open display:
Run 'gedit --help' to see a full list of available command line options

What does any of this mean? Thanks for any help.

---

### Post by stefan_bahrens on 2013-08-03
Thanks for your response zteam2. No SDD, I have a hard disk. The laptop is a Samsung NP Q45. If I type 'sudo apt-get update' I notice that a lot of archives (I am in UK) are marked "Temporarily Moved" and an IP address follows. Should I still try the LightDM edit you suggest using nano? I'll have to sleep now but I'll try anything tomorrow. I think the video adaptor is an Intel X3100 Graphics Accelerator. Is there a problem with x-server? I've no idea.

---

### Post by zteam2 on 2013-08-04
> **stefan_bahrens said:**
> Thanks for your response zteam2. No SDD, I have a hard disk. The laptop is a Samsung NP Q45. If I type 'sudo apt-get update' I notice that a lot of archives (I am in UK) are marked "Temporarily Moved" and an IP address follows. Should I still try the LightDM edit you suggest using nano? I'll have to sleep now but I'll try anything tomorrow. I think the video adaptor is an Intel X3100 Graphics Accelerator. Is there a problem with x-server? I've no idea.

Trying out the LightDM fix, can be good in this case too yes :-)

I think I have hard about these LightDM isssues with people with only harddrives also, but it it seems alot more frequrent for those using a SSD.

You can also try to simply type just "Lightdm" (without the quotes of course) at the terminal to see if LightDM starts then, if so I highly reccomend you to try the fix.

and gksudo and gedit can only be used in the graphical enviroment.

If you run from the terminal you should use sudo and nano instead.

:o

---

### Post by stefan_bahrens on 2013-08-04
Will try LightDM. In the meantime I attempted a re-install from disk and this failed. Basically what happened is that everything went as usual until the "UBUNTU" splash screen. This flickered across the screen and was stretched vertically and with some wrong colours (just like when I attempt normal boot). And then the screen went grey and that was that.

---

### Post by stefan_bahrens on 2013-08-04
I ran
sudo lightdm
I got a brief flash and then nothing. Screen stayed black.
This is beyond me. Is there a hardware fault in the video adapter?

---

### Post by VMC on 2013-08-04
You didn't say whether you get a grub screen. It so then type 'e' and add to the end of the linux line *nomodeset* then push F10. If it boots then you have at least found video as the issue.

---

### Post by stefan_bahrens on 2013-08-04
thanks for your reply VMC. I have no idea what a 'grub screen' is. If I hold the left shift key down while booting I get a screen labelled "GNU GRUB version 2.00-13ubuntu3". Is that it? Underneath I have the options -

Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

If I select the second option I get a screen with -

Ubuntu, with Linux 3.8.0-25-generic
Ubuntu, with Linux 3.8.0-25-generic (recovery mode)

below this outside the text box it says I can type 'e' as you suggest. If I type 'e' I get a screen that starts with "setparams" and continues with about another 15 lines of jargon. I don't know what you mean by "and add to the end of the linux line *nomodeset* then push F10". I can see a line that starts with "linux" and ends with "nomodeset". If I press F10 without doing anything else I get a basic coloured screen headed "Recovery Menu (file system state: read-only)". Under this there are 9 commands starting with "resume" and ending with "system-summary".

---

### Post by stefan_bahrens on 2013-08-04
I tried this. I don't know if it is what you meant.
I held down Ctrl+Alt+F1 while booting to get a command line and logged in. I used sudo nano to edit /etc/default/grub. Specifically I editted
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to say
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
and saved (CtrlX, Y and Enter)
this made no difference. Screen still goes black afetr I get a brief flicker of the distorted "Ubuntu" splash.

---

### Post by stefan_bahrens on 2013-08-04
S**t!!!!! I forgot to do "sudo update-grub". As soon as I did this to write the change into /etc/default/grub and booted it WORKED!!!!! I am very very happy. I have no idea what I've done or why it has worked. The resolution of my desktop is weird now but I can live with this. Thanks very much for all your suggestions. I also found this "How to" extremely helpful [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) I never thought for a minute that this would get fixed and had assumed that the video card was stuffed and I'd have to bin the laptop. Bearing in mind how this problem was fixed can anyone tell me what the problem actually was? 48 hours ago everything was fine and then the video card suddenly decided it could not cope with the resolution it was being asked for. At least I think that's it. Anyone? What went wrong?

---

### Post by VMC on 2013-08-04
If "nomodeset" is in effect, then you probably have reduced resolution. Change from "nomodeset" to "modeset=0" and see if that works better.

---

