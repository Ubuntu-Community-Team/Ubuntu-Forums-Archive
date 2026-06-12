---
title: "Gnome disk utility (palimpsest) - what happened?"
date: 2013-03-19
forum: General Help
---

### Post by frytek on 2013-03-19
Today I needed to repair an SD card which mounted "read only". I installed gnome-disk-utility from the repo and... 

It looks different (e.g. has a play / pause button for mounting / unmounting a partition) plus a right click menu. But the options are limited. There are no separate items like "format volume", "format drive" and -- the most important -- "check filesystem". The version is 3.x.x

I had to roll back my repo to 12.04 and install the 2.x.x version. Luckilly, it worked. 

Does anybody know what is happenning? Are the missing functions taken over by some other program or utility?

---

### Post by ManamiVixen on 2013-03-19
That's all part of Gnome's master plan. Remove as many unneeded features and options as possible. Gnome is moving to the tablet so disk utilities are not that important. If you need to manage disks. install gparted fro the software center.

---

### Post by frytek on 2013-03-20
I do hope you're just ironic. 

Why to make "disk utility" and then castrate it. 

If they need a tablet system, this piece of software should just not be installed by default. "Development" used to mean "adding or improving features, fixing bugs", and this is exactly the opposite.

---

### Post by Morbius1 on 2013-03-21
I'm fairly certain          ManamiVixen was not being ironic. Consider the following: You have an external USB storage device formatted in ext4 and you want it to be accessible by everyone so you do a chmod 777.

In Ubuntu 12.04 when you plugged it in it would automatically mount to /media/LABEL and it's permissions would be 777.

In Ubuntu 12.10 when you plug it in it mounts to /media/$USER/LABEL and despite the fact that the partition itself is still at 777 the permissions of /media/$USER allows only the user that plugged in the device to use it. 

The developer ( Red Hat employee btw ) who made this change ( to udisks ) also rewrote gnome-disk-utilty.

Was it a case of abandoning the desktop in favor of Tablets / Phones or just a simple case of lack of adult supervision? I don't know.

---

### Post by frytek on 2013-03-22
Then it's a tragedy. 

When I used Mandrake (before it became Mandriva) I got used to notorious spoiling some features in one release, while fixing others... And then spoiling the fixed ones and repairing the spoiled ones in a following release. 

When Ubuntu appeared I thought these days were gone. Gradually, each distro became better and better. I think I was too happy. 

But I know what you mean and what is the reason: some (young) guys think the more sophisticated ("intelligent") functions they include, the better. Even if these functions in fact make the situation worse. What comes to my mind is the Lotus Word Pro "dynamic interface". It was many years ago. The developers thought how bright it would be to show in the menu only the options that users might want or could use in certain situation. Like - there was no "Table" option at all, as long as you did not place your cursor in a table. No, there was only the "Insert" menu, where you could insert a table. But human brain does not work this way. Lots of us barely remember rarely used features so we *browse* the menu and search for a name that rings a bell. And a natural order is "Table? -> new table". Not "insert -> whatever, a table maybe". From the developers' point of view the dynamic interface was a step forward, but for users it was a real pain in the ass. (I don't like MS, but their feature of hiding unused items was a much better solution as browsing for required, often used features was quicker). It seems to me that mounting a USB drive under user's name is considered "intelligent" and more sophisticated, while it just sucks.

To be honest, I switched to Mint, because Gnome 2.x was ideal for me, I did not like the Unity's tablet-wise interface. But now it seams the new, poisonous trends start to leak out to regular applications and tools. And this really worries me.

---

### Post by Mechatism on 2013-04-06
The new gnome-disk app sucks for building custom systems. One of the most important features of gnome-disk-utility was that it showed to which port a drive was attached. Many motherboards have both SATA II and SATA III ports and attaching drives to the correct port is critical to building fast systems. Apparently the Gnome 3 project is determined to castrate user interfaces by removing critical features. If they wish to simplify them they should at least provide a mode option where all the original functionality is still available.

The new gnome-disk app gets nine smelly diapers from me.

---

### Post by rtimai on 2013-07-01
It was so-o-o HARD to discover that "Gnome-disk-utility" was Palimpsest! Looking up support references to this has been an unmitigated hassle! This thread may be the only substantial discussion of late, and it's three months old. Maybe it IS time to switch to GParted (but, with what consequential issues?) 

