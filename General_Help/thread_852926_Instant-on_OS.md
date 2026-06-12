---
title: "Instant-on OS"
date: 2008-07-08
forum: General Help
---

### Post by armageddon08 on 2008-07-08
Is it possible to create an instant-on OS from ubuntu hardy-- ones like the Phoenix Hyperspace or Splashtop so that I could quick boot into it to listen to music etc ?

---

### Post by p_quarles on 2008-07-08
Well, if you *only* want to use this box to listen to music, you could hypothetically strip out most services, apply some readahead magic, and get the boottime very low (though probably more like 10-15 seconds rather than "instant."

---

### Post by earthpigg on 2008-07-08
[http://www.puppylinux.org/home]("http://www.puppylinux.org/home")

puppy linux is pretty lightning fast - if you dont have your heart set on Ubuntu - and includes the media basics like region-coded DVD support, mp3, flash (youtube) by default.

---

### Post by aktiwers on 2008-07-08
Doesnt the splashtop install on the CPUs cache? This means it is a minimal Linux distro on 2-12mb. 
Isnt the splashtop build on the Linux Bios software?

---

### Post by Vivaldi Gloria on 2008-07-08
> **armageddon08 said:**
> Is it possible to create an instant-on OS from ubuntu hardy-- ones like the Phoenix Hyperspace or Splashtop so that I could quick boot into it to listen to music etc ?

Phoenix Hyperspace - I don't know what is that.

Splashtop etc. - These have special bios which contain some of the OS. That's why they are fast.

Unless you want to buy (or modify) a motherboard which has such a feature then you cannot reach such speeds. 

See

[http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)

---

### Post by mempman on 2008-07-08
Can't you just play cds directly without having to boot into any OS.

---

### Post by armageddon08 on 2008-07-08
> **Vivaldi Gloria said:**
> Phoenix Hyperspace - I don't know what is that.

Splashtop etc. - These have special bios which contain some of the OS. That's why they are fast.

Unless you want to buy (or modify) a motherboard which has such a feature then you cannot reach such speeds. 

See

[http://www.coreboot.org/Welcome_to_coreboot](http://www.coreboot.org/Welcome_to_coreboot)


Ok now I understand how my friend could boot up so quickly and perform media tasks........I thought that it might have been a linux OS simply installed in his laptop....I was wrong. thanks.

---

### Post by armageddon08 on 2008-07-08
> **earthpigg said:**
> [http://www.puppylinux.org/home]("http://www.puppylinux.org/home")

puppy linux is pretty lightning fast - if you dont have your heart set on Ubuntu - and includes the media basics like region-coded DVD support, mp3, flash (youtube) by default.

Thanks man for that link!! Tried it .....its quite good, but Ubuntu is the best linux distro in this whole wide world........I just love it!!

---

### Post by anderson314159 on 2009-11-19
try slax.

or install casper and a filesystem.squashfs on your hd.  thats realy fast.


puppy running entirely in ram is the fastest.  and you can have longer battery life.  i get 30% longer batt life by using puppy and spinn down the hd.

if there was an installer that would create  usb key of ubuntu that worked like puppy.  its possible i think.

you can install casper and configure it,  compress your root fs image to squashfs,  it makes ubuntu faster,  but not like puppy.

the nice thing about puppy besides it being small is that it puts the root fs compressed in ram and writes to the disk/usb key in burst updates.

i dont know if puppy does that.

---

