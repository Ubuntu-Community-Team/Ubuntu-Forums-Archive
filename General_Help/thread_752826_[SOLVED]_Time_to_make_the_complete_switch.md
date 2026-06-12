---
title: "[SOLVED] Time to make the complete switch"
date: 2008-04-12
forum: General Help
---

### Post by dstein on 2008-04-12
I'm finally ready to make the complete switch - by complete I mean removing Windows from my system and using Ubuntu as my sole operation system. I know this is not necessary, but I would prefer to have the storage space for better usage. Before doing so, I have a few questions:

- Is there anyway to transfer my Windows files, such that the ASCII files are reformatted with Unix Newlines (which I think is LF as opposed to CRLF) and renamed such that the .txt appendage is removed? I would like this to be done automatically during the transfer of files.

- I have always used NERO for CD burning in Windows. Is there any Linux alternative?

- What are some good packages for burning/copying DVDs?

Thanks.

---

### Post by NightwishFan on 2008-04-12
Ubuntu Hardy comes with Brasero to burn, but there are a good many others I am sure. Just check the add/remove programs for such software, there is likely everything you need.

---

### Post by pbpersson on 2008-04-12
The package to burn CDs and DVDs in Linux is called K3B and it is very good, every bit as friendly as Nero, at least I thought so.

When it comes to ripping I will let someone else respond, I have not done that yet in Linux.

Edit to Add:  There is something called KAudioCreator here on my machine that claims it is a multi-purpose ripping application but I have never tried it

You can go to Synaptic and search on ripping and I'm sure it will give you an entire list of apps you can use for that.

---

### Post by harrybazeegar on 2008-04-12
There are a few things you might want to consider:

> [I know this is not necessary, but I would prefer to have the storage space for better usage.

You use your storage without having to erasing your windows install you know... and if I am not wrong, Ubuntu 7.10 mounts NTFS drives to be Read-Write enabled ( I myself use Ubuntu 7.04 and ntfs-3g driver )
So you dont actually need to nuke out Windows.

*But* if you really want the *feel* of having removed Windows, then follow these steps *Carefully*:
1. open up a terminal
2. go to /boot/grub
3. from now on... use sudo with all commands ( or just login as root, whatever you prefer)
4. backup the *menu.lst* file
5. now open up *menu.lst* file in your favourite editor
6. look for a set of entries that say:
```
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

7. put a '#' in front of all these lines ( that is, make them comments )
8. in the beginning of this file, there is a line 
```

default <some number>

```
replace this number with *0*
8. Voila! now when you boot up and see your boot menu, you wont see windows listed at all!!

This way you know that in some _reeeaal_ emergency that you are just not able to manage with Ubuntu you can fall back on the OS that you have lived with all your life.

> Is there anyway to transfer my Windows files, such that the ASCII files are reformatted with Unix Newlines (which I think is LF as opposed to CRLF)

well most of the popular text editors recongnize the encoding to be Ascii when you open these files... so you *don't need* to do this as such... but if this is really a personal vendetta of yours ( :P ) then... sorry cant help u :)

> I have always used NERO for CD burning in Windows. Is there any Linux alternative

There are three alternatives that I know of:
1. Gnome Baker - the CD/DVD burning software for GNOME
2. K3B - same, only built for KDE
3. Nero Linux - linux version of her CD/DVD burning software from Nero - the undisputed ruler of buring market 

these softwares will allow you to copy CD and DVDs too, just so you know...

---

