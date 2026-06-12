---
title: "Mind If Someone Explained This To Me..."
date: 2007-06-17
forum: General Help
---

### Post by shadows85 on 2007-06-17
I've been trying to install byond but I don't understand the readme file at all.. can someone explain it to me?

---

### Post by dreadlord_chris on 2007-06-17
> **shadows85 said:**
> I've been trying to install byond but I don't understand the readme file at all.. can someone explain it to me?

What is it you don't understand? Have you extracted the archive? Open a terminal and **cd** to the folder that you extracted it to. Now type **make**, that should start the installer.

---

### Post by splot on 2007-06-17
I'll give it a shot, not sure just how much of a beginner you are so I'm sorry if this is too dumbed down or vague, not knowing what this thing is that you're trying to install makes it harder and I don't have time to look it up.

Step 1: have you unzipped the file yet?  I think you'll use unzip or bunzip, prolly bunzip.

Step 2: cd into the directory it unzipped and type make...it's gonna start the install and ask you if you want to install to your directory, or somewhere in your system files...if you're not root, say in your dir for your own use, if you're root pick somewhere else if you have more than one person using your computer and you want them to use it too...most people put things in /usr/bin or somewhere like that.

Step 3: harder to explain, basically you may have to handchange some settings so that your machine can find what it needs to run that app.  Varies by the system.

Step 4: Add the setup file to your bash profile, so that the setup stuff will run whenever you open a terminal window with bash.  Varies by the system.


Hope that helps a little, it might just give you more ideas what kinds of specific questions to ask.
Good luck!

---

### Post by Raavea on 2007-06-17
I've simplified it in chunks for you, see below. I'm no expert and may have gotten bits wrong, so if something doesn't work as I say, I apologise. Hope I'm not being insulting or just repeating what everyone else has told you.

> Dantom.BYOND.Linux
Last updated for release: 312

Installation procedure:

1. Unzip byond-linux.zip.  (You probably already did this.)
 You downloaded the file byond-linux.zip and it's the thing you're trying to install. To get this readme out, I assume you already unzipped it. If not, you should be able to double-click it to open in with an archiving program or right-click to choose your archiving program from the right-click menu. My archiver (xarchiver) does not automatically use full path to extract, so make sure you've got this option clicked if it's there and not clicked.


> 2. Type 'make' and follow the instructions.  Basically, you have the option
   of installing here (for your personal use alone) or on the entire system.
Now you need to open up a terminal window and use the command** cd **to change directory until you are in the directory you unzipped byond-linux.zip into. It's probably byond-linux, so if I had unzipped this file into my user directory I would open the terminal and type **cd byond-linux** then I would type **make** and follow the on-screen instructions. You should be able to find a terminal program in your menu.


> 3. If you installed on the system and you changed the byond system location,
   be sure to add BYOND_SYSTEM to your environment settings.  You may also
   need to set LD_LIBRARY_PATH or modify /etc/ld.so.conf.  The default
   installation parameters should require no further setup.As I am not sure how this program actually works, I'm not 100% on this, but it looks like it is telling you about something you would have the option to change during the setup you begin with the **make** portion of the readme. As it says the default parameters should require no further setup and you seem pretty new to this program, I would personally keep the defaults if I were in your position. If you did change it, I reckon the environment settings file will be somewhere in the byond-linux directories, so look around them for a line that may look something like: BYOND_SYSTEM usr/yourname/byond-linux


 The rest of the readme means nothing to me, I'm afraid, though I hope if you need it, someone will be able to help you. Again, apologies if I've been insulting or repetitive! :D

---

