---
title: "Ubuntu 13.04. fails to start -&gt; NVidia drivers (Vostro laptop)"
date: 2013-04-25
forum: General Help
---

### Post by martin851 on 2013-04-25
i installed nvidia-drivers-103 after restart I see just blank purple screen during start-up and then just blank black screen appears and nothing happens after.

- i purged NVidia drivers in recovery mode but that did not helped, i noticed i have broken Unity in recovery mode (not launchpad/toolbars) so i followed :

[Unity doesn't load, no Launcher, no Dash appears]("http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears")

where i reinstalled my unity/compiz but this did not worked for me.  Which logs should i check and what could go wrong ? 

Currently i am without unity/compiz and NVidia drivers (using gdm) and i still cannot boot OS (only recovery mode works). I guess the reason is much more deeper than i expected. 
 How to restore original configuration ? 

HW : laptop Vostro 3750, Nvidia GT 525M, Intel Mobile HM67 Chipset

I noticed this message in boot.log (maybe there`s more stuff but i am not expert) :


[LIST=1]
[*] * Starting load fallback graphics devices[74G[[31mfail[39;49m]
[*]initctl: Event failed
[*] * Stopping [74G[[31mfail[39;49m]
[*] * Starting GNOME Display Manager[74G[ OK ]
[/LIST]

Any hints ? What i should check next ?

---

### Post by pqwoerituytrueiwoq on 2013-04-25
There is a bug with the kernel, using the mainline kernel will work around the issue

from recovery mode terminal:
fix the issue:
```
# mount -o rw,remount /
# cd /tmp
# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/linux-{image,headers}-3.9.0-030900rc8-generic_3.9.0-030900rc8.201304211835_amd64.deb
# wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc8-raring/linux-headers-3.9.0-030900rc8_3.9.0-030900rc8.201304211835_all.deb
# dpkg -i ./linux-*.deb
# reboot
```
if it was working before:
```
# mount -o rw,remount /
# apt-get purge nvidia-*-updates nvidia-settings-*
# rm /etc/X11/xorg.conf
# reboot
```

You can use this to help you keep the mainline kernel up to date
[http://askubuntu.com/questions/160535/how-do-i-add-the-mainline-kernel-ppa#answer-285613](http://askubuntu.com/questions/160535/how-do-i-add-the-mainline-kernel-ppa#answer-285613)

---

### Post by martin851 on 2013-04-26
This did not helped, kernel is upgraded but start always fails. Recovery mode works as before.

---

### Post by pqwoerituytrueiwoq on 2013-04-26
if you are using the 3.9 kernel try reinstalling the nvidia driver
run [FONT=courier new]uname -r[/FONT] to check that

---

### Post by martin851 on 2013-04-26
This is last message in the syslog :

```

Apr 27 00:28:22 umachine kernel: [  568.734181] mtrr: no MTRR for e0000000,3ff0000 found
Apr 27 00:28:22 umachine kernel: [  568.734181] mtrr: no MTRR for e0000000,3ff0000 found
Apr 27 00:28:24 umachine named[1837]: received control channel command 'stop -p'
Apr 27 00:28:24 umachine named[1837]: shutting down: flushing changes
Apr 27 00:28:24 umachine named[1837]: stopping command channel on 127.0.0.1#953
Apr 27 00:28:24 umachine named[1837]: stopping command channel on ::1#953
Apr 27 00:28:24 umachine named[1837]: no longer listening on ::#53
Apr 27 00:28:24 umachine named[1837]: no longer listening on 127.0.0.1#53
Apr 27 00:28:24 umachine named[1837]: no longer listening on 192.168.1.5#53
Apr 27 00:28:24 umachine named[1837]: exiting
Apr 27 00:28:25 umachine exiting on signal 15
```

..then it hangs -> i do hard restart.

I googled a bit about mtrr error and i found this thread :
[https://bbs.archlinux.org/viewtopic.php?id=161964](https://bbs.archlinux.org/viewtopic.php?id=161964)

I have latest kernel and i am using that kernel script for updates... (hopefully rc9 will be released soon).


[I]Nvidia drivers 304 / 310 break my unity even in recovery mode, so i have to be in gdm fallback mode. When i boot up recovery mode + unity i see warning that i did not selected screen size (propably some default settings is missing or autodetection does not work at all....).
[/I]

---

### Post by pqwoerituytrueiwoq on 2013-04-26
i don't think there will be a rc9 i think 8 is the last rc before 3.9 comes out
source: [http://www.phoronix.com/scan.php?page=news_item&px=MTM1Njg](http://www.phoronix.com/scan.php?page=news_item&px=MTM1Njg)

that sounds like the nvidia driver is not setup
if you try to open nvidia-settings it will tell you what to do
you can try ```
sudo dpkg-reconfigure nvidia-*
```

---

### Post by martin851 on 2013-04-27
As NVidia drivers totally broke recovery mode i** have to install whole OS from scratch. I lost 2 days because of that. **Worst thing is that i don`t know what exactly went wrong. Hard to blame Ubuntu/NVidia/Unity wihout proof.

**Please take full partition backup before you change kernel or before you install anything major in your Ubuntu.**

---

### Post by rsupera on 2013-06-24
This just happened to me. So I have to remove nvidia then run these commands to restore untiy:
[LEFT][FONT=Ubuntu Mono]
dconf reset -f /org/compiz/
[/FONT][FONT=Ubuntu Mono]unity --reset-icons &disown
[/FONT][/LEFT]

---

