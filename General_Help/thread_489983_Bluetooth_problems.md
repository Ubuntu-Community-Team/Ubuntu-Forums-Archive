---
title: "Bluetooth problems"
date: 2007-07-01
forum: General Help
---

### Post by El BrandO on 2007-07-01
Hey,

I'm having problems getting my bluetooth up and running.  I can run the 'hcitool dev' command and get a MAC address for my usb adapter.  However when I run the 'hcitool scan' command, it times out.  I've researched the problem, and it doesn't seem to effect a lot of people and I haven't found a resolution.  The two possible fixes I've found are adding an entry into the rc.local file.  That entry is:  'hciconfig hci0 inqmode 0'
The other one, you reset it with 'hcitool hci0 reset'.  

Neither of these have worked, but it is a step up from Fedora 7 not recognizing my dongle AT ALL.  My final goal is to be able to pair my phone, a Motorola Q, and my Wiimote for keyboard/mouse emulation.  I really appreciate any help you guys can offer.

Regards,

Brandon

---

### Post by gregmark on 2007-07-02
Have you tried running *hciconfig enable*?

---

### Post by El BrandO on 2007-07-02
Greg,

I was not aware of this command, I will execute it when I get home tonight. 

Thanks,

Brandon

---

### Post by El BrandO on 2007-07-02
After executing the command, it just said my device was up and running.  Yet it still did not pick up anything.  This is just a thought, I don't think I have USB 2.0 ports, could that be a problem or may this just be a bug?  This is a known working bluetooth adapter.  I find this very compelling.

Regards,

Brandon

---

### Post by fragos on 2007-07-03
"hcitool scan" will only work if bluetooth is enabled in the devices you are scaning.  My Palm E2 is easily detected.  Cell phones can be more troublesome because they are filled with safeguards to keep strangers from discovering your phone.  My LG 8300 is also scannable.

---

### Post by El BrandO on 2007-07-03
Hey,

I understand what the command does.  The devices are in discoverable mode.  Especially my phone, bluetooth is on and other devices are allowed to see it.  It is a Motorola Q and does run on Windows Mobile, so you do have an argument there.  The otherdevice is a Wiimote.  I can see both in Windows, but not in Linux.  This has stumped me completely.  Has this happened to anyone else?

Regards,

Brandon

---

### Post by fragos on 2007-07-04
I have a Plantronix bluetooth head set that won't register when scanned.  It did easily pair with my LG 8300.  My experience is limited to getting my own devices to work and may in some cases represent luck and not skill.  Best of luck to you.  I for one will be interested in learning the resolution to your problems.

---

### Post by Nanoboy on 2007-07-05
I have the same problem.

Tried the "hciconfig enable" command, outcome as follows:

```
hci0:   Type: USB
        BD Address: 00:10:C6:4E:07:51 ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:3712 acl:0 sco:0 events:359 errors:0
        TX bytes:340 acl:0 sco:0 commands:24 errors:0

```

Need to keep researching how to switch my bluetooth on my Dell Inspiron 9100 on.

---

