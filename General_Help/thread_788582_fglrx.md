---
title: "fglrx"
date: 2008-05-09
forum: General Help
---

### Post by McTek on 2008-05-09
Could someone walk me thru the install instructions at this URL

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

---

### Post by TransitMan on 2008-05-09
I really hate to say this, but those instructions at the site you posted a very self-explanitory. I even understand them and I'm still getting into this whole open/closed source ATI/nVidia drivers thing.

I don't think trying to re-explain them here would really help at all.

---

### Post by jocko on 2008-05-10
There's an even simplaer way to install ati's drivers.
Open up the restricted drivers manager (-->System --> Administration --> Hardware Drivers)
Enable the driver, reboot and you're done.

---

### Post by TransitMan on 2008-05-10
I've got one even better.

Install EnvyNG and let it do the work for you. It is in the repos and is a quick and easy way to get the video drivers you need.

Don't know why I didn't think about this 13 hours ago except I was tired.

---

### Post by ghost_ryder35 on 2008-05-10
> **jocko said:**
> There's an even simplaer way to install ati's drivers.
Open up the restricted drivers manager (-->System --> Administration --> Hardware Drivers)
Enable the driver, reboot and you're done.
this is a very very very easy way to do this :)

---

### Post by jocko on 2008-05-11
> **TransitMan said:**
> I've got one even better.

Install EnvyNG and let it do the work for you. It is in the repos and is a quick and easy way to get the video drivers you need.

In what way would envy be simpler than the restricted manager?
Envy should only be used by users who knows how to fix things from the command line when the driver gets broken (which will happen when the kernel is updated).
The restricted manager installs the driver from the repo, which means it will always be updated together with the kernel

---

### Post by McTek on 2008-05-11
I've done this and it tells me the driver is active.
But when I run  fglrxinfo
THis is what I get.

[COLOR="Red"][COLOR="Red"]
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
[/COLOR][/COLOR]

---

### Post by McTek on 2008-05-11
Thank you that is the politest RTMF I have every recieved.

---

### Post by jocko on 2008-05-12
> **McTek said:**
> I've done this and it tells me the driver is active.
But when I run  fglrxinfo
THis is what I get.

[COLOR=Red][COLOR=Red]
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
[/COLOR][/COLOR]
Do you have xserver-xgl installed? In that case fglrxinfo will not report the correct information (as it will usually look up the info on the wrong display).
Try running:
```
fglrxinfo -display :1
```
or:
```
fglrxinfo -display :0
```
One of them *may* show the correct info.

Otherwise, if you have fglrx installed and xorg set up to use it, and it fails to work properly, this may give some clues to what the problem is:
```
cat /var/log/Xorg.0.log | grep EE
```Will tell you if there are any errors during xorg startup.
```
cat /var/log/Xorg.0.log | grep fglrx
```will tell you if fglrx is loaded at all (no output means it's not used, if fglrx is loaded you will see lots of lines starting with "fglrx (0)" and "fglrx (1)").

---

### Post by McTek on 2008-05-13
> **ghost_ryder35 said:**
> this is a very very very easy way to do this :)

Tried envyNG, get error message when trying to install ATI driver.

---

### Post by McTek on 2008-05-13
> **TransitMan said:**
> I really hate to say this, but those instructions at the site you posted a very self-explanitory. I even understand them and I'm still getting into this whole open/closed source ATI/nVidia drivers thing.

I don't think trying to re-explain them here would really help at all.

Unfortunately they don't work on my system.

---