Anyway, I have a question about gnome-disk-utility, aka palimpsest. I have not been able to find any discussion on this scenario.

I have a bunch of USB drives, all of them came formatted as FAT16 for widest compatibility. For the sticks I intend to use solely on my Ubuntu laptop, I used Palimpsest to reformat them as EXT4. On one of them, as an experiment, I chose the option to password protect access to it, and it works fine. Okay, so here's my question:

When I plug it in, I'm prompted for the password, with the options, Forget Password Immediately, Remember Password For This Session Only, Remember Password Forever. 

What does Remember Forever Do? Where is the password for this mobile device stored? (It's got to be on the USB drive, no???) If I choose Remember Forever, is there a way to undo that decision without reformatting the d*** thing? Why is there no information?

rtimai@HP-Pavilion-dv6-3012he:~$ help palimpsest
bash: help: no help topics match `palimpsest'.  Try `help help' or `man -k palimpsest' or `info palimpsest'.
rtimai@HP-Pavilion-dv6-3012he:~$ man palimpsest
No manual entry for palimpsest
rtimai@HP-Pavilion-dv6-3012he:~$ man gnome-disk-utility
No manual entry for gnome-disk-utility
rtimai@HP-Pavilion-dv6-3012he:~$ man palimpsest
No manual entry for palimpsest
rtimai@HP-Pavilion-dv6-3012he:~$ gnome-disk-utility --help
gnome-disk-utility: command not found
rtimai@HP-Pavilion-dv6-3012he:~$  man -k palimpsest
palimpsest: nothing appropriate.
rtimai@HP-Pavilion-dv6-3012he:~$ 
(info palimpsest returns a long info page for GNU utilities, with no mention of palimpsest)

Okay, that was four questions.

---

### Post by mc4man on 2013-07-01
There is a man & it appears to be fairly consistent to the app itself (don't be wearing out the down key
man gnome-disks

There are a number of udisks man's - one in screen may have some info (didn't read much...

As far as the 'remember forever', I'd say it means that for the current user selecting the option (who knew/entered the password

---

### Post by mc4man on 2013-07-02
In 12.10 you could simply install any needed packages in 12.10, get the 12.04 disk utilty packages & any additionally needed from 12.04 & install with dpkg. Maybe one can still use the 12.04 packages in 13.04/13.10, don't know, haven't tried. (5 -7 packages or thereabouts

For the moment did a quick build & checkinstall here on 13.04, will have to use awhile & see if any issues.
(if not will maybe do a ppa for gdu 3.0.2 in raring/saucy shortly

---

### Post by rtimai on 2013-07-03
> **mc4man said:**
> There is a man & it appears to be fairly consistent to the app itself (don't be wearing out the down key
man gnome-disks

There are a number of udisks man's - one in screen may have some info (didn't read much...

As far as the 'remember forever', I'd say it means that for the current user selecting the option (who knew/entered the password

Eh? Thanks, but -- come again? It looks like you bumped the send button before finishing your reply. To clarify, I'm not having a problem, just want to know what "remember forever" does, and if it can be undone without having to reformat the USB (flash) drive. Sometimes you can wipe the password setting stored in a file, but I have no clue where a password for a mobile device such as a USB drive is stored (it's got to be on the device itself, but I can't find anything like it.)

rtimai@HP-Pavilion-dv6-3012he:~$ udisk --help
No command 'udisk' found, did you mean:
 Command 'udisks' from package 'udisks' (main)
 Command 'fdisk' from package 'gnu-fdisk' (universe)
 Command 'fdisk' from package 'util-linux' (main)
 Command 'gdisk' from package 'gdisk' (universe)
udisk: command not found
rtimai@HP-Pavilion-dv6-3012he:~$ man udisk
No manual entry for udisk
rtimai@HP-Pavilion-dv6-3012he:~$ man gnome-disk
No manual entry for gnome-disk
rtimai@HP-Pavilion-dv6-3012he:~$ gnome-disks --help

(gnome-disks:3066): GLib-GIO-CRITICAL **: This application can not open files.

man gnome-disks returns a help menu that prompts you to press 'h' -- which gives a help page for LESS, no gnome-disks info. ???

Okay, I think I'm beginning to understand that Palimpsest is a GUI for gnome-disks (aka gnome-disk-utility, aka 'disks' in Ubuntu) and that gnome-disks depends on the udisk bus service. So, a trivial question like 'what does remember forever do?' leads to curiouser and curiouser.

---

