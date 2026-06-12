---
title: "X is buggered-- Feisty"
date: 2007-06-06
forum: General Help
---

### Post by tdoggette on 2007-06-06
I'm running Feisty on an old Dell Dimension 2350 with integrated Intel graphics. It's got a 17 inch CRT monitor running at 1024x768. I rebooted it (not for the first time) and it was suddenly at 640x480. I ran "sudo dpkg-reconfigure xserver-xorg" and ran through it on defaults. When I restarted X, it wouldn't start, saying that it was incorrectly configured. The text mode (as seen when restarting X or shutting down) has always been odd on this system, wrapping oddly and not displaying correctly, so it's very difficult to use.

How can I make my computer usable again?

---

### Post by tdoggette on 2007-06-06
anyone?

---

### Post by Crafty Kisses on 2007-06-06
> **tdoggette said:**
> I'm running Feisty on an old Dell Dimension 2350 with integrated Intel graphics. It's got a 17 inch CRT monitor running at 1024x768. I rebooted it (not for the first time) and it was suddenly at 640x480. I ran "sudo dpkg-reconfigure xserver-xorg" and ran through it on defaults. When I restarted X, it wouldn't start, saying that it was incorrectly configured. The text mode (as seen when restarting X or shutting down) has always been odd on this system, wrapping oddly and not displaying correctly, so it's very difficult to use.

How can I make my computer usable again?

You can try to recover your xorg.conf file by trying the following:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

---

### Post by NeoLithium on 2007-06-06
Do you remember which video driver you selected, or was using before?

---

### Post by Crafty Kisses on 2007-06-06
> **NeoLithium said:**
> Do you remember which video driver you selected, or was using before?

I got a question, it's really not relevant but do I have to do something else besides enable my drivers for my NVIDIA GeForce 6800?

---

### Post by tdoggette on 2007-06-06
> **Codename said:**
> You can try to recover your xorg.conf file by trying the following:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

Like an idiot, I didn't back up my xorg.conf. I figured that it wasn't worth much anyway, being at 640x480 anyway. Know where I could get a default copy or something?

Or, better yet, get dpkg-reconfigure xserver-xorg to give me something usable.

EDIT: I just ran the aforementioned utility. If selecting something from the initial list will help, I'll need to know how many from the bottom it is-- I can't see. Eh heh.

---

### Post by NeoLithium on 2007-06-06
> **tdoggette said:**
> Like an idiot, I didn't back up my xorg.conf. I figured that it wasn't worth much anyway, being at 640x480 anyway. Know where I could get a default copy or something?

Or, better yet, get dpkg-reconfigure xserver-xorg to give me something usable.

Try using the Vesa driver and a bare minimum setup for it. (Vesa is usually the safe driver IIRC).  That might be able to get you inside a base xorg.conf.

---

### Post by NeoLithium on 2007-06-06
> **Codename said:**
> I got a question, it's really not relevant but do I have to do something else besides enable my drivers for my NVIDIA GeForce 6800?

I'm not an expert with the NVIDIA stuff, though [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  should be able to help you out with a walkthrough to see if you have anything additional you need to do. Or there are probably a few howto's if you search through the forums.

---

### Post by Crafty Kisses on 2007-06-06
> **NeoLithium said:**
> I'm not an expert with the NVIDIA stuff, though [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  should be able to help you out with a walkthrough to see if you have anything additional you need to do. Or there are probably a few howto's if you search through the forums.

Thanks man!

---

### Post by NeoLithium on 2007-06-06
No problemo :)

---

### Post by tdoggette on 2007-06-06
Could someone find out how many up the list vesa is from the bottom? Like I said, I can't see. Thanks.

---

### Post by NeoLithium on 2007-06-06
Oh bugger, the resolution is even off in the command line? Perhaps you might want to try booting with the option VGA=791. That should make it better when you try to get your xorg back up and running.

Edit - I'm just unable to go and check to count right now, so hopefully that will work if you cant' get someone that will be able to help you find it

---

### Post by Crafty Kisses on 2007-06-06
> **tdoggette said:**
> Could someone find out how many up the list vesa is from the bottom? Like I said, I can't see. Thanks.

I'Il look around. :p

---

### Post by tdoggette on 2007-06-06
> **NeoLithium said:**
> Oh bugger, the resolution is even off in the command line? Perhaps you might want to try booting with the option VGA=791. That should make it better when you try to get your xorg back up and running.

Edit - I'm just unable to go and check to count right now, so hopefully that will work if you cant' get someone that will be able to help you find it


