---
title: "Wireless HP card doesn't work. Help me please."
date: 2020-06-01
forum: General Help
---

### Post by camilob on 2020-06-01
Hello there,


I just installed an HP FH971AA wireless card in my HP Elite 8100 computer running Ubuntu 20.04. I can perfectly see my Wi-Fi network and all the nearby networks but I cannot connect to it, despite having tried different alternatives in the settings. I need help urgently and will appreciate any hints.

The specs of the card on the following link:

[https://h10057.www1.hp.com/ecomcat/hpcatalog/specs/provisioner/05/FH971AA.htm](https://h10057.www1.hp.com/ecomcat/hpcatalog/specs/provisioner/05/FH971AA.htm)

 Thanks a lot!

---

### Post by MoebusNet on 2020-06-05
Since no one else has pitched in, maybe I ca get you started. My first reaction when you mentioned upgrading an HP system was 'the dreaded HP whitelist issue'. HP, before about 2013, wouldn't allow any but HP parts like wifi cards to be added to their systems. They enforced this by a 'whitelist' of cards allowed to operate by their system's BIOS.  The most common recommendation I've read from people who have those afflicted systems is to use an external USB wifi adapter.

Since you say you can see wireless networks nearby, the HP card you got may (maybe not) be an approved card that will work with your system. Having said all that, if you believe you have the proper HP-approved wifi card for your system, the best thing to do is to go to the 'Networking & Wireless' part of the forum, read the sticky about 'Before posting in Network & Wireless', follow the directions and open a thread there. Chili555 knows his stuff, but you need to pay attention and provide the information he asks for promptly.

---

### Post by grahammechanical on 2020-06-05
Tell us about the WiFi router/hub. There should be some instructions that tell you how to connect to it from the Windows operating system. They are not much use to a Linux user but they contain some useful information. My router came with a sticker that had the following information:

Router Address; Router user; Router Password; Wireless name (this might be the name of the ISP if the router was purchased as part of the contract with the ISP): and the Wireless key.

The wireless key is important. It is also known as WPA-PSK key. You may also need to know the level of encryption.

In Ubuntu we open Systems Settings and choose WiFi. We select our WiFi network and open a settings dialog and then open the Security tab. From the drop down menu of the Security panel we select a security/encryption level. It could be WPA & WPA2 Personal. We then enter a password. This is not our Ubuntu password but that wireless/WPA-PSK key. We then click apply.

Have you tried any of this?

Regards.

---

### Post by camilob on 2020-06-07
Thanks MoebusNet & grahammechanical for your responses.

At the end, I' ve installed windows 10 in the HP machine and the card (a genuine HP wireless card) are working perfect. May be it is not in the w list mentioned above. Anyway, I can use an external usb card (Tplink) in order to use the HP machine with Linux.

Cheers...

---

### Post by MoebusNet on 2020-06-08
One last thing then - if you want to install Ubuntu in the future (ie, dual-boot with Windows), i would recommend checking to see if there is an update available to your BIOS firmware. It may be that the whitelist has been updated to include newer wifi cards in a newer version of your BIOS firmware. As an example, my antique Dell notebook was unable to boot from USB until I updated the BIOS firmware to gain that capability. Do your homework, follow the directions and decide if that is what you want to do. Worked for me!

---

