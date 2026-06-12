---
title: "Different Machines, Same User, USB drive mounted Home dir"
date: 2006-11-27
forum: General Help
---

### Post by FearNoIdea on 2006-11-27
First post, be kind :) I did try searching and google before posting.

Here's what I want to do...  
I have 6.06 installed at both home and office.  I have a user setup at home and the office with the same username and password both places.  I want both my home machine and office machine to be identical.  Hardware wise, they are both from the same manufacture, home machine is AMD work is Intel. They have the same dvd drives, harddrives etc etc.  Thanks to the day after thanksgiving sales, I picked up a WD MyBook 400GB REALLY cheap.  I want to be able to take my "user and home dir" with me.  So say, I am working on a project at work and need to leave... Shut down work pc, grab usb drive, go home, plug in usb drive, boot up home machine, and notice no difference continueing where I left off.  I want to take my files, preferences, Evolution setup, etc etc.  You get the idea.

Here's what I've done...
Got the MyBook home, plugged it in, opened a terminal window.  Logged in as sudo su -  then pathed to my home dir.  I then copied my home dir to the usb drives root dir.  

find . -depth -print0 | cpio --null --sparse -pvd /media/My\ Book

This worked fine copying all my hidden files and what not.  I then backed up my home dir, created a new home dir for my user to path to.  I then unmounted the usb drive and remounted it as my user's home path.  Then logged out of Gnome and attempted to log in again.  No dice.  Failed to lock Ice file.  It then occurred to me that having my user's home dir on a vfat partition was probably not so good.  ##Palm hit forehead##  I rebooted.  Next I formatted the MyBook ext3 and copied my home dir again using the same method.  Mounted the usb drive, logged out, logged back in... Sweet, it worked this time.  Preferences were good, ssh config good, firefox bookmarks good, Evolution inbox not so good...  I added the following line to fstab

/dev/sda1       /home/fearnoidea    ext3    rw,auto,nosuid,nodev    0       0

Assuming it would auto mount and I would log into my user on the usb drive.  Nope.  In order to become the user and use the home dir on the usb drive my current work around is to.  Log in, open terminal, mount -a, log out, log back in.  Kinda lame.  I'm assuming what I am trying to do is possible, I am also assuming I am not the first person to want to do this.  Kinda think that once working this will be pretty cool.  I will be able to at that point have a workstation at the various places I go, and take my user with me.  Ie, take my Evolution, boomarks, ssh config, source code, music, movies, I could go on but you already know.  I know I am long winded, so if you got to this point I thank you, and would appreciate your input.

---

### Post by FearNoIdea on 2006-11-27
If anyone is interested in an update.  I seem to have resolved the issue on my first test machine.  The conflict appears to have been with the pass.  My hda1 was pass 0 and per the original fstab, I had my usb drive set to pass 0.  By changing the pass to 2, the issue appears to be resolved.  I have tested several applications and my Evolution folders.  Btw, Evolution was telling me there was a problem with my inbox after synch.  Not exactly sure what this meant, however after using the package installer {advanced} tab to reinstall the files necessary for Evolution, the problem went away.  I will continue testing things out on this system, as this system is the source of the user I have "Ghosted" to my usb drive.  In the AM I will be attempting to imprint my ghost user on my work machine.  Basically I intend to login normal, move my user's home dir, create a new home folder, then make the same entry to my fstab.

/dev/sda1 /home/fearnoidea ext3 rw,auto,nosuid,nodev 0 2

We'll see if this works.  I will post back with my results.  I would also like to hear others thoughts on this.  Especially if you have done this, something like it, or have any creative ideas for me.  I am open to any cool integration ideas.  Right now I am pretty stoked about the idea of basically have drone machines about, with my user as a free range ghost. :cool:

---

### Post by FearNoIdea on 2006-11-27
SUCCESS!!!

I came into work this morning.  moved my user's home dir to a backup path. Created /home/user_name

added the following line to /etc/fstab
/dev/sda1 /home/user_name ext3 rw,auto,nosuid,nodev 0 2

Reboot.

Bingo, my user is here.  My Evolution email client works beautifully. My user is now a ghost.  I have a drone machine at home and at work.  The ghost is on my USB Harddrive.  Same files, same settings, it's a beautiful thing.

Please if anyone else has done, wants to do, or otherwise has thoughts on this type of thing, comment.

---

