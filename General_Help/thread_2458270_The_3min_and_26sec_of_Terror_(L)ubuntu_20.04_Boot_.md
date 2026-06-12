---
title: "The 3min and 26sec of Terror: (L)ubuntu 20.04 Boot Time"
date: 2021-02-20
forum: General Help
---

### Post by angelo16 on 2021-02-20
Don't you believe ?  Check this out:   [https://youtu.be/of6qpvQWGj0](https://youtu.be/of6qpvQWGj0)

Yes and yes I did.

I've read all posts about slow booting  time, but as I am not an expert in linux or even ubuntu, so I need some advice from the community.
is there anything wrong ? 

before  Lubuntu 20.04 this system booted  Win10 in approximately 2:30-2:35 min

----------------------


My system: Core 2 duo, 4 GB RAM, 140Gb HDD.

```

dell@dell-inspiron1525:~$ systemd-analyze time
Startup finished in 7.220s (kernel) + 1min 15.729s (userspace) = 1min 22.950s 
graphical.target reached after 1min 15.709s in userspace

```

and


```
dell@dell-inspiron1525:~$ systemd-analyze blame
35.220s systemd-journal-flush.service                  
29.611s snapd.service                                  
24.969s networkd-dispatcher.service                    
22.286s accounts-daemon.service                        
21.948s dev-sda1.device                                
19.371s NetworkManager-wait-online.service             
17.901s udisks2.service                                
12.847s dev-loop0.device                               
12.840s dev-loop3.device                               
12.242s dev-loop6.device                               
11.690s polkit.service                                 
11.172s NetworkManager.service                         
10.705s dev-loop5.device                               
10.643s avahi-daemon.service                           
10.612s dundee.service                                 
10.575s ModemManager.service                           
10.574s ofono.service                                  
10.550s dev-loop4.device                               
10.246s apparmor.service                               
 9.410s thermald.service                               
 9.402s wpa_supplicant.service                         
 9.398s systemd-logind.service                         
 9.372s dev-loop2.device                               
 7.811s gpu-manager.service                            
 6.007s dev-loop1.device                               
 5.827s apport.service                                 
 5.623s systemd-resolved.service                       
 5.232s grub-common.service                            
 4.904s rsyslog.service                                
 4.551s e2scrub_reap.service                           
 3.517s systemd-udevd.service                          
 2.988s systemd-rfkill.service                         
 2.792s snapd.apparmor.service                         
 2.150s lm-sensors.service                             
 2.127s grub-initrd-fallback.service                   
 2.090s setvtrgb.service                               
 1.859s systemd-modules-load.service                   
 1.523s pppd-dns.service                               
 1.324s systemd-sysusers.service                       
 1.281s alsa-restore.service                           
 1.208s snapd.seeded.service                           
 1.021s systemd-random-seed.service                    
  883ms snap-core-10823.mount                          
  815ms bluetooth.service                              
  806ms snap-gtk2\x2dcommon\x2dthemes-13.mount         
  788ms keyboard-setup.service                         
  779ms systemd-tmpfiles-setup.service                 
  771ms systemd-tmpfiles-setup-dev.service             
  763ms systemd-sysctl.service                         
  753ms snap-p7zip\x2ddesktop-220.mount                
  737ms upower.service                                 
  711ms kerneloops.service                             
  707ms systemd-journald.service                       
  673ms systemd-backlight@backlight:acpi_video0.service
  666ms sddm.service                                   
  557ms systemd-timesyncd.service                      
  550ms snap-gtk\x2dcommon\x2dthemes-1514.mount        
  524ms systemd-udev-trigger.service                   
  485ms snap-snapd-11036.mount                         
  398ms ufw.service                                    
  380ms snap-core20-904.mount                          
  375ms snap-core18-1988.mount                         
  340ms dev-hugepages.mount                            
  339ms dev-mqueue.mount                               
  337ms sys-kernel-debug.mount                         
  336ms sys-kernel-tracing.mount                       
  332ms blk-availability.service                       
  329ms kmod-static-nodes.service                      
  325ms lvm2-monitor.service                           
  292ms user@1000.service                              
  290ms systemd-update-utmp.service                    
  290ms console-setup.service                          
  243ms plymouth-quit.service                          
  187ms systemd-remount-fs.service                     
  107ms systemd-user-sessions.service                  
  102ms systemd-tmpfiles-clean.service                 
   98ms hddtemp.service                                
   66ms rtkit-daemon.service                           
   38ms user-runtime-dir@1000.service                  
   20ms plymouth-start.service                         
   13ms systemd-update-utmp-runlevel.service           
   13ms plymouth-read-write.service                    
   10ms sys-kernel-config.mount                        
    7ms sys-fs-fuse-connections.mount                  
    3ms snapd.socket
```


and

