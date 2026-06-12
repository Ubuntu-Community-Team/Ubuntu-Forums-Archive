---
title: "Run exisitng windows install with Vmware player"
date: 2007-04-16
forum: General Help
---

### Post by simonsocial on 2007-04-16
I have been trying to run my existing windows installation with Wmware but i'm finding it very hard to get anywhere.

Using the following instructions : [COLOR="DarkRed"][http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")[/COLOR]

I have downloaded the necessary files but I can't get the information required from my harddrive. My harddrives are SATA, so the question I ask is...

Do I have to do something different with the parted command to get this info? or is NTFG-3 causing me the problem. In the terminal I type: -

[LIST]
[*]sudo parted /dev/sda1
[*]unit s
[*]print (nothing is displayed and it comes up with an error)
[/LIST]

Any info will be helpful, thanks

---

### Post by thelinuxguy on 2007-04-16
Not directly related to your question but if you decide to convert your physical Windows installation into a virtual machine, try out [http://www.howtoforge.com/vmware_converter_windows_linux](http://www.howtoforge.com/vmware_converter_windows_linux)

---

### Post by simonsocial on 2007-04-16
I don't want to convert it or create an image of it.

---

### Post by sirevert on 2007-04-16
use: sudo parted /dev/sda
instead of 
sudo parted /dev/sda1
;) you want the info about the disk not the partition

---

