---
title: "Duplicate entries in grub"
date: 2018-12-08
forum: General Help
---

### Post by manmath on 2018-12-08
Hi All,
I'm running Windows 10 and Kubuntu in a dualboot setup. It's running fine, but a minor problem is, the grub shows 5 entries whereas I've only 1 kernel installed in Kubuntu. So, ideally it should show only 3 entries such as: 1st Kubuntu, 2nd Kubuntu rescue mode, and 3rd Windows 10. Please have a look at the attached files /boot/grub/grub.cfg as well as /etc/default/grub.

Note: I'm running a custom kernel that runs without initram disk.

---

### Post by oldfred on 2018-12-08
You can manage your own grub.cfg if you want.
You turn off the scripts that create the grub.cfg and add your own entries in the 40_custom script.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

I turn off os-prober as I have multiple Ubuntu installs, and do not want it to find my obsolete ones. 
       
 In /etc/default/grub I added this line for os-prober:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub 
    

You can copy the boot stanza's you want into 40_custom. Then turn off the other scripts (execute bit as shown above with chmod). 
Always rerun the sudo update-grub after any changes to update menu.

       From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40) 
   
If you copy boot stanza, you do just must be sure to copy entire stanza.
I typically like to add some of the configuration files, like colors or some other settings as shown in first link above.


General menuentry Construction Rules: The first  must start with menuentry and end with {
[LIST] 
[*]The area between the quotation symbols is what will appear on the GRUB 2 menu. Edit as desired. 
[*]The last  of the menuentry must be } 
[*]Do not leave empty spaces at the end of s 
[*]The set root=  should point to the GRUB 2 /boot location ( sdXY ) 
[*]The root reference in in the linux  should point to the system partition. 
[/LIST]
    o If GRUB 2 cannot find the referenced kernel, try replacing the UUID with the device name (example: /dev/sda6 ).

---

### Post by manmath on 2018-12-09
Thank you! Problem solved.

---

