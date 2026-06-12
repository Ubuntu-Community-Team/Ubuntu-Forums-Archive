---
title: "Problems with Sound Drivers Acer V5"
date: 2020-12-18
forum: General Help
---

### Post by dorpapst on 2020-12-18
Hello,
I am having problems in getting to work the drivers on an Acer V5 which my aunt bought some days ago.

That is the output of the current grub, ubuntu and kernel versions.
```
$ lsb_release -s -rdc
Ubuntu 20.04.1 LTS
20.04
focal

$ update-grub --version
grub-mkconfig (GRUB) 2.04-1ubuntu26.7

$ uname -r
5.4.0-58-generic


```

I have no idea on how to fix that, but in the settings of Ubuntu, there is only a "Dummy" available for sound output. (Input doesn't work either).

I found an article on StackOverFlow which recommends to change the GRUB versions:
[https://askubuntu.com/questions/1218123/ubuntu-18-04-fresh-install-on-acer-sound-output-dummy-output-no-input](https://askubuntu.com/questions/1218123/ubuntu-18-04-fresh-install-on-acer-sound-output-dummy-output-no-input)

But that entry is some days old with a different Ubuntu version and I have absolutely no idea how to change it do which version, so I don't want to destroy something.

Is there anybody out there who either has a nice idea to solve our issue or can tell us which file I should change to which kernel version to make everything work?
Maybe somebody had similar problems?

Many greetings and Thanks,
Lukas

Edit:
```
lspci -nnk | grep -A2 Audio
sudo dmesg | grep -i audio
```
Those two commands have an empty output, returning nothing if I type that into the terminal of that specific computer

---

### Post by #&amp;thj^% on 2020-12-18
if you will add this to your first post. (EDIT)
And add the output from:
```
lspci -nnk | grep -A2 Audio
```
Also this one as well:
```
sudo dmesg | grep -i audio
```

---

### Post by dorpapst on 2020-12-19
Hey
Thank you for your answer!
I have now checked both of the commands and none of them has any sort of output. 
Both of them are empty.

Can that be correct? It seems logical to me because the sound doesn't work, but I don't know.

I will put that information in the first entry

---

### Post by CelticWarrior on 2020-12-19
Maybe unrelated, maybe not... But an almost obligatory question in this day and age: Have you installed in UEFI mode as it should be or in Legacy mode?

---

### Post by dorpapst on 2020-12-19
I used UEFI mode

---

### Post by CelticWarrior on 2020-12-19
OK, so I assume you also disabled Secure Boot? Disabling Fast Boot also recommended. And, if dual-booting with Windows you *must* disable its (Windows) Fast Startup "feature".

---

### Post by #&amp;thj^% on 2020-12-19
If all that fails, **_and only if that fails_**
Try adding this line to "/etc/modprobe.d/alsa-base.conf"
To do this use:
```
sudoedit /etc/modprobe.d/alsa-base.conf
```
Then at the bottom of that file paste this line in.
```
options snd_hda_intel model=acer-aspire-8930g
```
save it, then close it and reboot. Now what do we have?

---

