---
title: "Best way to rebuild a broken system"
date: 2022-09-16
forum: General Help
---

### Post by georgesgiralt on 2022-09-16
Hello,
I have a laptop which broke after upgrading to Jammy 22.04.1 LTS. The break is so strange (all sound hardware present and running, no sound system showing in Gnome properties and or panels) that I plan to reinstall the whole system directly in 22.04.1LTS. 
But this system has had a long time use and a lot of software installed and configured. 
So if you had to recreate this system (minus the bug, of course) how would you do it ? 
Backup /etc to retain the various configuration files ? Fill a list of the applications installed including their repo information ? 
Something else ? 
I would be delighted to hear from people having done so  !
Thanks in advance for your insights and help ! 

P.S. : I've put Jammy on a USB stick and updated it to the "same" level of update as the broken system and found that the sound system is running perfectly on the live system. So it is not at all hardware related but it is software configuration or packets miss installed. See : [https://ubuntuforums.org/showthread.php?t=2479085](https://ubuntuforums.org/showthread.php?t=2479085)

---

### Post by vanadium on 2022-09-16
You can reinstall the operating system *without* formatting the system drive. That way, existing data, configuration and installed applications are preserved. Especially if you do such reinstall with the same Ubuntu version, there is a very high chance that this will fully repair your system.

To do that, load the installer from the live USB, in the installer, select "Something else", then manually assign your partition to be used as root (and eventually other partitions if any), and, importantly, *uncheck* "format" so the volume is not reformatted before installation.

---

### Post by georgesgiralt on 2022-09-16
Vanadium; 
Interesting idea. 
You are right it may work if the problem comes from a missing part/packet/configuration file. But if the problem lies in an extra packet wrecking havoc on a functionning system, your method won't solve the problem because it will still be there. 
But I can give it a shot. 
Now I'm making some backups because I do not want to be bitten .....

---

### Post by ActionParsnip on 2022-09-16
Reinstall clean OS
Restore settings and casual user data from backups

---

### Post by mrshadowstreet on 2022-09-16
best way to do so is of course reinstall your system and backup the data
but if you have nothing to lose you can try to handle it in a such way 
[https://www.youtube.com/watch?v=517n8vYqm]("https://www.youtube.com/watch?v=517n8vYqmO0")[O0]("https://royallie.com")
hardest case

---

### Post by guiverc on 2022-09-16
I'll provide a link to the [Understanding the Lubuntu QA testcases]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") which sort of describes what @vanadium was describing...  Lubuntu uses it in their QA; search for "*Install using existing partition*"

Note:  The install type takes note of your installed packages; erase system directories -- thus package problems, erased system files etc, are dealt with, as the *manually installed* packages get auto-reinstalled (*if internet exists during installation*)... I think I use `clementine` or a music player as example, as it's not a default package for Lubuntu - thus it's one of the packages I look for post-install to ensure it's re-installed; & I have my music playlist & files present as I continue validating the install when I perform it ~weekly.

What it won't fix; is **USER CONFIGURATION issues**; as user configs are stored in $HOME or your user directory - and this install type doesn't touch anything in $HOME; thus those problems will survive... but package problems are fixed.

It's only tested with Ubuntu repository software.. so if you've loads of **3rd party packages**; those are not QA-tested by Ubuntu (*or flavors like Lubuntu*)... but the install type works with** all *flavors* of Ubuntu too, plus main Ubuntu Desktop**.

**If your system is a server; as system directories are wiped prior to re-install; server app configs can be lost.**.. it's really a desktop re-install (*repair it used to be called; the canary installer is likely to offer it again; though it's not working yet last I checked*)..

