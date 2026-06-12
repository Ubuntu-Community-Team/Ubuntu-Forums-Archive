---
title: "missing letters in files and directories"
date: 2014-05-14
forum: General Help
---

### Post by cmcanulty on 2014-05-14
I am running xubuntu 14.04 and recently got the weird effects shown in screenshot. Missing letters. Both in thunar and nautilus not firefox though. When I hover over name the letters fill in.

---

### Post by Toz on 2014-05-14
I've seen similar artifacts on Intel graphics cards with SNA acceleration method enabled. However, this became default a while back so if it is this, its interesting that you are seeing it only now.

What graphics card/driver are you using? This should help to identify it:
```
lspci -k | grep -iA2 VGA
```

And out of curiosity, what is "recently"? Has Xubuntu 14.04 worked fine for a while then it started?

---

### Post by cmcanulty on 2014-05-15
here is the output. It started yesterday. I did a clean install of Xubuntu 14.04 64 bit about a week ago, thank you
```
cmcanulty@ubuntu1:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1439
	Kernel driver in use: i915
cmcanulty@ubuntu1:~$
```

---

### Post by sudodus on 2014-05-15
This works for some old Intel graphics cards. It may be worth trying also in your case (to switch from SNA to UXA acceleration)

If the command 
```
lspci | grep -i vga
```

gives the output

```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```
or similar from the 8xx family you need to create an /etc/X11/xorg.conf file with the following contents:

```
Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection

```

There's a tab in front of the three middle lines. 
Without the xorg.conf the resolution is coarse and Youtube videos are  rendered in an interesting display of green and purple colours. 

In 14.04 the bug is more or less fixed, but still you might get a nicer  looking display using the xorg.conf. Try with and without, if there's no  improvement just delete the file.

---

### Post by cmcanulty on 2014-05-15
I get
```
cmcanulty@ubuntu1:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
cmcanulty@ubuntu1:~$
```

---

### Post by sudodus on 2014-05-15
You have another (probably newer) Intel graphics chip. I don't know if the UXA acceleration tweak will work for you, but it is worth trying.

---

