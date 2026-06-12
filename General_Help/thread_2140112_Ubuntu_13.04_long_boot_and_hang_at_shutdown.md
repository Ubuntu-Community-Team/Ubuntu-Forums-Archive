---
title: "Ubuntu 13.04 long boot and hang at shutdown"
date: 2013-04-28
forum: General Help
---

### Post by open.source on 2013-04-28
Hello everyone, I just installed Ubuntu 13.04 amd64 and I'm having problems with my laptop. At almost every boot and and shutdown the following happens:

- There is a long delay at boot, normally Ubuntu boots in about 6 seconds on my laptop but now it's taking over a minute sometimes before the login window appears from GRUB.
- Every time the aforementioned happens, the computer is unable to shutdown cleanly and the following appears during shutdown (see screenshot in addition to this):
           
         nm-dispatcher.action: Caught signal 15, shutting down...                [[COLOR=#ff0000]fail[/COLOR]]

The specs of the laptop are as follows (in case they are needed):

- Dell Precision M4500
- Mobile QM57 Chipset
- Core i7 extreme 920xm
- Nvidia Quadro FX1800m (configured using NVIDIA 313.30 drivers from repository)
- 16 GB DDR3-1333 ram (tested with Memtest86+)
- OCZ Vertex 4 512 GB SSD (no problems with SMART readout)
- Intel Centrino Ultimate N-6300 wifi (connected to WPA2 wireless N)
- Certified to work with Ubuntu

Please note that the above hardware functioned properly in Ubuntu 12.10 and there are also no problems in Windows 7. I'm also surprised that no one else seems to be experiencing my issue. I would appreciate any help I could get because I really like Ubuntu 13.04, it's faster, has new apps and better suits my workflow. Apart from the boot problem the system is very stable. The screenshot is attached to this post. :)

EDIT: This review also seems to mention the same issue I am experiencing (on a second gen Core i3 laptop). It could be more widespread then it looks.
[http://www.hecticgeek.com/2013/04/performance-ubuntu-13-04-review/](http://www.hecticgeek.com/2013/04/performance-ubuntu-13-04-review/)

---

### Post by arulanand on 2013-04-30
I am facing this issue while shutdown / reboot.

my Laptop is dell. Shutdown hangs indefinitely. It's quite frustrating.

---

### Post by Cheesehead on 2013-04-30
After a reboot, please attach copies of your /var/log/dmesg and /ver/log/syslog files to this thread.
Please attach...NOT copy-and-paste. Big files.

---

### Post by FernandoBasso on 2013-05-01
My ubuntu (32 bits on a sony vaio laptop) takes about 2 minutes until it shows the login screen.
I don't have problems with shutdown, although I classmate of mine has the boot time problem and
the shutdown problem.

Here's my dmesg file.
[https://gist.github.com/FernandoBasso/5494592](https://gist.github.com/FernandoBasso/5494592)

I couldn't attach because the uploader said it was "too big"...

---

### Post by Cheesehead on 2013-05-01
That post has 854 lines, covering the first 32 seconds (not 2 minutes) of the boot. No delay problems evident that I can see.
What about your /var/log/syslog?

---

### Post by technoholic on 2013-05-01
I also am having shutdown hang problem after upgrading 12.10 64bit to 13.04, 64bit. Shutdown stops with unmount failure messages. My syslog is:

May  1 07:49:34 richlinux anacron[21949]: Job `cron.daily' terminated
May  1 07:49:34 richlinux anacron[21949]: Normal exit (1 job run)
May  1 08:17:01 richlinux CRON[22801]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 09:17:01 richlinux CRON[23000]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 10:17:01 richlinux CRON[23253]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  1 10:38:08 richlinux dbus[1055]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
May  1 10:38:08 richlinux dbus[1055]: [system] Successfully activated service 'org.freedesktop.hostname1'

---

### Post by technoholic on 2013-05-01
See also Launchpad Bug #1170911

---

### Post by mlamprou on 2013-05-02
check this

[http://askubuntu.com/questions/287792/not-been-able-to-shut-down-ubuntu-13-04-error-related-with-acpid-and-speech-dis](http://askubuntu.com/questions/287792/not-been-able-to-shut-down-ubuntu-13-04-error-related-with-acpid-and-speech-dis)

---

### Post by Blue-Tiger on 2013-05-06
Just to weigh in, I also experience this problem on all 3 of my machines that I have. All of them where clean installs of 13.04, not upgrades.  Two machines are laptops, one is a desktop machine. All have installed the proprietary nvidia-drivers (313 version) and have unencrypted swap (I mention this because sometimes the shtudown hangs on "deactivating swap".

---

### Post by FernandoBasso on 2013-05-06
I checked dmesg again today after a 2-minute boot, and indeed, the last entry is at this time. 33.512254.
I really don't know what is going on.

---

### Post by sinkr on 2013-05-15
> **FernandoBasso said:**
> I checked dmesg again today after a 2-minute boot, and indeed, the last entry is at this time. 33.512254.
I really don't know what is going on.

Same here, fresh install hangs at reboot/shutdown circa these messages:

```

* Asking all remaining processes to terminate...
* All processes ended within 1 seconds....

```

I have physical terminal access and none of the VTs give me any diagnostic info.  I am current on the patches, including *dist-upgrade*.

---

### Post by open.source on 2013-05-15
This appears fixed in the latest kernel from proposed for me.

---

### Post by gidoca on 2013-05-17
> **open.source said:**
> This appears fixed in the latest kernel from proposed for me.

I have the same problem. Which version is it that fixed it for you?

---

### Post by open.source on 2013-05-17
Hi, if you go to software sources in settings and check off raring proposed in the updates tab, you will have the option of upgrading to the latest fixed kernel.

It was fixed in 3.8.0-20.31 and newer for me, hope this helps.:)

---

### Post by cbcollins on 2013-05-21
Updating the kernel worked for me too!!!! Ive been struggling with ubuntu on my work laptop (dell e6410 with i7 and nvidia graphics card) for almost a month and now it works beautifully! But I was unable to get the kernel to update the way open.source did, I ended up upgrading to 3.9.0 by following this link [http://www.liberiangeek.net/2013/04/ready-for-linux-kernel-3-9-install-upgrade-your-kernel-in-ubuntu-13-04/](http://www.liberiangeek.net/2013/04/ready-for-linux-kernel-3-9-install-upgrade-your-kernel-in-ubuntu-13-04/)

---

### Post by merc669 on 2013-05-21
Followed open.sources suggestions and now it all works great!! Many Thanks open.source!! I hope the others use this to correct issues....

---

### Post by lufermi on 2013-05-21
Eu também instalei o ubuntu 13.04 64 bits e estou tendo mesmo problema eu sou iniciante e estou ficando sem esperanças de conseguir resolver o problema.

---

### Post by lufermi on 2013-05-21
Não consegui encontrar na aba Atualizações esse lugar onde posso atualizar o kernel.

---

### Post by lufermi on 2013-05-22
consegui atualizar o kernel.Vou ver se melhorou não tenho experiencia tenho dificuldade para saber o que esta errado.

---

### Post by merc669 on 2013-05-22
Mine went bad this morning again with updates. But I believe it to be the Oracle 8 update (If you install) since during the update it hangs and will not complete. You need to force quit the updater and rebooting causes the issue again. I removed the Oracle 8 and now trying to check the packages and do a fsck to see if I can get the system back to working again.

Bill...

---

