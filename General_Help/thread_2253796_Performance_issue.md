---
title: "Performance issue"
date: 2014-11-22
forum: General Help
---

### Post by nlr2 on 2014-11-22
[COLOR=#000000][FONT=Arial]Hello,
I have experienced performance issues on my Dell laptop since I use Ubuntu on it (~1 year and a half). It takes around 3 or 4 minutes to boot, and when it seems completely up, I have to wait a long time until the first program loads (this is the main problem and it has been occurring since Ubuntu 13.04 at least). Then, after a couple of hours using it, everything starts to lag. My mouse starts jerking on my screen as soon as I try to move it. 9 times out of 10, I have to manually restart my computer, since I can't launch a TTY, X seems completely frozen and my computer has no more reaction.

My laptop is a Dell Inspiron 7520 (15R) running the following hardware :
CPU : Intel(R) Core(TM) i7-3632QM CPU @ 2.20GHz, 
GPU low-energy : Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
GPU high-performances : Advanced Micro Devices, Inc. [AMD/ATI] Chelsea LP [Radeon HD 7730M] (rev ff) (I think the problem might be caused by the GPU(s))
RAM : 8Go 
OS : Ubuntu Gnome 14.10 utopic 64 bits

Thanks for your help.
nlr2
[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-11-22
Look in your log files and see what is going on.  Open a terminal:

```
more /var/log/syslog
```

Don't post it, just cut and paste any error messages or things related to graphics errors.  Also:

```
more /var/log/Xorg.0.log
```

Graphics problems are difficult to troubleshoot.  Try turning off the ATI graphics in BIOS and just use the Intel graphics and see if the behavior changes.

---

### Post by nlr2 on 2014-11-22
Thanks for you answer @tgalati4.

Here is an excerpt of my syslog boot sequence : [http://paste.ubuntu.com/9177380/](http://paste.ubuntu.com/9177380/) . Take a look at the last lines. Launching Chromium browser seem to cause a segfault in [COLOR=#000000]i965_dri.so (It is not the first time I see this error). Also, I get the last line thousand of times in the whole log, even if I copied it only one time.[/COLOR]
And my Xorg.0.log : [http://paste.ubuntu.com/9177548/](http://paste.ubuntu.com/9177548/) .

Unfortunately, I can't turn off any of my GPUs in the BIOS. There is no option for that.
Thanks,
nlr2

---

### Post by sandyd on 2014-11-22
> **nlr2 said:**
> Thanks for you answer @tgalati4.

Here is an excerpt of my syslog boot sequence : [http://paste.ubuntu.com/9177380/](http://paste.ubuntu.com/9177380/) . Take a look at the last lines. Launching Chromium browser seem to cause a segfault in [COLOR=#000000]i965_dri.so (It is not the first time I see this error). Also, I get the last line thousand of times in the whole log, even if I copied it only one time.[/COLOR]
And my Xorg.0.log : [http://paste.ubuntu.com/9177548/](http://paste.ubuntu.com/9177548/) .

Unfortunately, I can't turn off any of my GPUs in the BIOS. There is no option for that.
Thanks,
nlr2

Have you installed the ATI fglrx (properitary) drivers?

If so, just use
```

sudo aticonfig --px-dgpu
```
To use the ati card, and
```

sudo aticonfig --px-igpu
```
to use the intel drivers.

After running that, run
```

sudo service lightdm restart
```

Alternatively, you can add a applet in your systray to switch between the two gpus. That is available from [https://github.com/beidl/amd-indicator/blob/master/amd-indicator_0.9b6_all.deb?raw=true](https://github.com/beidl/amd-indicator/blob/master/amd-indicator_0.9b6_all.deb?raw=true)

---

