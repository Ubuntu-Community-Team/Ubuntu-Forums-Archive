---
title: "LINUX or MS windows DESKTOP ANTI-VIRUS SCAN for android phone"
date: 2020-05-09
forum: General Help
---

### Post by dokbrown2 on 2020-05-09
LINUXor MS windows DESKTOP ANTI-VIRUS SCAN for android phone


isanyone aware of a linux app that can scan android/apple for viruses ?


Ido not want to install anti-virus & slow down my galaxy phone butI do want to make sure it is not compromised.  I am thinking aboutputting  a local firewall on the phone. Any recs ?

---

### Post by dokbrown2 on 2020-05-09
IJUST FOUND THIS, so i assume clamtk scan the phone.  Any other appspeople rec for scanning android phones/tablets ? 
I'mstill looking for a good but light firewall for galaxy/android ???
lbjr

Re: How to scan a cell phone for malware?

[https://ubuntuforums.org/showthread.php?t=1963188&page=2](https://ubuntuforums.org/showthread.php?t=1963188&page=2)

---

### Post by CelticWarrior on 2020-05-09
Only a mobile app can scan mobile phones.

---

### Post by dokbrown2 on 2020-05-21
So there is no way to scan my phone externally from Ubuntu  or windows ?  That seems odd

---

### Post by Holger_Gehrke on 2020-05-21
Not so odd if you think about the fact that Android strictly separates system data and programs from user data. Only the latter is visible when you connect a PC to an Android device. You could of course use ADB (Android Debug Bridge) and pull everything from the device but ADB has to be enabled on the Android device and even if it is Android stays firmly in control of the connection and sufficiently smart malware could take over that control. Add to this that you'd need signature data to scan for and you can see why nobody has written anything like that.

Holger

---

### Post by dokbrown2 on 2020-05-22
bitdefender seems the least intrusive

[https://www.lifewire.com/best-free-antivirus-android-4151993](https://www.lifewire.com/best-free-antivirus-android-4151993)

---

### Post by dokbrown2 on 2020-05-22
> **holger_gehrke said:**
> not so odd if you think about the fact that android strictly separates system data and programs from user data. Only the latter is visible when you connect a pc to an android device. You could of course use adb (android debug bridge) and pull everything from the device but adb has to be enabled on the android device and even if it is android stays firmly in control of the connection and sufficiently smart malware could take over that control. Add to this that you'd need signature data to scan for and you can see why nobody has written anything like that.

Holger


"i see "
):p

---

### Post by SeijiSensei on 2020-05-23
Whenever I install an app on my Android phone, it gets scanned automatically before installation. Other than general and often reasonable paranoia, is there something in particular that concerns you?

Desktop AV scanners look primarily for threats to Windows and, much less commonly, threats to other OSs like MacOS or Linux.  You could look for threats in downloaded files by mounting the phone in Linux and running something like clamscan from the clamav package against the files in the mounted directories. [This article](https://www.trishtech.com/2014/12/using-clamav-antivirus-to-scan-android-storage/) shows how to do this in Windows.

---

