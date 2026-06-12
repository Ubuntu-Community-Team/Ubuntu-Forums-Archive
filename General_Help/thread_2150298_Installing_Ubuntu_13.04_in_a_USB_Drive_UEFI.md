---
title: "Installing Ubuntu 13.04 in a USB Drive UEFI"
date: 2013-05-31
forum: General Help
---

### Post by xtsuname on 2013-05-31
Following the advice of [fantab]("http://ubuntuforums.org/member.php?u=1275004") I am starting a new thread with reference to: 

 [Installing Ubuntu 13.04 to USB HDD for UEFI]("http://ubuntuforums.org/showthread.php?t=2134026")

Background:
I have just bought a USB 3.0 USB Drive
I have a sony Vaio duo 11

Purpose:
I want to install ubuntu on the USB 3.0 USB Drive as I don't have enough space on my 128GB Internal SSD.

So Far:
I have successfully gotten boot-repair to acknowledge my efi partition in my USB by copying the efi partition in the Internal SSD.
I am still unable to boot through the USB Drive

Any help will be greatly appreciated.

Thank you.

Edit:
         For those who wants to do the same thing that I did. This might not be the best way, but it works, and I'm good as long as it works.

         1). Follow the Windows Version on how to burn Ubuntu into a USB Drive.
         2). Press the Assist button near the left speaker.
         3). Boot from USB
         4). Install as per usual, remembering to include 1 partition for EFI (260mb with 1mb preceding)
         5). Remember to ensure that grub is installed in the USB Drive
         6). Finish the installation but do not restart the computer
         7). Open a terminal and start gparted
         8). Delete the EFI partition from the USB Drive (the 260mb)
         9). Copy the EFI partition from the internal SSD and paste it on the 260mb unallocated USB Drive.
       10). Mount the EFI of the internal partition and back up everything
       11). Install and run boot-repair
       12). Run the boot-repair, clicking on advance and making sure that the efi partition is selected as the USB Drive.
       13). Mount the EFI partition and copy the items inside the folder ubuntu onto the EFI/Boot Folder

Done!

---

### Post by YannBuntu on 2013-05-31
Thanks for your feedback.
Please could you indicate your [BootInfo URL]("https://help.ubuntu.com/community/Boot-Info")?

---

