---
title: "Printer (Brother) not working"
date: 2016-08-19
forum: General Help
---

### Post by markodd on 2016-08-19
Hello,

I'm trying to print something on my desktop with Xubuntu 16.04 but I'm being unsuccessfull. The weird thing is that it works perfectly on my laptop (with the same version OS, same drivers, etc).

Here are the outputs of ```
tail -f /var/log/syslog 
``` before and after plugging my printer:

```
Aug 19 11:50:26 mypc kernel: [  124.382330] usblp 3-10.3:1.0: usblp1: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x04F9 pid 0x035B
Aug 19 11:50:50 mypc org.freedesktop.PackageKit[3064]: DEBUG:Checking for inactivity (30s)
Aug 19 11:51:20 mypc org.freedesktop.PackageKit[3064]: DEBUG:Checking for inactivity (60s)
Aug 19 11:51:36 mypc kernel: [  193.883546] usb 3-10.3: USB disconnect, device number 5
Aug 19 11:51:36 mypc kernel: [  193.883747] usblp1: removed
Aug 19 11:51:36 mypc udev-configure-printer[5268]: remove /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.3
Aug 19 11:51:36 mypc udev-configure-printer[5268]: URI of detected printer: usb://Brother/DCP-1610W%20series?serial=E74230B5N526398, normalized: brother dcp 1610w series serial e74230b5n526398
Aug 19 11:51:36 mypc udev-configure-printer[5268]: URI of print queue: usb://Brother/DCP-1610W%20series?serial=E74230B5N526398, normalized: brother dcp 1610w series serial e74230b5n526398
Aug 19 11:51:36 mypc udev-configure-printer[5268]: Queue ipp://localhost/printers/Brother-DCP-1610W-series has matching device URI
Aug 19 11:51:36 mypc udev-configure-printer[5268]: Disabled printer ipp://localhost/printers/Brother-DCP-1610W-series as the corresponding device was unplugged or turned off
Aug 19 11:51:40 mypc colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Aug 19 11:51:43 mypc kernel: [  200.962335] usb 3-10.3: new high-speed USB device number 6 using xhci_hcd
Aug 19 11:51:43 mypc kernel: [  201.051201] usb 3-10.3: New USB device found, idVendor=04f9, idProduct=035b
Aug 19 11:51:43 mypc kernel: [  201.051204] usb 3-10.3: New USB device strings: Mfr=0, Product=0, SerialNumber=3
Aug 19 11:51:43 mypc kernel: [  201.051205] usb 3-10.3: SerialNumber: E74230B5N526398
Aug 19 11:51:43 mypc kernel: [  201.053024] usblp 3-10.3:1.0: usblp1: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x035B
Aug 19 11:51:43 mypc systemd[1]: Starting Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:14.0-usb3-3\x2d10-3\x2d10.3)...
Aug 19 11:51:43 mypc udev-configure-printer[5285]: add /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.3
Aug 19 11:51:43 mypc udev-configure-printer[5285]: device devpath is /devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10.3
Aug 19 11:51:43 mypc udev-configure-printer[5285]: MFG:Brother MDL:DCP-1610W series SERN:- serial:E74230B5N526398
Aug 19 11:51:43 mypc kernel: [  201.078847] audit_printk_skb: 63 callbacks suppressed
Aug 19 11:51:43 mypc kernel: [  201.078850] audit: type=1400 audit(1471603903.429:118): apparmor="DENIED" operation="open" profile="/usr/sbin/ippusbxd" name="/etc/ld.so.preload" pid=5299 comm="ippusbxd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 19 11:51:47 mypc colord-sane: io/hpmud/pp.c 627: unable to read device-id ret=-1
Aug 19 11:51:48 mypc kernel: [  206.136838] audit: type=1400 audit(1471603908.485:119): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5309 comm="cups-exec" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 19 11:51:48 mypc kernel: [  206.137116] audit: type=1400 audit(1471603908.485:120): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5309 comm="cups-deviced" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 19 11:51:48 mypc kernel: [  206.140017] audit: type=1400 audit(1471603908.489:121): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5311 comm="ipp" requested_mask="r" denied_mask="r" fsuid=7 ouid=0
Aug 19 11:51:48 mypc kernel: [  206.145184] audit: type=1400 audit(1471603908.493:122): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5314 comm="serial" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 19 11:51:48 mypc kernel: [  206.148449] audit: type=1400 audit(1471603908.497:123): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5316 comm="ipps" requested_mask="r" denied_mask="r" fsuid=7 ouid=0
Aug 19 11:51:48 mypc kernel: [  206.150067] audit: type=1400 audit(1471603908.497:124): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/etc/ld.so.preload" pid=5320 comm="usb" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Aug 19 11:51:48 mypc kernel: [  206.156124] usblp1: removed
Aug 19 11:51:48 mypc kernel: [  206.163011] usblp 3-10.3:1.0: usblp1: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04F9 pid 0x035B
Aug 19 11:51:48 mypc hp[5313]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Aug 19 11:51:48 mypc python3: io/hpmud/pp.c 627: unable to read device-id ret=-1
Aug 19 11:51:48 mypc udev-configure-printer[5285]: URI contains USB serial number
Aug 19 11:51:48 mypc udev-configure-printer[5285]: URI match: usb://Brother/DCP-1610W%20series?serial=E74230B5N526398
Aug 19 11:51:48 mypc udev-configure-printer[5285]: URI of detected printer: usb://Brother/DCP-1610W%20series?serial=E74230B5N526398, normalized: brother dcp 1610w series serial e74230b5n526398
Aug 19 11:51:48 mypc udev-configure-printer[5285]: URI of print queue: usb://Brother/DCP-1610W%20series?serial=E74230B5N526398, normalized: brother dcp 1610w series serial e74230b5n526398
Aug 19 11:51:48 mypc udev-configure-printer[5285]: Queue ipp://localhost/printers/Brother-DCP-1610W-series has matching device URI
Aug 19 11:51:48 mypc udev-configure-printer[5285]: Re-enabled printer ipp://localhost/printers/Brother-DCP-1610W-series
Aug 19 11:51:48 mypc systemd[1]: Started Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:14.0-usb3-3\x2d10-3\x2d10.3).
Aug 19 11:51:50 mypc org.freedesktop.PackageKit[3064]: DEBUG:Checking for inactivity (90s)
^C
```


