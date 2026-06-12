---
title: "Printing slow since upgrade from Ubuntu 10.04 to Ubuntu 14.04"
date: 2015-04-17
forum: General Help
---

### Post by darknomel on 2015-04-17
[SIZE=2][FONT=arial]Hi guys,

Posted this [here]("http://askubuntu.com/questions/609036/printing-slow-since-upgrade-from-ubuntu-10-04-to-ubuntu-14-04") on ask Ubuntu, but I'm getting desperate as no one is answering.

Hope someone can help here - I've been struggling with this for a while. Since I upgraded from Ubuntu 10.04 LTS to Ubuntu 14.04 LTS, printing in general has been extremely slow.
I manage to compare /etc/cups/printers.conf on both systems, and found the following difference:

Slow config:
```
<Printer Collec525>
UUID urn:uuid:4fbfddb9-186a-33a6-62d9-8e2fea311fd5
Info Collec525
MakeModel HP LaserJet 500 MFP M525 Postscript (recommended)
DeviceURI dnssd://Collec525._ipp._tcp.local/
PPDTimeStamp *
State Idle
StateTime 1428943167
Type 8425684
Accepting Yes
Shared Yes
ColorManaged Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```

Working config:
```

<DefaultPrinter Collec525>
Info Collec525
MakeModel HP LaserJet 500 MFP M525 Postscript (recommended)
DeviceURI dnssd://Collec525._pdl-datastream._tcp.local/
State Idle
StateTime 1428910412
Type 8425684
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 hplipjs
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```
The following two config lines are missing from the slow printing system:
```

Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 hplipjs

```
If I add them in, everything works perfectly. However, cups seems to rewrite this config and remove any manual settings added to it. I found a similar post asking about this problem here:

[http://ubuntuforums.org/showthread.php?t=2139624](http://ubuntuforums.org/showthread.php?t=2139624)

But it has no replies. Does anyone know which userspace tool is used to add these lines? Can they be added using lpadmin for example?

Thanks in advance![/FONT][/SIZE]

---

### Post by dino99 on 2015-04-17
open a bug report against cups or hplip, devs are usually answering quickly

---

### Post by SeijiSensei on 2015-04-17
After you take 9d9's advice and file a bug report, here's a way you can keep CUPS from overwriting the configuration.

Files in Linux have a set of "attributes," one of which is "immutable."  That will make it impossible even for the root user to overwrite a file.  
```

cd /etc/cups
sudo lsattr printers.conf
[enter your password]
-------------e-- printers.conf

sudo chattr +i printers.conf

sudo lsattr printers.conf
----i--------e-- printers.conf

```
You can turn off the immutable bit with "sudo chattr -i /etc/cups/printers.conf".

---

