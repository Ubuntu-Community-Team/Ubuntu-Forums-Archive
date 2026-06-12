---
title: "Booting Is Faster Via Recovery Mode"
date: 2017-04-07
forum: General Help
---

### Post by spode2 on 2017-04-07
I have an Inspiron 1525 laptop which has become slow, and sometimes fails, to boot since I updated to Lubuntu 16.10. I am now using 17.04, but the problem is still there. It is very quick to boot up and shut down if I select recovery mode/continue with normal boot from the grub menu, and everything seems to operate as usual if I do this.

The obvious difference between the default and recovery mode is the graphics renderer used. With a normal boot, this is Mesa DRI Intel(R) 965GM x86/MMX/SSE2 and in recovery mode it is Gallium 0.4 on llvmpipe(LLVM 4.0, 128 bits).

My question is, how can I select the renderer used as default in order to check that this is the problem and, if it is, how can I make the change permanent?

---

### Post by kc1di on 2017-04-08
Hello spode2, 
many things can cause slow boot process.  on way to find out what's hogging boot time is to issue this command in a terminal. 
after booting up with normal boot not recovery mode.
```
systemd-analyze blame
```

Post the out put here and we will try to help.

---

### Post by lammert-nijhof on 2017-04-08
You can select the video driver to use in the "additional drivers" tab in "software and updates". Maybe the names are slightly different in Lubuntu. Your choice has consequences, you might be selecting the secure less performant open source driver over the driver provided by Intel. That Intel driver might be more complex and better for normal use and games, but requires more time to initialize during boot-up.

---

### Post by spode2 on 2017-04-08
Thanks for the replies. I think updates might have cured this at last. Boot time today is just over a minute, which is acceptable, and I have rebooted several times without a failure.

Just for the record:

systemd-analyze blame
         12.074s networking.service
         10.980s systemd-resolved.service
         10.345s irqbalance.service
         10.318s grub-common.service
          8.661s colord.service
          6.029s NetworkManager-wait-online.service
          2.597s dev-sda1.device
           705ms upower.service
           554ms systemd-rfkill.service
           522ms ntp.service
           507ms accounts-daemon.service
           501ms keyboard-setup.service
           471ms systemd-udev-trigger.service
           434ms ModemManager.service
           389ms systemd-journald.service
           346ms console-kit-log-system-start.service
           316ms gpu-manager.service
           307ms systemd-logind.service
           304ms nullmailer.service
           297ms smbd.service
           282ms lm-sensors.service
           280ms avahi-daemon.service
           266ms rsyslog.service

No alternative graphics drivers are shown in additional drivers.

---

### Post by kc1di on 2017-04-08
I don't see anything that you can improve in your readout. 
Though it's about 35 seconds slower than my own.  But that could just be differences in machines. 
Glad the update seems to have helped.

---

