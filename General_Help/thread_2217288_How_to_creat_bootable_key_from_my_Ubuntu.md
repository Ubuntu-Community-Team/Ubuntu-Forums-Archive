---
title: "How to creat bootable key from my Ubuntu?"
date: 2014-04-16
forum: General Help
---

### Post by M1k4 on 2014-04-16
Hi,
I am so sorry for that <snip> crap questions feeling me sick
But how? :confused:

I thought I didn't need anything so I copy/pasted my fresh installed Ubuntu 13.10 on a key...
and it didn't work (in spite of my computer run key before HDD from BIOS)

I saw that I can need to install multisystem?
But this software isn't present in the logitheque so I installed from softonic... but it requires 2 hours
What's wrong?

---

### Post by oldfred on 2014-04-16
You cannot copy as that is not bootable.

You use tools depending on what system you are currently running.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
      
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
    
There are advanced ways to create bootable flash drives that use grub2 to directly mount an ISO that you copy as an ISO to a flash drive. But you need to be running Linux to install grub to flash drive. There also are scripts which agian most are set up to run in Linux to create multi-boot flash drives.
You also can do a full install to a larger flash drive like any install to an external drive, but need two flash drives, one as installer and the other as the place to install into.

---

