---
title: "Ubuntu studio audio help"
date: 2008-04-20
forum: General Help
---

### Post by darkhorse186 on 2008-04-20
Hi,
I installed the ubuntu studio audio and it then said to restart but when I restarted I wasnt able to get to the login screen and the monitor went to stand by. the only way i can get it to run is to go into GRUB and go to the generic one
 how can i fix this??? 
Thanks 
Darkhorse

---

### Post by BuffaloX on 2008-04-20
Try to see if you have restricted drivers....
System->Administration->restricted drivers manager
Disable restricted drivers, reboot
Then try reenabling restrictive drivers...

---

### Post by darkhorse186 on 2008-04-20
Hi,
after disabling the restricted drivers and rebooting it works but i now cant open the restricted drivers manager.

Edit: it also says this when i try to open it "You need to install the package linux-restricted-modules-2.6.22-14-rt for this program to work."

---

### Post by Ajay Chahar on 2008-04-20
Do you already have that package installed?

---

### Post by darkhorse186 on 2008-04-20
Thanks, I just had to install that program.
Darkhorse

---

### Post by pscholl on 2008-04-30
Hi, I'm getting the same problem as the OP, but I have the latest restricted-modules package installed and the real-time kernel still doesn't boot up when the video drivers are enabled. (I have to either disable the drivers, or use the old generic kernel instead)

I'm running Hardy, on an HP laptop with nvidia graphics, if that's any help.

---

