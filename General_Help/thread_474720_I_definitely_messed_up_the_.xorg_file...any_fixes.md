---
title: "I definitely messed up the .xorg file...any fixes?"
date: 2007-06-15
forum: General Help
---

### Post by Tekee on 2007-06-15
I'm a new user with Ubuntu, so seeing as I didn't know what I was doing, I attempted editing the .xorg to run widescreen, but now whenever I boot up Ubuntu, I get a command prompt type screen (no graphical login) and am not quite sure what to do.

It also gives me something like "Problem with X" or something of the sort.  It also lets me look at the error that won't let it run, and I noticed that the error was exactly what I had edited.
Is there some sort of way to redownload the .xorg through the terminal that I'm at?

Thanks for the help.

EDIT:  Yes, I realize I was oblivious enough not to back it up before editing it, but that's what I get for being a noob, right?

---

### Post by statictonic on 2007-06-15
> **Tekee said:**
> I'm a new user with Ubuntu, so seeing as I didn't know what I was doing, I attempted editing the .xorg to run widescreen, but now whenever I boot up Ubuntu, I get a command prompt type screen (no graphical login) and am not quite sure what to do.

It also gives me something like "Problem with X" or something of the sort.  It also lets me look at the error that won't let it run, and I noticed that the error was exactly what I had edited.
Is there some sort of way to redownload the .xorg through the terminal that I'm at?

Thanks for the help.

EDIT:  Yes, I realize I was oblivious enough not to back it up before editing it, but that's what I get for being a noob, right?

On the command line type "sudo nano /etc/X11/xorg.conf" you will then be able to edit the file, just set the resolution back to what it was.  You may have a backup in the folder anyhow though.
"cd /etc/X11" then type "ls" see if u can any backup files in there if u do, you can copy them in place of xorg.conf  EX: "sudo cp xorg.conf.original-0 xorg.conf"

If you need a web browser you can use lynx "sudo apt-get install lynx" will install it for you, otherwise if u need simple file downloads only just use "wget http://whereever"

---

### Post by mopey on 2007-06-15
When I delete my xorg file I usually just put in a live cd (an ubuntu disk would be fine).

I mount the hard drive.  Something like $mount /dev/hda1 /media.  Or if you have a knoppix disc there it is graphical and you can just right click and say 'mount'.

Then you can copy the live cd's xorg file (usually in /etc/X11/xorg.conf) to the xorg.conf cd on your hard drive (which you just mounted at /media, so it would be /media/etc/X11/xorg.conf).

so

```

cp /etc/X11/xorg.conf /media/etc/X11/xorg.conf

```

---

### Post by dannyboy79 on 2007-06-15
you can simply rerun the xserver config program from the command line after logging in, the command is:
sudo dpkg-reconfigure xserver-xorg
Now, it will ask you many many questions that you will probably not have any idea how to answer, make sure you  read every single page and answer the things that you can, like the driver you want to use (if you only want to get back into the gui, use "vesa"), you'll be able to answer the resolutions choices for your card (use arrows up and down, then hit space bar to chose resolutions you know work for your card), and just select the defaults for anything you don't know and everything will be fine! then aafter that's done, you would type in these 2 commands seperately

sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm start
then log in!

---

