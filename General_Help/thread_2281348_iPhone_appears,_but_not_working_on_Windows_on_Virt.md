---
title: "iPhone appears, but not working on Windows on Virtualbox - running on Ubuntu 14.04"
date: 2015-06-06
forum: General Help
---

### Post by KernowInExile on 2015-06-06
So, after years of dual booting Ubuntu and Linux I've gone to Linux only (14.04 LTS), on top of this I have Virtualbox installed and have Windows 7 running within that. Like many people I have an iPhone and want to be able to add/remove music to it. Having read various ways of doing it I thought I should be able to do this with iTunes on Windows within Virtualbox.

My device *is *being recognised in that when you plug it in you get a Windows audio sound and within the device manager it shows: 
Apple mobile device (under USB)

If I open it up it has error code 10 - device cannot start. I've tried reinstalling iTunes and manually assigning the driver to no avail. 

When I go to driver details there are two files shown with the first one highlighted:
...\usbaapl64.sys
...\usbaaplrc.dll

Any suggestions? Seems a shame to give up and go back to dual booting (getting another phone isnt an option for the time being either)...

---

### Post by leunam12 on 2015-06-06
maybe the automated troubleshooter will help you

[https://support.microsoft.com/en-us/mats/hardware_device_problems](https://support.microsoft.com/en-us/mats/hardware_device_problems)

---

### Post by KernowInExile on 2015-06-06
Unfortunately not, it says that it could fix the error. It says hardware devices are not fixed or are not working in Windows.

---

### Post by SeijiSensei on 2015-06-06
Did you [install the Extension Pack]("https://www.virtualbox.org/manual/ch01.html#intro-installing")? Create a USB "[filter]("https://www.virtualbox.org/manual/ch03.html#settings-usb")" for your device?

---

### Post by KernowInExile on 2015-06-06
Yes, thats all done and the guest OS (Windows) does recognize that there is a USB device attached, and that its an apple mobile device but for some reason cannot make it work.

---

### Post by leunam12 on 2015-06-06
Do you have "Enable USB 2.0 (EHCI) Controller:" in Settings> USB checked?

---

