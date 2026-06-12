---
title: "[SOLVED] /etc/rc.local boot problem"
date: 2008-05-23
forum: General Help
---

### Post by *B* on 2008-05-23
Greetings:

I am running the 32bit version of 7.1 on a Nvidia NForce2 board with an NVidia GeForce4 Ti4200 AGP card. I have Ubuntu installed on my master drive, and 32 XP Pro installed on my second drive. Everything has been working fine for a good while (stable at least, a few problems here and there, nothing major) until the other day. I hadnt booted to Ubuntu in a good while. When I tried to the other day, the splash screen came up, the progress bar showed it as loading...... then it stopped. The following screen flashed 4 times, then stayed solid and it wouldnt change or go any further: 

Setting up ALSA... done.
Starting anac(h)ronistic cron: anacron.
Starting deferred execution scheduler: atd.
Starting periodic command scheduler: crond.
Enabling additional executable binary formats: binfmt support.
Checking battery state...
Running local boot scripts (/etc.rc.local).

I hadnt done any updates or upgrades. Everything worked fine the last time I booted to Ubuntu. Any ideas?

---

### Post by bingoUV on 2008-05-23
Can you post the contents of /etc/rc.local file here?

---

### Post by pointone on 2008-05-23
Chances are it has nothing to do with rc.local; it is simply the last script run during the boot process. More than likely there is a problem preventing GDM from starting properly.

What happens if you press Ctrl+Alt+F7 at that screen?

---

### Post by shrimphead on 2008-05-23
or try hitting ctrl-C that should interrupt the process and drop you to a login prompt.

once you login in the console, you can run sudo /etc/init.d/gdm start to manually start X

---

### Post by *B* on 2008-05-24
First off, thanks for the responses. Secondly, here are the results:

bingoUV - My computer wont boot into Ubuntu. If there is another way to access that file, I am unaware of it. 

pointone - Ctrl+Alt+F7 merely takes to a blank screen with a flashing "-" prompt.

shrimphead - Ctrl+C does nothing at all

I tried Ctrl+Alt+F2 which took me to a login prompt. I logged in and typed "sudo /etc/init.d/gdm start". It asked for my password. After entering the p/w, it said "starting gnome display manager" and returned back to the prompt, but didnt boot the machine.

---

### Post by *B* on 2008-05-27
bump

---

### Post by pointone on 2008-05-28
Try running:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

...to regenerate your xorg.conf file. When prompted for which video driver to use, test the nv or vesa drivers instead of the proprietary nvidia driver, which may be causing the problems.

---

### Post by *B* on 2008-05-28
pointone....THANKS! That did the trick. 

Im not sure what you meant by testing another driver. AFter I typed in the command you suggested, I receieved the following: "xserver-xorg postinst warning: overwriting possibly-customized configuration files; backup in etc/x11/xorg.conf20080528075332". Then it took me back to the prompt. I rebooted and the system came up just fine. The system is not using the "restricted NVidia driver" that it always has, and its noticeable. But, its booting, thats the main thing. Thanks again!

---

### Post by Zorael on 2008-05-28
> ***B* said:**
> The system is not using the "restricted NVidia driver" that it always has, and its noticeable. But, its booting, thats the main thing. Thanks again!
Upon reconfiguring xserver-xorg, your settings for X (the graphical interface) are wiped. X autodetects a lot when it comes to videocards and monitors, but it will never default to a proprietary driver unless explicitly told to. As such, you're likely running the open **nv** driver right now. At worst, the vanilla **vesa** one.

Enter this in a terminal to reenable the proprietary **nvidia** driver, provided you have it properly installed (though disabled).
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --randr-rotation
```
Save, log out, restart X with Ctrl+Alt+Backspace, see if it worked.

---

### Post by *B* on 2008-05-30
I thought I wouldnt be able to run that command. After getting the machine to boot, and it seeming stable, I updated it to 8.04. I had updated my laptop without any problems, so I figured Id update this tower. Big mistake. Now, I cant start anything administrator related. I cant even open synaptic or hardware drivers........ nothing. I have a shortcut on my desktop with the "gksudo "gnome-open %u"" command which makes it easy to drag a file to the command and have it opened with root privileges to edit it and save it. whenever I click on that command, or anything admin related, its says "starting administration.." in the panel.... but nothing happens. I was though finally able to open a terminal and run the command you listed, and it evidently changed me back to my NVidia driver, as I have the "effects" active again. Due to the above problem though, I cant open anything to check which driver or what version etc... According to the system now, it sees my drives even as SATA (now listed as sda...) and they arent. Im wishing I hadnt updated to 8.04

---

