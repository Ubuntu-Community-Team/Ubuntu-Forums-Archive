---
title: "PS3 Varioius Issues"
date: 2008-06-18
forum: General Help
---

### Post by penguinpages on 2008-06-18
Hello.

Just joined Ubuntu. I am an RHCE but wanted to give Deb distro a bit of a chance and to edumacate myself on ubuntu a bit more.

I have a PS3 that I have working with xubuntu as I had issues getting other distros working on my initial test.


After getting past the typical learning curve of how things are done to get the install complete, I have a litany of mostly small issues which I have been searchinging though as I hit my head on the functionality problem. If someone has, from their experiance, been down this road, it would save me a lot of trial and error.

My $.02
1) I would also have to say that a lack of runlevels for dropping gui is a bit annoying. It is nice to foce the system to KISS and start off runlelvel 3 and then validate X works correctly before jumping to runlelvel 5. I would classify this as a drawback to ubuntu.

2) I choose xubuntu as it completed the installer without major heroics but it likly does not reflect the best of breed. I prefer KDE... and am now remembering why (most noted below). It would be nice to get a differentiator of xubuntu vs kubunutu vs ubuntu (seemed to me at the time to be just the "default" WM... but seems to be a bit deeper)

Issues:
1) Display is FINALLY working. The only way to get the system to stop "adjusting the screen" off the edge of (so 1/2 the icons / menu etc were missing and shell was not usable) was to append "video-ps3fb:mode:42 rhgb"  even the use of mode 133 (which SHOULD have been 1080p Full screen) does not work). To that effect I need to fnd a way to get the FULL screen. I hvae 3" margins around my beautif 52" TFT that I would like to eliminate. I also tried ps3videomode -v 42 -f and same issue where it then pushes the shell / xwindow outside (like it is too big).

2) I have not been able to get sound to work. I believe the issues is that I have to get audio to play only external through the opical cables as my DSP only takes optical in. I have played around with various xwindows settings per other forums but non work. Is their a shell way to validate sound and get a bit more "debug" level?

3) It would appear that 3D for PS3 is dead at this time. I have seen this to be a common thread amounst the forums. Just tossing out confermation to that effect or if their is maybe a DRI project in the works that I did not see.

4) The most annoying thing of the whole install (which I guess speaks to how much linux has come) is that when I tell the PS3 to boot OS Other... it hangs and requires power off and on of system. And the inverse is the same from Linux back to PS3 (boot-game-os). I don't have any grub messages or shell / logs to help debug this further (at this time) but maybe someone coudl enlighten me as to a bit more details as to how this reboot works. I would guess thatt 'boot-game-os just sets the grub entry on the root partition of the PS3 to boot its kernel. I have not tried to "hack" and mount that partition but maybe this is the way to debug this a bit more.

******************
user@nix:~$ cat /boot/etc/kboot.conf
message=/etc/kboot.msg
default=linux1080p
timeout=10
linux='/vmlinux initrd=/initrd.img root=UUID=1d2e29b2-c900-4d23-8a89-4e32b3a97fa5 quiet splash'
linux1080p='/vmlinux initrd=/initrd.img root=UUID=1d2e29b2-c900-4d23-8a89-4e32b3a97fa5 quiet splash video=ps3fb:mode:42 rhgb'
old='/vmlinux.old initrd=/initrd.img.old root=UUID=1d2e29b2-c900-4d23-8a89-4e32b3a97fa5 quiet splash'
user@nix:~$ 

*******************



I will return to this thread and post as I fix and or find more "features"... 

wish me luck on my PS3 hacking

---

