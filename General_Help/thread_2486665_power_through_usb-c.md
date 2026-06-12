---
title: "power through usb-c"
date: 2023-05-08
forum: General Help
---

### Post by matrooswolf on 2023-05-08
Hi, 
Does anybody knows how to power the computer through USB c? It should be possible under windows, but I'm not sure if it works under Ubuntu. I've tried it, but it doesn't charge, but I don't know if a certain setting is needed or if the charger is strong enough, I don't know anything about ampere etc...

If anybody knows if it is possible and how to check it, or what is needed, I would be grateful.

(Laptop I'm using: Lenovo Ideapad 3 Ryzen 7 16GB 512GB)

---

### Post by TheFu on 2023-05-08
All USB ports aren't created equal.

Power is controlled by the hardware and firmware it runs.

If there is a separate power connector for the computer, then that is almost always the **only way** to provide it power/charging.  Google found this article: [https://www.pcmag.com/how-to/how-to-charge-your-laptop-with-usb-c-your-questions-answered](https://www.pcmag.com/how-to/how-to-charge-your-laptop-with-usb-c-your-questions-answered)  which tries to explain.

---

### Post by MAFoElffen on 2023-05-08
[quote=TheFu]"If there is a separate power connector for the computer, then that is almost always the **only way** to provide it power/charging."[/quote]
+1 with TheFu.

No.

It is not possible to power the device via the USB-C port. As per Lenovo. Even when it is connected to the Ultra Dock, it has a power cable going from the dock to the power connection of the device.
Re:
[https://psref.lenovo.com/syspool/Sys/PDF/IdeaPad/IdeaPad_3_15ALC6/IdeaPad_3_15ALC6_Spec.pdf](https://psref.lenovo.com/syspool/Sys/PDF/IdeaPad/IdeaPad_3_15ALC6/IdeaPad_3_15ALC6_Spec.pdf)
[https://download.lenovo.com/pccbbs/options/tp_usb3_ultra_dock_pro_dock_sp40h10911_en.pdf](https://download.lenovo.com/pccbbs/options/tp_usb3_ultra_dock_pro_dock_sp40h10911_en.pdf)

---

### Post by grahammechanical on 2023-05-08
> It should be possible under windows, but I'm not sure if it works under Ubuntu.

As indicated in the above post the ability to charge using USB-C is independent of the OS. Does the machine have a dedicated power port and a charger that plus into that port? Then I would guess that USB-C cannot be used to charge the machine. To charge the machine through a USB-C port then that port must be designated a "Thunderbolt" and have the downward pointing jagged lightning arrow logo alongside it.The supplier should specify that the machine is charged through USB-C (Thunderbolt) and should provide an AC charger that has an USB-C Thunderbolt connector.

The USB-C Thunderbolt port is a different shape to the usual USB-C port. There are USB-C cables that have a connector that will fit a thunderbolt port but they cannot be used to charge the machine. These particular cables can be use for high speed data transfer and for powering a connected USB device but not for powering the machine.

I nearly purchased a laptop with thunderbolt ports. The specification of both products that I reviewed it was stated "Ports: 1xUSB Type C (power)" in the case of one machine and Thunderbolt 4 USB-C port with the comment "charges via USB-C port"

If you do not have any information like that for your machine, then I would suggest that you cannot use USB-C to charge the machine.

Regards

---

### Post by MAFoElffen on 2023-05-08
I should say as an aside to other Users reading this, with other kinds of devices... Who may come upon this thread later...

Dell has some devices that do power through USB-C, with 60 to 120 amp USB-C power supplies, but the OP's Lenovo IdeaPad 3 is not designed to be powered through a USB-C connection. Lenovo has their own proprietary power connection for their devices.

I know, in that I had to replace these power ports occasionally as a Certified Onsite Lenovo, Dell, and HP Warranty Repairs Technician.

* And Lenovo does have "Tablets", that do power through USB-C (alibi), but this device is a Laptop, not a Tablet.

---

### Post by matrooswolf on 2023-05-09
Thanks everybody,

I thought all usb-c could be powered by usb, but apparently not. And the Lenovo I have has only usb-c data transfer. So, only regular power charger for me...

Thanks!

---

