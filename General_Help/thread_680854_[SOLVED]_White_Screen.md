---
title: "[SOLVED] White Screen"
date: 2008-01-28
forum: General Help
---

### Post by Bruce M. on 2008-01-28
Well I'm using W2K right now.  :(

Feisty (7.04)  has **a white screen and a mouse pointer**.  I can move the pointer around but all I see is white.

If I don't try things, I won't know, now I know not to try this again.

In Feisty I tired the "experimental" desktop affect to make the "window" wobble when I move it....  oopps!  White screen!

I can boot to recovery mode command line, but have NO idea how to turn this thing off from there.

Obviously I can't cut and paste any command results here for you as I'm in W2K, and only have recovery mode for Ubuntu.

If I use my 6.06 LTS LiveCD, (I have a 7.04 Alt-CD) can I get into the system to change things from there?

In fact, I'll do that, use 6.06 Live CD, and come back with Firefox.  Should have done that first.

I hope someone can help me.
Bruce

**EDIT** OK, I am here with 6.06 Live CD running.

---

### Post by ebash on 2008-01-28
I had the same symptoms: the white screen with only the mouse visible when I was using compiz with an ATI video card. I don't know how to fix compiz in order to work but I can help you to disable compiz.

When you login, change your session and try to use one of the failsafe sessions. You can change your session at the login screen, look for the options menu. Once you are in the failsafe try to disable the 3d effects that break your configuration. Logout and log back in. If the white screen is still there, logout and try again to play with your settings through a failsafe session.

To logout, actually to kill the X server, press CTRL+ALT+Backspace simultaneously. This will restart you X server and bring you to the login screen. It's faster than rebooting the computer.

---

### Post by Bruce M. on 2008-01-28
> **ebash said:**
> I had the same symptoms: the white screen with only the mouse visible when I was using compiz with an ATI video card. I don't know how to fix compiz in order to work but I can help you to disable compiz.

That's it, the **compiz** thing.  Can't get rid of it without dropping "Ubuntu Desktop" but can't use it (here).

> **ebash said:**
> When you login, change your session and try to use one of the failsafe sessions. You can change your session at the login screen, look for the options menu. Once you are in the failsafe try to disable the 3d effects that break your configuration. Logout and log back in. If the white screen is still there, logout and try again to play with your settings through a failsafe session.

To logout, actually to kill the X server, press CTRL+ALT+Backspace simultaneously. This will restart you X server and bring you to the login screen. It's faster than rebooting the computer.

Great, trying that now.  Thanks so much for the hope!

---

### Post by Bruce M. on 2008-01-28
I tried the different sessions:
Options are:
 Last session
 1. Run Xclient script
 2. GNOME
 3. failsafe GNOME
 4. failsafe Terminal
-----------------------------
 3. failsafe GNOME
 - Displays a message: You will be logged into "Default" Session of GNOME without the start up scripts being run. This should be used to fix problems in your configuration.
 - brings me to the white screen.

 2. GNOME
 - brings me to the white screen.

 4. failsafe Terminal
 - put me in Terminal, exit; takes me to the white screen.

**NOTE:** When I use [Ctrl]+[Alt]+[Backspace] I see my background image briefly.

*So the question has changed:*

 1. How do I disable compiz from a Live CD session Terminal?
 2. How do I disable compiz from Recovery Mode's CLI

I'll search while waiting to see if something shows up here.
Thanks
Bruce

---

### Post by Bruce M. on 2008-01-28
Found [this]("http://ubuntuforums.org/showpost.php?p=3569131&postcount=2"), it's for 7.10 but might work.

