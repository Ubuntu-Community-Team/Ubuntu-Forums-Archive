---
title: "Support for UbuntuStudio?"
date: 2007-05-11
forum: General Help
---

### Post by jegHegy on 2007-05-11
[UbuntuStudio](http://www.ubuntustudio.org/) 7.04 was just released today, and I'm really eager to try it. Do the developers of Wubi plan on supporting this third-party remix of Ubuntu?

---

### Post by ago on 2007-05-11
If it uses kernel 2.6.20-15-generic there is no problem. 

Let us know:

URL to ALTERNATE ISO 
MD5
File size in bytes

If it uses a different kernel, Lupin must be compiled on that kernel, you need to modify IsoList.ini within wubi adding a UbuntuStudio section and disabling all the other sections since other Ubuntu distros will not be available

---

### Post by joejaxx on 2007-05-11
ISO URL:

[http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso](http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso)

MD5SUM:

[http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso.MD5SUM](http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso.MD5SUM)

Kernel for the d-i is 2.6.20-15-generic

But we install -lowlatency if the users chooses the audio creative path (task). If you do not install audio then -generic is the only one installed.

---

### Post by ago on 2007-05-11
> **joejaxx said:**
> ISO URL:

[http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso](http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso)

MD5SUM:

[http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso.MD5SUM](http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso.MD5SUM)

Kernel for the d-i is 2.6.20-15-generic

But we install -lowlatency if the users chooses the audio creative path (task). If you do not install audio then -generic is the only one installed.

I also need the size of the ISO file in bytes (it will spare me a download). You will have it in next build.

---

### Post by joejaxx on 2007-05-11
joejaxx@equinox:~$ du -b ubuntustudio-7.04-alternate-i386.iso
909676544       ubuntustudio-7.04-alternate-i386.iso

---

### Post by ago on 2007-05-11
> **joejaxx said:**
> joejaxx@equinox:~$ du -b ubuntustudio-7.04-alternate-i386.iso
909676544       ubuntustudio-7.04-alternate-i386.iso

How do you fit that on a CD? Is that a DVD iso? iso9660?

---

### Post by ago on 2007-05-11
I have added a Wubi Customization section to our [WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by jegHegy on 2007-05-11
According to my burning software it's indeed ISO9660 (with Joliet). Thank you for your effort!

---

### Post by ago on 2007-05-11
It will be available from next build, probably by this w/e

---

### Post by joejaxx on 2007-05-11
it is DVD image. Too bad they do not make 900mb cds anymore :P

---

### Post by max littlemore on 2007-05-11
> **joejaxx said:**
> ISO URL:

[http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso](http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso)

MD5SUM:

[http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso.MD5SUM](http://download.linuxaudio.org/ubuntustudio/ubuntustudio-7.04-alternate-i386.iso.MD5SUM)

Kernel for the d-i is 2.6.20-15-generic

But we install -lowlatency if the users chooses the audio creative path (task). If you do not install audio then -generic is the only one installed.

Sorry, just wandered into this while I was about to compile my own kernel for real time audio... Excuse me if I have missed something.......

Does the low latency kernel used allow me to set group permissions to use real time locks starting jack using feisty on amd64? If so THANK YOU THANK YOU THANK YOU!!!

Seriously, I was so happy about the announcement ubuntu studio release, I went and bought a new computer. It meant I could just use all the tools I had working on Dapper without the screwing around.

I was disappointed at the delay and I set tonight aside to compile my own kernel and get it so my wife wouldn't notice, but if this is released, I'm happy. BTW I have a spare partition to test (~70GB) but limited bandwidth till the end of the month....I can't really do front line.

Will this work with X2 AMD62 3800++? Should I wait? Can I set real time for a group using PAM?
:guitar:

---

### Post by ago on 2007-05-11
[http://ubuntuforums.org/showthread.php?t=440609](http://ubuntuforums.org/showthread.php?t=440609)

---

