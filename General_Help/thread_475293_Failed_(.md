---
title: "Failed :("
date: 2007-06-15
forum: General Help
---

### Post by The Wisedude on 2007-06-15
Hey,  I got a reallllllly big problem, and when i say really, i mean it.. Ok.. this is what happened.. yesterday, I was on my home PC, Yea it had windows Xp 2003.. And i was fed up with it.. so i decided to TRY to install Ubuntu, Well.. I read your TuT. And i downloaded that EXE program from the Ubuntu forums. I ran it.. Chose Ubuntu.. And I used my whole partition.. And at the end I chose ' Ubuntu Desktop'.

10 Minutes later.. I tryed to turn on my PC and it comes up in a black dialog box (Fills the whole screen) And just says "Starting up" In white writting then it says

'Begening GRUB 5.0'

'Starting Ubuntu blah blah blah' 

And then says

'User login'

All of this is in a WHITE writting on a black screen, I cannot run the recovery partition i made early because its basicly tooken over..

What did I do wrong?! :'( I hate this man.. I really want to use Ubuntu.. and I dont want to buy a new Harddrive :'( :(

Thanks, if you can help. :)

---

### Post by cookies on 2007-06-15
Looks like the GUI didn't boot. Maybe X didn't start or there was an error in install. Why did you use the ubuntusetup.exe, though?

---

### Post by The Wisedude on 2007-06-15
> **cookies said:**
> Looks like the GUI didn't boot. Maybe X didn't start or there was an error in install. Why did you use the ubuntusetup.exe, though?


Why? Is that a bad thing to use  ubuntusetup.exe?..

I just want to know how to fix this problem :(

---

### Post by dasunst3r on 2007-06-15
Since the GUI failed to boot, you should log in with the user name and password of your choosing anyway, and then perform the following steps:
1. Give the command *sudo dpkg-reconfigure xserver-xorg*, and go through a basic configuration.
2. After you are done, give the command *sudo /etc/init.d/gdm restart* to try to start the GUI again.

Tell me if that works.

---

### Post by Crafty Kisses on 2007-06-16
> **The Wisedude said:**
> Hey,  I got a reallllllly big problem, and when i say really, i mean it.. Ok.. this is what happened.. yesterday, I was on my home PC, Yea it had windows Xp 2003.. And i was fed up with it.. so i decided to TRY to install Ubuntu, Well.. I read your TuT. And i downloaded that EXE program from the Ubuntu forums. I ran it.. Chose Ubuntu.. And I used my whole partition.. And at the end I chose ' Ubuntu Desktop'.

10 Minutes later.. I tryed to turn on my PC and it comes up in a black dialog box (Fills the whole screen) And just says "Starting up" In white writting then it says

'Begening GRUB 5.0'

'Starting Ubuntu blah blah blah' 

And then says

'User login'

All of this is in a WHITE writting on a black screen, I cannot run the recovery partition i made early because its basicly tooken over..

What did I do wrong?! :'( I hate this man.. I really want to use Ubuntu.. and I dont want to buy a new Harddrive :'( :(

Thanks, if you can help. :)
You should also try backing up your X server file after you reconfigure it, you can do this by doing the following commands:

This is to back up your X server file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

This is how you recover your backed up X server file if anything goes wrong:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by The Wisedude on 2007-06-16
None of that worked :(

---

### Post by cookies on 2007-06-16
> **The Wisedude said:**
> Why? Is that a bad thing to use  ubuntusetup.exe?..

I just want to know how to fix this problem :(

Because ubuntusetup.exe isn't stable.

If none of the above worked, try an install from burning the ISO to a CD.

---

### Post by DagMan on 2007-06-16
Try hitting ctrl-alt-f7 just to see...

Another thing would be to try to log in at that white text.  I presume you would have created a user and a password when installing though I don't know what a windows .exe installer is.

Try to log in using the username and password and then type in this:

sudo apt-get install gdm xserver-xorg ubuntu-desktop

it will ask for your password again and you won't be able to see it while typing

First though, maybe try these one by one and see if they work... after logging in assuming you are able to log in.

sudo /etc/init.d/gdm restart

startx

or even these 2 lines together:
sudo apt-get install openbox firefox
/usr/bin/startx /usr/bin/openbox

and if you get anything at all from the last, right click and select a web browser and hopefully you'lle at least be able to get in to get help for your system while running the OS and get things sorted.



If you still have your XP install on the drive and can't get it back, there's a utility on the XP disks to start in a DOS like environment and fix the MBR so you can boot again.  The other way, assuming windows is still there, would be to have the bootloader send you off into it which if it isn't already doing, it can be setup to do and may not require downloading the Ubuntu install CD if you are able to login at that white login thing.

Do you still have Windoes on the drive, and can you access it?

---

### Post by The Wisedude on 2007-06-16
Thanks everyone.. I'm going to try to install it from burning it onto a CD. Wish me luck..

EDIT:

Ok i put the CD on my PC.. (Home PC)

Now I clicked "Install andstart Ubuntu"\

And now a loading bar came up and has the ubuntu logo..

Is this right so far?

---

