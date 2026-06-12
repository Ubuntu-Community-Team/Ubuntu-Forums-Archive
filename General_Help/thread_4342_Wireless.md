---
title: "Wireless"
date: 2004-11-14
forum: General Help
---

### Post by spirospr on 2004-11-14
I am trying to make my Dell true mobile wireless card to work. The card is based on a  Broadcom  BCM94306 802.11g chip. I have found other people who made it work with the same chip but i can't.  I'm doing the following :

1. install ndiswrapper utilities with no problems
2. install the windows drivers of my card (sudo ndiswrapper -i bcmwl5.inf)
3. i check if the driver is installed ( ndiswrapper -l) and it is installed
4. i write : sudo modprobe ndiswrapper
4. i make a new wireless network connection by writing "wlan0" in device
 
but when i write : sudo ifup wlan0 
i get the message that there is no such device.

After some research i found that for Dell's adding this during boot up : [COLOR=DarkRed]acpi_irq_isa=7[/COLOR] fix some known problems of Dell  wireless card and sound.

Does anyone have any idea how to add this ?????


I have no idea where to put it so that it loads during boot up.

---

### Post by randy on 2004-11-14
You need to create a network configuration to use ifup and ifdown.  To get around this you can use the following commands if you use dhcp.  

     ifconfig wlan0 up
     dhclient wlan0

To create a network config your probably best off using gnome-system-tools.

---

### Post by spirospr on 2004-11-14
well i tried that but i got the response that there is no such device.........

---

### Post by spirospr on 2004-11-14
Well i have tried everything to make my wireless card to work. For right now i have two questions :

1. Where do i have to put this "[COLOR=Red]acpi_irq_isa=7[/COLOR]" 
after some research lot of people solved same problems with me , by adding this in some file to load during start up

2. Is there any chance that my wireless card is set up sth different than "wla0" after installing drivers with ndiswrapper? How can i check if it called sth else?

Please help me i'm almost desperate for a solution.....

Thank you

---

### Post by Razvan on 2004-11-14
acpi_irq_isa=7 goes to the kernel options in your bootloader.

-restart your computer
-wait till it says "bootin<whatever>, press esc to view grub menu" or shows the grub menu
-in the grub menu, press a arrow-key to stop it from booting
-now look what it says there must be some key to edit the boot options, press thet key and add your acpi_irq_isa=7


...this is only how to get that acpi_irq_isa=7 in there...dunno if it helps or somethin'

---

