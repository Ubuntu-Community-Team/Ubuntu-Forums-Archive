---
title: "ubuntu not mounting ipod, and not recognizing usb headset"
date: 2007-09-09
forum: General Help
---

### Post by nerdman978 on 2007-09-09
All the documentation I have read says that ubuntu automatically mounts ipods. Either my system sucks, or I missed something. Ubuntu just won't mount my ipod (its a 1st gen nano if that helps). Also, I have a Gigaware USB headset that I use to chat (microphone) and listen to music, etc. but ubuntu doesnt recognize it (i looked in system>preferences>sound but no luck there.

---

### Post by moore.bryan on 2007-09-09
*can't help-out on the headset, but the 1st gen nano's usually need [gtkpod]("http://www.gtkpod.org/"), [yamipod]("http://www.yamipod.com/main/modules/home/"), or [amarok]("http://amarok.kde.org/") to work nicely.  i personally was never able to get mine working properly; i.e., it would take **forever** to transfer music (>2 hours for one album of 10 songs).  i solved my problem with install [rockbox]("http://www.rockbox.org/") onto the nano.  once i got used to the rockbox setup, i love it and will **never** go back.*

---

### Post by nerdman978 on 2007-09-09
by "ubuntu doesnt mount my ipod" i mean that it doesn't recognize it at all. it isn't on my desktop nor under the /media/ directory

---

### Post by moore.bryan on 2007-09-09
*yeah, i got that.  same problem i had.*

---

### Post by nerdman978 on 2007-09-09
its a little hard to install rockbox on something my computer says doesnt exist. (i've used rockbox before and really didnt like it)

---

### Post by moore.bryan on 2007-09-09
[I]yeah, i had to hit-up a windows machine.  fair enough on the rockbox.

first, so you have another usb cable to check if it's just the cable?  if you've done that already, do you have the "out-of-the-box," default ubuntu install?  if so, you might want to install ivman to manage your usb devices and see if that works.
[/I]

---

### Post by nerdman978 on 2007-09-09
I installed ubuntu this afternoon (on this computer), but other than that I've used ubuntu for awhile. So I do have the "out of the box" install (but i've been tweaking all day). I have no idea what to do now. oh, and the cable is fine.

---

### Post by moore.bryan on 2007-09-09
*well, that means you're using gnome-volume-manager.  now, i've had issues with gvm (hence my switch to ivman), but no guarantee that's it.  sorry i don't have any specifics...*

---

### Post by nerdman978 on 2007-09-09
what is "ivman"

---

### Post by nerdman978 on 2007-09-09
Ok right now I'm installing ipodlinux. hopefully this should solve all my problems. if not, i will be very upset XD

---

### Post by moore.bryan on 2007-09-11
> **nerdman978 said:**
> what is "ivman"
*it's just another hal device handler...*

---

### Post by airtonix on 2008-01-07
> Ok right now I'm installing ipodlinux. hopefully this should solve all my problems. if not, i will be very upset XDYour going to be very upset.

When you plug wither your headset or your ipod in you want to check the output of this command in the terminal. ( it will tell you if the OS is actually detecting the device and hooking it into the right place for use by bovine means)

1. Open terminal (alt+f2 -> type: gnome-terminal, enter)
2. plugin usb device(headset first)
3. type: sudo lsusb
4. sudo password is your password.

does it list your device? 
when you plugged the device in did you notice hard drive activity?

repeat procedure for ipod.

That will lat least tell you if you can move to th next step of mounting the device for bovine usages.

---

