---
title: "Can't load Recovery Mode -- starts to load and never finishes"
date: 2007-08-08
forum: General Help
---

### Post by DSDxp on 2007-08-08
I'm new to linux so I really don't know whats going on.  My original problem was after I installed ubuntu, I can't get into it because the screen goes blank on my laptop as ubuntu is trying to load.  After doing some research I found that I may have to edit xorg.conf.  The only way to edit this that I know of is through recovery mode.

When I try loading recovery mode from Grub, it starts loading and I see several lines of text explaining different things its doing.  It stops after the last two lines and just sits there and nothing ever ends up loading.

here are the last 2 lines it loads:

[0.000045] CPU # 0 had -105 usecs TSC skew, fixed it up.
[0.000096] CPU # 1 had 105 usecs TSC skew, fixed it up.

I'm not sure what those mean, or if thats why its not loading any further, but it does not load past that.

I have a HP Pavilion dv6000 laptop with:
AMD Turion 64 X2, nvidia geforce go 6150, 2gb memory

Any help is appreciated!!

---

### Post by DSDxp on 2007-08-08
maybe there's another way to edit the xorg.conf file?  if there's a way to edit it from within windows that would be great, but i dont even see any of the linux files when i look on my hard drive from within windows.  i'm good with computers, but have never used linux ever so im not sure what to do here.

---

### Post by apetresc on 2007-08-08
> **DSDxp said:**
> maybe there's another way to edit the xorg.conf file?  if there's a way to edit it from within windows that would be great, but i dont even see any of the linux files when i look on my hard drive from within windows.  i'm good with computers, but have never used linux ever so im not sure what to do here.

I'm not sure what's causing your problem (not even Google does! :o) But I can help you with editing your xorg.conf file from Windows. The reason you can't do it by default is because Linux's default filesystem (ext3 most likely) is not recognized by Windows. You need to install an ext3 driver. Fortunately this is easily done. Just install this and follow its instructions: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by dabl on 2007-08-08
When you attempted to boot normally, and got the black screen, did you try Ctrl-Alt-F1, to open a "virtual console"?

If that works for you, then here's the rest of what you need to do: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

HTH  :)

---

### Post by DSDxp on 2007-08-08
> **dabl said:**
> When you attempted to boot normally, and got the black screen, did you try Ctrl-Alt-F1, to open a "virtual console"?

If that works for you, then here's the rest of what you need to do: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

HTH  :)

Just tried ctrl-alt-f1 during the normal startup and nothing happens.  tried it during the recovery mode also and still nothing.  when it goes to a blank screen after the loading screen of normal startup, i do not ever hear any sound that its loading or anything else, its just a blank screen and nothing happens.

---

### Post by DSDxp on 2007-08-08
> **AdrianP said:**
> I'm not sure what's causing your problem (not even Google does! :o) But I can help you with editing your xorg.conf file from Windows. The reason you can't do it by default is because Linux's default filesystem (ext3 most likely) is not recognized by Windows. You need to install an ext3 driver. Fortunately this is easily done. Just install this and follow its instructions: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Downloaded that and can now see and open the xorg.conf file (using notepad).  now the question is, how can I edit it.... its pretty much a jumble of different things.  some of the other posts say when using nano, type "nano -Bw /etc/X11/xorg.conf" to fix video issues, but thats assuming that you can get to the console.  any ideas how to perform that while looking at the file in notepad?  thanks for the help!

---

### Post by apetresc on 2007-08-08
> **DSDxp said:**
> Downloaded that and can now see and open the xorg.conf file (using notepad).  now the question is, how can I edit it.... its pretty much a jumble of different things.  some of the other posts say when using nano, type "nano -Bw /etc/X11/xorg.conf" to fix video issues, but thats assuming that you can get to the console.  any ideas how to perform that while looking at the file in notepad?  thanks for the help!

Don't open it using Notepad; notepad only works with Windows-style line endings (which Linux obviously does not use). However, Wordpad will work fine (and it is also included with Windows IIRC).

If you want, post your xorg.conf file here, along with some information about your video card, and we'll take a look to see if it's alright.

---

### Post by DSDxp on 2007-08-08
> **AdrianP said:**
> Don't open it using Notepad; notepad only works with Windows-style line endings (which Linux obviously does not use). However, Wordpad will work fine (and it is also included with Windows IIRC).

If you want, post your xorg.conf file here, along with some information about your video card, and we'll take a look to see if it's alright.

Sounds like a good idea.  I restarted my computer a min ago and now (in windows) when i try to open the partition with linux, windows tells me that the disk is not formatted and asks me to format it.  so i tried reiinstalling that program that allows you to see linux files and assigned a different drive letter to the linux partition but still get the same error.  so, now i cant even see the linux partition anymore...

this is a mess.

---

