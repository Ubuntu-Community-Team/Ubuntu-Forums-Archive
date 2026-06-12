---
title: "fn Keys not working? This may help!"
date: 2014-04-22
forum: General Help
---

### Post by KitsuneAkki on 2014-04-22
I own an **Asus Eee PC 1011PX** Successfully running Kubuntu. Ubuntu. Linux Mint 16.

I have done several updates and hardware upgrades with little to no  hassle at all! Even updated the bios, installed SSD, upgraded the WiFi  card to a 300 mbps + BT 4.0 card.

The ONLY issues I have had was with the **fn keys**, but after furiously fighting  with acpi and grub, I found out that most laptops with any debian  install will have issues with acpi events and **fn keys** if the **SATA** Hard Drive options in the **BIOS** are set to **AHCI** instead of **IDE**.

Setting it as **IDE** will resolve many **ACPI** issues as well as the **fn** + **F1** - **F12** keys not functioning correctly.
As well as the WiFi on off fn key, or scr lk or other...
( I have seen so many forums and blogs flooded with questions and solutions that are workarounds as best! )

Re-mapping the keys will not work, as the machine will not allow the hardware key press to be recognized or even be seen by probing tools such as **xev**.
Only by doing the above, did the hardware respond to key presses, and show the codes in **xev**

Once they start responding normally after a reboot, and you have checked that they work, then you could remap them to your heart's desire...

Hope this helps?!

---

