---
title: "Getting sound running properly in VMware (Windows 98se Guest)"
date: 2007-01-28
forum: General Help
---

### Post by Gobboman123 on 2007-01-28
I installed Win98SE in VMware Workstation/Player in order to replay some of my old games but initially had some problems getting the sound to run properly.

[www.easyvmx.com](www.easyvmx.com) is one of the easiest ways to get the virtual machine set up.  

If you use Ensonic ES1371 support for sound then you need to install some PCI drivers in the virtual machine.  When you are booted into Win98SE locate the file SBPCI_WebDrvsV5_12_01.exe on the Creative Labs website ([[COLOR="Blue"]SBPCI_WebDrvsV5_12_01.exe[/COLOR]]("http://ca.creative.com/support/downloads/download2.asp?MainCategory=1&Product=1864&dlcentric=1843&Product_Name=Sound+Blaster+PCI+128&filetype=1&OSName=Windows+98SE")).  Also download eapci8m.ecw.  This is the 8m waveset and is much better than the default 2m waveset.

Copy eapci8m.ecw to c:\windows\system\   then Install SBPCI_WebDrvsV5_12_01.exe.  Restart and let the hardware wizard do its thing.  Next, go to the device manager (right click my computer -> properties) and find the area for sound.  Go to SB PCI(WDM) and change the Midi Synthesizer Waveset to 8mb GM/GS Waveset ver 5.  Things should work now.  You may need to 
add the lines -

pciSound.DAC1InterruptsPerSec = 0
pciSound.DAC2InterruptsPerSec = 0

to your windows 98.vmx file if the sound is way to fast or runs high pitched.  Anyhow, you need these sound drivers if you want to have proper sound in your games.  I initially tried the SB16 drivers but was getting a lot of popping and hissing.  I hope that this all works for you.

---

### Post by Damiel on 2007-04-03
Thanks! Sound is fine now on my win98 vm.

---

### Post by oarion7 on 2008-06-17
Worked for me too! Thanks!

---

