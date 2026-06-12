---
title: "Compiz could not be enabled"
date: 2008-06-16
forum: General Help
---

### Post by HiImMatt on 2008-06-16
Hey I am very new to linux, I just in,stalled it on this old laptop I had laying around. Its a compaq presario 1200 I believe it was made in 2000 or so, but anyways, I havnt a clue as to what video card it has and Ive run compiz-check and this is what i got in return


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Trident Microsystems CyberBlade i1 (rev 6a)
 Driver in use:         trident
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Something potential problematic has been detected with your setup:
 Warning: Detected driver is not on Compiz' whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not known to work with Compiz and thus may be blacklisted on
 certain distributions.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y
urination@urination-laptop:~$ Compiz
bash: Compiz: command not found
urination@urination-laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (800x600) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0



Im generally good with computers but have only spent maybe two days on any linux distrobution so I hae no clue what Im doing or looking for. If anyone could help, or tell me what needs to be done Id greatly appreciate it 

Oh btw my keyboard has some buttons that work on and off, most of them are on the bottom row, but they will randomly start working and Ill leave the computer alone for 2-3 hours and they wont work for a day or so.

---

### Post by benoy4007 on 2008-06-16
Open System > Preferences > Appearance. Click on the Visual Effects tab. If Compiz and desktop effects are enabled, Normal, Extra, or Custom will be selected. If Compiz is disabled, None will be selected. To switch modes, simply click on another selection. Changes take effect immediately.

_**Check this link to know if your card is supporting one or not**_
[http://ubuntuforums.org/showthread.php?t=765875]("http://ubuntuforums.org/showthread.php?t=765875")

---

### Post by HiImMatt on 2008-06-16
I know how to enable it, Ive seen some one do it on a different computer, but this laptop that im using now will not allow me to enable the effects. Is it possible for the graphics card to just be too slow to work at all? I have the compiz-check posted in my original post, I dont know what to make of all that data so if someone would tell me what it means or how to fix it, I would greatly appreciate it.

---

### Post by HiImMatt on 2008-06-16
bump

---

### Post by psyopper on 2008-06-16
Try this bug report, it looks pretty promising...

[https://bugs.launchpad.net/xf86-video-trident/+bug/223774](https://bugs.launchpad.net/xf86-video-trident/+bug/223774)

Remember: Google is your friend. THe above link was number 3 when I searched *compiz trident cyberblade*.

Good luck!

---

### Post by HiImMatt on 2008-06-17
Im very sorry if i seem like a complete idiot, Its because I am. I reviewed that post above but the link didnt seem to say anything about compiz, even if it uses the same graphics card or configuration/ whatever I dont know what to do with any of that data If someone could tell how to do this as if you were trying to explain it to someone whos never touched linux before Id be endebted to you for life...

---

### Post by Forlong on 2008-06-17
I don't think it's possible to run Compiz on that graphics chip.

Although I have to say, the output of Compiz-Check does look promising.

Please post your **/etc/X11/xorg.conf** -- and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by ubonetu on 2010-07-21
Somehow I stumbled into a hack for this...

I copied an xorg.conf from this forum and when I click the on button on the compozitor Screenlet (installed from apt), compositing works.  I checked it with glxinfo and low and behold, it's on!

The drawback is you can't use the themes from emerald...  If anyone knows how to fix that, thanks in advance (when you click on the theme it simply doesn't load).

Anyway, I can run AVN (Avant Window Navigator) now and have a few effects.  Altogether nicer interface.

I'll attach my xorg.conf below...

---

### Post by ubonetu on 2010-07-21
I shot a screenshot.  Just so you know I'm not yanking your chain =D

---

