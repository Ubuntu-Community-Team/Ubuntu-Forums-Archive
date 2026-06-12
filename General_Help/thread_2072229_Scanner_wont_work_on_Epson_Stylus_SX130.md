---
title: "Scanner wont work on Epson Stylus SX130"
date: 2012-10-17
forum: General Help
---

### Post by capo1949 on 2012-10-17
Hi All,

I have installed the all in one epson driver and the copy and print functions work fine. I am using a wired usb connection.
It wont scan, using simple scan, and after doing the ususal legwork with google and the forums, I installed iscan  iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb and iscan-data_1.18.0-1_all.deb.
Now I get the alarm 'could not send command to scanner. Check the scanners status' . I do not know how to procced form here, googled the alarm, but responses did not make a lot of sense to me. Could someone help please
lsusb gives;-

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 004: ID 0c45:6417 Microdia Integrated Webcam
Bus 002 Device 016: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 011: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 012: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 013: ID 0bc2:3320 Seagate RSS LLC 
Bus 002 Device 014: ID 0bc2:5021 Seagate RSS LLC FreeAgent GoFlex USB 2.0
Bus 002 Device 023: ID 04b8:0883 Seiko Epson Corp. 
Bus 002 Device 015: ID 0bc2:5021 Seagate RSS LLC FreeAgent GoFlex USB 2.0

Thanks 
graham

---

### Post by pdc on 2012-10-17
I guess if one checks the 2 packages were installed fully

if you copied and pasted

> sudo dpkg -l | grep iscan

into a terminal: [COLOR="DeepSkyBlue"]the | line is shift\ and is called a pipe command I believe[/COLOR]

....that should give you the same result as opening synaptic (the GUI package manager)

........*[COLOR="SeaGreen"]If you copied and pasted the results back here[/COLOR]* ......

I would be interested in the order **_that the packages are listed_**:

I note from this page on FAQs; 

[http://download.ebz.epson.net/faq/linux/faq_ls_00002.html](http://download.ebz.epson.net/faq/linux/faq_ls_00002.html)

that Epson say 

>  [**[COLOR="Red"]data package[/COLOR]**]

    [COLOR="SeaGreen"]*Install this package first, it is always required*[/COLOR].  

.........I just wonder if that might be a key thing; eg with Canon printers, one MUST install the common package first; then the specific package for one's particular printer ....

......you absolutely seem to have downloaded the very appropriate and latest drivers from Epson; well done to find all those ..

.....if you installed  iscan_2.29 first and then the data package, I wonder about deleting both and re-installing with data first and then the iscan after.......

---

### Post by capo1949 on 2012-10-18
Hi pdc
Many thanks for your prompt response. I knew the data had to be installed first and thot I had done the, so b4 going any further I deleted the packages and reinstalled. Yup it solved the problem. Many thanks again
Graham

---

### Post by pdc on 2012-10-18
great! delighted to hear it is all working for you Graham;

enjoy!

You can edit your thread to say: SOLVED 

....and it may help others coming in your wake .............

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

enclosed is a how to, as I think only you can do it .....

---

