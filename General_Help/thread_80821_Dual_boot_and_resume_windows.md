---
title: "Dual boot and resume windows"
date: 2005-10-23
forum: General Help
---

### Post by erland on 2005-10-23
I am running Ubuntu in a dualboot configuration with XP and inside XP I'am also running the same Ubuntu installation inside coLinux. The ubuntu running inside coLinux in XP is the same ubuntu partition as the dualboot partition for ubuntu.

My problem is the following:

When I am running XP and hibernates the computer, it will hibernate both XP and coLinux(with ubuntu inside). When the computer starts again and I get the boot menu and selects to boot Ubuntu the problem starts. The reason is that in this situation there is a hibernated copy of ubuntu(coLinux) in the XP partition and now when I boot Ubuntu from the boot menu is boots and everything looks fine. The problem is in the next reboot when I choose XP in the boot menu. The situation then is that it resumes the ubuntu(coLinux) from the previously hibernated copy on the XP partition. This is of course not a good idea since the ubuntu partition probably have been modified because the computer was dualbooted into ubuntu inbetween the hiberante and resume of XP. I actually tried this senario once and the result was a broken ubuntu ext3 filesystem with a lot of lost files and directories.

One solution is of course to remember to never dualboot into ubuntu if I hibernated XP and always make sure I really shutdown XP. But I would like a way to make sure I don't do this misstake again. I can see two possible solutions, but I have no idea if it is possible to configure it this way.

Solution 1: Configure GRUB in some way so it does not show the GRUB menu if XP has been hibernated and instead just resumes XP. The GRUB menu should only be shown if XP has been shutdown/restarted completely.

Solution 2: Configure coLinux in some way so it shuts down when I hit the hibernate button inside XP.

Does anyone know how to configure this and if it is even possible ?

---

### Post by Pigmudgeon on 2005-10-24
You got Ubuntu running in coLinux?

How did you do that? Please!

--p!

---

### Post by erland on 2005-10-24
[QUOTE=Pigmudgeon]You got Ubuntu running in coLinux?

How did you do that? Please!
[/QUOTE]
I wrote down a brief description of the setup in [http://ubuntuforums.org/showthread.php?p=439988]("http://ubuntuforums.org/showthread.php?p=439988")

---

### Post by Jadd on 2007-08-25
Solution 3: disable hibernation.

---

### Post by dyfrgi on 2008-03-13
Yes, there is. The Windows bootloader will automatically start Windows if it's hibernated - it does some detection of hiberfil.sys. So, if you use the Windows bootloader and load Grub from there, you'll never see the Grub menu unless Windows isn't hibernated!

To do so, you'll first need to load grub onto your boot or root partition. I use a separate boot partition, so it's:
grub-install /dev/sda1

Next, you need to pull grub off there so that you can hand it to Windows. Sadly, the Windows bootloader doesn't do chainloading, so you need to actually give it a file to load!

dd if=/dev/sda1 bs=512 count=1 of=boot.lnx

Copy boot.lnx to c:\ or some other convenient location in Windows.

Next, you'll need to edit the Windows bootloader's configuration. You can get there by right-clicking on My Computer, Properties, Advanced tab, Startup and Recovery -> Settings, Edit. Add a line in the Operating Systems section like this one:

c:\boot.lnx="Ubuntu"

Next, you'll need to get the Windows bootloader back into the MBR! fdisk /fixmbr will do this for you. When you reboot, you should see the Windows bootloader menu pop up with two options, one for Windows and one for Ubuntu. If you select the Ubuntu option, you should get into Grub. If you're coming out of hibernation, though, it'll go straight into Windows.

I actually find this rather annoying, so if you know how to make the Windows bootloader not do this, please let me know. I'm keeping the Windows bootloader since it's supposed to work better with the funky MediaDirect shadow bootloader that Dell uses.

---

