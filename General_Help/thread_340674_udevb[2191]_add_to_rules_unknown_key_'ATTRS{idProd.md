---
title: "udevb[2191]: add_to_rules: unknown key 'ATTRS{idProduct}'"
date: 2007-01-17
forum: General Help
---

### Post by AllesMeins on 2007-01-17
Hi,

my Edgy shows the following messages during booting:

udevb[2191]: add_to_rules: unknown key 'ATTRS{idProduct}'
udevb[2191]: add_to_rules: unknown key 'ATTRS{idVendor}'

These two lines are repeated over and over filling the whole screen. But after a few seconds booting continues as usual and the system works fine.
But what is it with this messages, what does it meen and how do i get rid of it?

---

### Post by dcstar on 2007-01-17
> **AllesMeins said:**
> Hi,

my Edgy shows the following messages during booting:

udevb[2191]: add_to_rules: unknown key 'ATTRS{idProduct}'
udevb[2191]: add_to_rules: unknown key 'ATTRS{idVendor}'

These two lines are repeated over and over filling the whole screen. But after a few seconds booting continues as usual and the system works fine.
But what is it with this messages, what does it meen and how do i get rid of it?

It looks like the udev system is finding some hardware in your setup that it can't handle, and is logging the messages to the screen during boot-up.

If your system works ok then you shouldn't be too concerned about it, but it may go away with a newer kernel update that is more compatible with your hardware.

---

### Post by John Jason Jordan on 2007-03-08
> **dcstar said:**
> It looks like the udev system is finding some hardware in your setup that it can't handle, and is logging the messages to the screen during boot-up.
If your system works ok then you shouldn't be too concerned about it, but it may go away with a newer kernel update that is more compatible with your hardware.
I just got bit by the same thing on my Edgy amd64 computer. On booting I suddenly got a couple screenfuls of the following:

udevd[2216] add-to-rules: unknown 'attrs{idProduct}'

The same line repeated for about a screenful worth on shutdown, but
after restarting, shutting down, and restarting a few times, it now
happens only on bootup. In spite of what appears to be an error
message, the computer seems to operate fine.

Whatever it means, it was caused by something in the following: Edgy
amd64 announced that I had half a dozen upgrades. I was applying the
upgrades with Synaptic when the computer locked up -- dead keyboard and
mouse, no disk activity. I had to hit the power button.

When Grub came back up I decided to run memtest. I have never done this
before, but I recently ran into a webpage suggesting that memory might
be a cause of lockups -- and I have one original 256 MB stick and one 1
GB replacement stick. Maybe there is a memory mismatch or something. So
I ran memtest one pass, a little over an hour. No errors, so I went
ahead and booted. That is when the above message suddenly appeared.

Google tells me that udevd is some kind of utility, but I don't
understand what it does. And the rest of it is in Greek. But if I
understood it I bet I would know what is wrong and have a fair chance
of fixing it. In the meantime, everything seems to be working fine, but error messages like that worry me.

---

### Post by fsando on 2007-03-09
Got the same
I also noticed that the cd does not turn up on the desktop after boot (I usually keep the ubuntu cd in the drive). It does turn up, however, when inserted.
According to [**[COLOR="RoyalBlue"]This link[/COLOR]**]("http://forums.gentoo.org/viewtopic-t-532612-highlight-unknown+key+attrs+idproduct+attrs+idvendor.html") it is related to two things: libgphoto2 and a specific version of udev.
In the file '/etc/udev/45-libgphoto2.rules' it says ```
# udev rules file for libgphoto2 devices (udev >= 0.98)
```In synaptics my udev is reported as v093.
My guess is that udev 093 does not yet know about those keys.
In the link above it is recommended to move the 'rules' file elsewhere or upgrade udev. Though one post suggest problems after upgrading.
The error should have no effect on performance.

---

### Post by vroy on 2007-03-09
I've been also getting the following error messages while booting since yesterday, when I installed the regular updates 
udevedd[2148]: add_to_rules: unknown key 'ATTRS{idProduct}'
udevedd[2148]: add_to_rules: unknown key 'ATTRS{idVendor}'

any idea?

---

### Post by Catsworth on 2007-03-09
Hey Guys,

Just thought I'd add to this thread.

Following the regular updates yesterday I'm getting exactly the same message, although at this time everything appears to be working normally.

Is there any way to find out what hardware is causing this, and then fix the problem?

Thanks.

---

### Post by precinto on 2007-03-09
From this [thread]("http://ubuntuforums.org/showthread.php?t=379319"), in which people report synaptics touchpad problems after update:

[QUOTE=amelyst]My solution is the following:

    * edit the file /etc/udev/rules.d/45-libgphoto2.rules
    * replace all occurances of ATTRS with SYSFS
    * save the file[/QUOTE]

I haven't tested this yet.

---

### Post by fsando on 2007-03-09
> **precinto said:**
> From this [thread]("http://ubuntuforums.org/showthread.php?t=379319"), in which people report synaptics touchpad problems after update:

> Originally Posted by amelyst
My solution is the following:

* edit the file /etc/udev/rules.d/45-libgphoto2.rules
* replace all occurances of ATTRS with SYSFS
* save the file
I haven't tested this yet.I have just done that: the errors disappear - no other problems yet (just rebooted - no real test)

---

