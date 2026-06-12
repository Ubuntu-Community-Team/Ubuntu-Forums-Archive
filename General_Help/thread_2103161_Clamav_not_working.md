---
title: "Clamav not working"
date: 2013-01-09
forum: General Help
---

### Post by lumaja on 2013-01-09
Seems that Clamav doesn’t update antivirus definition since 30-August-2012
 

 G41M-Combo:~$ freshclam 
 ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!). 
 ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log). G41M-G41M-Combo:~$
 

 [SIZE=5]**?**[/SIZE]         GUI version    4.44
 [SIZE=5]**V**[/SIZE]    Antivirus definition    Current
 [SIZE=5]V[/SIZE]    Antivirus engine     0.97.6
 

 How to fix this.

---

### Post by Frogs Hair on 2013-01-09
I found quote below in the software center comments under clam although I have not used clam since 9.10 and can't test it. The Ubuntu community documentation is refers to 10.04. [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

> Update can be done with two words

I'm not sure anyone mentioned it, but you can easily update Clam from the terminal with the command sudo freshclam.  That's it - two words.  No dark magic, no begging for scraps from the intelligentsia.  I'm doing it right now and yes, I'm one of the "There's no reason not have a GUI option" folks.  If there is, I'd like to hear it.

FAQ:[http://www.clamav.net/lang/en/faq/faq-cvd/](http://www.clamav.net/lang/en/faq/faq-cvd/)

---

### Post by BBQdave on 2013-01-09
> **lumaja said:**
> Seems that Clamav doesn’t update antivirus definition since 30-August-2012...

[**Clam AntiVirus**]("http://www.clamav.net/lang/en/") has nothing on there home page about update stoppage?

You are perhaps already aware of this, but Clam AV seeks and identifies Window's viruses. It is to protect Window's machines and your friends' with Window's machines. Your Ubuntu system has security measures in place, and Ubuntu does not use Clam AV for security :)

---

### Post by ajgreeny on 2013-01-09
Why do you believe that the virus signatures have not been updated since Aug 2012?  There is no information in your post to suggest any real problem, and if you installed clamav in the usual way from the repos, it will be setup to download new signatures regularly, daily I think, by running freshclam at boot.

You certainly can not run freshclam as a normal user as you seem to have tried to do, and as BBQdave says, it only finds windows viruses anyway, so I don't bother with a virus checker, and haven't for many years now, but I am not dual booting with windows.

---

