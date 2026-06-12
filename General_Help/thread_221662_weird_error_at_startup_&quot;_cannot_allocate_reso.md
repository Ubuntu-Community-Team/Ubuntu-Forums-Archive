---
title: "weird error at startup: &quot; cannot allocate resource region...&quot;"
date: 2006-07-23
forum: General Help
---

### Post by MrMojoRising on 2006-07-23
Since using the LTS version of Dapper I keep getting the same (error) messages during boot up.

```
Jul 23 14:32:50 Enoch kernel: [17179573.568000] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
Jul 23 14:32:50 Enoch kernel: [17179573.568000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
Jul 23 14:32:50 Enoch kernel: [17179573.980000] Cannot allocate resource for EISA slot 1
Jul 23 14:32:50 Enoch kernel: [17179573.980000] Cannot allocate resource for EISA slot 8

```

I pulled that out of the kern.log from /var/log/

Nothing seems to be affected by this error message although I'd like to know what it means. And possibly how to  fix the problem.

Thanks for any and all help.

---

### Post by mllr on 2006-07-23
I dunno if this problem is what im thinking... but...

for first, do it:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

All your USB or Firewires are ok?

If not, try reading (and doing, if you think this is your problem) this: [https://wiki.ubuntu.com/DebuggingRemovableDevices](https://wiki.ubuntu.com/DebuggingRemovableDevices)

[]'S

---

### Post by MrMojoRising on 2006-07-24
The apt-gets didn't do anything new.

To the best of my knowledge all my firewire and USB devices are working fine.
I have a built in card-reader....it works fine.

In doing all those debug options....i couldn't get anything to fail on me....so i have no reason to send a bug report.

One thing i tink might help but it's kinda to drastic for me to idly test is that i have an i686 system....and am using an i386 kernel. Although I used the same detup in Breezy and didn't get that error message.

Only after using Dapper do i get these nasty messages:

```
Jul 23 21:45:34 Enoch kernel: [17179573.064000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
Jul 23 21:45:34 Enoch kernel: [17179573.064000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
Jul 23 21:45:34 Enoch kernel: [17179573.064000] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
Jul 23 21:45:34 Enoch kernel: [17179573.064000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
```

---

### Post by MrMojoRising on 2006-07-24
When asking the all mighty google, i was told to try pci=routeirq as one of the boot parameters. I'll give it a shot...

Apparenty everyone else that sees that message sees it because their wifi isn't working..
My wifi works fine (notice i'm posting *online*)

---

### Post by micjustmic on 2006-10-03
I'm seeing a similar error.

```
PCI: Cannot allocate resource region 0 of bridge 0000:00:00.0
```

Everything seems to work, so I'm not too worried about it.  I just don't like seeing anything like this when everything else seems just peachy.

Mic

---

