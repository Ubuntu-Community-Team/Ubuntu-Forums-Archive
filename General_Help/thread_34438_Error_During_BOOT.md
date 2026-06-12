---
title: "Error During BOOT"
date: 2005-05-14
forum: General Help
---

### Post by byen on 2005-05-14
Hey guys,
Installed Ubuntu and fired my Presario laptop and finally got everything running.... however I have a few errors that keep apearing during and after boot. Can someone please tell me if these errors are something that I need to worry about?


Error 1: Appears During OS BOOT -  Warning: ATI Radeon AGP is not yet y fully tested

Error 2: load ndisdriver: load ndisdriver (309):file 14E4:4320:OE11.00E7.conf is ignored (this appears for about 2 minutes during which the entire system pauses booting.

The following appear after user login:

Error 3: Composite Manager crashed twice in 1 minute and is therefore disabled for this session.

Error4: Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

I know these might look silly but Id really appretiate it if you guys can help me out.


Byen

---

### Post by nad on 2005-05-14
Hello,

If you are new to ubuntu and/or GNU/Linux, welcome.

Error 1 is obviously only a warning. It looks like our friendly developers are being a little more wordy these days. This is a good thing.

Error 2, if I'm not mistaken, refers to a wlan driver module for a wireless network device. Your system will hang for a moment as it looks for a network connection. Two minutes however is close to a timeout period. Do you have a network connection? We can troubleshoot this in your next post.

Errors 3 and 4 are related and the resolution is noted in the message. From the drop down menus pick Applications->System Tools->Root Terminal. Type in your password at the prompt and you will be in a terminal window. Issue the command: cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig . This will copy your current X server configuration file to a safe place. Now type: gedit /etc/X11/xorg.conf . You will now edit and save this file making the edit as noted in the error message. You probably already have this section in the file and need only to add the Option "Composite" "Enable"  line. Save this file and the next time you start your computer, this error should not appear.

The reason for the convoluted edit is that you can only write this file as the superuser.

Any questions? ...

---

### Post by byen on 2005-05-14
Thank you for your quick response. And yes I am new to linux. and after initially struggling with my Graphic drivers and Wireless card... with the help of people such as yourself...i have come so far where for the first time in 5 years I havnt used Windows for 3 days. Really ...linux would never be here if it wasnt for the community...or shall i say family!! that being said....

I did try what was suggested...but the moment i add the text to the Xconfig file..BOOM! the errors dissapear but the screen literally crawls and the system screen is kinda hanging up with horrible..windows like behavior! any suggestions?

Once again thank you for your help.

byen

---

### Post by nad on 2005-05-15
Upon rereading your message I note that errors 1,3 and 4 are related.

Apparently the 'Composite' extension is not fully implemented yet.

This is why you made a backup copy of that config file. At the boot up menu selection screen, choose 'Recovery Mode'. You will be dropped into a terminal screen where you can copy the backup file to your config file: cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf .
Issue the command: /etc/init.d/gdm start  to get back to your ubuntu desktop.

You will have to live with the error messages or comment out the "Composite' line in your config file by putting a # at the begining of the line if it is there.

I don't understand why it tried to load this extension in the first place if it was not listed in your config file, but, if you are using the proprietary ATI driver module, only ATI knows.

---

### Post by byen on 2005-05-15
Hey nad,
Thank you for your reply again..... Though I cannot talk about the first 2... after doing some research and my recent customization back-track... I found out that on the KDE Desktop, there are certain functions such as transparancy  and shadow rendering (i made this word up) which are not stable and are reported to have bugs. so when i disabled certain transparency settings and shadow settings errors 3 and 4 dissapeared.
ABout errors 1 and 2... you were right.... 1 was supposed to be just a caution and 2 started only after i configured my WLAN card. SO i guess your theory was right!

thanx for your guidance.... will be back soon if there are any new issues.....

Byen

---

