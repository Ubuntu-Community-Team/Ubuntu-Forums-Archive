---
title: "how to get a pretty load screen"
date: 2004-11-05
forum: General Help
---

### Post by puzzledm on 2004-11-05
I would like to know how to get a pretty load screen rather than all those lines of scary writing that I know will freak my parents out if I put Ubuntu on their computer.

It would be nice to have a mandrake style - press F2 for verbose mode - sort of thing but otherwise a nice ubuntu picture to make it all clean.

Does anybody have any ideas?

---

### Post by xsos on 2004-11-05
helo, sory couldn't get your messege..

there is group booting screen, or gnome splash screen.
sorry.

---

### Post by Rancoras on 2004-11-05
Hoary will probably add a bootsplash to the mix.

---

### Post by HiddenWolf on 2004-11-13
Eagerly awaiting it.

---

### Post by Magneto on 2004-11-13
[QUOTE=puzzledm]I would like to know how to get a pretty load screen rather than all those lines of scary writing that I know will freak my parents out if I put Ubuntu on their computer.

It would be nice to have a mandrake style - press F2 for verbose mode - sort of thing but otherwise a nice ubuntu picture to make it all clean.

Does anybody have any ideas?[/QUOTE]

you can do it yourself now - just patch your kernel ,recompile your kernel appropriately and add an image to grub

