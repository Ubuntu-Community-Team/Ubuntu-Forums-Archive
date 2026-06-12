---
title: "High CPU Usage"
date: 2013-01-10
forum: General Help
---

### Post by milosdallas on 2013-01-10
Hello.
I installed Ubuntu 12.10 and sometimes CPU Usage goes to 100%. With just one active application, Chromium (or Firefox).

I was before on WinXP, same problems but rarely than on Ubuntu.

Intel P4 3.0Ghz
3GB Ram
Freshly installed Ubuntu 12.10

Thanks. :)

---

### Post by Impavidus on 2013-01-10
There're also some programs running in the background. Use the system monitor to find out which process is using that cpu time.

---

### Post by dannyboy79 on 2013-01-10
you can use "top" command to see what process's are all running. what graphics card? you may be better off using Unity 2D or Xubuntu or Lubuntu

---

### Post by milosdallas on 2013-01-10
Thanks for replying!

@Impavidus
gnome-system-monitor using up to 85% :/

@dannyboy79
My graphics card is: ASUS AH3650 Silent HDMI
I would use xubuntu but i need photoshop for my job...so that fels off.

Thanks!

---

### Post by Muratturat on 2013-01-10
> **milosdallas said:**
> Thanks for replying!

@Impavidus
gnome-system-monitor using up to 85% :/

@dannyboy79
My graphics card is: ASUS AH3650 Silent HDMI
I would use xubuntu but i need photoshop for my job...so that fels off.

Thanks!

I had same problem even I had quad core. 
Only way to solve it is to install Jupiter, have you ever tried or heard about Jupiter software ?

---

### Post by milosdallas on 2013-01-10
> **Muratturat said:**
> I had same problem even I had quad core. 
Only way to solve it is to install Jupiter, have you ever tried or heard about Jupiter software ?

No. Is this what are you talking about:
[http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10](http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10) ?

Thanks.

---

### Post by Muratturat on 2013-01-10
> **milosdallas said:**
> No. Is this what are you talking about:
[http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10](http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10) ?

Thanks.

Yes, install it and then restart the computer.
After you have installed, switch profile to power saver and you can also change video and graphic settings.

If it doesn't help try preload software: It keeps softwares in your memory so next time when you run softwares it will open it faster and use less CPU.
```
sudo apt-get install preload
```

I've used  ubuntu 2 years and always when I've installed new version of ubuntu it's been loud days for CPU :)

Try these softwares 2-3 days if they doesn't help, then only choice is to install Lighter Desktop Environment, for example LXDE, XFCE and also a lot of more you can check from google.

---

### Post by milosdallas on 2013-01-11
> **Muratturat said:**
> Yes, install it and then restart the computer.
After you have installed, switch profile to power saver and you can also change video and graphic settings.

If it doesn't help try preload software: It keeps softwares in your memory so next time when you run softwares it will open it faster and use less CPU.
```
sudo apt-get install preload
```

I've used  ubuntu 2 years and always when I've installed new version of ubuntu it's been loud days for CPU :)

Try these softwares 2-3 days if they doesn't help, then only choice is to install Lighter Desktop Environment, for example LXDE, XFCE and also a lot of more you can check from google.

Thanks. But that didn't help alot.
Still is laggy, and high cpu usage. When i am trying to play YouTube video it's freeze if i have chrome+software center active.

I can't imagine if is this problem with youtube video, how it will be when i install photoshop :o

Thanks.

---