My printer is the Brother-DCP 1610w. I can scan perfectly fine with it, it's just the printing that's not working. Under "Printers", I see the printer there with the green check-mark, though after asking to print something, nothing happens. 

Any idea what might be happening and I should I go about fixing this?


EDIT: If I go to "Printers", I see the jobs as "completed".

EDIT2:
Doing `sudo cat /etc/cups/printers.conf` while the printer is turned OFF gives me the following:

    ```
# Printer configuration file for CUPS v2.1.3
    # Written by cupsd
    # DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
    <DefaultPrinter Brother-DCP-1610W-series>
    UUID urn:uuid:3f49b902-e331-31f5-558a-cf8be931977d
    Info Brother DCP-1610W series
    Location mypc
    MakeModel Brother DCP-1610W for CUPS
    DeviceURI usb://Brother/DCP-1610W%20series?serial=E74230B5N526398
    State Stopped
    StateMessage Unplugged or turned off
    StateTime 1471611395
    ConfigTime 1471603824
    Reason paused
    Type 8392708
    Accepting Yes
    Shared Yes
    JobSheets none none
    QuotaPeriod 0
    PageLimit 0
    KLimit 0
    OpPolicy default
    ErrorPolicy retry-job
    </DefaultPrinter>
    <Printer DCP1610W>
    UUID urn:uuid:b62f3751-a91c-39b0-59ee-2fb82efd5755
    Info DCP1610W
    MakeModel Brother DCP-1610W for CUPS
    DeviceURI usb://Brother/DCP-1610W%20series?serial=E74230B5N526398
    State Stopped
    StateMessage Unplugged or turned off
    StateTime 1471611395
    ConfigTime 1471606686
    Reason paused
    Type 8392708
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

With the printer ON, I get:

    ```
