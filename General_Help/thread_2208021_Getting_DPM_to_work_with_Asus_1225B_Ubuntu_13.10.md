---
title: "Getting DPM to work with Asus 1225B Ubuntu 13.10"
date: 2014-02-26
forum: General Help
---

### Post by zemega on 2014-02-26
Hi. I have an ASUS 1225B. I installed 13.04 previously. Then I upgraded to 13.10. Turn out my kernel was not updated, stuck with 3.8. So I did 'sudo apt-get install linux-generic', which updated my kernel to 3.11 generic. I then follow the instruction on webupd8 (link below). I got this comment popping out eacch tim I'm starting Ubuntu. I believe that the DPM is not working. Can anyone help me or shed some light? I am waiting for 14.04 to come out and do fresh install, but I still want to sort this out.

[ seconds] Support for cores revision 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1.

 [http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)

---

### Post by Yellow Pasque on 2014-02-26
b43 is the Broadcom wireless module/driver, so the error is unrelated to radeon dpm. What makes you think dpm is not working?

---

### Post by zemega on 2014-02-26
Because it was running on full fan speed inside an air conditioned room. So that error must have been because I disabled the Bluetooth in BIOS (it was a pain whenever I work inside Windows, had to switch on/off wireless bluetooth in some sequence). One of the app, Kingsoft Presentation didnt close properly. Its supposed to be closed already, but the fan is still loud. When I check the System Manager, the app was still there, using 100% CPU, so I killed it, the CPU usage also dropped to normal level, but the fan didnt slow down even after half an hour.

---

