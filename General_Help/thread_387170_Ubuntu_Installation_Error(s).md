---
title: "Ubuntu Installation Error(s)"
date: 2007-03-18
forum: General Help
---

### Post by guitarist809 on 2007-03-18
Hello,

When I'm installing Ubuntu 6.10 (from the Live CD), I get the following errors, after waiting 5 minutes watching the splash screen with the bouncing bar thing do it's thing:

[17179717.540000] hdc: ide_intr: huh? expected NULL handler on exit
[17179717.588000] Buffer I/O error on device hdc, logical block 357564

This repeats many times, but the 1717xxxx.xxxxxx is always a different number.

When I saw hdc, I recognised it as my CD drive, so I figured it was a bad cd. I reburned the image 3 times (all using different settings, and the last 2 was on 8x speed). When I gave up with that, I decided to replace my CD player with another spare. Amazingly, It got past this error, but came up with a corrupted-looking screen telling me (forgot the name, but there was an X somewhere in it. I think it was X Windows). Anyway it asked me if I wanted to see a report, but I said 'No'. I was then directed to a useless command prompt, which only accepted a few commands and told me to type exit when I was done. I typed "exit". it just repeated the message (I repeated this like 7 times). I rebooted.

Heres some information (if it's needed):
- My hard drive is SATA, so its sda, which isn't the error here
- Just to make sure it wasn't the error, i re-particioned my hard drive making much of it ext3.
- My image file is _not_ corrupted, and the hash file is the same as one I found on google.
- In order for me to see these errors, I have to set my resolution (pressing F4) to 1280x1024 32), if I leave it at the default, the splash screen shows for about 10 minutes, then completly crashes.
- My other particion is NFTS (win xp)
- My CPU is 64 bit, but I'm using the 32 bit for stability.


Any help will be greatly appreciated.

Thanks,
Matt

---

### Post by guitarist809 on 2007-03-18
Sorry for bumping, but this is kind of urgent.

---

### Post by peabody on 2007-03-18
Did you verify the md5sum on the iso file you used?

---

### Post by guitarist809 on 2007-03-18
uh... maby?

How do you do that?

(I can't even check the cd from the menu option, gets stuck in the same place =\)

---

### Post by guitarist809 on 2007-03-18
Oh, I also think this might be a cause of these errors.

I have a PCI/e ATI Radion X700 gfx card. I searched the forums, and i was getting the same error that others were getting. I couldn't find a solution for installing it (it was only for those who already had it installed =\ )

---

### Post by peabody on 2007-03-18
It's not something you do from the CD, it's something you do to the image before you burn the CD.

This is a list of MD5sums for the 6.10 CD:

```
283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso
```

Save that to a file in the same folder as your iso and then run "md5sum -c sumfilename" from a terminal.

EDIT: Of course, if you leave every line in there you'll get a lot of "file not found messages"  You only care about "OK" messages.  If your particular image file is verified OK, then it's not a problem with the iso image, and you should look into that other cause you were considering.

---

### Post by guitarist809 on 2007-03-18
> **peabody said:**
> It's not something you do from the CD, it's something you do to the image before you burn the CD.

This is a list of MD5sums for the 6.10 CD:

```
283158c7da8c0ada74502794fa8745eb  ubuntu-6.10-alternate-amd64.iso
549ef19097b10ac9237c08f6dc6084c6  ubuntu-6.10-alternate-i386.iso
5717dd795bfd74edc2e9e81d37394349  ubuntu-6.10-alternate-powerpc.iso
99c3a849f6e9a0d143f057433c7f4d84  ubuntu-6.10-desktop-amd64.iso
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso
a3494ff33a3e5db83669df5268850a01  ubuntu-6.10-desktop-powerpc.iso
2f44a48a9f5b4f1dff36b63fc2115f40  ubuntu-6.10-server-amd64.iso
cd6c09ff8f9c72a19d0c3dced4b31b3a  ubuntu-6.10-server-i386.iso
6f165f915c356264ecf56232c2abb7b5  ubuntu-6.10-server-powerpc.iso
4971edddbfc667e0effbc0f6b4f7e7e0  ubuntu-6.10-server-sparc.iso
```

Save that to a file in the same folder as your iso and then run "md5sum -c sumfilename" from a terminal.

EDIT: Of course, if you leave every line in there you'll get a lot of "file not found messages"  You only care about "OK" messages.  If your particular image file is verified OK, then it's not a problem with the iso image, and you should look into that other cause you were considering.


Well, I tried doing that, but im not running linux. I'm still on winxp (mce 2005).

I also switched to my old cd player, i got that x server message up, but now I can't get back to the command prompt to type the sudo nano /ect/X11/xorg.conf thing to change the ATI to vesa :(

I also burned the CD w/ Nero Rom v7...

Is my computer just not Ubuntu worthy?

---

### Post by peabody on 2007-03-18
I believe there's a freeware md5summer for windows called something like winmd5sum.  has a gui to boot.  google could be helpful here.

---

### Post by guitarist809 on 2007-03-18
Well, it took like 5 mins to do it, but it passed.

What do I do now?

---

### Post by peabody on 2007-03-18
We've ruled out there being any issue with the CD, so now its definitely an issue with your hardware.  It's not my realm of expertise, but it's probably time to start looking into kernel parameters for the install disk.  Something like acpi=off or something like that (I can never remember those things)...

---

### Post by guitarist809 on 2007-03-18
Alright, I'll research some of that stuff on the website.

Thx for helping me :)

---

