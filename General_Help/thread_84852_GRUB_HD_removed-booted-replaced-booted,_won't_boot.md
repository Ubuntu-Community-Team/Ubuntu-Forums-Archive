---
title: "GRUB: HD removed-booted-replaced-booted, won't boot"
date: 2005-11-01
forum: General Help
---

### Post by snuffy on 2005-11-01
Dual boot Windows XP & Ubuntu 5.10.
Newbie, sorry.

Problem:
I removed a hard drive, tried to boot to windows (dual boot), wouldn't
boot. realised that the HD i removed was the windows HD, so replaced
it. tried to boot, and now can't start windows or ubuntu.

if i try to select WINDOWS through grub i get the following error:
-------------------------------------------------------------------------------
booting 'microsoft windows xp pro'
root  (hd0,0)
   Filesystem type is ext2fs, partition type 0X83
savedefault
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue
-------------------------------------------------------------------------------


if i try to select UBUNTU through grub i get the following error:
-------------------------------------------------------------------------------
Booting 'Ubuntu, kernel 2.6.12-9-386

root (hd1,0)
  Filesystem type is fat, partition type 0xc
kernel  /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash

Error 15: File not found

Press any key to continue
-------------------------------------------------------------------------------

i have no idea where to even start looking. all the documentation
online about grub is so complicated for a total beginner, and
google has been no help to me. all i can see is that somehow the
entries have been mixed up so that when i try to load windows grub
looks at the ubuntu HD, and vice versa.

as you can probably imagine, i'm a bit worried right now as i can't
get into either operating system... hope i have not lost it all!

Thanks for your time.
tim.

---

### Post by bam on 2005-11-01
looks like the hdd's are in the wrong slots, (just a guess)

---

### Post by dom on 2005-11-01
yes this is probably it. Their order may have being swapped.

You can check this easily in grub.

get into the command line mode

type "root (hd0" and press tab and you'll get tab completion.

he should show you the partitions available on that drive, and what the FS types are. 

If you expect =, for. e.g., linux on hd0, and it shows partition type = fat, then you know your driver order is swapped.

You can swap the driver,  perhaps, or could be able to change something in the bios fo this.

Or, you could leave them as they are, edit the linux entry and change root so that it points to the correct device, then boot in there and fix grub to work with the new drive order

---

### Post by snuffy on 2005-11-01
thanks dom, ok, i get the general idea of what you are suggesting, however, i am a newbie, and i haven't a clue what to change in the bios or how to edit the  grub entries to point to the correct device.  could you give me a few more hints? i don't expect to be spoon-fed the answer, but i could do with a little more to go on.

thanks again.
tim.

[QUOTE=dom]yes this is probably it. Their order may have being swapped.


You can swap the driver,  perhaps, or could be able to change something in the bios fo this.

Or, you could leave them as they are, edit the linux entry and change root so that it points to the correct device, then boot in there and fix grub to work with the new drive order[/QUOTE]

---

### Post by snuffy on 2005-11-01
on boot up to grub, i changed the ubuntu entry by pressing 'e' then changed the line 'root (hd1,0)'   to 'root (hd0,0) then pressed 'b' to boot.  and it worked!

then i went to boot/grub/menu.lst and edited the line there to also read 'root (hd0,0), and now when i reboot the entry is there and correct to boot to ubuntu.


**however....**
i'm pretty sure i've found out that hd1,0 is my windows drive, so tried to change the entry for windows in grub to 'root (hd1,0) but when i then press 'b' to boot, the system hangs with the following:

```

root (hd1,0)
file system type is fat, partition type 0xc
savedefault
make active
chainloader +1

```

I'm lost. please give me a few hints. :-(

thanks for your time
tim.

---

### Post by dom on 2005-11-02
excellent, that's exactly what was needed.

well one solution as others have pointed out.

The thing with windows is that it is no longer the first device, and it wants to be or it won't work.

However, GRUB is nice and lets us trick windows into thinking that it's the first device, regardless of where it actually is.

I had the same situation, where windows hung the very same way without booting.

So try something like this :

```

title                 the win system
map  (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
root (hd1,0)
make active
chainloader +1

```

if that does not work, try replacing ```
root (hd1,0) 
``` with ```
rootnoverify (hd1,0)
```

if that doesn't work, we'll have to try again :)

---

### Post by snuffy on 2005-11-02
excellent dom... cheers.

the 'map' bits held the answer. i'd actually just found that out after a bit of trial and error and your previous hints, but thanks for the reply, much appreciated.  i'm one step closer to understanding 'everything!'  grub is definitely becoming less complicated than i'd originally thought.

thanks again dom. 

title                 the win system
map  (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
root (hd1,0)
make active
chainloader +1

---

### Post by dom on 2005-11-02
no worries,

glad to be of any help

---