### Post by lumaja on 2013-01-10
Thank you all who answered.
 My OS is Ubuntu 12.04 LTS and I am not dual booting.
 New with Ubuntu and Clamav. Dint know it was for Windows.  
 I come from windows in Ubuntu never seen any information on Clamav updating I thought it never did.
 I do online banking with Windows and my bank insists I should have Rapport for security, I want
 to move online banking into Ubuntu I been searching for banking security like Trojans, Spyware, Adware, Phishing and others to be secure. [SIZE=4]**Please advise on this one.**[/SIZE]
 [SIZE=3]In Clamav scanning history seen two reports with FOUND and PUA mention, don’t know how to read[/SIZE]
 [SIZE=3]this, notice that found 1558489 virus I ask your kind people for assistance of what it means. (report follows sorry to be so long) .[/SIZE]
 [SIZE=3]Appreciate any good help and in advance Thank you.[/SIZE]
 

 /home/Videos/My Videos/SaveAs.exe: PUA.Win32.Packer.SetupExeSection FOUND 
 /home/Videos/Videos to Download/The Green Mile: PUA.Win32.Packer.SetupExeSection FOUND 
 /home/My Videos/SaveAs.exe: PUA.Win32.Packer.SetupExeSection FOUND 
 /home/.wine/drive_c/windows/Installer/116f.msi: PUA.Win32.Packer.MsVisualCpp-3 FOUND 
 /home/.wine/drive_c/windows/Installer/13ab.msi: PUA.Win32.Packer.MsVisualCpp-3 FOUND 
 /home/wine/drive_c/users /Temp/msi1a4a.tmp: PUA.Win32.Packer.MsVisualCpp-3 FOUND 
 /home/My Pictures From XP/Removable Disk (E)/AVAST (AntiVirus)/setupeng.exe: PUA.Win32.Packer.Upx-28 FOUND 
 /home/My Pictures From XP/Removable Disk (E)/setupeng.exe: PUA.Win32.Packer.Upx-28 FOUND 
 /home/My Pictures From XP/My Pictures/Removable Disk (E)/AVAST (AntiVirus)/setupeng.exe: PUA.Win32.Packer.Upx-28 FOUND 
 /home/My Pictures From XP/My Pictures/Removable Disk (E)/setupeng.exe: PUA.Win32.Packer.Upx-28 FOUND 
 /home/Cannon- ALL/IB5[1].8-EN.PDF: PUA.Script.PDF.EmbeddedJS-1 FOUND 
 /home/Cannon- ALL/AdbeRdr70_enu_full.exe: PUA.Win32.Packer.Upx-28 FOUND 
 /home/Documents/My Documents/IMPORT_BANK/OTHERS/Product Comparison - At a glance.mht: PUA.Script.Packed-2 FOUND 
 /home/Documents/My Documents/IMPORT_BANK/OTHERS/Internet Access - ADSL - What Is It.mht: PUA.Script.Packed-2 FOUND 
 /home/Documents/My Documents/IMPORT_BANK/OTHERS/registryfix.exe: PUA.Win32.Packer.InnoInstallerCo-1 FOUND 
 /home/Windows Data/kyo2006.zip: PUA.Win32.Packer.InnoInstallerCo-1 FOUND 
 /home/Private from Windows/IMPORT_BANK/OTHERS/Product Comparison - At a glance.mht: PUA.Script.Packed-2 FOUND 
 /home /Private from Windows/IMPORT_BANK/OTHERS/Internet Access - ADSL - What Is It.mht: PUA.Script.Packed-2 FOUND 
 /home /Private from Windows/IMPORT_BANK/OTHERS/registryfix.exe: PUA.Win32.Packer.InnoInstallerCo-1 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/1/96/32A84d01: PUA.Phishing.Bank FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/1/24/B1079d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/E/E9/7C899d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/E/66/C2A35d01: PUA.JS.Obfus-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/6/37/E9B06d01: PUA.JS.Xored FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/6/58/30782d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/6/2C/905B7d01: PUA.Phishing.Bank FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/A/EE/BAA0Ed01: PUA.Script.Packed-1 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/4/69/00D58d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/F/52/D6EFBd01: PUA.Phishing.Bank FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/F/64/157DFd01: PUA.Script.Packed-1 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/F/0B/4D793d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/F/0E/1F8A9d01: PUA.Script.Packed-1 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/F/E7/DC040d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/5/EE/76609d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/5/70/4A84Dd01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/7/5F/E0B10d01: PUA.Script.Packed-1 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/D/3D/47951d01: PUA.JS.Xored FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/B/7B/D706Bd01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/B/E7/FDEB8d01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/B/BE/1D0EAd01: PUA.Script.Packed-2 FOUND 
 /home /.mozilla/firefox/y4x1b7jq.default/Cache/B/31/98CE8d01: PUA.Script.Packed-1 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.bin-le.cpioaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.odc.cpioaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.exe.binhexaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam-mew.exeaa: PUA.Packed.MEW-1 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.exe.mbox.base64aa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam-petite.exeaa: PUA.Win32.Packer.Petite-26 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.newc.cpioaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam-upack.exeaa: PUA.Packed.UPack-2 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam-aspack.exeaa: PUA.Win32.Packer.Asprotect-2 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.exe.htmlaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.bin-be.cpioaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam_IScab_int.exeaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam_IScab_ext.exeaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam-pespin.exeaa: PUA.Packed.PESpin FOUND 
 /home /Desktop/clamav-0.97.6/test/.split/split.clam.exeaa: PUA.Win32.Packer.PrivateExeProte-15 FOUND 
 /home /Other Documents/kyo2006.zip: PUA.Win32.Packer.InnoInstallerCo-1 FOUND 
  
 ----------- SCAN SUMMARY ----------- 
 Known viruses: 1558489 
 Engine version: 0.97.6 
 Scanned directories: 5653 
 Scanned files: 29327 
 Infected files: 57 
 Data scanned: 4120.57 MB 
 Data read: 54024.54 MB (ratio 0.08:1) 
 [SIZE=3]Time: 835.942 sec (13 m 55 s)[/SIZE]

