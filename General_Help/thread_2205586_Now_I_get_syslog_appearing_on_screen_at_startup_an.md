---
title: "Now I get syslog appearing on screen at startup and shutdown."
date: 2014-02-14
forum: General Help
---

### Post by desconocido on 2014-02-14
I have a new computer which has the amd64 version of Ubuntu 12.04.3 installed. (Also has unity and unity2d removed and gnome-shell installed - I use Gnome Classic.)

Because of other problems, I have re-installed this Ubuntu, and because of advice received, I let Upgrade Manager upgrade the system.
It upgraded 282 packages, including a new version of kernel & new grub and grub2 related packages.

Now what seems to be bits of syslog stream up my screen at startup (20-30 seconds) and at closedown (half a screenful).

This is unsightly and looks unprofessional.

Is it a bug? Should I report it somewhere?

Alternatively, is there a settings file or script I could edit in order to remove it?

---

### Post by mikewhatever on 2014-02-15
It is a known visual bug, related to the proprietary AMD/Nvidia drivers. No point reporting it, just "me too" it, if you want to.
You could try this [http://randomandlinux.blogspot.co.il/2013/05/fix-ubuntu-boot-screen-after-installing.html](http://randomandlinux.blogspot.co.il/2013/05/fix-ubuntu-boot-screen-after-installing.html).

PS: ...don't think anything needs editing in order to remove it, what ever that means.

---

### Post by desconocido on 2014-02-15
> **mikewhatever said:**
> It is a known visual bug, related to the proprietary AMD/Nvidia drivers. No point reporting it, just "me too" it, if you want to.
You could try this [http://randomandlinux.blogspot.co.il/2013/05/fix-ubuntu-boot-screen-after-installing.html](http://randomandlinux.blogspot.co.il/2013/05/fix-ubuntu-boot-screen-after-installing.html).

Thanks, my graphics hardware is described as "(AMD E1-1200 APU @ 1.4 GHz with Radeon HD Graphics)" so I am not sure that it's the same as AMD/Nvidia.
I have just tried installing 
```
System Settings -> Additional drivers
 ATI/AMD proprietary FGLRX grapgics driver (**experimental**beta)
 Video driver for the AMD Radeon and FireGL graphics accelerators.
 This package provides 2D display drivers and hardware accelerated OpenGL.
``` but with no improvement.

I'll search in that url you quote a bit more tomorrow.

It's worth noting that the first time I installed Ubuntu, I didn't have the problem, only after the re-install.

> PS: ...don't think anything needs editing in order to remove it, what ever that means.
By "it", I meant the phenomenon of syslog data appearing on my screen. A lot of the stuff in that url you quote involves things like editing /etc/default/grub. Thanks.

---

### Post by desconocido on 2014-02-15
More info: the graphics card is decribed as "AMD Radeon HD 7310 Graphics".

---

### Post by mikewhatever on 2014-02-16
So, you do have an AMD GPU, and do use a proprietary AMD driver. The solution I posted is from May 2013, and has been reported (see the comments) to work for Ubuntu 13.04.

---

### Post by desconocido on 2014-02-17
> **mikewhatever said:**
> So, you do have an AMD GPU, and do use a proprietary AMD driver.

Thanks for that. I hadn't realized that Radeon was the same as Nvidia.

I tried the method you mentioned. I had difficulty getting to the grub menu. Neither SHIFT nor F8 while booting worked, but ESC did. However trying vmeinfo at the grub> prompt gave me
```
error: unknown command `vmeinfo'.
```
and help gave me
```
error: secure Boot forbids loading module from (hd0,gpt2)/boot/grub/help.mod
```
(and in fact there isn't a vmeinfo.mod file in /boot/grub)

So I had to try and guess the screen resolutions that would be acceptable. My maximum
```
GRUB_GFXPAYLOAD_LINUX=1366x768-32
```
didn't work and nor did my minimum
```
GRUB_GFXPAYLOAD_LINUX=800x600-32
```

Your reference says "P.S.: If this didn't work for you, try this method." with a link to [http://www.randomlinuxstuff.tk/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html]("http://www.randomlinuxstuff.tk/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html") So I tried that.

```
sudo apt-get install v86d
```
in /etc/default/grub change
```
GRUB_CMDLINE_LINUX="i8042.nomux=1 i8042.reset"
```
to
```
GRUB_CMDLINE_LINUX="i8042.nomux=1 i8042.reset quiet splash nomodeset video=uvesafb:mode_option=800x600-32,mtrr=3,scroll=ywrap"
```
and add
```
GRUB_GFXPAYLOAD_LINUX=800x600-32
```
```
sudo update-grub
```

This worked. Thanks.

I might try higher resolutions, but it actually looks fine as it is.

I have just realised that I omitted steps 8 and 9 of this second method. However [shrug].

---

### Post by tamulionis on 2014-02-20
> **desconocido said:**
> Thanks for that. I hadn't realized that Radeon was the same as Nvidia.

I tried the method you mentioned. I had difficulty getting to the grub menu. Neither SHIFT nor F8 while booting worked, but ESC did. However trying vmeinfo at the grub> prompt gave me
```
error: unknown command `vmeinfo'.
```
and help gave me
```
error: secure Boot forbids loading module from (hd0,gpt2)/boot/grub/help.mod
```
(and in fact there isn't a vmeinfo.mod file in /boot/grub)


That's vbeinfo, not vmeinfo

---

### Post by desconocido on 2014-02-20
> **tamulionis said:**
> That's vbeinfo, not vmeinfo
Thanks for the correction, although actually I get the same "unknown command" message. If I type v followed by a tab, it suggests videoinfo and videotest, but both of those get the "secure boot forbids" message. This is grub2 by the way. Hey ho.

---

