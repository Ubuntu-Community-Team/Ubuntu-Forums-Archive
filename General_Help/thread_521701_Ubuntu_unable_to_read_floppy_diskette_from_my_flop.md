---
title: "Ubuntu unable to read floppy diskette from my floppy drive"
date: 2007-08-09
forum: General Help
---

### Post by Universered on 2007-08-09
Description of prob: I can't get my computer to open floppy; to access the files

---

### Post by Universered on 2007-08-10
Anybody else with this specific floppy problem?

---

### Post by milton1 on 2007-08-10
can you describe exactly what you have tried to gain access to the floppy?

---

### Post by philinux on 2007-08-10
!. Put diskette in floppy drive.

2. Click Places>Computer.

3. Right click on floppy and select mount.

If that does not work something else wrong.

---

### Post by Vanish00 on 2007-08-10
I have a Mitsumi 3.5" Combo Floppy/USB 2.0 7-In-1 Card Reader, and when I select mount floppy nothing happens.  Any ideas?

---

### Post by Universered on 2007-08-20
Bump

---

### Post by Universered on 2007-08-23
> **philinux said:**
> !. Put diskette in floppy drive.

2. Click Places>Computer.

3. Right click on floppy and select mount.

If that does not work something else wrong.

Hi philinux, thanks for your advice
but I don't have 'Places/Computer' in the menu on my computer. I'm currently using Xubuntu Edgy 6.10.
The problem still persists, or, its me who isn't able to open the Floppy drive.

If anybody (including Mr. philinux) has any further advice on this case, I would be very pleased if I'm supported with it.

Thanks again:)


Note: my English isn't very good. I'm not good at grammer etc, I'm sorry for all the miswritten parts of the text.

---

### Post by agemon on 2007-09-03
hy, try mounting it from the console:
```

sudo mount /dev/fd0 /media/floppy0

```

and this may sound silly, but check if the LED on the floppy drive is lighting up while mounting, if it doesn't, this means that the cables are improperly connected or, the floppy drive is busted.

You may also try 
```
dmesg | grep -i floppy
```
to see if the kernel has any problems detecting the drive

---