# Printer configuration file for CUPS v2.1.3
    # Written by cupsd
    # DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
    <DefaultPrinter Brother-DCP-1610W-series>
    UUID urn:uuid:3f49b902-e331-31f5-558a-cf8be931977d
    Info Brother DCP-1610W series
    Location mypc
    MakeModel Brother DCP-1610W for CUPS
    DeviceURI usb://Brother/DCP-1610W%20series?serial=E74230B5N526398
    State Idle
    StateTime 1471702911
    ConfigTime 1471603824
    Type 8392708
    Accepting Yes
    Shared Yes
    JobSheets none none
    QuotaPeriod 0
    PageLimit 0
    KLimit 0
    OpPolicy default
    ErrorPolicy retry-job
    </DefaultPrinter>
    <Printer DCP1610W>
    UUID urn:uuid:b62f3751-a91c-39b0-59ee-2fb82efd5755
    Info DCP1610W
    MakeModel Brother DCP-1610W for CUPS
    DeviceURI usb://Brother/DCP-1610W%20series?serial=E74230B5N526398
    State Idle
    StateTime 1471702911
    ConfigTime 1471606686
    Type 8392708
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

** EDIT: New information:**

I've configured the printer to work via wireless, both on my laptop and on my desktop. On my laptop, it works flawlessly. On my desktop, it **DOES NOT** work. In the Document Print Status window, the documents I tried to print are defined as "completed", but the printer didn't print them...

I wonder if emailing brother would work?

---

### Post by SeijiSensei on 2016-08-19
Try restarting the printer itself.  I've had this happen once in a while with my Brother printer.

---

### Post by markodd on 2016-08-19
> **SeijiSensei said:**
> Try restarting the printer itself.  I've had this happen once in a while with my Brother printer.


I've restarted (turned OFF and ON) both the printer and the computer several times, no help.

---

### Post by markodd on 2016-08-28
Edited my main post with additional information.

---

### Post by Bucky Ball on 2016-08-28
Which driver are you using exactly? Did you download it [from here]("http://support.brother.com/g/b/downloadtop.aspx?c=as_ot&lang=en&prod=dcp1610w_eu_as")? If you open a web browser and type this in the address bar:

localhost:631

... do you get the CUPS interface and can you see the printer okay? Will that print a test page and if not, what is the error it gives?

---

### Post by markodd on 2016-08-28
@Bucky_Ball

Yes, I did download the drivers from there. Typing localhost:631 into the browser gets me to the CUPS interface. In the tab "Printers" I can see the printers just fine, yes. 

I don't know how to print a test page using that interface, though using the OS's Printers interface I cannot print a test page. After pressing "Print test page", a message appears which says "Submitted as job X". By going to the Document Print Status, it says that the job was completed, even though it didn't print.

---

### Post by Bucky Ball on 2016-08-28
> **markodd said:**
> By going to the Document Print Status, it says that the job was completed, even though it didn't print.

Hmm. Plot thickens. This may be totally whacky and off the mark, but you aren't printing to a file instead of the printer by any chance and you now have a bunch of files of the document you are trying to print in whatever folder is set in the print window when you print it? :-k Just a thought and a shot in the dark (duck!).

---

### Post by markodd on 2016-08-28
> **Bucky Ball said:**
> Hmm. Plot thickens. This may be totally whacky and off the mark, but you aren't printing to a file instead of the printer by any chance and you now have a bunch of files of the document you are trying to print in whatever folder is set in the print window when you print it? :-k Just a thought and a shot in the dark (duck!).

hehe. No, I'm not printing to a file. I'm printing to the printer. 

I agree with you that this behaviour is quite weird. As I mentioned in the OP, the printer/drivers work perfectly fine on my laptop, but not on my desktop. I've exactly the same OS and driver versions here, so I've no idea what's going on. Something similar happened 1 year ago or so, but it was the scanner giving problems (worked on laptop but didn't work on desktop).

I think my Desktop is cursed.

---

### Post by markodd on 2016-09-04
Added new information on the first post. 

TLDR: Configured printer via wireless, jobs still get "completed" but nothing gets printed.


I think this might be a bug. Should I report it on launchpad? Is it enough to just post whatever information I've posted in this thread?

---

