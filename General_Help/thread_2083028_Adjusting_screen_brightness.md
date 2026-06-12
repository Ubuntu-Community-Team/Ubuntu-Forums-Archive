---
title: "Adjusting screen brightness"
date: 2012-11-11
forum: General Help
---

### Post by vicke4 on 2012-11-11
Hi all i'm using Ubuntu 11.10 in my laptop.i have to reduce screen brightness everytime after i booted into Ubuntu.It is being reset into maximum after every reboot.How can i fix this?

---

### Post by LiamOS on 2012-11-11
There should be a file something like:
/sys/class/backlight/intel_backlight/max_brightness
and another like
/sys/class/backlight/intel_backlight/brightness or actual_brightness

Those might be different depending on your hardware, but there's likely something very similar on your laptop.
The way I'd sort it out is to write a script which runs on startup to echo whatever value you want to the actual_brightness/brightness file. My netbook running Gentoo does this.
If you're unfamiliar with shell scripting, something like this would do:
```
#!/bin/bash

echo "5" > /sys/class/backlight/intel_backlight/actual_brightness 
```
where the 5 would be whatever value is appropriate for your video card. You'd then have to make the script executable and place it in... I think /etc/rc.local/ in Ubuntu, but I could be wrong about that. There are many guide on this sort of thing, though.

There may also be a default value you can set somewhere in settings, but I'm not sure.

---

### Post by vicke4 on 2012-11-11
Should i edit the actual brightness to minimum?

---

### Post by LiamOS on 2012-11-11
That depends on whether you want it at the minimum value or not.

---

### Post by vicke4 on 2012-11-11
Yes i want it to be always minimum how to do that?

---

### Post by Impavidus on 2012-11-12
The relevant "files" are in /sys/class/backlight/intel_backlight and /sys/class/backlight/acpi_video0, both of which contain various brightness related files. I know nothing about them, so I suggest you first play a bit with your brightness and see how these files change. The ones in acpi_video0 seem to set the brightness level on a scale of 0 to max (somewhere around twenty most likely). Setting it to 0 should set your brightness to the lowest setting. The ones in intel_backlight seem to set the actual amount of light (varying exponentially). Setting this to 0 actually instructs your computer to switch of light completely, but I don't know whether it will actually do so. The file you want to edit is one with write permission.

If you've figured out which file to change and to what value, just make that script:```
#!/bin/bash
echo "0" /sys/class/backlight/acpi_video0/brightness
```or whatever you found out.

Be carefull. As I said, I know nothing about this, so I would first try to set this to a value I saw before to make sure it works as expected. Or wait for someone more knowledgeable to reply.

---

### Post by raja.genupula on 2012-11-12
It might be help you
[http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/149265#149265](http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/149265#149265)

---

