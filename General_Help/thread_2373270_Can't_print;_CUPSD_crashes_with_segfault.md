---
title: "Can't print; CUPSD crashes with segfault"
date: 2017-10-04
forum: General Help
---

### Post by HuaiDan on 2017-10-04
Hello;

Long time no see. Things have been going well for quite some time. Then I upgraded to 17.04.

Particulars: Ubuntu vanilla 17.04 AMD64, 4.10.0-35-generic, ASUS i7 laptop, cups version 2.2.2

Since upgrading from Xenial, I have been unable to print, and I am unable to add an HP printer. Cups crashes whether or not I have HPLIP installed.

dmesg:
```
[   37.184765] cupsd[946]: segfault at 0 ip 00007f07a8a8e715 sp 00007ffc05dccde8 error 4 in libc-2.24.so[7f07a8941000+1be000]
[   37.184775] audit: type=1400 audit(1507042144.954:37): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/proc/946/cmdline" pid=946 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```

 There's a bug report on this, unfortunately it's not a very active one,as it only affects one other user:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1706052](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1706052)

I was hoping someone in the community might have some useful feedback on this, as I do need to print.


17.04 has been extremely buggy for me. I had to set apparmor's handling of network manager to complain just so I could connect to the network. 

```
 1905  sudo aa-complain /sbin/dhclient
 1908  sudo aa-complain /usr/lib/NetworkManager/nm-dhcp-client.action
 1909  sudo aa-complain /usr/lib/NetworkManager/nm-dhcp-helper

```

Would a similar tact work for cups? I'm also getting numerous crash reports for Telepathy, which I think are just an annoyance as I don't use any messenger apps.

```
[   60.807534] telepathy-haze[3327]: segfault at 0 ip 00007f7d128a2715 sp 00007ffe8842c888 error 4 in libc-2.24.so[7f7d12755000+1be000]
[   60.807556] audit: type=1400 audit(1507042306.826:51): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/telepathy-*" name="/proc/3327/cmdline" pid=3327 comm="telepathy-haze" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[   61.462370] telepathy-haze[3433]: segfault at 0 ip 00007f69a8728715 sp 00007ffdcdc0a058 error 4 in libc-2.24.so[7f69a85db000+1be000]
[   61.462379] audit: type=1400 audit(1507042307.478:52): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/telepathy-*" name="/proc/3433/cmdline" pid=3433 comm="telepathy-haze" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[   62.242121] audit: type=1400 audit(1507042308.258:53): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/proc/3441/cmdline" pid=3441 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

```

I'm not aware of any easy alternatives for cups. Any ideas on how I can get print services working again, short of reinstalling/downgrading?
Thank you!

Crash report:
[https://paste.ubuntu.com/25674653/](https://paste.ubuntu.com/25674653/)

Sorry to post like this, but flash crashes when I try to attach file here.

---

### Post by HuaiDan on 2017-10-04
So I went ahead with setting apparmor's handling of cups:

```
sudo aa-complain /usr/sbin/cupsd
```

This got me printing again.

Before I mark this solved, is there any reason *not* to do this? Can anyone shed any light on why this was an issue to begin with?

---

### Post by HuaiDan on 2017-10-06
This fixed the problem:

> @{PROC}/*/cmdline r,

after the line

@{PROC}/*/auxv r,

in your /etc/apparmor.d/usr.sbin.cupsd file, then run

sudo aa-enforce /usr/sbin/cupsd

and reboot.

---

