---
title: "Brother printer doesn't scan"
date: 2014-06-02
forum: General Help
---

### Post by vik2 on 2014-06-02
Heeeeellllp please, my brother DCP-375CW printer isn't scanning. Downloaded all the drivers, tried about 3 different scanner applications to no avail. Simple scan source knows my brother printer details, but can't connect to scanner? Don't know, looked up help threads, but way over my head with some of the solutions. Running latest Ubuntu 64bit.

---

### Post by plucky on 2014-06-02
> **vik2 said:**
> Heeeeellllp please, my brother DCP-375CW printer isn't scanning. Downloaded all the drivers, tried about 3 different scanner applications to no avail. Simple scan source knows my brother printer details, but can't connect to scanner? Don't know, looked up help threads, but way over my head with some of the solutions. Running latest Ubuntu 64bit.

Open a terminal and post output for ```
dpkg -l | grep -i brother
```

That should show which drivers are installed for your printer.

Are you using USB or Wireless connection to the printer/scanner?

You also need to install sane-utils ```
sudo apt-get install sane-utils
```

The driver for your scanner is brscan3 [Here](http://support.brother.com/g/s/id/linux/en/download_scn.html)

The install instructions are [Here](http://support.brother.com/g/s/id/linux/en/instruction_scn1.html?c=us_ot&lang=en&redirect=on)

Good Luck

---

### Post by vik2 on 2014-06-02
Plucky, the Brother is connected via USB, it prints fine, just not scanning. I have the latest version of sane-utils and brscan3 installed as noted in the following, dpkg -l | grep -i brother                                                                                                                                                                 ii  brscan-skey                                           0.2.4-1                                             amd64        Brother Linux scanner S-KEY tool
ii  brscan3                                               0.2.11-5                                            amd64        Brother Scanner Driver
ii  dcp375cwcupswrapper                                   1.1.3-1                                             i386         Brother CUPS Inkjet Printer Definitions
ii  dcp375cwlpr                                           1.1.3-1                                             i386         Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                                 1.3-8                                               amd64        printer driver Brother P-touch label printers

I don't get this terminal command, [FONT=Arial][COLOR=#000000]**Command (for dpkg)  :  dpkg  -i  --force-all  (scanner-drivername), I've posted it with name but no good, what information do I use in **[/COLOR][/FONT][COLOR=#000000][FONT=Arial]**(scanner-drivername)? **[/FONT][/COLOR]

---

### Post by gifford on 2014-06-02
brscan3 is the scanner driver. You will want to copy [COLOR=#000000]brscan3 0.2.11-5 amd64.deb as the scanner driver in the command.[/COLOR]

---

### Post by vik2 on 2014-06-02
I'm having a "duh" moment, dpkg -i --force-all brscan3 0.2.11-5 amd64.deb, when entered, i receive the following dpkg: error: operation requires read/write access to dpkg status area. Can someone please pop up the right command line.

---

### Post by davidvandoren on 2014-06-03
You need to be sudo ```
sudo [COLOR=#000000]dpkg -i --force-all brscan3 0.2.11-5 amd64.de[/COLOR]
```



Go here and download [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on)

```
[COLOR=#000000][FONT=Arial]**Ubuntu 10.10, 11.4, 11.10, 12.04, 12.10, 13.04, 13.10**[/FONT][/COLOR]**1. **[Click here to download the file.]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brother-udev-rule-type1-1.0.0-1.all.deb&lang=English_lpr")(brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB)**2. **Run the command.
**Command:** dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb


```

**1. **[Click here to download the file]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brother-udev-rule-type1-1.0.0-1.all.deb&lang=English_lpr") [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brother-udev-rule-type1-1.0.0-1.all.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brother-udev-rule-type1-1.0.0-1.all.deb&lang=English_lpr)

```
sudo [COLOR=#000000][FONT=Arial]dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb[/FONT][/COLOR]
```

Reboot

---

### Post by davidvandoren on 2014-06-03
Or go here [http://support.brother.com/g/b/downloadlist.aspx?c=hk&lang=en&prod=dcp375cw_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=hk&lang=en&prod=dcp375cw_all&os=128)

and download the driver install tool.
Unzip the file into your home directory and run the linux-printer??? file in the terminal with
```
sudo sh linux-printer????? or whatever the file-name will be exactly.
```

---

### Post by vik2 on 2014-06-03
Thank you all, working like a charm, needed to download and install [COLOR=#000000][FONT=Ubuntu Mono]brother-udev-rule-type1-1.0.0-1.all.deb, ver.1.0.0-1, 2KB.[/FONT][/COLOR]

---

