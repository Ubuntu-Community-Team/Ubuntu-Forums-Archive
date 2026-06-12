---
title: "Noob needing help"
date: 2008-02-14
forum: General Help
---

### Post by Nevermind042 on 2008-02-14
Hi, I recently installed Ubuntu 7.10 on my laptop and I believe I may have done something wrong.

When it boots up, it displays a MS DOS looking prompt (just white text on black background) asking me for my username and login. When I do this, it sits there saying 

nevermind@Laptop:~$ _

I'm not sure why my Ubuntu doesn't look like the ones in the gallery here or ANY of the screencaps I've seen of it... what did I do wrong and how can I fix it?

---

### Post by mozetti on 2008-02-14
For some reason, your X session (X is the GUI program/server for Ubuntu/Linux) isn't starting. Normally, the GUI would come up and the desktop would load automatically when you login. If you don't use a GUI, or don't set it to autostart, then you get what you're seeing now. It's the command-line interface (CLI) and is basically barebones Linux without the GUI.

To start, could you please tell us about your laptop: brand, model, any info you have about the hardware, especially your video card.

Also, what method did you use to install Ubuntu? Was it a regular LiveCD, the Alternate CD, or did you install the Server edition?

I'm not very advance, but I think the command you type to get the GUI to start up is ```
sudo startx
```

Someone else will probably be by in a bit with some more knowledge, but the info I asked you for should help them get a better answer for you, too.

---

### Post by Nevermind042 on 2008-02-14
It's a crappy old laptop I got for free. It's a Gateway Solo 5300. It can handle Windows XP Pro, so I would assume that it would have no issues with Ubuntu. The DVD rom drive broke a long time ago and it would be cheaper to replace the entire laptop than to replace the drive, so I installed Ubuntu via the "install from network" link I found somewhere.

---

### Post by Nevermind042 on 2008-02-14
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

this is what I used to install ubuntu

Also, I tried running the command you suggested, it says:
> xauth:   creating new authority file /home/nevermind/.serverauth.4436
X:  cannot stat /etc/X11/X (No such file or directory), aborting.
xinit:   Server error.
nevermind@Laptop:~$ _

Letter for letter. It's weird that it says "Cannot stat" instead of "Cannot start"...

---

### Post by Nevermind042 on 2008-02-14
After reading for a bit, I have deduced that "gnome" is what I'm missing.

I don't recall exactly what command I used, but it was something like "sudo apt-get install gnome"

I'm installing that and we'll see if it works from there.

---

### Post by Nevermind042 on 2008-02-14
no dice, it installed something but still won't load.

says I need "get-edid" and "discover"....

I installed discover with "sudo apt-get install discover", but neither "sudo apt-get install get-edid" nor "sudo apt-get install edid" work.

Please help!

---

### Post by mozetti on 2008-02-14
try ```
sudo aptitude install ubuntu-desktop
```

That should download everything you need for a working GUI, including gnome. If you don't run through a setup process with a blue background dealing with your video, like video card, monitor, resolution during or after everything installs, then try ```
sudo dpkg-reconfigure xserver-xorg
```. That will run through the xserver configuration. After you do all that, restart the computer and see what happens.

---

### Post by Nevermind042 on 2008-02-14
> **mozetti said:**
> try ```
sudo aptitude install ubuntu-desktop
```

That should download everything you need for a working GUI, including gnome. If you don't run through a setup process with a blue background dealing with your video, like video card, monitor, resolution during or after everything installs, then try ```
sudo dpkg-reconfigure xserver-xorg
```. That will run through the xserver configuration. After you do all that, restart the computer and see what happens.
It's going slowly, only about 365kb/s. Give me about 15 mins and I'll report back.

Edit: Also, another question that I cant' seem to find an answer for...

Will I be able to network via folders with my Windows XP computers? (IE use the "Shared Documents" folder)

---

### Post by fyo on 2008-02-14
> **Nevermind042 said:**
> no dice, it installed something but still won't load.

says I need "get-edid" and "discover"....

I installed discover with "sudo apt-get install discover", but neither "sudo apt-get install get-edid" nor "sudo apt-get install edid" work.

Please help!

It seems like A LOT of stuff wasn't installed.

Fortunately, it's quite easy to get a list of installed packages:

```
$ dpkg --get-selections
```

That should spit out quite a lengthy list, probably too much to just post here. You might want to just try installing xorg:

```
sudo apt-get install xorg
```

Personally, I would be very temped to start over using the "official" Ubuntu network install procedure, as described in the Wiki:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

Oh, and just for reference, the "stat" thing previously is not a misspelling of "start". The program "stat" gets information about the status of a file. In this case, it wasn't possible to "stat" the directory (folder) in question, because it didn't exist (and this error information was included in the output).

---

### Post by fyo on 2008-02-14
> **Nevermind042 said:**
> Edit: Also, another question that I cant' seem to find an answer for...

Will I be able to network via folders with my Windows XP computers? (IE use the "Shared Documents" folder)

Yes, it's called "Samba".

---

### Post by Nevermind042 on 2008-02-14
> **fyo said:**
> It seems like A LOT of stuff wasn't installed.

Fortunately, it's quite easy to get a list of installed packages:

```
$ dpkg --get-selections
```

That should spit out quite a lengthy list, probably too much to just post here. You might want to just try installing xorg:

```
sudo apt-get install xorg
```

Personally, I would be very temped to start over using the "official" Ubuntu network install procedure, as described in the Wiki:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

Oh, and just for reference, the "stat" thing previously is not a misspelling of "start". The program "stat" gets information about the status of a file. In this case, it wasn't possible to "stat" the directory (folder) in question, because it didn't exist (and this error information was included in the output).

Thanks for the information, but I don't have a floppy drive for it either. The bay sits empty currently and I don't see that changing in the near future.

---

### Post by fyo on 2008-02-14
Okay then... here's a better way:

Make a bootable USB flash device with Ubuntu on it. Most people seem to have a USB "pen drive" lying around somewhere.

If it's a reasonably large one (i.e. >700MB), you can just download the normal CD image file and use that. If it's a small one, you could use the previous "floppy disk" approach.

---

### Post by Nevermind042 on 2008-02-14
> **mozetti said:**
> try ```
sudo aptitude install ubuntu-desktop
```

That should download everything you need for a working GUI, including gnome. If you don't run through a setup process with a blue background dealing with your video, like video card, monitor, resolution during or after everything installs, then try ```
sudo dpkg-reconfigure xserver-xorg
```. That will run through the xserver configuration. After you do all that, restart the computer and see what happens.

Worked like a charm!

Only, when I go to update or create new users, it says I don't have permission, yet mine is the only listed user account.

Is there an admin or root account I have to mess with?

---

### Post by Nevermind042 on 2008-02-14
Still can't update Ubuntu due to lack of permission... any ideas?

---

### Post by mozetti on 2008-02-19
Not sure if you're still checking, but in Ubuntu you use this before the command:```
sudo
```
This gives you temporary super-user (root) rights. Sudo stands for Super-User do.

So, to update you run:```
sudo aptitude update
sudo aptitude upgrade
```

To install anything you run:```
sudo aptitude install <package name>
```

---

