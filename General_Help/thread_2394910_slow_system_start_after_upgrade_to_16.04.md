---
title: "slow system start after upgrade to 16.04"
date: 2018-06-23
forum: General Help
---

### Post by arapaho on 2018-06-23
I upgraded from 14.04 to 16.04. Now system starts much more slowly. I see some dbus errors in logs but I don't know what to do it it. I see bttv error but this seem to me less important. Maybe more advance users can help to analyse it and find the real cause of the problem.

> [COLOR=#333333][FONT=Consolas]Scanning for Btrfs filesystems[/FONT][/COLOR]
I don't have btrfs filesystem. I only had attached another disk that I made btrfs on but it is removed now. How can I disable this search?

bootlog
[https://pastebin.com/fXiYA0gK](https://pastebin.com/fXiYA0gK)
kernlog
[https://pastebin.com/LNbeuTwV](https://pastebin.com/LNbeuTwV)
syslog
[https://pastebin.com/ka0ELdui](https://pastebin.com/ka0ELdui)
xorg
[https://pastebin.com/NHymryAv](https://pastebin.com/NHymryAv)
apport
[https://pastebin.com/mZBpS8Q8](https://pastebin.com/mZBpS8Q8)


```
[FONT=monospace][COLOR=#000000]sudo systemd-analyze critical-chain[/COLOR][/FONT]
[FONT=monospace]graphical.target@1min 50.207s 
&#9492;&#9472;multi-user.target @1min 50.206s
 &#9492;&#9472;getty.target @1min 50.177s 
   &#9492;&#9472;getty@tty1.service@1min 50.176s 
     &#9492;&#9472;[COLOR=#ff5454]**rc-local.service@1min 40.110s +10.047s**[/COLOR]
       &#9492;&#9472;network-online.target@1min 40.090s 
         &#9492;&#9472;[COLOR=#ff5454]**NetworkManager-wait-online.service@1min 30.677s +9.412s**[/COLOR]
           &#9492;&#9472;[COLOR=#ff5454]**NetworkManager.service@1min 30.512s +150ms**[/COLOR]
             &#9492;&#9472;dbus.service@1min 30.454s 
               &#9492;&#9472;basic.target@1min 30.411s 
                 &#9492;&#9472;sockets.target@1min 30.411s 
                   &#9492;&#9472;dbus.socket@1min 30.411s 
                     &#9492;&#9472;sysinit.target@1min 30.398s 
                       &#9492;&#9472;[COLOR=#ff5454]**apparmor.service@1.092s +350ms**[/COLOR]
                         &#9492;&#9472;local-fs.target@1.087s                                                               
                           &#9492;&#9472;run-user-1001.mount@1min 31.704s                                                   
                             &#9492;&#9472;local-fs-pre.target@478ms                                                        
                               &#9492;&#9472;[COLOR=#ff5454]**keyboard-setup.service@221ms +197ms**[/COLOR]
                                 &#9492;&#9472;system.slice@196ms                                                           
                                   &#9492;&#9472;-.slice@177ms [/FONT]
```[FONT=monospace]                                                             
[/FONT]
```
dmesg > /tmp/boot.txt
```
[https://pastebin.com/2TCd6dUh](https://pastebin.com/2TCd6dUh)

```
[COLOR=#333333][FONT=Consolas]systemd-analyze blame[/FONT][/COLOR]
```
[https://pastebin.com/jLpts8yP](https://pastebin.com/jLpts8yP)

It is on SSD drive. 

It looks like system is looking for an encrypted disk that I labelled green. But it is not mounted and doesn't have fstab entry. How can I fix it?


```
[K[[0;31m*[0;1;31m*[0m[0;31m*   [0m] (1 of 2) A start job is running for...c50.device (1min 28s / 1min 30s)
[K[ [0;31m*[0;1;31m*[0m[0;31m*  [0m] (1 of 2) A start job is running for...c50.device (1min 29s / 1min 30s)
[K[  [0;31m*[0;1;31m*[0m[0;31m* [0m] (1 of 2) A start job is running for...c50.device (1min 29s / 1min 30s)
[K[[0;1;31m TIME [0m] Timed out waiting for device dev-di...\x2db31c\x2d86b18549cc50.device.
[[0;1;33mDEPEND[0m] Dependency failed for Cryptography Setup for green.
[[0;1;33mDEPEND[0m] Dependency failed for dev-mapper-green.device.
[[0;1;33mDEPEND[0m] Dependency failed for Encrypted Volumes.
```

What other data can I provide?

update:
I figured out what is going on.

this is very helpful command that shows errors:
```
journalctl -b -p 3
```
I use it with send to txt option because I don't know how to make Terminal  show  full lines. So it is:
```
journalctl -b -p 3 >01.txt
```

In my case the problem was that I used to have encrypted disk and system was looking for it in /etc/crypttab.
The temporary workaround is to # whatever is there. This file contain entry similar to those you can find in fstab.
Some people advice to add noauto to this disk entry but it didn't work for me. Now instaed of 
```
[FONT=monospace][COLOR=#000000]systemd-analyze[/COLOR]
Startup finished in 2.930s (kernel) + 3min 585ms (userspace) = 3min 3.515s
[/FONT]
``` 
[COLOR=#000000][FONT=monospace]I have
[/FONT][/COLOR]```
[FONT=monospace][COLOR=#000000]systemd-analyze[/COLOR]
Startup finished in 1.225s (kernel) + 20.912s (userspace) = 22.137s[/FONT]
```

What a difference!

---

### Post by TheFu on 2018-06-24
Thanks for posting the solution, but if you mark the thread SOLVED, we don't have to click and read 3 pgs to find that out.
Thread tools --> Solved
Please.

---