---

### Post by lisati on 2013-01-10
> **lumaja said:**
> Seems that Clamav doesn’t update antivirus definition since 30-August-2012
 

 G41M-Combo:~$ freshclam 
 ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!). 
 ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log). G41M-G41M-Combo:~$
 


Simple:
```
**sudo** freshclam
```

---

### Post by lumaja on 2013-01-10
I forgot to add something else to my lost reply, when I shut down computer an black screen
 opens and as some text the first line is about Clamav and pipe broken I can't read everything
 because is to fast and black screen goes off, I ask this forum how to keep the screen open to read it but never gave me an answer.
 

 Now I did “sudo freshclam” not sure but looks like the results are positive but still want
 to know what should I get to be secure while banking and what is  all virus on the report
 that I send before.
 

 Thank you lisati for your answer, result follows is this how should Clamav look like?
   
 -G41M-Combo:~$ sudo freshclam 
 [sudo] password for luis:  
 ClamAV update process started at Thu Jan 10 13:35:13 2013 
 main.cvd is up to date (version: 54, sigs: 1044387, f-level: 60, builder: sven) 
 daily.cld is up to date (version: 16457, sigs: 530720, f-level: 63, builder: neo) 
 bytecode.cld is up to date (version: 209, sigs: 40, f-level: 63, builder: neo) 
 -G41M-Combo:~$

---

### Post by munkee on 2013-07-13
I have noticed that ClamAV is not updating due to it not finding a log file.  Following the file path "/var/log/clamav/freshclam.log", there no log file there to write/append to.  I would imagine this would be created when ClamAV is initially installed.  

I'm having a stab at fixing this as I'm writing this post btw.

Right this is what I've done. All the terminal commands are in quote marks.


[LIST=1]
[*] In "Terminal"  I've typed "sudo -i" to put me into root user access. 
[*] Type cd / to knock back into the root directory. 
[*] Type "mkdir /var/log/clamav" to create the log directory for ClamAV 
[*] Type "gedit /var/log/clamav/freshclam.log"  (other text editors are available), to create a dummy log file. I entered the line "#ClamAV Dummy" then save and close it. 
[*] Type "chmod 777 gedit /var/log/clamav/freshclam.log".   This might be a bit contentous, the permissions I've used might be set too low.  Any guidence on the correct permission levels would be greatly appreciated. 
[*] Type "sudo freshclam -v" and after trying to hit several servers the latest anti-virus pattern files should download. 
[*] Type "sudo freshclam -v" again, and should confirm the latest are downloaded. 
[*] Type "exit" to put you back to normal user level. 
[/LIST]

I'm going to test further to see if freshclam carries out the updates during the week.  I'll update this post to properly confirm if this workaround is successful or not.

---

### Post by dean-westray on 2013-08-21
_**Update!!!**_
I found why ClamAV was not updating in my case.  This may apply if you are using a SDD as a boot/app drive.  When I initially set up my machine, I did a tweak to the fstab file to create a temporary file space (or RAM disk) for /var/log (as below).

[COLOR=#0000FF]tmpfs      /var/log        tmpfs      defaults,noatime        0    0[/COLOR]

When you run freshclam it will save the log file to the temporary file space in RAM.   Once you reboot the log file is lost.   If you have added this line in your fstab file, you will need to remove it for freshclam to update ClamAV properly.

I have tested this now for a week and I have had no further issues with missing/unwritable log files when freshclam runs.

For further SDD config info check this site:  [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

