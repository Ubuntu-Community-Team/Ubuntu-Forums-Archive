---
title: "My results after doing systemd-analyze tests."
date: 2022-06-08
forum: General Help
---

### Post by dgkking on 2022-06-08
Hi All
If possible can someone check these results for me. I am not sure if they are good or bad for what I am running or if there are any problem to be found within the results. I am stil a bit of a novice with Linux and it has been a quite large learning process to dual boot these Systems and set them up. However I have enjoy the process and learnt a lot while doing so. Linux is now my operating system of choice. There is a long way to go yet as I try to master Linux and my age  of 70 years doesn't help:( but I will get there. I hope I have included enough information. 

My system
```
ASUS PRIME B460M-K
Memory      16.0 GiB
Processor Intel core i5-10600KF CPU @ 4.10 GHz x12
Graphics NVIDIA Corporation GK208B [GeForce GT710]
Disk Capacity  2.5 TB
OS Name  Ubuntu 22.04 LTS, Linux Mint 20.03, Windows 11 pro (reluctantly but needed for family use)
OS Type 64-bit
Gnome Version 42.1
Windowing System  X11
```


```
systemd-analyze blame
427ms dev-sda3.device
420ms fwupd.service
196ms udisks2.service
172ms NetworkManager.service
165ms systemd-resolved.service
134ms systemd-logind.service
133ms e2scrub_reap.service
128ms accounts-daemon.service
124ms zram-config.service
122ms systemd-udev-trigger.service
112ms systemd-journald.service
104ms switcheroo-control.service
103ms apparmor.service
 89ms systemd-oomd.service
 88ms [email]user@1000.service[/email]
 
 systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @5.304s
&#9492;&#9472;gdm.service @5.246s +57ms
  &#9492;&#9472;systemd-user-sessions.service @5.235s +7ms
    &#9492;&#9472;network.target @5.223s
      &#9492;&#9472;NetworkManager.service @5.049s +172ms
        &#9492;&#9472;dbus.service @5.046s
          &#9492;&#9472;basic.target @5.033s
            &#9492;&#9472;sockets.target @5.032s
              &#9492;&#9472;uuidd.socket @5.031s
                &#9492;&#9472;sysinit.target @4.998s
                  &#9492;&#9472;systemd-timesyncd.service @4.910s +86ms
                    &#9492;&#9472;systemd-tmpfiles-setup.service @4.875s +24ms
                      &#9492;&#9472;local-fs.target @4.861s
                        &#9492;&#9472;boot-efi.mount @4.803s +57ms
                          &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-7EB1\x2d2BA2.servi>
                            &#9492;&#9472;dev-disk-by\x2duuid-7EB1\x2d2BA2.device @4.749s
lines 1-19/19 (END)
```

 systemd-analyze 
Startup finished in 15.128s (firmware) + 3.387s (loader) + 3.305s (kernel) + 5.761s (userspace) = 27.583s 
graphical.target reached after 5.304s in userspace

Many thanks
Dave

---

### Post by oldfred on 2022-06-08
I have older Intel chip and GT620 and found the Intel chip was faster? Unless nVidia providing something you need, try the Intel internal video.
[https://www.videocardbenchmark.net/compare/Intel-UHD-630-vs-GeForce-GT-710/3826vs2910](https://www.videocardbenchmark.net/compare/Intel-UHD-630-vs-GeForce-GT-710/3826vs2910)

I added my first SSD almost 10 years ago. It was only 60GB and just a boot drive. 
If you really want faster boot times a SSD or NVMe drive will speed boot & load of larger programs a lot. With the RAM you have programs will run just the same as in RAM. And recent programs are cached in RAM, so reloading also fast.  Only read & write to drive will be faster. 

I changed to Kubuntu which is more midle weight compared to Ubuntu and removed some apps that do not apply when booting on my older system. I also changed a few settings. And recently upgraded to a NVMe drive.

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.426s (kernel) + 5.611s (userspace) = 10.038s  
graphical.target reached after 5.590s in userspace
[/FONT]
```

Most motherboards do not yet support UEFI update with fwupd. Mine does not, so I remove it.
Devices using LVFS for firmware updates, you can see if yours is on list
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Some settings you can change:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) 

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by TheFu on 2022-06-08
I must have missed the question.  Is there some goal?

Systemd-analyze is helpful, but often lies.  Be certain to read the manpage for how it lies and the caveats.

Also, you didn't say what the purpose of this system is.  Is it a server or a desktop? Does it run 24/7 or just a few hours a day?

In my world, here's a few physical systems:
```
$ systemd-analyze 
Startup finished in 10.131s (kernel) + 43.575s (userspace) = 53.707s
graphical.target reached after 14.637s in userspace

$ uptime 
 11:38:29 up 11 days,  1:49,  5 users, 
```
That is a system with 1TB of storage as a 500G SSD and a 500G HDD. It doesn't really matter to me how quickly it boots, since it is left on almost always.

```

$ systemd-analyze
Startup finished in 7.795s (kernel) + 39.668s (userspace) = 47.463s
graphical.target reached after 39.665s in userspace

$ uptime 
 11:39:09 up 11 days,  2:12,  2 users,  

```
That is a system with nearly 40TB of storage, some internal, some external arrays, and an NVMe SSD. Also, running nearly all the time.

If we move into systems where boot speed might matter, just slightly more, then my main desktop, running inside a virtual machine is below.  This browser, thunderbird, and a few other desktop programs are run on this system all-the-time. It boots fast.
```
$ systemd-analyze
Startup finished in 2.308s (kernel) + 6.080s (userspace) = 8.389s 
graphical.target reached after 6.055s in userspace

$ uptime
 11:40:25 up 11 days,  1:50,  1 user,
```
Virtual machines always seem to be faster here.  I stopped dual booting about 15 yrs ago and started using virtualization.  I run Windows inside a VM. It isn't booted now, but I need it about once a week for finance data entry and stock management.

So, if a system takes 10 seconds or 2 minutes to boot, really doesn't matter all that much considering they are routinely booted at least 2 weeks between kernel patching that requires a reboot.  Everyone has different needs.

---

### Post by grahammechanical on 2022-06-08
I suggest that we keep in mind that in order to give the impression of Ubuntu not being slow to boot many services are loaded after the login screen is reached and also while the desktop is being drawn. Systemd-analyze is useful to developers who are working to improve Ubuntu boot times or identify services that need to have their efficiency improved.

I imagine that the only thing that a user can do improve these logged times is to put in a faster CPU and faster system memory (RAM).

Regards

---

### Post by TheFu on 2022-06-08
Or remove services that aren't needed.  

Each of us and our systems are unique, so having different daemons started is expected.  But we can also choose which we specifically don't want as well.

---

