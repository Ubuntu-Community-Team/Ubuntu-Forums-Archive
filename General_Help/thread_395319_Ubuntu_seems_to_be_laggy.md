---
title: "Ubuntu seems to be laggy"
date: 2007-03-28
forum: General Help
---

### Post by gannina on 2007-03-28
I've been using Ubuntu for a few days now, and I've noticed that everything seems "laggy" in it. Everything from running firefox to opening programs, etc... Is there test program or something to kinda pinpoint what could be causing this? I have a pretty decent computer, and it flies in XP and thats with a lot more applications running. Thanks in advance.

Oh, and I have disabled ipv6 in firefox, which seems but it made no difference.

---

### Post by ppatalano on 2007-03-28
Is it laggy when you drag around your windows and scroll in windows, etc?

---

### Post by gannina on 2007-03-28
Scrolling large web-pages tend to be jittery, and small ones are all right, but compared to XP there is quite a difference. I've noticed that on Digg ( a website I frequent) that showing or hiding comments is really buggy, and it's not very smooth at all. It could just be me trying to get use to Ubuntu, I have been a windows user pretty much all my life, and things just seem to run a lot smoother on XP for me.

---

### Post by kostkon on 2007-03-28
From your desription it looks like to me a graphics card driver problem. It seems that your pc is slow at drawing the screen graphics. What graphics card you have? Have you checked your *xorg.conf* file?

---

### Post by wj32 on 2007-03-28
Check if /etc/hosts contains:

127.0.0.1 localhost

---

### Post by kostkon on 2007-03-28
> **wj32 said:**
> Check if /etc/hosts contains:

127.0.0.1 localhost

Good work wj32!! I haven't thought about this. Indeed, there is this strange bug that makes everything in Ubuntu to be slow. There are more chances that the lagginess is caused by this bug and not by the graphics card, as I said.

So, gannina, check your */etc/hosts* file for sure.

There is also a bug report filled at Launchpad about this but I don't have the link right now to give it.

---

### Post by gannina on 2007-03-28
Hi, here is the contents of the /etc/hosts file, I'm not sure if I should change anything


```
127.0.0.1 localhost
127.0.1.1 gannina-linux

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by neoaddict on 2007-03-29
[LEETturtle - Disable IPv6](http://leetturtle.com/guides/guide_ubuntuipv6.php)

Could you tell us how much RAM you have and the services you have enabled?

System > Administration > Services

---

### Post by leucippus on 2007-03-29
I also just started using Ubuntu, and was having a similiar problem. I downloaded a program called ENVY that this good man on this thread [http://www.ubuntuforums.org/showthread.php?t=255929](http://www.ubuntuforums.org/showthread.php?t=255929)provided, and it got me fixed up. Good Luck...

---

### Post by ceeg on 2007-03-29
> **gannina said:**
> Hi, here is the contents of the /etc/hosts file, I'm not sure if I should change anything


```
127.0.0.1 localhost
127.0.1.1 gannina-linux

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Make this look like this:

```
127.0.0.1 localhost  gannina-linux
127.0.1.1 gannina-linux

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

```


Restart gnome with
```
sudo /etc/init.d/gdb restart

```

If you get a blank screen, reboot.

---

### Post by neoaddict on 2007-03-29
ceeg, don't you mean:

[FONT=monospace]```
sudo /etc/init.d/gdm restart
```

XD

@gannina, Can you tell us what video card you use?
[/FONT]

---

### Post by gannina on 2007-03-29
I'm currently using a geforce 6600gt with driver version 9.xxx something

---

### Post by neoaddict on 2007-03-29
Could you run this command in Terminal:

```
sudo nano /etc/X11/xorg.conf
```

And copy and paste the file?  (or more specifically Section "Device")

---

### Post by herbster on 2007-03-30
> **ceeg said:**
> Make this look like this:

```
127.0.0.1 localhost  gannina-linux
127.0.1.1 gannina-linux

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

```


What exactly does the change do?

---

### Post by ceeg on 2007-03-30
> **herbster said:**
> What exactly does the change do?

[QUOTE=kerry_s]
This is a fix for the new system that was started back in edgy where the host name was split off to 127.0.1.1, the problem is that some applications still look for the host name @ 127.0.0.1, so to keep those applications happy and running smoothly you simple need to add the host name where those applications expect it to be.
[/QUOTE]

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048)
[http://www.oreillynet.com/linux/blog/2007/01/debian_and_localhostlocaldomai.html](http://www.oreillynet.com/linux/blog/2007/01/debian_and_localhostlocaldomai.html)

---

### Post by gannina on 2007-03-30
Hi, here's he section for my monitor and device.



```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       50.0 - 81.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    Option	   "AddARGBGLXVisuals" "True"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by neoaddict on 2007-03-30
I think you've done this, but try:

[Getting Envy](http://albertomilone.com/nvidia_scripts1.html)
[Installing Xorg 7.2](http://ubuntuforums.org/showthread.php?t=373087&highlight=xorg)

---

### Post by gannina on 2007-04-01
I think my performance has gotten a bit better, especially in firefox, so it must have been that ip6 thing. Thanks for all the help!

---

