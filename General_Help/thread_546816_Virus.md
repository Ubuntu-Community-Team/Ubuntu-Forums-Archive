---
title: "Virus?"
date: 2007-09-09
forum: General Help
---

### Post by vjzeitgeist on 2007-09-09
After an update yesterday, i'm on feisty fawn, grub lost the vista boot opiton in the grub menu. i edited it so it can load vista gain. After i restarted, i loaded vista with grub, donloaded some files in vista, restarted, and now grub is missing ? I started the rescue from the ubuntu cd, but there are no ubuntu partitions ? my entire ubuntu s missing !!
There is just my vista partition...

Is it possible that i picked up a virus on vista ? I downloaded a program by torrent. 

btw this is what i added in grub's menu..

title           vista
root           (hd0,1)
chainloader    +1

/dev/hda2/ is vista.

Where did my ubuntu go ? :confused:

---

### Post by rbprogrammer on 2007-09-09
> **vjzeitgeist said:**
> 
...
my entire ubuntu s missing !!
...

when you say your ubuntu is missing, do you mean the partition is no longer there?? or do you mean your partition is there but ubunu is not in the grub list??  i would suggest the [SuperGRUB]("http://supergrub.forjamari.linex.org/") disc that will reinstall GRUB.  i have not used the disc yet, but i would think you would be able to view partitions and make sure that ubuntu is still there, just not bootable.

> **vjzeitgeist said:**
> 
...
Is it possible that i picked up a virus on vista ? I downloaded a program by torrent. 
...

well, that depends on the program you downloaded. it is a real possibility that a person can write a program that acts as a diversion so that it can install and run a virus or something malicious..

---

### Post by vjzeitgeist on 2007-09-09
there are absolutely no ubuntu partitions !!
there's just unpartitioned space :(

---

### Post by rbprogrammer on 2007-09-10
did you check to see if the partition was there or not within windows??

b/c i doubt that vista can read an ext2/ext3 partition by default.  if you have not already, try booting up the live cd and use gparted or qtparted (whichever is on the cd) and see if they register as ext2 or ext3 partitions.

---

### Post by bodhi.zazen on 2007-09-10
Well, if you can boot Vista your Ubuntu partition exists :)

My guess would be you deleted or changed the Ubuntu stanzas in /boot/grub/menu.lst

Boot the live Ubuntu CD,

You can restore Grub like this :

		Boot the Ubuntu CD
		Open a terminal
		Enter : ```
sudo grub
```You will get the grup prompt :> grub >

		At the grub prompt enter : ```
grub > find /boot/grub/stage1
```

		This will return your ubutnu partition in grub terminology (hdx,y) for example (hd0,0)

		If you have more then one version of Linux installed you will get more partition listed ...

		Now at the grub prompt, enter root (hdx,y), substituting your partition listed above

		```
grub > root (hd0,0)
```

		Now install grub : setup (hd0) = install to MBR ; setup (hd0,0) = install to root partition

		```
grub > setup (hd0)
```

		Quit grub : ```
grub > quit
```

		Reboot and you should be good to go ...

==========

But to answer you question, sounds unusual for a virus :twisted:

---

