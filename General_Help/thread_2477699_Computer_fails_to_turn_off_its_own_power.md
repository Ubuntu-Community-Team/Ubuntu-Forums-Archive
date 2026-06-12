---
title: "Computer fails to turn off its own power"
date: 2022-08-03
forum: General Help
---

### Post by artist-wavenet on 2022-08-03
In the Ubuntu 22.04 Studio's Konsole terminal emulator, when I use the command:

```
sudo poweroff
```
the computer shuts down its own power as expected.

But when I navigate to "Application Launcher => Shut down (power  icon on lower right) => Shut Down (third icon from the left), the  computer fails to power down. The screen freezes, and it does not respond to  user input anymore. The seconds countdown stops.

 In spite of the GUI freezing I am still able to login remotely by  SSH. Then when the command "sudo poweroff" is remotely entered, the computer  powers off.

 Why is failed power down happening, and how is this fixed?

 
The OS is a custom install of Ubuntu 22.04 with ZFS files system,  encryption, and RAID. The details of the installation, and the hardware, can be downloaded  here: [https://www.mediafire.com/file/2w8mdb96tbzslub/Ubuntu_22.04_Root_on_ZFS_Encryption.odt/file](https://www.mediafire.com/file/2w8mdb96tbzslub/Ubuntu_22.04_Root_on_ZFS_Encryption.odt/file)

---

