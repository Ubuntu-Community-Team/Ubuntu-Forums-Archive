---
title: "change login resolution on extenal monitor"
date: 2015-06-11
forum: General Help
---

### Post by bookie2 on 2015-06-11
Hi guys!
I have a Sony Vaio with a broken screen so it is connected to an external monitor....at the moment it is 1280x1024 after logining in...

Is there a way to make the login screen appear at the right resolution instead of a small screen with black border...

I will probably be going to use a bigger external monitor at some point and would like it automatically to go to that resolution before I login...

Is there an easy way to achieve this?

bookie2

---

### Post by bookie2 on 2015-06-11
Hi again!
I have got as far as adding new modes to xrandr and saving them...but now when I boot the laptops screen comes to live and stays alive until I login?
Just can't seem to find anything that really relates to why the resolution on the login screen is so small and how to fix that...once I log in it goes to full screan no problems...
bookie2

---

### Post by Bashing-om on 2015-06-11
bookie2; Hello;

Try this:
Make an edit to one of grub's config files; " /etc/default/grub "
in the line: " #GRUB_GFXMODE=640x480 " change it:
1) remove the comment character '#"
2) change " 640x480 " to " 1280x1024 " as you know it is an acceptable resolution.
For the change to take effect:
```

sudo update-grub

``` to propgate the change to the system.

Reboot to see the effect.

In my use case for my system, this works for me.

[INDENT][INDENT]might for you also
[/INDENT][/INDENT]

---

### Post by bookie2 on 2015-06-11
Thanks for that but it doesn't work....same problem the login pic is as wide as the screen but not as high?
Big black area under the pic...how is it managing the width and not the height
bookie2

---

### Post by Bashing-om on 2015-06-12
bookie2; Welp;

I be look'n to find the way to change the screen resolution. Need to know what release you are running and what desktop ?
So we know what files to edit to affect that change .

[INDENT][INDENT]it be that process of learning
[/INDENT][/INDENT]

---

