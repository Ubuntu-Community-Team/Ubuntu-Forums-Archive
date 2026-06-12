---
title: "Netgear WG511 in Dapper, Help!!!"
date: 2006-07-31
forum: General Help
---

### Post by vijirajan on 2006-07-31
I am trying to setup Dapper on a Dell Inspiron 8100 with Netgear WG511 wireless card. Dapper recognizes this card as Intersil Prism ISL3890  and loads prism54 driver but I couldn't connect to internet at all. I am trying to connect to my home network which has WPA enabled.

Can somebody point me to a HOW-TO on how to setup this card correctly in Dapper? Any help on this would be greatly appreciated.

Thanks,
Rajan

---

### Post by tim- on 2006-07-31
you need to follow this guide [http://www.ubuntuforums.org/showthread.php?t=156228](http://www.ubuntuforums.org/showthread.php?t=156228)

i have a wg511 too and this quide got me up and running perfectly :)  you will prolly have a newer card which doesn't use the prism54 driver, you must use the smc windows xp driver with ndiswrapper

good luck with it

---

### Post by grozny on 2007-02-02
hi,
absoultlly new so will need some help from you guys. After several tries i am about to give up on that wg511 card. i thought this
[ instruction ]("http://www.ubuntuforums.org/showthread.php?t=156228") posted by tim-

 will end my misery but it didn't. it went quite nice till _sudo modprobe ndiswrapper_ i receive the error msg and my computer and ubuntu freeze.

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

could some1 help and navigate me [hold my hand] :]

Thanks

---

### Post by phossal on 2007-02-03
Have you installed ndiswrapper yet?

---

### Post by grozny on 2007-02-03
the commands i went through so far!

sudo modprobe -r prism54

sudo gedit /etc/modprobe.d/blacklist

i've add the code

# this part is for the netgear wg511
blacklist prism54
blacklist islsm_pci
blacklist islusb
blacklist isl3886

sudo apt-get update
sudo apt-get install ndiswrapper-utils

cd /home/user$/WG511
sudo ndiswrapper -i netwg511.inf

sudo ndiswrapper -l

Installed ndis drivers:
netwg511                driver present, hardware present

and all the respond till that moment was fine
till .....sudo modprobe ndiswrapper 

this is where error appears

---

### Post by phxcxh on 2007-02-10
I got my card running my trying the following...please note, these are Edgy instructions (which I'm using), beforehand I also received the same error message when I modprobe ndiswrapper

    * Install ndiswrapper and drivers (due to a bug in Edgy, you need to specify ndiswrapper-utils-1.8) 

sudo apt-get install ndiswrapper-utils-1.8
sudo ndiswrapper -i /location_of_your_wireless_driver/your_driver.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper

    * Set ndiswrapper to load on startup 

sudo ndiswrapper -m
gksudo gedit /etc/modules

    * Add the following module to the list 

ndiswrapper

    * Now you can configure your wireless card with ifconfig and iwconfig. 

    e.g. Supposing wlan0 is your wireless device. 

sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed
iwconfig

    * You sould now be able to see the MAC address of the access point and signal rate. 


I'll try to insert the link here[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

---