here's directions
[http://www.desktop-linux.net/bootsplash.htm](http://www.desktop-linux.net/bootsplash.htm)

---

### Post by saBrEwolf on 2004-11-23
This has confused me.. how come the LiveCD version of warty has bootsplash, whereas the install version doesn't? Would there be a way to perhaps copy it over from the LiveCD.. or is it actually there as the option is there, just with splash written on the end instead of just quiet like on the Live disc.

Just a thought

---

### Post by oddabe19 on 2004-11-23
The live cd isn't necessarily Ubuntu. It's based off of Morphix (which patches it's kernel with a boot splash)... it's morphix with a ubuntu look/feel.

The boot splash screen (like what fedora/mandrake, suse, whoever) is a kernel thing.  If you patch your kernel, and recompile it, you should have it, but it sounds like you're just starting, so i wouldn't recommend it.

IT IS planned for Hoary (4.05) the next release. it wasn't released in time for Warty.

did that help?

---

### Post by arctic on 2004-11-23
i think waiting till hoary ships with a bootsplash is not the worst thing that happens... ;)

---

### Post by Magneto on 2004-11-23
Yes setting it up is not for the unintiated. I have it working with fbsplash and an Ubuntu theme I made, just have to get the progress bar working- id post a screenshot but fbgrab doesn't want to cooperate.

---

### Post by p!=f on 2004-11-23
Compiling the kernel with the bootsplash support won't make it to work. You also need to patch your rc and rcS scripts found in /etc/init.d.
Anyway, bootsplash is a beast. It may break some things.
I would recommend to wait for usplash which won't require any kernel patching which means it will be 100% in userspace.
More info here:
[http://www.ubuntulinux.org/wiki/USplash](http://www.ubuntulinux.org/wiki/USplash)

---

### Post by Magneto on 2004-11-23
[QUOTE=p!=f]Compiling the kernel with the bootsplash support won't make it to work. You also need to patch your rc and rcS scripts found in /etc/init.d.
Anyway, bootsplash is a beast. It may break some things.
I would recommend to wait for usplash which won't require any kernel patching which means it will be 100% in userspace.
More info here:
[http://www.ubuntulinux.org/wiki/USplash](http://www.ubuntulinux.org/wiki/USplash)[/QUOTE]
 Im not using bootsplash- im using fbsplash/gensplash  Yeah I know about   actually setting it up bootsplash/fbsplash is pretty easy - easier in gentoo than debian but still easy. I had issues with the framebuffer drivers and my specific hardware.

Usplash looks interesting but I wouldnt wait. I don't like how debian does kernels so I make my own patched kernels anyway. fbsplash is heading to userspace too I believe -  many people working on better mousetraps in this instance
Bootsplash and FBsplash don't break anything that I have seen- my radeon video card and all the present framebuffer drivers only like to display at the optimum resolution so that was an issue but vesafb, vesafb-tng and radeonfb share this problem- i think its my vid card's bios

Do you know the progress on usplash? I didnt see a timeline- is it the hoary release in april?

---

### Post by BWF89 on 2004-11-23
[QUOTE=puzzledm]I would like to know how to get a pretty load screen rather than all those lines of scary writing that I know will freak my parents out if I put Ubuntu on their computer.[/QUOTE]
I think it's really cool that Linux has all that code running across the screen. It's alot more interesting than watching the progress bar run across the screen like Win XP...

---

### Post by saBrEwolf on 2004-11-24
[QUOTE=oddabe19]The live cd isn't necessarily Ubuntu. It's based off of Morphix (which patches it's kernel with a boot splash)... it's morphix with a ubuntu look/feel.

The boot splash screen (like what fedora/mandrake, suse, whoever) is a kernel thing.  If you patch your kernel, and recompile it, you should have it, but it sounds like you're just starting, so i wouldn't recommend it.

IT IS planned for Hoary (4.05) the next release. it wasn't released in time for Warty.

did that help?[/QUOTE]

Ahh, that explains it, after exploring the disc I noticed the Morphix directory

The boot splash that Fedora uses is actually just an X based program called rhgb

After reading through this post, I think I'll just wait for the hoary release, I'm not a newbie, but I'm not all that experienced when it comes to kernel patching and the like.

Thanks for the help

---

### Post by p!=f on 2004-11-24
[QUOTE=Magneto]
Usplash looks interesting but I wouldnt wait. I don't like how debian does kernels so I make my own patched kernels anyway.[/QUOTE]
I see. :) 
Which patchset/patches you use? Just curious.
I use CKO patchset, the "Con Kolivas patchset based overloaded kernel"
[http://kem.p.lodz.pl/~peter/cko/](http://kem.p.lodz.pl/~peter/cko/)
It already contains fbsplash and vesa-tng but I experience some annoying troubles with nVidia drivers and TVout on the console when both used.
Anyway, I think, Spock is doing great job.
[QUOTE=Magneto]
Bootsplash and FBsplash don't break anything that I have seen- my radeon video card and all the present framebuffer drivers only like to display at the optimum resolution so that was an issue but vesafb, vesafb-tng and radeonfb share this problem- i think its my vid card's bios
[/QUOTE]
Glad to hear you're the lucky one. :)
[QUOTE=Magneto]
Do you know the progress on usplash? I didnt see a timeline- is it the hoary release in april?[/QUOTE]
Unfortunately no. I'm all for the testing, tho. :) I hope we'll get some official word on this.

---

### Post by Magneto on 2004-11-24
[QUOTE=p!=f]I see. :) 
Which patchset/patches you use? Just curious.
I use CKO patchset, the "Con Kolivas patchset based overloaded kernel"
[http://kem.p.lodz.pl/~peter/cko/](http://kem.p.lodz.pl/~peter/cko/)
It already contains fbsplash and vesa-tng but I experience some annoying troubles with nVidia drivers and TVout on the console when both used.
Anyway, I think, Spock is doing great job.

Glad to hear you're the lucky one. :)

Unfortunately no. I'm all for the testing, tho. :) I hope we'll get some official word on this.[/QUOTE]

Yeah I use ck too, Id been using an entire kernel source version though and the fbsplash patch was taken out so I had to redo it.
Yeah I can only get fbsplash with radeonfb and that wont work with atitvout i dont think 
Yeah Spock is one bad polak- i think he's only 18 too
Yeah I wouldnt mind testing the Ubuntu version either beats having to use radeonfb like this

---

### Post by wallijonn on 2004-11-25
[http://www.tldp.org/LDP/LG/current/jayanth.html](http://www.tldp.org/LDP/LG/current/jayanth.html)

sudo gedit /boot/grub/menu.lst :
```

splashimage=(hd0,0) /boot/grub/splash.xpm.gz
title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

```

[http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)

[http://ruslug.rutgers.edu/~mcgrof/grub-images/checksplash.sh](http://ruslug.rutgers.edu/~mcgrof/grub-images/checksplash.sh) :

```

# sudo sh checksplash.sh
Your stage2 file seems to support splashimages
Splashimage support found
#

```

So it seems that splashimages are supported in Ubuntu.



.

---

### Post by Magneto on 2004-11-25
[QUOTE=wallijonn]
So it seems that splashimages are supported in Ubuntu.



.[/QUOTE]
 yeah for grub but not framebuffer
this thread is about Framebuffer splash  aka bootsplash & gensplash

---

### Post by wallijonn on 2004-11-25
Magneto,

You're absolutely right. I tried it and it just wouldn't work. I'm sorrry if I lead any astray.

---

### Post by Magneto on 2004-11-25
? wouldn't work? that's weird I have splashimage set in grub and have a nice ubuntu picture as my grub menu background-  but that wont put a background on a console -

---

### Post by wallijonn on 2004-11-26
Yeah, I did the 640x480 / 14 colour / xpm / gzip thing and it wouldn't come up with a picture - the video was all garbled. At mid point boot (half way through the boot process) I was able to actually read the characters that were on the screen.

---

### Post by piedamaro on 2004-11-26
> The boot splash screen (like what fedora/mandrake, suse, whoever) is a kernel thing.

Plain wrong. It's an X server.

---

### Post by Magneto on 2004-11-26
yeah ive seen that before  when tryin to get my own images working- have you tried with another gzipped xpm that is known to work?

---