```
dell@dell-inspiron1525:~$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @1min 15.709s
&#9492;&#9472;multi-user.target @1min 15.709s
  &#9492;&#9472;snapd.seeded.service @1min 14.499s +1.208s
    &#9492;&#9472;snapd.service @44.884s +29.611s
      &#9492;&#9472;basic.target @43.285s
        &#9492;&#9472;sockets.target @43.285s
          &#9492;&#9472;snapd.socket @43.281s +3ms
            &#9492;&#9472;sysinit.target @43.171s
              &#9492;&#9472;systemd-timesyncd.service @42.614s +557ms
                &#9492;&#9472;systemd-tmpfiles-setup.service @41.575s +779ms
                  &#9492;&#9472;systemd-journal-flush.service @6.352s +35.220s
                    &#9492;&#9472;systemd-journald.service @5.626s +707ms
                      &#9492;&#9472;systemd-journald.socket @5.613s
                        &#9492;&#9472;-.mount @5.605s
                          &#9492;&#9472;system.slice @5.605s
                            &#9492;&#9472;-.slice @5.605s


```

```
dell@dell-inspiron1525:~$ uname -r
5.8.0-43-generic


```


and

```
dell@dell-inspiron1525:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3926        1344        1253         169        1328        2178
Swap:             0           0           0
dell@dell-inspiron1525:~$ 

```




Did I miss something ?

---

### Post by oldfred on 2021-02-20
I prefer standard apps, not snaps.
But it seems that Software Center uses snaps, now? I only use synaptic or command line.
Snaps are not quite as slow as before, but still become part of boot process.

See if some of these apply.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

### Post by HermanAB on 2021-02-20
Boot times are so 20th Century, if you use Suspend.

---

### Post by Dennis N on 2021-02-20
> My system: Core 2 duo, 4 GB RAM, 140Gb HDD.

Your 4200 rpm laptop HDD has a lot to do wth how fast it boots. I have a direct comparison: booting first to the OS on 7200 rpm HDD, took 1 min 9 sec from grub screen to log in screen. Booting the same OS version, but installed on an SSD in the same computer, took 16 seconds measured the same way.

If you want to improve your boot time, install an SSD in that laptop.

---

### Post by angelo16 on 2021-02-20
Yeah, I agree with all of you, but something is strange. 

How can Win10 is faster than Lubuntu ?

About snap: I read that we should not use snap and I removed some snap packages I had installed. But for my surprise, it seems that some other packages are installed by default in Lubuntu, this is because I did not install them !! So, I am afraid to remove them. Can I do it ?

---

### Post by angelo16 on 2021-02-20
Hi fred, thank you.

I will perform what you said in this post

 [https://ubuntuforums.org/showthread.php?t=2409173&p=13826670#post13826670](https://ubuntuforums.org/showthread.php?t=2409173&p=13826670#post13826670)

---

### Post by GhX6GZMB on 2021-02-20
When installing Lubuntu (20.04.1), the first thing I do is to kill snapd completely.

That said, I'm running a machine with similar specs as yours: Core Duo, 4 GB.
With my original HDD, boot time was around 1 min 35 sec. Your listing shows 1 min 23 sec, which is comparable.
Installing an SSD brought down boot time to 26 sec.

That's it.

EDIT: reviewing your video, I see a boot time of 2 min 25 sec, which is unacceptable. The black screen after the "Lubuntu walking dots" is strange, from there you'd normally go directly to login. Do a fresh install and kick snapd to hell.

---

### Post by angelo16 on 2021-02-20
> **ml9104 said:**
>  Do a fresh install and kick snapd to hell.

24h to kick snapd ass....

First, I Gonna try to remove manually, as I already installed everything I wanted to.

---

### Post by GhX6GZMB on 2021-02-20
Good lusk!
My experience after dozens of "coming to a cropper" as newbie is, that a reinstall (including programs) is faster and easier than trying a (doubtful) repair.

Let us know how you get along.

---

### Post by CelticWarrior on 2021-02-20
> **angelo16 said:**
> Yeah, I agree with all of you, but something is strange. 

How can Win10 is faster than Lubuntu ?

In almost all certainty isn't. Question: Do you have Fast Startup disabled in Windows? If not disabled you can't compare. Fast Startup is actually a form of hibernation implemented since Windows 8 with the purpose of give the impression Windows boots faster. 
Also of importance is the fact that a just installed Ubuntu will check for updates at boot time whereas a Windows that you've been using for some time (days) likely did all the updates in the background and a few optimizations.

---

### Post by DuckHook on 2021-02-20
This won't help a lot, but every little bit adds up:

In addition to all of the comments above (I especially agree with the speed of SSD vs old HDD), note that the longest startup service in your blame output is the journal. Please do: ```
sudo journalctl --disk-usage
```

If the result is massive (> 1 GB) then you may be able to cut down boot times by trimming journal size down to something more reasonable—say, 100 MB. [Instructions ¼ way down the page here]("https://www.certdepot.net/rhel7-get-started-systemd/"). However, don't expect miracles. Your main problem is a slow HDD, which all the tweaking in the world will not solve.

FWIW, my own opinion is that it's not advisable to nuke snap. I do understand the temptation and, if one is a power&#8209;user and knows exactly what trouble one is buying, then anything goes, but for general users who really don't understand what they are getting themselves into (**not** assuming anything about you here), nuking an element as central to Ubuntu as the devs have made snaps is not advisable.

The problem is that more and more functionality is being hived off into snaps. There's no point in griping about this because that's just what the devs have decided and we, as end users, have to figure out how to work with it rather than against it. For example, Chromium is now only available as a snap. Nix snap; bye-bye Chromium. I don't agree with this decision, but my disagreement is immaterial. That's just how things are.

If you are the sort who has no problem compiling Chromium from source, then snaps are superfluous. But if you are a general user, getting rid of snaps will be very self&#8209;limiting (and even more so as time goes on).

---

### Post by HermanAB on 2021-02-21
"How can Win10 is faster than Lubuntu?" - Windows10 uses Suspend.  So you are comparing apples with giant pumpkins.

---

### Post by angelo16 on 2021-02-21
> **HermanAB said:**
> "How can Win10 is faster than Lubuntu?" - Windows10 uses Suspend.  So you are comparing apples with giant pumpkins.

Hi HermanAB, thank you for support.

I will look for what Suspend is or does. 

Now, I do understand why someone on previous post has cited it.:):lolflag:

