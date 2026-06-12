---
title: "problems loading/saving with new libreoffice"
date: 2018-02-21
forum: General Help
---

### Post by bjlockie on 2018-02-21
I just updated to a new libreoffice and I can't open 

$ libreoffice HT.ods
I got this output in the terminal and thought that was the problem.
** (soffice:2474): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files

I googled the solution:
$ sudo apt-get install at-spi2-core

$ libreoffice HT.ods
No output to the terminal but I still get an access denied dialog.
I get this in the log but it might have been there before.

```
$ dmesg
[ 1364.487081] kauditd_printk_skb: 2 callbacks suppressed
[ 1364.487083] audit: type=1400 audit(1519248122.627:95): apparmor="DENIED" operation="open" profile="libreoffice-oopslash" name="/sys/devices/pci0000:00/0000:00:11.0/ata4/host3/target3:0:0/3:0:0:0/block/sda/queue/rotational" pid=2693 comm="oosplash" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.540465] audit: type=1400 audit(1519248122.681:96): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/uevent" pid=2711 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.540518] audit: type=1400 audit(1519248122.681:97): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/uevent" pid=2711 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.574374] audit: type=1400 audit(1519248122.715:98): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/uevent" pid=2711 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.574382] audit: type=1400 audit(1519248122.715:99): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/uevent" pid=2711 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.574419] audit: type=1400 audit(1519248122.715:100): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/uevent" pid=2711 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.574439] audit: type=1400 audit(1519248122.715:101): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0/uevent" pid=2711 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1364.604209] audit: type=1400 audit(1519248122.744:102): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/home/rjl/.cache/mesa/index" pid=2711 comm="soffice.bin" requested_mask="wrc" denied_mask="wrc" fsuid=1000 ouid=1000
[ 1364.725910] audit: type=1400 audit(1519248122.866:103): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/home/rjl/.icons/default/index.theme" pid=2710 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 1364.733631] audit: type=1400 audit(1519248122.874:104): apparmor="DENIED" operation="open" profile="libreoffice-soffice" name="/home/rjl/.icons/default/index.theme" pid=2710 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
```
I can save and load a new calc file to my root disk but not to other disks.
"saving the document Untitled 1:
/other/Untitled 1.ods does not exist.".

/other is a mounted ext4fs hard drive.

It works if I copy the file to my root drive.

---

### Post by vasa1 on 2018-02-22
Someone else has reported something similar: [https://askubuntu.com/questions/1008664/app-armor-blocks-openoffice-kubuntu-17-10-after-update-to-libreoffice-5-4-5-0ubu](https://askubuntu.com/questions/1008664/app-armor-blocks-openoffice-kubuntu-17-10-after-update-to-libreoffice-5-4-5-0ubu)

---

### Post by bjlockie on 2018-02-22
Except mine works on some disks.

---

### Post by bjlockie on 2018-02-22
sudo apt-get remove apparmor
worked for me.
I don't know if apparmor is needed for anything else.

---

### Post by #&amp;thj^% on 2018-02-22
> **bjlockie said:**
> sudo apt-get remove apparmor
worked for me.
I don't know if apparmor is needed for anything else.

Glad that worked for you but this is some information regarding:
AppArmor is an important security feature that&#8217;s been included by default with Ubuntu since Ubuntu 7.10. However, it runs silently in the background, so you may not be aware of what it is and what it&#8217;s doing.

AppArmor locks down vulnerable processes, restricting the damage security vulnerabilities in these processes can cause. AppArmor can also be used to lock down Mozilla Firefox for increased security, but it doesn&#8217;t do this by default.
What is AppArmor?

AppArmor is similar to SELinux, used by default in Fedora and Red Hat. While they work differently, both AppArmor and SELinux provide &#8220;mandatory access control&#8221; (MAC) security. In effect, AppArmor allows Ubuntu&#8217;s developers to restrict the actions processes can take.

For example, one application that&#8217;s restricted in Ubuntu&#8217;s default configuration is the Evince PDF viewer. While Evince may run as your user account, it can only take specific actions. Evince only has the bare minimum of permissions needed to run and work with PDF documents. If a vulnerability were discovered in Evince&#8217;s PDF renderer and you opened a malicious PDF document that took over Evince, AppArmor would restrict the damage Evince could do. In the traditional Linux security model, Evince would have access to everything you have access to. With AppArmor, it only has access to things that a PDF viewer needs access to.

AppArmor is particularly useful for restricting software that may be exploited, such as a web browser or server software.
I would file a bug against libreoffice.
There now you have some food for thought.

EDIT: You can check things in AppArmor via:
```
sudo apparmor_status
```

You&#8217;ll see whether AppArmor is running on your system (it&#8217;s running by default), the AppArmor profiles that are installed, **_and the confined processes that are running._**

---

### Post by vasa1 on 2018-02-22
And here's the bug: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005)

Apparently, Apparmor won't allow LibreOffice to access files that are not in /home, /mnt or /media. So those with their *.od* files elsewhere may need to do some profile editing.> What you're seeing is apparmor confinement finally working as intended. The package had been shipping apparmor profiles for some time, but they were not functional, and they have been fixed.
Those profiles allow reading/writing office documents in $HOME, /mnt and /media (that excludes /home2/).from comment #3 in the bug.

---

### Post by #&amp;thj^% on 2018-02-22
> **vasa1 said:**
> And here's the bug: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1751005)

Apparently, Apparmor won't allow LibreOffice to access files that are not in /home, /mnt or /media. So those with their *.od* files elsewhere may need to do some profile editing.from comment #3 in the bug.

Interesting! Thanks for update vasa1 :)

---

### Post by vasa1 on 2018-02-22
> **1fallen said:**
> Interesting! Thanks for update vasa1 :)You're welcome!

---

### Post by vasa1 on 2018-02-22
There's mention of```
sudo apt-get install apparmor-easyprof-ubuntu
``` in [https://askubuntu.com/questions/1008880/libreoffice-5-4-5-1-gets-access-denied-on-nfs-mounted-filesystem](https://askubuntu.com/questions/1008880/libreoffice-5-4-5-1-gets-access-denied-on-nfs-mounted-filesystem)

I haven't meddled with Apparmor for some years now and don't remember having to install "apparmor-easyprof-ubuntu".

---

### Post by bilkay on 2018-04-22
What I seem to be missing here is whether the problem is coming from the server or the client, so it's not clear where any fixes need to be applied.

In my case, the problem arose (evident on my laptop) when I upgraded my server from 14.04 to 16.04 with my laptop client still running 14.04 using autofs to mount files from the server via nfs. Now that I've "upgraded" my laptop to 16.04, the problem persists.

One thing I noticed in the suggested "fixes" is that
```
 $ sudo ln -s /etc/apparmor.d/usr.lib.libreoffice.program.* /etc/apparmor.d/disable/
```
creates a link to a non-existent target on both my server and my laptop. Can't see how that can do anything - and it doesn't.

---

