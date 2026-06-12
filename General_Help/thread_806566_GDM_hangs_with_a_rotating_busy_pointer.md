---
title: "GDM hangs with a rotating busy pointer"
date: 2008-05-25
forum: General Help
---

### Post by nultodel on 2008-05-25
After one days' update (some days age), GDM hangs immediately prior to the greeter with a rotating busy pointer. Pointer moves with mouse. Keyboard is unresponsive except I can switch to console sessions with CTRL-ALT-F(1-etc) and can restart X with CTRL-ALT-Backspace (but GDM just hangs again in same manner).

If I switch to the console with CTRL-ALT-F1, I can login but issuing sudo /etc/init.d/gdm restart doesn't fix the problem.
There is only a pointer,and the background.

I tried to edit gdm.conf eg: sudo nano /etc/gdm/gdm.conf,Search for:      Greeter=/usr/lib/gdm/gdmgreeter  
and change to: 
          Greeter=/usr/lib/gdm/gdmlogin
and it didn't work.:(
 
  cp /usr/share/themes/Human/gtk-2/gtkrc 
         /usr/share/themes/Human/gtk-2.0/gtkrc.en
didn't work either.:(

---

### Post by warp99 on 2008-05-25
Did you try purging gdm then reinstalling? If not switch to a console (crtl+alt+F2) and issue the following:

```
sudo apt-get remove --purge gdm
```
Now this may ask to remove the ubuntu-desktop, but don't be alarmed since this is only a metapackage. Removing it will not actually remove the Ubuntu desktop only the metapackage, then
```
sudo apt-get install gdm
```
What these two little operations will do is remove all of the gdm configuration files and reinstall a new default set.

---

### Post by nultodel on 2008-05-25
> **warp99 said:**
> Did you try purging gdm then reinstalling? If not switch to a console (crtl+alt+F2) and issue the following:

```
sudo apt-get remove --purge gdm
```
Now this may ask to remove the ubuntu-desktop, but don't be alarmed since this is only a metapackage. Removing it will not actually remove the Ubuntu desktop only the metapackage, then
```
sudo apt-get install gdm
```
What these two little operations will do is remove all of the gdm configuration files and reinstall a new default set.

Thanks , i tried this too.
but question is the same.

---

### Post by nultodel on 2008-05-25
it's ok now!
The problem is when i set up qt/embeded environment.
i edit /etc/ld.so.conf ,and add the lib path for qt/embeded
and compile qt,tmake....

So i delete what i add in /etc/ld.so.conf
and The whole dir of qt/embeded.

and then it works.:):lolflag:

---

### Post by Zeppe on 2008-05-28
I think I bumped in the very same error yesterday, I was banging my head against the keyboard wondering what it was due to. Blinking rotating busy pointer, no response from the system, tried to reconfigure gdm with no success, and everything else as described. 

I didn't do anything related to qt, but I did actually changed the /etc/ld.so.conf file recently. Tonight I'll try to revert the changes, if the error disappears, I owe you one! :)

Anyway, pretty bad something makes the system crash in such a silent way (no errors in the logfiles...)

Best wishes,

Giuseppe

---