---

### Post by mikewhatever on 2021-02-21
I agree with the others, snaps are a small problem here, the big problem is slow and old hardware.

Also, I don't see the point of hating snaps, as you don't have to use them, but alas, linux users will always find something to hate.

---

### Post by GhX6GZMB on 2021-02-21
> **mikewhatever said:**
> I agree with the others, snaps are a small problem here, the big problem is slow and old hardware.

Also, I don't see the point of hating snaps, as you don't have to use them, but alas, linux users will always find something to hate.

Yes. Like hating "old and slow hardware". Not everyone is a millionaire.

As I wrote earlier, my machine, which is comparable to the OP's, boots in 26 seconds. I find that acceptable.

---

### Post by mikewhatever on 2021-02-21
> **ml9104 said:**
> 

[QUOTE=mikewhatever;14022191]
I agree with the others, snaps are a small problem here, the big problem is slow and old hardware.

Also, I don't see the point of hating snaps, as you don't have to use them, but alas, linux users will always find something to hate. 


Yes. Like hating "old and slow hardware". Not everyone is a millionaire.

As I wrote earlier, my machine, which is comparable to the OP's, boots in 26 seconds. I find that acceptable.[/QUOTE]

I really hope, for your sake, there aren't too many more things you hate. It is not fun. At least, keep the rest secret, because haters are depressing. As for myself, I had better enjoy snaps and old hardware, before they are kicked and banished to hell. Thanks.

---

### Post by angelo16 on 2021-02-21
> **DuckHook said:**
> This won't help a lot, but every little bit adds up:

In addition to all of the comments above (I especially agree with the speed of SSD vs old HDD), note that the longest startup service in your blame output is the journal. Please do: ```
sudo journalctl --disk-usage
```

If the result is massive (> 1 GB) then you may be able to cut down boot times by trimming journal size down to something more reasonable&#8212;say, 100 MB. [Instructions ¼ way down the page here]("https://www.certdepot.net/rhel7-get-started-systemd/"). However, don't expect miracles. Your main problem is a slow HDD, which all the tweaking in the world will not solve.




```
dell@dell-inspiron1525:~$ sudo journalctl --disk-usage
[sudo] password for dell: 
Archived and active journals take up 408.0M in the file system.
```


This is what I was afraid. Not higher than 1Gb, but higher (4x) than DuckHook said.

I was checking the boot messages. There is something related to anydesk at the final part of the boot, just before the login screen. This should be related to the wifi issue I am facing  with rtl8188fu. Gonna have to fix this before anything else;

---

### Post by DuckHook on 2021-02-21
Actually, 400 MB is not really "excessive". Mine was 1.7 GB before I took a weed&#8209;whacker to it and, even bloated, it did not appreciably impact my boot times because I use a SSD. Please note that my laptop has very similar HW specs to those you quote, with the single exception that I use a new SSD whereas you use an old HDD. My boot times are less than 30 seconds.

---

### Post by DuckHook on 2021-02-21
> **DuckHook said:**
> &#8230;Please note that my laptop has very similar HW specs to those you quote, with the single exception that I use a new SSD whereas you use an old HDD. My boot times are less than 30 seconds.
On second thought, the above is not really fair. I don't install OSes the same way most people do. I use a CLI image and add only what I need. This gives me a very lean system without the cruft that most people get from a typical install.

Note, however, that snapcraft is NOT one of the services that I forego. In my experience, its presence is not really that burdensome whereas its absence would be quite limiting.

---

