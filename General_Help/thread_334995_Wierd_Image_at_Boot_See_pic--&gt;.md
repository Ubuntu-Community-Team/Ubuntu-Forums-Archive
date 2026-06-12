---
title: "Wierd Image at Boot? See pic--&gt;"
date: 2007-01-09
forum: General Help
---

### Post by featherking on 2007-01-09
Can anyone help me fix this issue? (see pic)

I am using Edgy Eft (upgraded from dapper and this was when this all began) I have reinstalled usplash and followed several different tutorials on how to customize usplash in an effort to change this picture but nothing seems to change the picture. I cannot remove usplash from apt because then it wants to remove the entire ubuntu-desktop.

i have run
```

sudo update-alternatives --config usplash-artwork.so
```
among other things, i have added vga=791 (among other numbers) but all those do is change the resolution of this image. 

Is there any way possible to fix it?

---

### Post by Sandlst on 2007-01-15
I would just like to say, that I too am experiencing this problem, Im running dapper, but have followed a guide ([here]("http://ubuntuforums.org/showthread.php?t=264883")) to get the edgy usplash in dapper.

---

### Post by featherking on 2007-01-16
Must be a really rare issue, 2 people out of millions experiencing it. I have tried everything i can think of, to no avail. It must be something to do with upgrading from dapper to edgy because you said you were just using the edgy bootsplash and i upgraded the whole system.

Still you would think out of all the upgrades that happened, someone would know how to fix?

---

### Post by virtual_zero on 2007-01-16
After I upgraded I experienced this problem as well. Sadly, I don't remember how I corrected it.

---

### Post by hikaricore on 2007-01-16
O.o that's the same splash screen from the beta and pre-beta releases of edgy before they added an actually splash image.  The only reason I can imagine it would be showing is that your usplash file is corrupt or made incorrectly.

---

### Post by featherking on 2007-01-17
Well aside from completely reinstalling usplash (complete removal also removes ubuntu-desktop) i cannot figure out how to change it. i have even followed guides on customizing it to a completely different picture

All things lead to the same result..., It really is a shame that virtual_zero cant remember how he fixed it

---

### Post by Littleweseth on 2007-01-17
For reference, if removing something uninstalls ubuntu-desktop, that's not really an issue - 'ubuntu-desktop' isn't really a package - it's a metapackage which has been made to depend on everything in the default ubuntu install (so that installing ubuntu-desktop is as easy as marking 'ubuntu-desktop' for installation.) It doesn't actually contain anything.

The same is true of other packages like ubuntu-base, kubuntu-desktop, edubuntu-desktop, and similar. Go ahead and aptitude purge usplash, aptitude install usplash.

---

### Post by featherking on 2007-01-17
i did not realize that, i am trying it now...

---

### Post by featherking on 2007-01-17
Well it did remove the picture, which it has never done before, but when i reinstalled usplash after rebooting and tried rebooting again, it was the same grey picture! Any ideas? a bad package was my first thought so i am going to delete the files in my apt cache and try installing usplash again.. 

Any ideas? please post

---

### Post by featherking on 2007-01-17
Still the same grey picture!! I dont even know where this file could be coming from, but completely removing usplash gives me a text boot up. But as soon as I install usplash-theme-ubuntu it goes to that wacky grey screen..

What is going on

---

### Post by featherking on 2007-01-18
it was suggested to me to run:

```
sudo update-initramfs -u
```

unfortunately this too yields the evil grey screen

---

### Post by featherking on 2007-01-19
SOLVED:

I was tipped off to a tool called [[COLOR="Red"]startup-manager[/COLOR]]("http://web.telia.com/~u88005282/sum/index.html") (whether this tool is really required or not, im not sure, keep reading) The tool manages grub/usplash settings in a gui window. I thought id try changing my usplash from within it, what the heck right?

Well when i went to the usplash setting screen, it listed my current usplash theme as 'usplash-fix'. ??? I have never heard of this 'usplash-fix' so i clicked to see my installed themes and my options were 'usplash-fix' and 'usplash-theme-ubuntu'. I have never seen this 'usplash-fix' file listed anywhere, never in update-alternatives or anything! So of course i removed it from my available themes and selected 'usplash-theme-ubuntu'.

The reason i say that startup-manager may not be required is i would think you could just search the harddisk for this usplash-fix (im pretty sure that was the exact name) and remove just the .so file and then usplash would default to the 'usplash-theme-ubuntu', however using startup-manager did work for me.

Now everything is in great working order!

---

### Post by frolle on 2007-01-19
Thank you for the fix :)

---

### Post by featherking on 2007-01-19
No problem!, which way did you fix it if i may ask? did you find this 'usplash-fix' file or did you just use startup-manager?

---

### Post by bartman on 2007-01-24
I had THE SAME problem on shutdown except that this testing image was split in half, see attachment.

The weird thing besides it being split in half was that on startup I would get the old Dapper all brown logo. After browsing through the forums I found this command:
```
$ sudo update-alternatives --config usplash-artwork.so
```
It produced no output! So i went and checked what was inside the folder /usr/lib/usplash. Empty?!
```
$ aptitude search usplash
...
$ sudo aptitude install usplash-theme-ubuntu
...
$ sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
```

Reboot. Progress! Now i have the Edgy usplash. :)
It seems the upgrade from dapper was worse than I thought. I still have some other issues.

While the old dapper and the beta edgy usplash themes are gone the new usplash isn't displayed correctly. See my 2nd and 3rd attachments for the glitches I'm axperiencing.

EDIT: Found a way to improve my usplash experience - I deleted the kernel argument vga=794 which I've been passing via GRUB and then the resolution defined in /etc/usplash.conf kicked into effect. Seems the vga=794 argument was overriding this. But now the colour depth is shallow :) - only 8 bits I would say. And it seems you can increase it only by recompiling the kernel... Is this true?

---

### Post by featherking on 2007-01-24
The vga=794 sets the usplash to display at a certain resolution and color depth, these are the values you should pick from and put one of them back in the grub menu.lst. If one of these isnt found i think it defaults to like 640x480 and probably 8 bit like you say. It seems like people usually recommend the numbers in the 16 bit row in this table:

```
colour depth       | 640x480  800x600  1024x768 1280x1024
256           (8bit)|    769          771           773          775
32000     (15bit)|    784          787           790          793
65000     (16bit)|    785          788           791          794
16.7 Mill. (24bit)|    786          789           792          795
```

---

### Post by bartman on 2007-01-25
I know about these arguments, thanks though. Unfortunately  they break my usplash as demonstrated in the attachments in my previous post. Besides, I have a widescreen monitor with a resolution of 1920x1200 and a stretched usplash doesn't really look so good on it.

---

### Post by featherking on 2007-01-25
well you could check to be sure your /etc/usplash.conf is the same as what it is set at in your grub file. i would make try running:

```
sudo update-initramfs -u
```

If it is still broken look into that startup manager program i mentioned to see if you can change those settings to help your screen problem

---

### Post by bartman on 2007-04-25
Ever since i updated to feisty fawn (7.04) everything works peachy - the usplash works at the native resolution and the colour depth is, how should i put this, deep enough! :KS

---

