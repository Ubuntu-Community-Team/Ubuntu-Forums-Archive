---
title: "send and clear a file every 10 run"
date: 2017-08-17
forum: General Help
---

### Post by cazz on 2017-08-17
Hi
Right now I use lubuntu usb boot persistent data to save mac address and the serialnumber of the computer that I going to deploy

That I have done is that I have a script on the desktop on the usb boot that read and save first serialnumber and then read and save mac address to same textfile.

After a while I use another usb that have FAT32 so I move the textfile with the info from lubuntu to the FAT32 usb.

After that I remove the file and start to collect information from other computers.

It works but it take sometime so I'm curious if I can do something better like if it understand that I have use it on 10 pc it send the file to a windows share folder with date and time as the filename

That mean I do not need another USB to move the file and also one person can use lubuntu to read the serialnumber and mac address and the other can use the file to import the information into the deploy system.

---

### Post by aromo2 on 2017-08-18
> [COLOR=#000000]Hi[/COLOR]
[COLOR=#000000]Right now I use lubuntu usb boot persistent data to ...[/COLOR][COLOR=#000000]
As long as you use persistent data on your USB Lubuntu installation, you can achieve the desired result. You just have to include the logic at the end of the script that gathers the serial number and the MAC address of the machine you're running it on.[/COLOR]

---

### Post by cazz on 2017-08-18
Thanks for the replay

yes with a little search here I have found info to put in in a script and got it to work :)

---

