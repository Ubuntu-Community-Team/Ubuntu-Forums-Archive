---
title: "Slow, slow. Much too slow."
date: 2019-02-09
forum: General Help
---

### Post by christon74 on 2019-02-09
Good evening fellow Ubunters_ I have already changed desktop (from Gnome to Lubuntu). In a previous post (display latency) I have already told what happens when I open Firefox and click on a new tab, or on any tab in a previously saved session.  Vertical or horizontal lines breaking the pages and scrolling down takes forever. I am really raking my brains to sort this out. In this message I will just give the output of "grep "error"  /var/log/syslog" and 
                          "vmstat 10 4" _ I am sparing you  the "dmesg" and the "systemd-analyze blame"             

which both are much too long to display here and I guess expert Ubuntu users (and I'm not really one) already know that .



  
                           ```
christophe@christophe-ESPRIMO-E5731:~$ vmstat 10 4
 procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
  r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
  3  0      0 2145684 280384 2008336    0    0   160    96  895 2180 25  4 68  3  0
  1  0      0 2141588 280424 2008392    0    0     0   148 1531 3187 20  3 77  0  0
  0  0      0 2139076 280432 2008392    0    0     0    14  612 1128  7  1 92  0  0
  2  0      0 2129140 280448 2008392    0    0     0    42 2042 4474 19  5 76  0  0

                        
christophe@christophe-ESPRIMO-E5731:~$ grep "error"  /var/log/syslog
 Feb  9 06:55:12 christophe-ESPRIMO-E5731 firefox[3182]: Theme parsing error: <data>:1:34: Expected ')' in color definition
 Feb  9 06:55:12 christophe-ESPRIMO-E5731 firefox[3182]: Theme parsing error: <data>:1:77: Expected ')' in color definition
 Feb  9 06:55:31 christophe-ESPRIMO-E5731 kernel: [  414.688029] EXT4-fs (sdb6): error count since last fsck: 1
 Feb  9 06:55:31 christophe-ESPRIMO-E5731 kernel: [  414.688032] EXT4-fs (sdb6): initial error at time 1543727465: __ext4_get_inode_loc:4618: inode 18612225: block 74448928
 Feb  9 06:55:31 christophe-ESPRIMO-E5731 kernel: [  414.688035] EXT4-fs (sdb6): last error at time 1543727465: __ext4_get_inode_loc:4618: inode 18612225: block 74448928
 Feb  9 06:56:31 christophe-ESPRIMO-E5731 thunderbird.desktop[2635]: [Parent 3182, Gecko_IOThread] WARNING: pipe error (238): Connection reset by peer: file /build/firefox-HN7tk_/firefox-65.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 349
 Feb  9 06:57:09 christophe-ESPRIMO-E5731 thunderbird.desktop[2635]: [Parent 3182, Gecko_IOThread] WARNING: pipe error: Broken pipe: file /build/firefox-HN7tk_/firefox-65.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 718
 Feb  9 08:19:07 christophe-ESPRIMO-E5731 thunderbird.desktop[2635]: [Child 7956, Chrome_ChildThread] WARNING: pipe error: Broken pipe: file /build/firefox-HN7tk_/firefox-65.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 718
 Feb  9 08:19:07 christophe-ESPRIMO-E5731 thunderbird.desktop[2635]: message repeated 7 times: [ [Child 7956, Chrome_ChildThread] WARNING: pipe error: Broken pipe: file /build/firefox-HN7tk_/firefox-65.0+build2/ipc/chromium/src/chrome/common/ipc_channel_posix.cc, line 718]
 christophe@christophe-ESPRIMO-E5731:~$ 

Question: Is there something amiss there and can I fix it without too much of a headache. Thanks in advance for all help and trouble.
Ubuntu flavour: 18.04_ up to date. 
Hardware: Fujistu-Siemens Esprimo 5731 E Stars. 
The display is an old Orion TV set connected with a VGA cable.
Graphics drivers: i-965-va-drivers
llvmpipe (LLVM 7.0, 128 bits)
```

---

### Post by oldos2er on 2019-02-09
> I am sparing you  the "dmesg" and the "systemd-analyze blame" You can post them on [https://paste.ubuntu.com/](https://paste.ubuntu.com/) and include the link here.

---

### Post by HermanAB on 2019-02-09
Run top or htop and see what is going on.

---

### Post by christon74 on 2019-02-10
Hello again Herman and Oldos _ I think I have found a way to end all this lagging and this is why I am marking this thread as solved. I have reconfigured gdm. Well, I have switched from gdm to lightdm. And I have noted that everything is now much faster. Thanks anyway. ;)

---

