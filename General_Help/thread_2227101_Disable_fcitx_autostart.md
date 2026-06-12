---
title: "Disable fcitx autostart"
date: 2014-05-30
forum: General Help
---

### Post by magpie7 on 2014-05-30
Since I installed fcitx, it always autostarts but I dont always want it and it slows down my boot-up time. But I cant work out where it autostarts from!  

There are no fcitx autostart files in:         
[B]/etc/xdg/autostart/         
/etc/init.d/         
 /home/$user/.config/autostart/         
 /home/$user/.config/openbox/autostart/[/B]

Nor are there any fcitx files in my runlevel **/etc/rc.*/** folders!  

And **fcitx-config-gtk3** doesnt provide any 'disable autostart' features 

 How do I disable autostart? Why is it this difficult!?

---

### Post by bapoumba on 2014-05-30
Not quite sure as I am not using fcitx.
From here : [https://wiki.archlinux.org/index.php/fcitx](https://wiki.archlinux.org/index.php/fcitx), anything in your ~/.profile ?
Or here [https://bugs.launchpad.net/ubuntu/+source/fcitx/+bug/1275708](https://bugs.launchpad.net/ubuntu/+source/fcitx/+bug/1275708), in /usr/bin/fcitx-autostart
Also, although the original question is marked as invalid, may be some info here : [https://bugs.launchpad.net/ubuntu/+source/fcitx/+bug/1275708](https://bugs.launchpad.net/ubuntu/+source/fcitx/+bug/1275708)

---

### Post by magpie7 on 2014-05-31
Thank you for your reply bapoumba
No mention of "**fcitx**" or "**/usr/bin/fcitx**" in my **~/.profile** or **/etc/profile** :(

I had a look at the bug reports you mentioned but I didnt find anything to shed light on the situation because I cant find any ***.desktop** files relating to fcitx

It must be autostarting from somewhere! I guess just not from the normal runlevel or autostart folders/scripts...

---

### Post by magpie7 on 2014-05-31
I found a fix! I searched my whole OS for any mention of /usr/bin/fcitx:
```
grep -rl "/usr/bin/fcitx"
```

found "/usr/share/im-config/data/22_fcitx.rc ." (amongst other files). 

Then I just moved it:

```
sudo mv /usr/share/im-config/data/22_fcitx.rc .
```

On restart, fcitx doesnt autostart but still starts if I run it myself. :p:p:p I have control of my desktop again!

---

### Post by bapoumba on 2014-05-31
Hey :)
I'm always hesitant to change the root system files, and always prefer to set user rules or change /home configs.

For info, I have this file too, although have not installed fcitx. Have you looked if there is a way to make it wait some other input method kick in first ?

I had a look at /usr/share/im-config/data/00_default.rc and /usr/share/im-config/data/01_auto.rc
ibus is 20 and fcitx is 22, so ibus should take the preference. Not sure why it is not, there must be something else going on.

---

