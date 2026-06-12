---
title: "No sound at all after attempted alien arena install"
date: 2007-10-14
forum: General Help
---

### Post by konungursvia on 2007-10-14
No login or system sounds, no xmms sound, nuttin! So I tried reinstalling alsa libraries and base, but still nothing. When booting linux, however, I still hear the speakers come on about 20% of the way through the bar, as usual, when sound is (I guess) initialized.

Does anyone know what other packages to reinstall to get sound back to normal? Not sure what alien arena did, but the install didn't seem to work either :(

---

### Post by konungursvia on 2007-10-14
Oh yeah, and herea re the devices


pete@dell:~$ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: U0xd8c0x0c [USB Device 0xd8c:0x0c], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by konungursvia on 2007-10-15
Well no one answered and the page on fixing "all" sound problems didn't work for me, so I tried upgrading to gutsy. Still trying to complete that through partial upgrades, as the ca.ubuntu.archives are hit and miss, and always time out for about a quarter of the bigger files. Hope hope.

---

### Post by Butthead on 2007-10-15
Possible dumb question here, but did you ever try starting the game using the ./crx-sdl (I think it was?) extension (as explained in the accompanying readme file)? :confused:

---

### Post by konungursvia on 2007-10-16
Thanks! A reply! But no, that I never tried, I just wanted my sound back, as music is everything to me. I think I'll switch from Ubuntu to Fedora soon, I never get my questions answered here, and ubuntu keeps borking.

---

### Post by konungursvia on 2007-10-16
Did not try, sorry, as I was more concerned with this sound probem. Have now upgraded to Gutsy, and still no sound. also, now, there are no window borders. Beryl and emerald are still there (I had to reinstall emerald) but no gnome theme underneath, so no window edges. Strange, isn't it? During the upgrade, it suggested I try running asoundcard(1) set-default-card macro, but don't see how. Any ideas? Thanks for any help.

---

### Post by konungursvia on 2007-10-16
The new gutsy alsa mixer let me mute then unmute pcm and pc speakers, and now sound is back, finally! I still have no window borders, however. Thanks for the help, butthead.

---

### Post by Butthead on 2007-10-16
No problem!  Isn't Beryl that Ubuntu 3D desktop thingie?  That might be your problem with the window borders not showing up right there.  I know I always seemed to have problems playing DVD's running compiz (Mandriva's version of the 3D desktop).  Any way to turn it off temporarily and then re-try playing Alien Arena?

---