The resolution's always been off in the command line. BIOS is fine, GRUB is fine, and when it gets into the OS, it's all screwy.

How can I make it boot as described above?

EDIT: that is, with said option

---

### Post by tdoggette on 2007-06-07
Can anyone help me, either by giving me a walkthrough to a usable desktop, or even telling me how many spots from the bottom "vesa" is on the list?

---

### Post by djchandler on 2007-06-07
> **tdoggette said:**
> Can anyone help me, either by giving me a walkthrough to a usable desktop, or even telling me how many spots from the bottom "vesa" is on the list?

One of the advantages of being a "Spare Hardware Guy" is that I usually have some spare something or other laying around (until my wife makes me take it to the re-cycler.) Any chance you can get your hands on another monitor? I'm more than a little suspicious that you are about to see blue smoke come out its backside, or nothing but a blank screen. Maybe a friend will let you borrow theirs until you get this thing solved. In the Kansas City area, our Surplus Exchange has 17" monitors for $30 or less, probably $10 for a 15".

---

### Post by tdoggette on 2007-06-07
I've got a spare 15" somewhere. I'll dig it up and see if it improves at least the text mode, but I still have no idea how to get X working.

---

### Post by tdoggette on 2007-06-07
No improvement with the 15", but both monitors work with a dusty old WinXP install. Perhaps a driver problem?

I booted into "recovery mode", which is at least looking like a usable command line as it checks my hard drive.

---

### Post by tdoggette on 2007-06-07
As near as I can figure, my best bet is recovery mode. It gives med a clear, visible command line as root.

How can I go from that to something that I can use? I need help.

---

### Post by djchandler on 2007-06-08
> **tdoggette said:**
> As near as I can figure, my best bet is recovery mode. It gives med a clear, visible command line as root.

How can I go from that to something that I can use? I need help.

Ok, this will get you a new xorg.conf and you'll at least get back to square one.
I have a lot of time on my hands, so you're not that special other than you've given me something to do. I do appreciate it.

Kill all processes and shutdown. Now boot from your regular Ubuntu Feisty Install CD. When you get to the desktop, put a formatted floppy in the floppy drive. (I sent a personal message to you, but I'm going ahead and posting this anyway.) Go to the top menu bar, got to **Places** and select anything so a Nautilus window comes up. This should also automatically mount the floppy and anything else including your hdd.

Browse to /etc/X11 under filesystem, not your hard drive. You won't have permission to write to hdd unless you have a shared folder with absolutely no restrictions on it. Find xorg.conf and copy to the floppy root directory. Unmount floppy, and reboot from you hdd after removing the CD. 

Digression

One of the reasons it takes a long time to boot the install CD is it must create temporary writable areas for the necessary files to launch x-windows and the GUI, including creating a brand new xorg.conf among other interesting little things.

End Digression

Now comes the *fun* part!

Log-in as yourself. I suppose you can log in as root if you can, and it will simplify things slightly.

Follow these steps: (Substitute your account name for "you" and your system name for "yourbox."

[B]you@yourbox:~$ cd ..
you@yourbox:/home$ cd ..
you@yourbox:$ mount /dev/fd0
you@yourbox:$ cd media
you@yourbox:/media$ ls
cdrom  cdrom0  floppy  floppy0
you@yourbox:/media$ cd floppy
you@yourbox:/media/floppy$ ls
xorg.conf
you@yourbox:/media/floppy$ sudo cp xorg.conf /etc/X11/
Password:
you@yourbox:/media/floppy$[/B]

If something went wrong, you won't get back to the command prompt without an error message. If you want to make sure the new file has been copied, do the following:

[B]you@yourbox:/media/floppy$ cd ..
you@yourbox:/media$ cd ..
you@yourbox:$ cd /etc
you@yourbox:/etc$ cd /X11
you@yourbox:/etc/X11$ ls x*
xorg.conf

xinit:
xinitrc  xinput.d  xserverrc

xkb:
compat      geometry      keycodes.dir  rules          symbols      types.dir
compat.dir  geometry.dir  keymap        semantics      symbols.dir  xkbcomp
compiled    keycodes      keymap.dir    semantics.dir  types

xserver:
SecurityPolicy
you@yourbox:/etc/X11$[/B]

After that, kill all processes and shutdown, and re-boot from your hdd with your new xorg.conf file.

If something goes awry, let me know.

Good Luck!

Regards,
D. J. Chandler

PS This may also work with USB media, but I'm not sure how to get to it from the command prompt. Maybe somebody else can help with that. I'm done until tomorrow.

---

