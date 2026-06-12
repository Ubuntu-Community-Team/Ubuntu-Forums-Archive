---
title: "Xsane Invalid Arguments"
date: 2014-03-14
forum: General Help
---

### Post by Pieman15 on 2014-03-14
Hello,

Previously, Xsane was working fine for over a year. I do not know what happend, but I can no longer open Xsane. I continuously get an error stating something like:

Error:
Failed to open device 'brother4:bus6:dev1': 
Invalid arugment.

That is the error when attempting to connect to through USB, I get a similar error when attempting to connect over WiFi (different bus and dev numbers). I can print wirelessly without issue. I have restarted my computer and the printer, but the issue persists. A Googling of the issue brought up other posts, but not a solution that worked for me.

I am on Ubuntu 12.04. 
Printer is a Brother MFC-J430W.
```
:~$ lpstat -s
system default destination: Brother_MFC-J430W
device for Brother_MFC-J430W: dnssd://Brother%20MFC-J430W._pdl-datastream._tcp.local/

```
I am not sure what other information is pertinent for troubleshooting.

Thank you in advance for any assistance.

---

### Post by gifford on 2014-03-14
Let's start by using this: [FONT=Ubuntu Mono]dpkg -l | grep Brother
and posting the results.[/FONT]

---

### Post by Pieman15 on 2014-03-15
```
dpkg -l | grep Brother
ii  brscan-skey                            0.2.4-0                                       Brother Linux scanner S-KEY tool
ii  brscan4                                0.4.1-2                                       Brother Scanner Driver
ii  mfcj430wcupswrapper                    3.0.0-1                                       Brother CUPS Inkjet Printer Definitions
ii  mfcj430wlpr                            3.0.0-1                                       Brother lpr Inkjet Printer Definitions
ii  mfcj432wlpr                            3.0.0-1                                       Brother lpr Inkjet Printer Definitions
ii  printer-driver-ptouch                  1.3-3ubuntu0.1                                printer driver Brother P-touch label printers

```

---

### Post by Pieman15 on 2014-03-20
Bump

---

### Post by gifford on 2014-03-20
Has anything changed with your configuration? When was the last time you were able to use Xsane?
The reason I ask is that I had a similar problem recently that was caused by changing modem/routers. 
The ip address had changed and I had to change it for the printer/scanner to be found.
It looks as all drivers are correctly installed.
Also, from your post of the results of  lpstat -s, it looks as if you are not USB connected.
This is the last line I get when running that command: device for MFC495CW: usb:/dev/usb/lp0 
Although my connection is not USB but done through my router over ethernet.

---

### Post by Pieman15 on 2014-03-22
Gifford - Thank you for your help.

Actually, now that you mention it, the printer was setup using a static IP address. That became problematic on my network, so I switched it to a DHCP address. I believe I also installed the CUPS driver at that time. The scanner has not worked since.

Regarding the USB connection, despite the results of lpstat -s, the USB cable is plugged in, and when I open Xsane, I get two options, brother4:net1;dev0 (wireless) and brother4:bus6;dev1 (USB), both fail to open giving the error message in my original post.

At this point, I think I will start fresh and reinstall the printer and Xsane and see what happens. I'll post my results when I get around to doing that. I am open to suggests in the mean time.

---

### Post by Pieman15 on 2014-03-27
My scanner is still not working, I thought it was because XSane will at least open now, but when I go to scan, I get the following error: Failed to start scanner; Invalid argument. Any ideas how to fix this?
> scanimage --list-devices
device `brother4:net1;dev0' is a Brother Brother MFC-J430W

Here's what I did leading up to this point:
1. I set my printer back to a static ip address. 
2. I upgrade from Ubuntu 12.04 to 12.10 and then to 13.10
3. After upgrading to 13.10, my scanner and printer did not work. I reinstalled the printer driver and the Brother scanner driver which fixed the issue. The drivers were still installed based on the dpkg -l |grep Brother command, but the device was not working.
4. With the newly installed scanner driver, I added my scanner using: brsaneconfig4 -a name=Brother model=MFC-J430W ip=xx.xx.xx.xx

By the way, Brother has good instructions for linux users: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by Pieman15 on 2014-03-28
I started using Simple Scan which suits my need. So, in my case, I will consider this solved.

---

### Post by JLUbunt on 2014-06-20
Hello
The guys from Brother fixed my scanner problems MFC-9120 CN for Windows 8.1. and then also for Ubuntu 14.04. I used to used it for Windows but had never tried with Ubuntu.  For Ubuntu Xsane was installed. I used it a couple of times but now get the "Failed to start scanner: Invalid Augment" error.  Which is a pity as Xsane seems very useful.  I have an idea what an augment might be, but would not know where to look for it.  With my limited knowledge I asked if he would use a static IP address which he did easily.  Since it stopped working I checked the scanner and confirmed that the Scanner still displays the same IP address that previously worked.  
I was pleasantly surprised how helpful they were for an aging printer scanner. check the link to the Brother site you referred to and will try simple scan to see if it works. Thanks

---

### Post by JLUbunt on 2014-06-28
I tried Simple Scan. Worked perfectly. Then installed Gscan2 pdf.  That worked well as well.

---

### Post by kelvinator on 2014-12-02
In my case replacing a defective cable corrected the problem for a scanner that had worked through multiple upgrades of Ubuntu over two years.



[QUOTE=Pieman15;12956983]Hello,

Previously, Xsane was working fine for over a year. I do not know what happend, but I can no longer open Xsane. I continuously get an error stating something like:

Error:
Failed to open device 'brother4:bus6:dev1': 
Invalid arugment

---