There can be complications if re-installing an older release... but it does allow changing release (going forward, re-install of same release, or backward) but complexities can be involved if **not** the same release (*these relate to the programs where data matters to you; so homework is required to ensure a perfect result will occur may need to be performed where a different release** I'm not touching here - package level issues*).

---

### Post by SeijiSensei on 2022-09-16
If you end up reinstalling, I suggest putting /home on a separate partition so your personal information and settings will survive future updates.

During the installation sequence, choose "Manual" from the disk options, then create two partitions, one for the main OS root ("/") and one for all your files ("/home"). Usually the root partition can be about 10-20 GB. I'm running Kubuntu 22.04 on this machine and have 20 GB allocated to the root; only five GB are currently in use. Allocate whatever remains to /home.

---

### Post by TheFu on 2022-09-16
[Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927](Https://ubuntuforums.org/showthread.php?t=2474107&p=14091927#post14091927) is how I do it.

---

### Post by georgesgiralt on 2022-09-17
> **SeijiSensei said:**
> If you end up reinstalling, I suggest putting /home on a separate partition so your personal information and settings will survive future updates.

During the installation sequence, choose "Manual" from the disk options, then create two partitions, one for the main OS root ("/") and one for all your files ("/home"). Usually the root partition can be about 10-20 GB. I'm running Kubuntu 22.04 on this machine and have 20 GB allocated to the root; only five GB are currently in use. Allocate whatever remains to /home.
Thank you for your advice, but as a long time user of LVM (on various Unixes during my work) I've a laptop with LVM and a volume for various things. Sometimes, when I've a HDD and a small NVME os mSata drvie, I use two PV, and the system goes to the NVME or mSata and all the rest lies on the slower HDD. 
On the desktop computer my wife use, there are two disks, software mirrored and the array is the PV of the LVM system. 
Old habits die hard.... 

This night I've made a copy of my setup on the problematic laptop on an external disk. Today, if time permits, I4ll reinstall using the advice given above... 
We'll see what comes out of it...

---

### Post by georgesgiralt on 2022-09-17
> **guiverc said:**
> I'll provide a link to the [Understanding the Lubuntu QA testcases]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") which sort of describes what @vanadium was describing...  Lubuntu uses it in their QA; search for "*Install using existing partition*"

Note:  The install type takes note of your installed packages; erase system directories -- thus package problems, erased system files etc, are dealt with, as the *manually installed* packages get auto-reinstalled (*if internet exists during installation*)... I think I use `clementine` or a music player as example, as it's not a default package for Lubuntu - thus it's one of the packages I look for post-install to ensure it's re-installed; & I have my music playlist & files present as I continue validating the install when I perform it ~weekly.

What it won't fix; is **USER CONFIGURATION issues**; as user configs are stored in $HOME or your user directory - and this install type doesn't touch anything in $HOME; thus those problems will survive... but package problems are fixed.

It's only tested with Ubuntu repository software.. so if you've loads of **3rd party packages**; those are not QA-tested by Ubuntu (*or flavors like Lubuntu*)... but the install type works with** all *flavors* of Ubuntu too, plus main Ubuntu Desktop**.

**If your system is a server; as system directories are wiped prior to re-install; server app configs can be lost.**.. it's really a desktop re-install (*repair it used to be called; the canary installer is likely to offer it again; though it's not working yet last I checked*)..

There can be complications if re-installing an older release... but it does allow changing release (going forward, re-install of same release, or backward) but complexities can be involved if **not** the same release (*these relate to the programs where data matters to you; so homework is required to ensure a perfect result will occur may need to be performed where a different release** I'm not touching here - package level issues*).

Hello again !
Yesterday I thought this was pure magic. 
It seems I was right. 
I tested the process this morning. Installation was straightforward, the longest part being to manually add each filesystem and verify the "format" box was unchecked. 
Installation was fast, thanks for the fast Ethernet link, but after reboot, I was relieved to see I had sound and disappointed that all my apps are gone. Even those which ARE in the standard Ubuntu repos .... 
So the remaining of the day will be spent in adding the apps I need most and trying to remember which one I had I do not use that often. 
Anyway, thanks for your help !

---

### Post by TheFu on 2022-09-17
> **georgesgiralt said:**
> Hello again !
Yesterday I thought this was pure magic. 
It seems I was right. 
I tested the process this morning. Installation was straightforward, the longest part being to manually add each filesystem and verify the "format" box was unchecked. 
Installation was fast, thanks for the fast Ethernet link, but after reboot, I was relieved to see I had sound and disappointed that all my apps are gone. Even those which ARE in the standard Ubuntu repos .... 
So the remaining of the day will be spent in adding the apps I need most and trying to remember which one I had I do not use that often. 
Anyway, thanks for your help !

'apt-mark' will create a list of installed APT applications.  You can ask for the list of manually installed applications, which should be 90% shorter.  I update/include that list as part of my daily backups, since it makes recreating a system after any failure much easier.

---