**EDIT:** It worked, but only for the session I was in ( I saw the Terminal border change to my theme), once I exited the Terminal - white screen. Marking this [Solved] will post new question in proper thread - How do I disable compiz from Recovery Mode's CLI.
 **2.** changed to unsolved, still need an answer.  :(

---

### Post by Bruce M. on 2008-01-28
In failsafe Terminal (Feisty), will this work?

To remove compiz and beryl/emerald. Open a terminal and type in the following code

sudo apt-get remove compiz* && sudo apt-get autoremove

then:

sudo apt-get remove beryl* emerald* && sudo apt-get autoremove

The only reason I know about this is i too tried compiz and didn't like its results. Couldn't seem to get all settings to work.

Do I need to remove beryl and emerald?
What are they?
Will this remove "Ubuntu Desktop" or metacity?

**EDIT:** sudo apt-get remove compiz* && sudo apt-get autoremove, doesn't work.  :(
**Help! Please, somebody!**

---

### Post by ebash on 2008-01-29
Sorry, for the delay but I was sleepin, we're probably in different timezones!

You don't need to remove compiz, just to disable it for your session. Login with a fail safe session, 
without the line CD. Then go to the menu > System > Preference > Appearance. Then go to the tab Visual Effects and select none. Logout and login with a normal session.

If this doesn't do it or if you really want to fix the issue with a live cd. Try the following, go to your home account and find the following file: .gconf/desktop/gnome/applications/window_manager/%gconf.xml

This file should have the directives that indicate which window manager to use. If you see /usr/bin/compiz in it, simply replace this strings by /usr/bin/metacity.

---

### Post by Bruce M. on 2008-01-29
> **ebash said:**
> Sorry, for the delay but I was sleepin, we're probably in different timezones!

No doubt, it's a big world, I'm -3GMT (Buenos Aires, Argentina). Where are you?

> **ebash said:**
> You don't need to remove compiz, just to disable it for your session. Login with a fail safe session, 
without the line CD. Then go to the menu > System > Preference > Appearance. Then go to the tab Visual Effects and select none. Logout and login with a normal session.

I thinks you missed this is Post #4:
> 
3. failsafe GNOME
- Displays a message: You will be logged into "Default" Session of GNOME without the start up scripts being run. This should be used to fix problems in your configuration.
- brings me to the white screen.

and also, "Visual Effects" is a Gutsy thing, I think, I'm running Feisty.  And I need to disable it "forever", it's not compatable with my old P-III I believe.

> **ebash said:**
> If this doesn't do it or if you really want to fix the issue with a live cd. Try the following, go to your home account and find the following file: .gconf/desktop/gnome/applications/window_manager/%gconf.xml

This file should have the directives that indicate which window manager to use. If you see /usr/bin/compiz in it, simply replace this strings by /usr/bin/metacity.

I have 3 options open to me:

 **1. failsafe Terminal**
 - puts me in Terminal, exit; takes me to the white screen.

 **2. Recovery Mode:** I think it's just a CLI, not terminal, and I don't know enough about the commands to mount the drive and navigate to where I need to go. I'm new at this, been using Linux for 6 months now. Check it out: [HELP - Restoring Home folder problems.]("http://ubuntuforums.org/showthread.php?t=678938"), I was going to post my solution but the snowstorm stopped me.


 **3.** And last but not least, the: **Live CD:** Can I start nautilus with gksudo from a Live CD? - Nope!

```
ubuntu@ubuntu:~$ gksudo nautilus

(nautilus:7813): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
closing
ubuntu@ubuntu:~$ sudo mount /dev/hda5/
mount: can't find /dev/hda5 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$
```

Darn it, I do not want to have to re-install, again!
Tell me something, is this file:

.gconf/desktop/gnome/applications/window_manager/%gconf.xml

in **/** or in **/home** - and just as important, is it a Feisty or a Gutsy file?

Because if it is in /home, I'm in serious trouble if I have to re-install.  I only just moved it to it's own partition, /media/sda7/, and the next day I get the white screen, I haven't had time to backup yet.

It took me two days to unarchive my backup because (HUBackup) HURestore does NOT work.  I had to research and read stuff for two and a half days as no one could help me with DAR extracting a /home folder complete with permissions.

Another day...
Bruce

---

### Post by ebash on 2008-01-29
It's true that the tips that I gave you where for gutsy. I'm not sure if compiz is set through gconf in the other versions of Ubuntu. The folder .gconf is in your home account.

Don't be afraid, you don't need to reinstall your computer. But, having some basic command line knowledge will get you out of your troubles faster. I hope that you are familiar with the commands: cd, ls, rm, less and nano.

What you need is to have a command line access to your computer without the live CD. This is because the live CD will probably not mount in write mode your disks and you will need to do it manually.

You can gain access to the console in your computer the following way. Reboot it and wait until you are at the login screen. Once there press Crtl+Alt+F1 this will bring you to a fullscreen console. Login there using your usual login/password. You will be in a command line terminal, there's no GUI in this mode is command all they way.

Now check if the file .gconf/desktop/gnome/applications/window_manager/%gconf.xml contains any reference to compiz.:

```
nano -w .gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

Nano is a console based text editor. It should be easy to get your way around since it has a help menu at the bottom of the screen (Ctrl-X saves the file and closes the editor).

If so remove all references to compiz and replace them with metacity. Go back to the graphical login screen (press Crtl+Alt+F7) and try to log in. If the white screen is still there zap the X server (Crtl+Alt+Backspace) and go back to your terminal (Crtl+Alt+F1).

If the white screen is still there, let's try something more radical, let's get rid of you .gconf folder. Actually just rename it, it will do the trick. Try:

```
mv .gconf .gconf-SAFE
```

Switch to the graphical mode (Ctrl+Alt+F7) and try to login.

---

### Post by Bruce M. on 2008-01-29
> **ebash said:**
> It's true that the tips that I gave you where for gutsy. I'm not sure if compiz is set through gconf in the other versions of Ubuntu. The folder .gconf is in your home account.

Don't be afraid, you don't need to reinstall your computer. But, having some basic command line knowledge will get you out of your troubles faster. I hope that you are familiar with the commands: cd, ls, rm, less and nano.

What you need is to have a command line access to your computer without the live CD. This is because the live CD will probably not mount in write mode your disks and you will need to do it manually.

You can gain access to the console in your computer the following way. Reboot it and wait until you are at the login screen. Once there press Crtl+Alt+F1 this will bring you to a fullscreen console. Login there using your usual login/password. You will be in a command line terminal, there's no GUI in this mode is command all they way.

Now check if the file .gconf/desktop/gnome/applications/window_manager/%gconf.xml contains any reference to compiz.:

```
nano -w .gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

Nano is a console based text editor. It should be easy to get your way around since it has a help menu at the bottom of the screen (Ctrl-X saves the file and closes the editor).

If so remove all references to compiz and replace them with metacity. Go back to the graphical login screen (press Crtl+Alt+F7) and try to log in. If the white screen is still there zap the X server (Crtl+Alt+Backspace) and go back to your terminal (Crtl+Alt+F1).

If the white screen is still there, let's try something more radical, let's get rid of you .gconf folder. Actually just rename it, it will do the trick. Try:

```
mv .gconf .gconf-SAFE
```

Switch to the graphical mode (Ctrl+Alt+F7) and try to login.

***SUCCESS!***

I actually did it before seeing this post, my head kicked in: *Safe Terminal*

I did this:

 1. Booted to *safe Terminal* mode, that way I was in my system, not Live CD.
 2. cd'd my way down one folder at a time to see if each existed.
 3. upon reaching: window_manager I did a DIR and saw the file.
 4. Tried **nano %gconf.xml** ... it created an empty file, no not right, exited;
 5. **sudo nano %gconf.xml** <<-- did the trick.

The file contained a total of 8 lines I think, and I changed two references of compiz to metacity.
 Saved and exited Terminal, and here I am.

> cd, ls, rm, less and nano.
Yes, I'm familiar with them.  I like Treminal, reminds me of my DOS days, just not totally familar with Linux commands, but I'm learning.

> Once there press Crtl+Alt+F1 this will bring you to a fullscreen console.
Oh, now that I like, will file away for future reference.

Thank you my friend!
Bruce Milmine

---

### Post by ebash on 2008-01-29
> **Bruce M. said:**
> ***SUCCESS!***

 4. Tried **nano %gconf.xml** ... it created an empty file, no not right, exited;
 5. **sudo nano %gconf.xml** <<-- did the trick.


I don't understand why you had to use sudo, the command listed in 4. should have worked. Anyhow the important is that you have your graphical sessions back.

Just make sure that the file that you have edited belongs to you, otherwise you could have some troubles when you will try to change these settings. Check the owner ship of the files with this command:

```
ls -al .gconf/desktop/gnome/applications/window_manager/
```

Make sure that the %gconf.xml file belongs to you if it doesn't change it's owner ship with:

```
sudo chown USER.GROUP %gconf.xml 
```

Where USER is your user name and GROUP your main group (usually it's the same as your username).

You're welcome.

---

