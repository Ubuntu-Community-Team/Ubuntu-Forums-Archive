---
title: "What is the backend command Ubuntu uses to hibernate?"
date: 2008-05-10
forum: General Help
---

### Post by worc on 2008-05-10
Hi everyone!

Does anyone knows what is the backend command Ubuntu 8.04 uses to hibernate?

I'm considering to let laptop_mode to hibernate my laptop when it is on battery and the power is critically low. To do that, I edited 
/etc/default/acpi-support
and set 
ENABLE_LAPTOP_MODE=true

Then I found when the power is critically low, my laptop is just rudely powered off, and I lost all unsaved data. After some blind messing around, I found in /etc/laptop-mode/laptop-mode.conf, it says
HIBERNATE_COMMAND=/usr/sbin/hibernate
But I don't have that command in my system. I guess this is the reason.
With more research, I found the script "/usr/bin/gnome-power-cmd.sh".I've tried "gnome-power-cmd.sh hibernate" in a terminal shell to test if that works, I thought if it does, I can just replace the one in /etc/laptop-mode/laptop-mode.conf with "gnome-power-cmd.sh hibernate". (Hoping I'm right.)
Actually, it seems that gnome-power-cmd.sh does hibernate my laptop except it does not switch off the power afterwards. I mean I have to keep pressing on the power button for some seconds to switch it off. If I then push the power button again, I get a resume from hibernate. The resume succeeded. So I assume the previous hibernate worked but somehow it did not switch off the power.
But if I hibernate the machine by choosing ubuntu hibernate option (Menubar/System/Quit, then hibernate), the hibernate works great with power being switched off. So I guess Ubutnu is not simply or directly executing "gnome-power-cmd.sh hibernate" to do the job. 

So what is the real command(s)/script(s) Ubuntu executes to hibernate the machine? There must be one somewhere, right?

---

### Post by bingoUV on 2008-05-10
Do you have /usr/sbin/pm-hibernate ?

---

### Post by ryanhaigh on 2008-05-10
There are lots of different backends that can be enabled for suspend and possibly also for hibernate. When I installed a friends laptop I found out that gnome uses hal to hibernate, the scripts in these files are what control the backend used:
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

If you can find what commands work for you then you can change the scripts to use those commands.

EDIT: Found a [howto thats related]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

---

### Post by worc on 2008-05-10
> **bingoUV said:**
> Do you have /usr/sbin/pm-hibernate ?

Yes, I do.
Actually I did tried that one. That did not lock my screen when suspend/hibernate as Ubuntu does. 
I meant to not mention that just because I guess that is at most 'portion' of what's behind Ubuntu's suspend/hibernate menu item.

Thanks for the hint anyway.

---

### Post by worc on 2008-05-10
> **ryanhaigh said:**
> There are lots of different backends that can be enabled for suspend and possibly also for hibernate. When I installed a friends laptop I found out that gnome uses hal to hibernate, the scripts in these files are what control the backend used:
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

If you can find what commands work for you then you can change the scripts to use those commands.

EDIT: Found a [howto thats related]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html")

When I looked into the 2 files you pointed out, I found it clearly says only pm-utils is supported.
I did checked the howto tutorial you linked. That's another story in case of Ubuntu's 'native' suspend/hibernate doesn't work. But the 'native' one does work great on my laptop except I will lose my sound after resume from a suspend, which I believe is not alsa's problem as I used to think. ( [http://ubuntuforums.org/showthread.php?t=786902](http://ubuntuforums.org/showthread.php?t=786902) )
I'm right now hunting some kind of Ubuntu's native method to do the job. That can not negative your help anyway. Thank you very much. If I failed on seeking what I am wanting to do right now, I will plan to try "uswsusp" for sure. 
Once again, thanks for the reply.

---

### Post by ryanhaigh on 2008-05-10
Ok well if the actual mechanism used is working for you then you can probably just call that script and see if it hibernates in the way you want.

---

### Post by worc on 2008-05-11
> **ryanhaigh said:**
> Ok well if the actual mechanism used is working for you then you can probably just call that script and see if it hibernates in the way you want.

Tried to directly call the script, it says 
```
Can't open hal-functions
```
"hal-functions" is actually right in the same path where the scripts are. Then I modified the script to add path prefix for "hal-functions" and execute the script again. Then it says
```
org.freedesktop.Hal.Device.UnknownError
Missing or empty environment variable(s).
This script should be started by hald.
```
So I guess the script is as said not supposed to be executed directly in shell.

Also tried uswsusp. Only get s2both and s2disk, no s2ram. man page says s2both is actually a S3 suspend to memory, so I guess it is s2ram. But it actually did a hibernate to my laptop and it requires root permission to run. I believe it will work after some config, but as the native one does work for me, I don not want to make things get complicated right now. 

Anyway, thanks for the hint.

Still hunting for the native commands. Anyone has any suggestion on where to find the answer other than google and ubuntuforums.org?:confused:

---

### Post by ryanhaigh on 2008-05-13
From here [http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f](http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f)
> 
You can put the system into hibernation using the following:
(edit: this is supposed to be a single line command)
dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate

Sorry it took so long to respond, I got the same error when I tried it on my own system and haven't had time to look for the correct method until today. If you use this in the laptop mode script you should change dbus-send to the full path /usr/bin/dbus-send.

---

### Post by worc on 2008-05-13
> **ryanhaigh said:**
> From here [http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f](http://live.gnome.org/GnomePowerManager/FAQ#head-ca9ddd6e2954f42fa6fb45b392ece499a6f8ab6f)

Sorry it took so long to respond, I got the same error when I tried it on my own system and haven't had time to look for the correct method until today. If you use this in the laptop mode script you should change dbus-send to the full path /usr/bin/dbus-send.

Hey ryanhaigh, it's so kind of you to keep my problem within your thought! Thank you very much!

Actually the page you linked was the first web page I've ever read to try to fit my demand. I found the command is actually right the core of the script /usr/bin/gnome-power-cmd.sh, which I've found does can hibernate my laptop except it does not switch off the power. Having that experience, I ignored the command on that web page.

Whatever, I tried the command today. 
```
$ dbus-send --session --dest=org.gnome.PowerManager --type=method_call --print-reply --reply-timeout=2000 /org/gnome/PowerManager org.gnome.PowerManager.Hibernate
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.PowerManager was not provided by any .service files
```

Any ideas?

By the way, do you think the command is different to the script /usr/bin/gnome-power-cmd.sh?

---

### Post by jamesrl on 2008-10-09
```
dbus-send --session --dest=org.freedesktop.PowerManagement --type=method_call /org/freedesktop/PowerManagement org.freedesktop.PowerManagement.Hibernate
```

See: [http://ubuntuforums.org/showpost.php?p=5663386&postcount=4](http://ubuntuforums.org/showpost.php?p=5663386&postcount=4)

---

