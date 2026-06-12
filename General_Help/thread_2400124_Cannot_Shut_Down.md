---
title: "Cannot Shut Down"
date: 2018-09-02
forum: General Help
---

### Post by emilward on 2018-09-02
Let me just preface this first by saying that I am aware that many people have posted this issue in this forum already however I have tried all their solutions over the last few days already, but none work. Basically, Linux freezes when trying to shut down. I say "linux" because it doesn't seem to matter what distro I use. I prefer Ubuntu which is why I'm posting here. The only way I can get the computer to shut down is to hold the power button after it freezes at the splash screen. I changed grub so I could see the terminal output and I saw that it was getting stuck at "reached target shutdown". Everywhere I read, users said I needed to add "acpi=force" and "apm=power_off" and the success of that is hit or miss. Sometimes it shuts down and sometimes it doesn't. But it mostly doesn't. So I removed the splash screen during boot up to see if there were any errors and I saw a failure at "Failed to start Load Kernel Modules" and under it said to "See 'systemctl status systemd-modules-load.service'" for more information. So after booting in I ran it in terminal and it returned 

```

eric@eric-Satellite-A215:~$ systemctl status systemd-modules-load.service
&#9679; systemd-modules-load.service - Load Kernel Modules
   Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-09-02 18:23:13 PDT; 28min ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 648 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=1/FAILURE)
 Main PID: 648 (code=exited, status=1/FAILURE)

Sep 02 18:23:13 eric-Satellite-A215 systemd[1]: Starting Load Kernel Modules...
Sep 02 18:23:13 eric-Satellite-A215 systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAI
Sep 02 18:23:13 eric-Satellite-A215 systemd[1]: Failed to start Load Kernel Modules.
Sep 02 18:23:13 eric-Satellite-A215 systemd[1]: systemd-modules-load.service: Unit entered failed state.
Sep 02 18:23:13 eric-Satellite-A215 systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
```

So now I don't know where to go from here. I am currently using Xubuntu 16.04 32-bit but I have tried 64-bit as well as 18.04 32 and 64 bit. My system is a Toshiba Satellite A215-S7437 with an AMD Turion 64 X2 TL-58 CPU, integrated ATI RS690 GPU, 4GB of RAM, 120GB SSD, and an Intel Centrino Wireless-N 2230 wireless NIC. 

I have tried booting into Xubuntu using the other provided kernels and I still have the same problem.

---

### Post by sgian on 2018-09-03
[https://superuser.com/questions/997938/how-do-i-figure-out-why-systemctl-service-systemd-modules-load-fails](https://superuser.com/questions/997938/how-do-i-figure-out-why-systemctl-service-systemd-modules-load-fails)  Does this help?  It looks like it might be a firmware issue, and that laptop is getting old.

---

