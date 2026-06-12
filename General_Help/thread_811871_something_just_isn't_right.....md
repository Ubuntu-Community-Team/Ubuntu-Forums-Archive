---
title: "something just isn't right...."
date: 2008-05-29
forum: General Help
---

### Post by Aesir09 on 2008-05-29
I installed 8.04 a week ago and everything has been going fine, until i noticed how weird and sluggish firefox is, 

the scrolling is horrible, i uninstalled the "Grab and Drag" extension and it didn't help. 

>  Firefox is linux based so why does it run slow!!1!?

i also have installed kubuntu-desktop and kde 4 via terminal and ive already "removed" them says the terminal.

well they are still there, halp!

i just want ubuntu (mainly firefox) to run as smoothly as vista does on my laptop. 

any ideas? thanks

PS: can you appeal a name change on ubuntuforums?

---

### Post by cdenley on 2008-05-29
Are you sure your problem is specific to firefox? What video driver are you using?
```

cat /var/log/Xorg.0.log|grep LoadModule

```
Are "Visual Effects" enabled?
System>Preferences>Appearance

Did you try firefox2?
```

sudo apt-get install firefox-2
firefox-2

```

> i also have installed kubuntu-desktop and kde 4 via terminal and ive already "removed" them says the terminal.

well they are still there, halp!
If apt says they're removed, what makes you think they're not? kubuntu-desktop is a meta-package, and kde4 might as well be. You can still have a fully functional KDE desktop without those packages. This command should remove the other KDE packages if they were installed dependencies.
```

sudo apt-get autoremove

```

---

### Post by Aesir09 on 2008-05-29
thanks i will try these, and also i want Firefox 2, but how do i remove the Firefox 3 beta? **also i want to keep all my firefox settings/bookmarks etc**

[B][COLOR="Red"]it seems it removed all settings anyways. i installed 2 and removed beta 3 and it didn't backup anything :/[/COLOR]
[size=3] wait the  extensions are still in the add ons window but i can do anything with them, when i click on preferences (for the extension) it does nothing, so maybe i can save myself some time and change something?[/size]

oh well. seems to run a little smoother though.[/B]

here you go:

```

dom@WarMachine:~$ cat /var/log/Xorg.0.log|grep LoadModule
(II) LoadModule: "pcidata"
(II) LoadModule: "glx"
(II) LoadModule: "extmod"
(II) LoadModule: "dbe"
(II) LoadModule: "freetype"
(II) LoadModule: "record"
(II) LoadModule: "dri"
(II) LoadModule: "fglrx"
(II) LoadModule: "synaptics"
(II) LoadModule: "mouse"
(II) LoadModule: "kbd"
(II) LoadModule: "vgahw"
(II) LoadModule: "int10"
(II) LoadModule: "vbe"
(II) LoadModule: "fglrxdrm"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "fb"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) LoadModule: "xaa"
(II) LoadModule: "fglrxdrm"

```

yes visual effects are enabled but when do:
```

metacity --replace
```
**i just did it and it closed firefox?**

and things are fairly smoother thanks! i wish they were even more though, **how can i change my scroll step?**

and thanks i did
```
sudo apt-get autoremove
```

and it seems -_-
firefox crashed again lol.

ok but once i install firefox 2 how do i remove 3 beta 5?

thanks alot for the help btw

---

### Post by cdenley on 2008-05-29
> 
ok but once i install firefox 2 how do i remove 3 beta 5?

You can leave them both installed, but if you want to remove firefox-3...
```

sudo apt-get remove firefox-3.0

```
You will have to edit the properties for the firefox launcher at the top, if you want it to launch firefox-2.

Your firefox-3 profile will not work in firefox-2, but will still work in firefox-3. You can always open firefox-3, export bookmarks, close firefox-3, open firefox-2, import bookmarks.

You can try disabling ATI's proprietary video driver.
System>Administration>Hardware Drivers
Maybe the open-source ati driver will work better. I think this usually isn't the case, though. If you have a newer video card, it might not work at all.

---

