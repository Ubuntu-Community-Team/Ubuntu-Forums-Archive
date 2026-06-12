---
title: "DCIM folder not listed when I connect my phone"
date: 2017-06-17
forum: General Help
---

### Post by greenbreen on 2017-06-17
I'm running Ubuntu 17.04 and connecting a Fairphone 2 running Android 6.0.1.  When I connect the phone and tell it to connect as an MTP device, it shows up in Ubuntu and displays the phone's internal memory, but the directory that should contain the DCIM directory isn't listed.  In fact, out of 33 directories that I count in that root directory from my phone's file explorer, only 15 show up, although all 9 files in that directory show up.  I have the check box to show hidden files checked.  The phone's screen is not locked.  If I right-click and tell it to display in a terminal, "ls -a" gives the same result.  Any ideas about why those folders aren't being listed?

---

### Post by gordintoronto on 2017-06-17
Rather than use MTP, you should be able to open the phone from Nautilus, where it should appear as "6 GB Device" or some such. The file browsing might work better.

But I don't have an answer to your actual question.

---

### Post by greenbreen on 2017-06-17
I assume Nautilus is the default file manager in Ubuntu 17.04--correct me if I'm wrong.  So here's the process I'm using to connect the phone.  I plug one end of the USB cable into the phone and the other into the computer.  On my phone, I swipe down and there is a notification that the phone is in charging mode.  I tap that, and it brings up 4 options:  charging mode, connect with MTP, connect with PTP and connect as a MIDI device.  I select connect with MTP and Nautilus pops up a window on the computer showing icons for the phone's internal memory and the external SD card.  When I double-click the internal memory, I see a list of files and directories, but DCIM is not listed among them, although it should be.

---

### Post by gordintoronto on 2017-06-19
Yes, Nautilus is Ubuntu's file manager.

Here is what I do to access the files on my phone, which does not have a slot for an SD card. I plug the phone into the USB cable, and I put the phone down on top of my desktop computer, and I don't touch it again until it's charged. If memory serves, this approach started working with 16.10. Before that I use an app called Airdroid.

I open the file manager on my computer. The phone appears on the left side as "8 GB Device" and I click on it. Then I can traverse the directory structure to my heart's content, including DCIM/camera, and copy, play/view or delete files. You might get two Devices, one for the internal storage, and one for the SD card.

By the way, I installed an app called "File Manager" from the Play Store, and it lets me browse the files on the phone, on the phone.

Are you sure that DCIM is not on the SD card?

---

### Post by greenbreen on 2017-06-19
I use an app called "Amaze" as the file manager for my phone.  I'm sure the DCIM folder is in the internal storage and not the SD card because I can navigate to if from Amaze.  Admittedly, the file system on the phone is confusing.  The path Amaze reports is "/storage/emulated/0", and I am not able to traverse closer to root than that.  I believe that this path corresponds to the root of the "storage" reported by Ubuntu because the files and directories in the two are the same, minus the missing folders.  Also, before I upgraded to Marshmallow, I was able to connect my phone to the computer and manipulate files or folders, and those changes would be reflected in the "/storage/emulated/0" location.

By the way, I tried connecting my phone to my Xubuntu 14.04.1 laptop, and it behaves the same way--no DCIM folder.

---

