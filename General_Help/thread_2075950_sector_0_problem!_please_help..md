---
title: "sector 0 problem! please help."
date: 2012-10-25
forum: General Help
---

### Post by DrAlbert on 2012-10-25
Hi! 
I  installed kubuntu. Recently the computer won't load the OS automatically when i power it on.
If i want to start, i have to press F12 (the key for showing boot option in bios) to enter the Boot Menu and select the Hard Drive specifically and then grub2 will start and kubuntu boot and work perfectly fine.
I checked that in the BIOS the Hard Drive is selected as the first boot device. my kubuntu booted fine before until i wanted to use a live backtrack 5 live cd after that these strang things happenned. i had this problem before and I had to erase all of my partition and repartitioning. after that my problem solved.
So my question is how do i get kubuntu to boot automatically without having to go into the boot menu every time i turn on my computer?
When i push the power button, the computer posts, loads the BIOS and then sits with a black screen with a flashing white underscore cursor.
If I let it sit like this, nothing changes and it unresponsive to any input. I does not give any error messages or beeps to indicate anything is wrong, it just fails to boot kubuntu on it's own.
so I think something happened to my partition table or mbr or something like it that bios can't load grub automaticcally. but I don't understand why when i press f12 during bios startup i can boot!

---

### Post by oldfred on 2012-10-25
If you are using f12 to select same drive as BIOS has as first drive that is very strange. When you changed drive in BIOS are you sure you saved updates. And is system old and battery depleted. You should also notice time issues if battery is an issue.

Just to see if booting looks ok.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

