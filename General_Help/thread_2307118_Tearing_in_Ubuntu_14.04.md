---
title: "Tearing in Ubuntu 14.04"
date: 2015-12-22
forum: General Help
---

### Post by nester17 on 2015-12-22
I've recently installed Ubuntu 14.04 and Windows 10 in a dual boot configuration on my MSI laptop. I'm getting system wide video tearing. I've tried many fixes but to no avail. I don't get any tearing on windows 10.

I've tried
-adding the -bs flag in 50-xserver-command.conf located at  /usr/share/lightdm/lightdm.conf.d/
-ForceFullCompositionPipeline option
-Trying to change settings in nvidia-settings and compiz config (Neither of these had the options I was supposed to change(Sync to Vblank/Refresh rate settings))

My specs
- i7 5700HQ
- 16GB RAM
- 128gb SSD
- 1TB HDD
- GTX 970M

The tearing is somewhat hard to notice but becomes very obvious when I run videos on my HDTV. The tearing is there regardless of whether the TV is connected.

Thanks in advance.

---

### Post by mc4man on 2015-12-22
You have a couple of choices with nvidia mobile (optimus
1. Try a distro without compositing
2. Just use the Intel gpu
3. Get rid of nvidia-prime & try bumblebee
4. Try workaround from this ppa, go to page & read carefully first (this is what I use, works fine & eliminates about 99% of tearing

[https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test](https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test)

---

### Post by nester17 on 2015-12-23
[FONT=arial]> **mc4man said:**
> You have a couple of choices with nvidia mobile (optimus
1. Try a distro without compositing
2. Just use the Intel gpu
3. Get rid of nvidia-prime & try bumblebee
4. Try workaround from this ppa, go to page & read carefully first (this is what I use, works fine & eliminates about 99% of tearing

[https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test](https://launchpad.net/~mc3man/+archive/ubuntu/tearfree-test)

Ok so my good buddy walked me through the troubleshooting for this. We pretty much used your launchpad link and found out some other things.

Unrelated but I was originally using my graphics card but I discovered that I can switch to my Intel graphics to save power. You can switch back and forth using nvidia-settings under PRIME profiles.

What I did

- switched to the 355.11 nvidia driver listed in the launchpad link

- I originally tried changing the /etc/X11/xorg.conf file manually without using the ppa program, however I found that between switching to the Intel Graphics and the GTX 970M the xorg.conf file would get overwritten without the VERY IMPORTANT "Option "TearFree" "True"" line. Upon using [COLOR=#333333]ppa:mc3man/tearfree-test the new xorg.conf configurations would be rewritten with the TearFree option.

- When I switch between graphics devices I get a dated xorg.conf(MMDDYYYY) file and a normal "xorg.conf". my graphics driver switches between these two but both of them have the TearFree in them.

RECAP: 
I basically followed the instructions mc4man provided in option 4. It works great except when things interact with my cursor, videos left to play on their own together, play fine.

Thanks goes out to my friend and mc4man for their post and program.[/COLOR][/FONT]

---

