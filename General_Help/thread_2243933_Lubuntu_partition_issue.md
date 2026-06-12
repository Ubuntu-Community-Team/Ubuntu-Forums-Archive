---
title: "Lubuntu partition issue"
date: 2014-09-12
forum: General Help
---

### Post by simonf2 on 2014-09-12
Hello

I am trying to install Lubuntu on an Asus Eeepc that is presently running Elementary OS quite happily.  I want to install Lubuntu over EOS but I get so far and it says the partition is not big enough.  I should stress I have little understanding of what to do with partitions.  I tried to alter the size and it says that I need to save changes to a disc which I cannot do.  Is there any help that anyone can offer on what I should do.  Please note I am not a technical person!

Thanks

simonf:confused::confused::confused:

---

### Post by Impavidus on 2014-09-12
Describe your hardware. What hard disks/SSDs are present? Run```
sudo fdisk -l
```from the live disk and post the output. Some other information on the hardware may be useful too. Ram, CPU, just to catch possible complications.

---

### Post by simonf2 on 2014-09-12
Thanks for the post but I am not a Linux user so feel a bit challenged with the suggestions.  For example, there is no obvious way of getting to the command prompt (if that is what it is called in Linux) although there probably is if you know what to do.

The netbook came to me with XP but was very slow.  I loaded EOS (overwrote XP) and that was ok but as I want to run Ubuntu on my laptop I thought Lubuntu would be good to use on netbook.  It has an Intel Atom processor, 20 GB SSD and 1 GB DDR2 so it should be ok.

Is there any way I can just get rid of all the partitions and then start again?

---

### Post by yancek on 2014-09-12
It is usually referred to as a terminal or konsole.  Look in the Menu on Elementary when it is booted for either term.  If you find it and can open it, type the command suggested and post the output.  Usually there is a menu icon, often in the lower left of the Desktop.  I've never used Elementary so can't be more specific.

---

### Post by Impavidus on 2014-09-12
If it only has a 20GB SSD, then installing automatically (as in, wipe the drive and install Lubuntu as the only system) should give decent results. 1GB ram is enough for Lubuntu.

---

### Post by Dennis N on 2014-09-12
If you want Lubuntu to be the only operating system on the laptop, then in the first "Installation Type" screen in the installer, select the option which replaces the existing operating system. This should wipe out any existing disk contents and create a new partition table with the necessary partitions for Lubuntu. Do not choose side-by-side.

---

### Post by simonf2 on 2014-09-13
Thanks for the posts but as mentioned, when I tried to wipe the existing system by choosing the appropriate option on the installer, it gave me the error messages regarding partitions.  In frustration I ran it again and selected the side by side installation and this worked.  I freely admit to being non-technical but with Windows I have always muddled through and found solutions.  Here I am struggling to say the least.  I now have in effect a dual boot although it goes into Lubuntu by default.  I would like to now uninstall EOS if anyone can guide me on this ...

---

### Post by yancek on 2014-09-13
EOS is an operating system so you don't "uninstall" it the way you would an application.  Do you now have EOS and Lubuntu installed?  If you installed Lubuntu and accepted the default the fact that it boots Lubuntu by default is expected behavior.  Of course it can be changed.  Boot Lubuntu and open a terminal and run command suggested by impavidus above and post the output.  While you are in the terminal run this command also?  df -h

Post the output of both commands.

---

### Post by simonf2 on 2014-09-14
I cannot simply copy and paste the output and after some delving around leant about pastebinit but I cannot get this to work either.  I  am grateful for the posts but I am giving up before this netbook causes a divorce.  I will reinstall the original Asus software then reinstall Lubuntu and see what happens.  Thanks again

---

