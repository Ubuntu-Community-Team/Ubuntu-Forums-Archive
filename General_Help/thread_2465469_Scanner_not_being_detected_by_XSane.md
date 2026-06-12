---
title: "Scanner not being detected by XSane"
date: 2021-08-02
forum: General Help
---

### Post by victor432 on 2021-08-02
I'm running Ubuntu 20.04 and I have a Brother DCP-7020 scanner and printer (all-in-one). The printer is detected by Ubuntu and it works just fine but the built-in scanner does not get detected so I'm unable to use it. I followed the instructions from the manufacturer website as shown [here ]("https://upport.brother.com/g/b/downloadhowto.aspx?c=ca&lang=en&prod=dcp7020_us&os=128&dlid=dlf006637_000&flang=4&type3=566")I installed the driver and was able to verify that the scanner driver was successfully installed. Does anyone have any ideas ?

$$$$$$$@:~/Downloads$ dpkg -l | grep Brother
ii  brscan2                                    0.2.5-1                             amd64        Brother Scanner Driver
ii  printer-driver-brlaser                     6-1build1                           amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                      1.4.2-3                             amd64        printer driver Brother P-touch label printers

---

### Post by iamjiwjr on 2021-08-04
I wish I did. My Brother HL-L2390DW laser printer-scanner chronically does not work  with any Ubuntu-based distro I've tried except Linux Mint. It works great with all non-Ubuntu-based Debian, rpm, arch, and Solus distros I've tried. I just had to leave Ubuntu behind. Good luck.

---

