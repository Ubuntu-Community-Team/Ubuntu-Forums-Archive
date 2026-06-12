---
title: "Desert or Sky"
date: 2008-05-03
forum: General Help
---

### Post by jkinmk on 2008-05-03
Days of googling & forum searching, but I get no desktop with Gnome:

Installed Hardy Heron (proper release, not a beta) from the alternate CD on a Thinkpad R31 (my daughter's cast-off after she bought a new one.  Its only 128MB so I know it won't be fast - when I get it working I can add memory).

But after a normal GUI-based sign-on all I see is the colour of sand - no icons, taskbars (is that a windoze word?  Sorry)  Nothing to click on but there is a mouse pointer to click with.

So found ctrl-alt-F2 and "apt-got" and installed XFCE in case it was memory-lack stopping the desktop.  Same story with XFCE but its sky-colour of course.

Tried an old Knoppix live-cd and that works like a charm - full of GUI-goodness icons, menus etc, etc.  

Can anyone suggest how to analyse what's broken?  I'm fairly new to Linux but experienced with computers generally.

Thanks,
      John

---

### Post by ghostknife on 2008-05-03
> **jkinmk said:**
> , taskbars (is that a windoze word?  Sorry)
Not really, but in Gnome it's called a panel Window List.

> **jkinmk said:**
> Can anyone suggest how to analyse what's broken?  I'm fairly new to Linux but experienced with computers generally.

This is a hard one. Try seeing if something weird is happening in /var/log/Xorg.0.log or /var/log/gdm/:0.log.

The fact that nothing is starting is very odd. One would think it's gnome, but if XFCE isn't starting either it's probably because of GTK.

You can try using KDE which is based on Qt. Install the kubuntu-desktop through apt-get. If you really want to use gnome, tell me what you see in your logs and we can solve the problem. Post both logs online (inside ```

``` blocks)

You can try 7.10 instead. 8.04 is infected with a lot of beta software.

---

### Post by jkinmk on 2008-05-03
> **ghostknife said:**
> 

This is a hard one. Try seeing if something weird is happening in /var/log/Xorg.0.log or /var/log/gdm/:0.log.


You can try 7.10 instead. 8.04 is infected with a lot of beta software.

I'm embarrassed !   I let it boot for the nth time and went away for a few hours.  When I came back there was some kind of acid-trip flamingo background and a file directory window open.  Still nothing else in the way of desktop furniture so I tried the recovery mode thing I had seen elsewhere and that succeeded.  All looks normal so I guess it is just down to memory.  

Thanks for the log info though, now I know where to look next time something weird happens !  Bit disturbed by the news of 8.04 having beta stuff though, maybe 7.10 is a good plan.

Thanks again,
John

---

### Post by ryanhaigh on 2008-05-03
Did you create some swap partition during the install?

---

### Post by jkinmk on 2008-05-10
(if you're still watching) - on the partition question I took the "use the whole disc" option and let the software decide the details.
JK

---

### Post by ryanhaigh on 2008-05-10
If you post the contents of your /etc/fstab file we can see whether you have swap enabled.

---

