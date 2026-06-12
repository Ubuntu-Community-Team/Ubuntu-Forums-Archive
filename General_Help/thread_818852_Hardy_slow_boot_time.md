---
title: "Hardy slow boot time"
date: 2008-06-04
forum: General Help
---

### Post by steveneddy on 2008-06-04
I have a fully updated Hardy and since the -.17 kernel I am getting slow boot times. Slow like 3-4 minutes.

It hangs on "Loading Hardware Drivers" .

I have searched the UF and Google and have tried every fix out there.

So far nothing has worked.

System 76 Serval Performance Type 1 (kinda like an Asus or Acer)

Core 2 Duo @ 2 Ghz

2 Gig RAM

Firewire, USB, Bluetooth, DVD, nVidia, SD Card Reader

Any and all help appreciated.

Maybe someone could tell by a log file of some kind?

Would posting the output of

```
dmesg
```

help anyone?

Thanks in advance.

---

### Post by steveneddy on 2008-06-05
It seems as if the boot time is getting longer and longer each time I try and boot the laptop.

I'm up to almost five minutes. I used to have a 30-45 second boot time.

I really can't figure this out.

Any help appreciated.

Thanks in advance.

---

### Post by steveneddy on 2008-06-05
I have added this to Launchpad bug report.

---

### Post by steveneddy on 2008-06-06
I'm starting to wonder if I'm the only one with this issue.

---

### Post by zaatary on 2008-06-08
me too i'm facing the same problem , very slow boot up , even sometimes it freez and forced to reboot.. any help plz .. thx

---

### Post by relemons on 2008-06-09
I've been having this problem too, though it's unpredictable. Sometimes it's fine, sometimes it takes five minutes.

It hangs at the "scanning" orange bar.

I read about this program called bootchart, it charts your boots, anyway, heres an example of an extraordinarily long one...

[http://img162.imageshack.us/img162/7389/hardy200806092pk1.png]("http://img162.imageshack.us/img162/7389/hardy200806092pk1.png")

---

### Post by steveneddy on 2008-06-18
Just trying to see if there is an answer.

Anyone have a clue about this?

---

### Post by VMC on 2008-06-18
do this
```
  vi /var/log/messages
```

Then look for something like start or restart and count from there. You should get the time of your boot process. If it takes 5 minutes thee may be a lot of messages. But at least you can track down the culprit.

---

### Post by steveneddy on 2008-06-18
Here's a portion of the log from tonight.

Anyone have problems with npviewer?

```

**Jun 18 19:05:35 jupiter syslogd 1.5.0#1ubuntu1: restart.**
Jun 18 19:16:36 jupiter kernel: [ 1321.622482][COLOR="Blue"] npviewer.bin[/COLOR][20281]: segfault at f5b24030 rip f7918540 rsp ffb16d8c error 4
Jun 18 19:16:53 jupiter kernel: [ 1333.566124] [COLOR="Blue"]npviewer.bin[/COLOR][20311]: segfault at f5b82030 rip f7976540 rsp fffc6a3c error 4
Jun 18 19:17:15 jupiter kernel: [ 1348.086226] [COLOR="Blue"]npviewer.bin[/COLOR][20349]: segfault at f5b70030 rip f7964540 rsp ff8692dc error 4
Jun 18 19:17:20 jupiter kernel: [ 1352.633282] [COLOR="Blue"]npviewer.bin[/COLOR][20395]: segfault at f5b27030 rip f791b540 rsp ffe800fc error 4
Jun 18 19:27:43 jupiter -- MARK --
Jun 18 19:36:30 jupiter kernel: [ 2355.624102][COLOR="Blue"] npviewer.bin[/COLOR][22359]: segfault at f5b21030 rip f7915540 rsp ffa4dc2c error 4
[COLOR="Red"]Jun 18 19:47:43 jupiter -- MARK --
Jun 18 20:07:43 jupiter -- MARK --
Jun 18 20:27:43 jupiter -- MARK --
Jun 18 20:47:43 jupiter -- MARK --[/COLOR]
Jun 18 20:51:39 jupiter kernel: [ 4922.138382] iwl3945: Radio Frequency Kill Switch is On:


```

This is a two to three minute boot time where i was getting around 30 second boot times before Hardy and shortly after the upgrade, but something happened to totally kill my boot times and it's frustrating.

---

### Post by steveneddy on 2008-06-26
A backup of data and a full reinstall solved all of my issues.

I've got to remember that upgrading is bad.

I always have to eventually reinstall, no matter what.

You'd think that after 6 versions of Ubuntu that I would have learned my lesson by now.

At least I'm good at it now and I know what to copy from my /home directory to make the new install good as new, or like the old. 

Now to get wireless and Bluetooth working and I'll be set.

---

### Post by cariboo on 2008-06-26
That error you're getting is to do with Adobe Flash. It looks like its trying to load the flash player on boot up. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856)

There might be something on that page to help.

Jim

---

### Post by steveneddy on 2008-06-28
> **cariboo907 said:**
> That error you're getting is to do with Adobe Flash. It looks like its trying to load the flash player on boot up. There is a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856)

There might be something on that page to help.

Jim

Well, that may have been true, but after I reinstalled, all of the issues I had before, and the slow boot issue in particular, all went away.

I just seem to remember that after each new version, there should be an upgrade via total reinstall instead of an upgrade via updating through Synaptic.

I looked through my notes and noticed that I had issues every time I tried to update the OS and not reinstall at a new version.

I will keep my eye on this issue though, as I did install **nspluginwrapper** along with flash again, but all seems to be working fine.

Thank you for your kind post on this matter.

---

