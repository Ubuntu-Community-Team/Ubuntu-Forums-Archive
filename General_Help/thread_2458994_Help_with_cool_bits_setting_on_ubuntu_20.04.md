---
title: "Help with cool bits setting on ubuntu 20.04"
date: 2021-03-08
forum: General Help
---

### Post by generic-username123432 on 2021-03-08
Hello everyone

I've gotten into Ethereum mining recently and I want to under clock my gpu. I'm trying to do this with Greenwithenvy, however in order to unlock the under/overclocking functionality I need to change the cool bits setting. 
I tried to do it with this command 

sudo nvidia-xconfig --cool-bits=12

and that generated [FONT=Noto Mono][COLOR=#1c1c1c]xorg.conf, however upon restart I was unable to boot and I had to delete this file in recovery mode

Then I found this

[/COLOR][/FONT]https://www.reddit.com/r/pop_os/comments/ca57ns/what_is_the_replacement_for_xorgconf_want_to_set/

With instructions that seemed like they would solve my problem however upon restart I was again unable to reboot.

Does anyone have a solution to this? It seems like when I generate the necessary configuration files I am unable to boot. 

Thank for any help you can give me

---

### Post by CatKiller on 2021-03-08
Create a file such as */etc/X11/xorg.conf.d/20-nvidia.conf*

Inside, put something like
```
Section "Device"
        Identifier      "Default Device"
        Option          "CoolBits"      "12"
EndSection
```

Restart X (or your computer).

---

### Post by generic-username123432 on 2021-03-08
I did try doing that but it unfortunately did not work. That was the method I followed in the reddit instructions.

---

