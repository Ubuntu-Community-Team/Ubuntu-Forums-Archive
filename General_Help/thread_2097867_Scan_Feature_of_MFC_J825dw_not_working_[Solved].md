---
title: "Scan Feature of MFC J825dw not working [Solved]"
date: 2012-12-24
forum: General Help
---

### Post by Mottq on 2012-12-24
I am running Ubuntu 12.10 and have recently purchased a Brother MFC J825DW. I am printing fine, however, the scan feature still won't work. I have run dpkg -l | grep Brother and it appears all the drivers are installed:

ii  brscan-skey                            0.2.4-0                                 Brother Linux scanner S-KEY tool
ii  brscan4                                0.4.1-3                                 Brother Scanner Driver
ii  mfcj825dwcupswrapper                   3.0.0-1                                 Brother CUPS Inkjet Printer Definitions
ii  mfcj825dwlpr                           3.0.0-1                                 Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

Neither Xsane nor Simple Scan work. Any suggestions?

---

### Post by plucky on 2012-12-25
> **Mottq said:**
> I am running Ubuntu 12.10 and have recently purchased a Brother MFC J825DW. I am printing fine, however, the scan feature still won't work. I have run dpkg -l | grep Brother and it appears all the drivers are installed:

ii  brscan-skey                            0.2.4-0                                 Brother Linux scanner S-KEY tool
ii  brscan4                                0.4.1-3                                 Brother Scanner Driver
ii  mfcj825dwcupswrapper                   3.0.0-1                                 Brother CUPS Inkjet Printer Definitions
ii  mfcj825dwlpr                           3.0.0-1                                 Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                          printer driver Brother P-touch label printers

Neither Xsane nor Simple Scan work. Any suggestions?

Are you using USB or Wireless connection?

From the Brother Website
> 
Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10, 12.04, 12.10
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".

    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Also,see if it is a permission problem by using ```
gksudo simple-scan
```


Good Luck

---

### Post by Mottq on 2012-12-25
I have a wireless connection. When I ran the Simple Scan command in terminal, it did not work

---

### Post by plucky on 2012-12-25
> **Mottq said:**
> I have a wireless connection. When I ran the Simple Scan command in terminal, it did not work

From the [Brother Website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1b.html)

> Step 5. Setting for your network scanner
    ***Use brsaneconfig (for brscan models), brsaneconfig2 (for brscan2 models) or brsaneconfig3 (for brscan3 models) accordingly.
    5-1. Add network scanner entry

        Command  :  brsaneconfig4  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx
        Example 

    5-2. Confirm network scanner entry

        Command  :  brsaneconfig4  -q  |  grep  (name  of  your  device) 

Change the values to match your scanner.

Also install **sane-utils** from synaptic package manager.

Good Luck

---

### Post by Mottq on 2012-12-25
I connected the Machine via USB. It Works great!!! Thank you

---

### Post by Mottq on 2013-06-18
I installed Kubuntu 13.04 and , of course my scanner is not working again :(.

---

### Post by Mottq on 2013-06-19
There was some sort of Glitch with the brother web page at first I couldn't get brscan4 and the scankey tool. I was able to install both packages this morning and scanner works!

---

