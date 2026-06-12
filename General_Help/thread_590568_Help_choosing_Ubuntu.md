---
title: "Help choosing Ubuntu"
date: 2007-10-24
forum: General Help
---

### Post by Dark Venom on 2007-10-24
I'm new to Linux and Ubuntu, and I want to know which one should I download? the x86 or x64 version?  I have an AMD Athlon x2 4200+ 64-bit, but I'm not sure to get the 64bit one cuz maybe there arent many applications that support this architecture?

Would x86 applications work on the 64bit OS?

Please help me. \\:D/

---

### Post by rsambuca on 2007-10-24
The repositories are almost identical between the 32 and 64bit versions, meaning they have been compiled to work in 64bit.  Flash works out of the box, codecs are one click away, so there really is no reason to not use 64bit these days.

---

### Post by Espreon on 2007-10-24
I highly suggest using the x86 version, since it is compatible with more stuff, ust cause you have a 64-bit processor does not mean you hafta use a 64-bit OS, 32-bit (x86) apps don;t work with 64-bit (x64) OSes.

It is possible to get x86 apps to work on x64 but you would have to compile them from source using a certain option, but not all x86 apps can be compiled for x64, but the point is compiling is not noob friendly.

Plus there is not much x64 apps in the Ubuntu repos (from what I have heard at least).

If you wanna take full advantage of your processor but make it easy to build x86 apps from source to work on x64 OSes, I suggest using a Source-based distro instead. For people new to Linux and source based distros and the real-world of computing (compiling) then I suggest Sabayon Linux (I used to use it and it is pretty damn good). Link: [http://www.sabayonlinux.org](http://www.sabayonlinux.org)

If you decide to go with Sabayon download the DVD image  rather than the CD (the CD edition is bad compared to the DVD, the DVD has much better software included)

Good Luck!

---

### Post by rsambuca on 2007-10-25
> **Espreon said:**
> I highly suggest using the x86 version, since it is compatible with more stuff, ust cause you have a 64-bit processor does not mean you hafta use a 64-bit OS, 32-bit (x86) apps don;t work with 64-bit (x64) OSes.

It is possible to get x86 apps to work on x64 but you would have to compile them from source using a certain option, but not all x86 apps can be compiled for x64, but the point is compiling is not noob friendly.

Plus there is not much x64 apps in the Ubuntu repos (from what I have heard at least).

If you wanna take full advantage of your processor but make it easy to build x86 apps from source to work on x64 OSes, I suggest using a Source-based distro instead. For people new to Linux and source based distros and the real-world of computing (compiling) then I suggest Sabayon Linux (I used to use it and it is pretty damn good). Link: [http://www.sabayonlinux.org](http://www.sabayonlinux.org)

If you decide to go with Sabayon download the DVD image  rather than the CD (the CD edition is bad compared to the DVD, the DVD has much better software included)

Good Luck!

This post contains so much incorrect information, I almost don't know where to begin.  First, all of the apps in the Ubuntu repositories have been compiled to work with the 64bit environment.  The difference between the gutsy 32bit and 64bit is under 1%.

In the event that you ever do have to compile a program from source, it is not difficult.  It takes three commands:

./configure
make
sudo make install

Not what I would call difficult, or "not noob friendly".  It is quite evident that you are merely guessing at this information.  Please try and refrain from posting pure FUD in the future.

---

### Post by Dark Venom on 2007-10-25
Thanks for the help, I downloaded the 64bit desktop edition, and I'm trying it out.  I have one more question though, how do you enable the 3d graphics, like beryl?

Thanks again.

---

### Post by PmDematagoda on 2007-10-25
Ubuntu 7.10 comes with Compiz-fusion built in so it won't be a problem, but if you want to change the settings then you can use Compiz Settings Manager.

---

### Post by por100pre1 on 2007-10-25
System> Preferences> **Appearance**

For more settings use Advanced Desktop Effects Settings

(System> Preferences> **Advanced Desktop Effects Settings**)

Be sure to install Advanced Desktop Effects Settings using Add/Remove

(Applications> **Add/Remove**)

You'll find it in the section **Other**.

---

