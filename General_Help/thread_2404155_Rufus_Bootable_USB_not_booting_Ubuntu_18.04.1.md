---
title: "Rufus Bootable USB not booting Ubuntu 18.04.1"
date: 2018-10-20
forum: General Help
---

### Post by JimHebert on 2018-10-20
Hi: :)

I have Windows 8.1 & wanted to try Ubuntu on a bootable USB stick before installing on my laptop.
I went through these steps  [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)  
All went very well.
Next I did these steps   [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)
When I completed step 4 of setting the booting order in the Bios menu (placed USB boot just ahead of OS boot, clicked enable, clicked yes to confirm, then exit), I turned off my laptop and then turned it on again. Ubuntu did not boot up. Instead laptop booted up in Windows as usual.

---

### Post by yancek on 2018-10-20
Generally in a BIOS you need to hit the F10 key and Enter key to save changes and exit.  Enabling may not be enough but we don't know what hardware you have.  Do you have separate options for boot priority for UEFI and Legacy boot?  Make sure you get that correct.

---

### Post by JimHebert on 2018-10-20
My laptop is an HP Probook 450 G2. I remember after moving, with the up/down arrow keys, the choice "USB Hard Drive" up to just before "OS Boot Manager", I looked at the bottom of the page it said Enable if I recall, I clicked it, then I tried to exit, but it wouldn't let me exit until I had clicked a yes box to confirm the changes I had made. After exiting Bios, I turned laptop off, then back on with USB in the port. Laptop booted into Windows. I went back to see if my settings in Bios were still there. Yes, they were still there as I had arranged them in the proper order earlier. I didn't see the 2 sets of options like you mention nor do I have any idea where to look? According to the first Link I sent in my original post, step 4 says talks about "Target System" field, & says that both, Bios and UEFI, will work in that default mode indicated. I didn't mess with that button at all during the installation of Rufus.

---

