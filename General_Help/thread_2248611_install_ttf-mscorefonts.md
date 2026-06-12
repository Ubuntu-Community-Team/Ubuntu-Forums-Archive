---
title: "install ttf-mscorefonts"
date: 2014-10-15
forum: General Help
---

### Post by Pedroski55 on 2014-10-15
I would like to install the ttf-mscorefonts. For some reason the Software Centre can't do this.   I followed the instructions on this page.  [http://www.blackmoreops.com/2014/07/31/install-fonts-on-linux/](http://www.blackmoreops.com/2014/07/31/install-fonts-on-linux/)    root@pedro-bedro2:/home/pedro# apt-get install ttf-mscorefonts-installer Reading package lists... Done Building dependency tree        Reading state information... Done ttf-mscorefonts-installer is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.    root@pedro-bedro2:/home/pedro#  ttf-mscorefonts-installer ttf-mscorefonts-installer: command not found    I tried  root@pedro-bedro2:/home/pedro# /usr/share/package-data-downloads/ttf-mscorefonts-installer bash: /usr/share/package-data-downloads/ttf-mscorefonts-installer: Permission denied root@pedro-bedro2:/home/pedro#     So I did:  root@pedro-bedro2:/home/pedro# chmod +x /usr/share/package-data-downloads/ttf-mscorefonts-installer  and I get:  root@pedro-bedro2:/home/pedro# chmod +x /usr/share/package-data-downloads/ttf-mscorefonts-installer   root@pedro-bedro2:/home/pedro# /usr/share/package-data-downloads/ttf-mscorefonts-installer /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 1: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 2: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 4: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 5: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 7: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 8: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 10: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 11: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 13: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 14: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 16: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 17: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 19: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 20: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 22: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 23: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 25: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 26: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 28: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 29: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 31: Url:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 32: Sha256:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 34: Script:: command not found /usr/share/package-data-downloads/ttf-mscorefonts-installer: line 35: Should-Download:: command not found   What am I doing wrong??

---

### Post by Dennis N on 2014-10-15
You already have it installed. You can tell from this output:

> Reading state information... Done ttf-mscorefonts-installer is already the newest version.

---

### Post by oldos2er on 2014-10-15
Please use code tags when posting terminal output; your post is near unreadable for me.

As Dennis N said, you already have the package installed. It's just a set of fonts, there's no executable program contained in it, so I'm at a bit of a loss trying to understand what you're doing.

---

### Post by Pedroski55 on 2014-10-15
What I'm trying to do is make  ttf-mscorefonts-installer run. It does not work. It should install the fonts. Ubu Software Centre also comes up with a permanent error.   I circumvented this by copying the fonts from Windows into /usr/share/fonts/anydirectory, then installing via fc-cache -fv, as mentioned in the link above.

---

### Post by ian-weisser on 2014-10-15
It does work.
Usually, it means you skipped past the curses screen with the license agreement.
If you don't agree to the license terms, the downloader won't start.

Hint: It's not a pretty dialog box with clickable buttons. Last time I used it, it was a big, ugly,  slightly scary old-school text screen with either CANCEL or OK highlighted in red. Choose OK.

---

### Post by Pedroski55 on 2014-10-15
Nope, didn't see that at all. I thought there had been a policy change at Ubuntu, no more msfonts. I'll try the same thing on my other laptop, see what that does.  Worked from the commandline on the other laptop, not from the software centre. Someone said that was the case in the comments area of the software centre.  Thanks for your trouble.

---

### Post by yancek on 2014-10-15
The license screen is set to default to NOT accept so you need to hit the tab key to get OK to the license.  Did this myself a while back.

---

### Post by lisati on 2014-10-16
> **oldos2er said:**
> Please use code tags when posting terminal output; your post is near unreadable for me.

^^^ This. 

@Pedroski55: 

Looks like you've lost the formatting, making the editing by yourself or a forum staff member to aid readability by others that much harder.

Don't be fooled by the .EXE filename extension. It's an archive that in Windows acts like a self-extracting archive.

---

### Post by buzzingrobot on 2014-10-16
It's possible for the EULA agreement panel to be hidden behind other windows, at least in my experience.  If the Software Center window is maximized, try unmaximizing it. 

The sure way is to open a terminal, do "sudo apt-get install ttf-mscorefonts-installer", and proceed. The EULA agreement will appear, you use the tab key to reply to *two* questions, and the font files are downloaded and installed.(I.e., the font files are not included in the ttf-mscorefonts-installer package.)

I've seen the server hosting the font files (usually Sourceforge) be very slow on more than one occasion, and I've seen it be down altogether at other times, causing the install to stall out and fail. 

Cacheing the new fonts (fc-cache), etc., is all handled by the installer. Do a ```
"ls /usr/share/fonts/truetype/msttcorefonts/
``` to verify they're there.

---

### Post by oldos2er on 2014-10-16
> **Pedroski55 said:**
> What I'm trying to do is make  ttf-mscorefonts-installer run. It does not work. It should install the fonts. Ubu Software Centre also comes up with a permanent error.   I circumvented this by copying the fonts from Windows into /usr/share/fonts/anydirectory, then installing via fc-cache -fv, as mentioned in the link above.

I still don't understand why you want to "run" the package if you already have the fonts installed. As others said, you need to agree with the EULA which pops up in an ncurses screen, and will remain there until it's agreed to or not. ```
sudo dpkg --reconfigure -a
``` will recall it (use Tab and Enter to agree) and clear the "permanent error" in Software Center if my assumption is correct. Otherwise we need more info on the "permanent error."

---

### Post by Pedroski55 on 2014-10-16
This comes up in a Window, which, as someone correctly remarked, lies hidden behind other windows. It is a message from Software Centre.    

"Data files for some packages could not be downloaded  The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.  ttf-mscorefonts-installer  This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem."

  ps I installed NoScript on Firefox, maybe that is causing the text formatting problems here, I never had that before!

---

### Post by buzzingrobot on 2014-10-16
There is this bug report on that package:  [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1371783](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/1371783). It may or may not be related. 


"  The following packages requested additional data downloads after  package installation, but the data could not be downloaded or could not  be processed..." -- ttf-mscorefonts-installer contains no fonts.  It downloads fonts from other, non-Canonical, servers. So, one explanation of that sentence is that the package did indeed install correctly, but that the server hosting the font files did not respond. I'd remove the package and reinstall and try again later.

But, as mentioned earlier, your first post indicates that fonts are already installed. Is that not the case?

---

