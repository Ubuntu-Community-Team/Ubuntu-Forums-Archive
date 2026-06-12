---
title: "How can I know why the jack application does not work well?"
date: 2022-05-16
forum: General Help
---

### Post by WHK on 2022-05-16
I use a fresh install of ubuntu 22.04 LTS and have installed jack:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04 LTS
Release:	22.04
Codename:	jammy
$ sudo apt -y install jackd qjackctl;
```

But when I try to configure the inputs and outputs nothing appears, as if I had no interface, but my audio works fine, I have a normal output (the typical green, light blue and pink). I often use the microphone without problem and I hear audio on my speakers.

How can I know where the error is?

In the settings use alsa driver but the graphic connections is empty.

---

### Post by DuckHook on 2022-05-16
Jack is notoriously finicky and difficult to install on your own. If you rely on it, you might consider installing Ubuntu Studio instead. Studio is an official flavour and is therefore supported by Canonical. I am recommending it because it installs Jack by default, and its maintainers have tweaked and configured Jack to work out of the box (well, mostly&#8212;in the end, Jack is Jack and will always be finicky). 

You can get an overview of the various 'buntu flavours by following the link in my sig. There is a brief description of Ubuntu Studio as the last entry under "[Official Ubuntu Flavours]("https://ubuntuforums.org/showthread.php?t=2415676&p=13848096#post13848096")".

Ubuntu Studio can be found at: [https://ubuntustudio.org/](https://ubuntustudio.org/)

Download and install from the ISO, just like you do any other flavour. I do suggest that you avoid the Ubuntu Studio Installer as recommended on the Studio website, but rather, use the ISO and do a pristine install. That is the best way to increase your chances of a successful working environment.

---

### Post by WHK on 2022-05-17
Thanks for the help but I don't think it's convenient to install an entire operating system just to play guitar, in that case I'd better use windows, the idea is to be able to use my usual ubuntu to play guitar. It has been very difficult to find stable software to play musical instruments on gnu/linux in general and same time use to develop software (i am a web developer).

For now use a loopback but without effects:

```
sudo apt install pavucontrol
pactl load-module module-loopback latency_msec=1
pactl unload-module module-loopback

```

---

### Post by DuckHook on 2022-05-17
You are the only person who can determine whether it is feasible to switch entirely over to a different flavour. I should mention that developing on Ubuntu Studio ought not to be much different from developing on vanilla Ubuntu. But this still requires you to change your flavour.

If Windows works better for you, then that's the better solution. We encourage people to use whichever tool is most appropriate for the job.

---

