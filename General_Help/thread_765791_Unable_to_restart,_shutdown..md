---
title: "Unable to restart, shutdown."
date: 2008-04-24
forum: General Help
---

### Post by Islington on 2008-04-24
Just installed Hardy, to enable the restricted driver for my screen for my video card, I have to reboot.

Whenever I reboot or shutdown, the screen freezes on the uspash screen with the orange on black bar, at this point nothing else works. I have tried doing ```
 sudo shutdown -r now 
``` and got the same result. 

Google reveals no results. Please help me.

---

### Post by Islington on 2008-04-24
bump

---

### Post by Islington on 2008-04-25
fixed shutdown and hibernate. by using [http://ubuntuforums.org/showpost.php?p=4786463&postcount=5](http://ubuntuforums.org/showpost.php?p=4786463&postcount=5) still need help figuring out reboot.

---

### Post by Islington on 2008-04-26
daily bump, would appriciate some help.

---

### Post by Cue2 on 2008-04-26
Does Logout give you the same problem? I think I may have the same problem as you.

---

### Post by Islington on 2008-04-26
unfortunately, no, logout seems to work for me.
Thanks for responding though.

---

### Post by Naatan on 2008-04-26
Does it give any debug information in /var/log/syslog or when you type the command?

To execute with verbose mode do;

$ sudo shutdown -rv now

---

### Post by Islington on 2008-04-26
This is what I see on the screen before it hands on the pretty black bar. I am copy pasting this from /var/log/syslog

```
Theta NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

I will attach the file if you want me to, I *really* apprieciate your help. Honestly, its the last problem I have on Hardy that isnt my fault.

---

### Post by Naatan on 2008-04-26
I can't imagen that being the problem but all the same you should try disabling wireless networking to see if that makes a difference.

What's this pretty black bar your speaking of?

---

### Post by Islington on 2008-04-26
> **Naatan said:**
> I can't imagen that being the problem but all the same you should try disabling wireless networking to see if that makes a difference.

What's this pretty black bar your speaking of?

Remember the ubuntu symbol on a black background and the black bar that becomes orange when you boot up? I get an orange bar, that becomes black when I am shutting down...

Could mounted disks have something to do with it? I am looking at the syslog file and a lot of it is about mounting and unmounting my mp3 player.

---

### Post by Naatan on 2008-04-26
Possibly.. you could try disabling all but the swap and root partition in /etc/fstab and see what that does (ironically a restart is required for this to take effect)

---

### Post by Cue2 on 2008-04-26
May have something to do with ACPI, APM if you don't get problems when you log out

try this maybe

[http://ubuntuforums.org/showpost.php?p=2260791&postcount=10](http://ubuntuforums.org/showpost.php?p=2260791&postcount=10)

SCRAP THIS
Just read shutdown works for you.

---

### Post by leeblack on 2008-04-28
> **Islington said:**
> Just installed Hardy, to enable the restricted driver for my screen for my video card, I have to reboot.

Whenever I reboot or shutdown, the screen freezes on the uspash screen with the orange on black bar, at this point nothing else works. I have tried doing ```
 sudo shutdown -r now 
``` and got the same result. 

Google reveals no results. Please help me.
I'm having the same problem you describe. I'm a relative newby to Linux but I would really like to get away from windows and Ubuntu seems like my best bet.

Dell XPS-410 Intel Core 2 6600 @ 2.4 GHz, 2 GB RAM, NVIDIA GForce 7300 LE.

---

### Post by Hesperion on 2008-04-28
New installation of Hardy, 8.04//EeePc 4G Surf//2 Gb ram

I have been reading and reading for a more exact match for my problem but not finding precisely the same issue being discussed. I find that the UI restart works just right and a cold start goes flawlessly (I think). But using the UI to shut down produces a lot of messages then a blank screen, the wireless light goes out but the power light stays on (whether plugged into ac or just batt. only). I can only effect a full shutdown by holding the power button for a few seconds. If left alone it would never fully power down. In reading these posts I am gathering that people are having this phenomenon but they are mostly getting other effects as well. This is the only issue I am having; the rest is all good. I figure that this is a simple matter that someone will recognise immediately. Can I supply some other details that might shed some light? I don't want to take up time and space here with extraneous gabble. What are your thoughts??

---

### Post by robelliott2125 on 2008-04-29
I've a sorta similar prob, although i don't get to the actual shutdown screens...

If I click on the shutdown button (top right) nothing happens, except "locking" my screen.

Basically, clicking it, nothing is displayed, but at the same time, I'm unable to click on any drives on my desktop, switch to desktop, or anything else.  My screen doesn't even start to fade.

Sorry about the jump on this thread, but a search of Unable to shutdown restart came up exactly with this thread, which is brilliant!

If someone can help, i would be very grateful, as CTRL + Alt and Backspace is becoming tiresome, and I'm unsure if i'm messing up my installation.  2 weeks in, and I've reinstalled 6 times...  Not good.  

Thank you,

---

