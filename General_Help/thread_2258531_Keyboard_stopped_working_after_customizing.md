---
title: "Keyboard stopped working after customizing"
date: 2014-12-28
forum: General Help
---

### Post by jf-moniquelevi on 2014-12-28
Laptop Lenovo R61 using Gnome.
I upgraded a few days ago from 13.04 to 14.04; went real well (compared to the old days)
The custom keyboard I had set-up was gone, reverted to standard US.
I edited the *usr/share/X11/xkb/symbols/us*, as I did before.
Didn't change.  
Deleted *var/lib/xkb/*.xkm*
No change
Then I ran a *dpkg* command ... can't remember which !

Now, when I boot, the keyboard is completely dead; cannot even enter the password. 
 If I get the keyboard layout map it has question marks in all keys.
Tried to boot a Guest session, same thing.
I only can boot in recovery mode, on command line, keyboard works fine.

Right now I am using a 12.04 USB stick to boot and type this message !!!

I am on a trip, and have no other machine.

Help would be appreciated a lot.

J.F.

---

### Post by schragge on 2014-12-28
Can you use onscreen keyboard to enter password and login? It should be among accessibility features (small man-with-spread-out-arms icon).

---

### Post by jf-moniquelevi on 2014-12-28
> **schragge said:**
> Can you use onscreen keyboard to enter password and login? It should be among accessibility features (small man-with-spread-out-arms icon).

[SIZE=3]Thanks[/SIZE]
[SIZE=3]
Tried that: the onscreen keyboard: it has "?" on each key and something like "X keyboard not found, trying again..." on the space bar.

However, I can get to a CLI using GRUB advanced option >> recovery.

My feeling is that I have to reinstall the keyboard package, not sure how to.
I tried   *sudo apt-get install --reinstall xserver-xorg-input-all*    from the GRUB CLI; it didn't do anything.

If I were home I would use an external KB, but it is 400 mi away !!![/SIZE]

---

### Post by schragge on 2014-12-28
Reinstall package *xkb-data* from recovery console:
```
apt-get --reinstall install xkb-data
```

---

### Post by jf-moniquelevi on 2014-12-28
> **schragge said:**
> Reinstall package *xkb-data* from recovery console:
```
apt-get --reinstall install xkb-data
```

Many thanks !!! Looks like it is what I am looking for.  Will try this tomorrow, gettig late here.

---

### Post by jf-moniquelevi on 2015-01-09
Belated thanks and Happy New Year !!!
It worked !

The only snag was getting the file system mounted  in R/W.  When you boot in recovery, the fs is mounted "read only".  Go to the option "Fix package" and it remounts the fs in R/W then **schragge's **&#8203; tip worked like a charm !!!

---

