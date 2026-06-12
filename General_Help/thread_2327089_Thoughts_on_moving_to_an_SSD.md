---
title: "Thoughts on moving to an SSD"
date: 2016-06-07
forum: General Help
---

### Post by makem2 on 2016-06-07
I have windows 10 dual booted with xubuntu on the system HDD. I have full backups of both systems and data.

Thoughts:

Steps:

1. Install a new xubuntu and copy the /home folder
2. Copy the backed up /home folder over the new home folder.
3. Put the old HDD in a caddy
4. Edit the new grub to point to windows on the HDD
5. Remove the old xubuntu from the HDD

Sounds simple but obviously far to simple.

If I have a 240GB SSD and a 1TB HDD, why not just clone the current HDD to the SSD and use the old HDD as a data drive? Only problem there is shrinking the data and two operating systems.

Which would you do and why please?

---

### Post by papibe on 2016-06-07
Hi makem2.

Sounds about right.

A few questions though?
[LIST]
[*]Is this a laptop or a desktop?
[*]Would the HDD be connected as an external USB, or internal SATA?
[*]Is this an UEFI computer?
[/LIST]
Regards.

---

### Post by makem2 on 2016-06-07
First, thank you for taking the time to respond.

Which choice sounds about right?


[LIST]
[*]This is a Toashiba P50-C laptop just under a year old
[*]The HDD would be in a caddy in the DVD drive bay so connected via internal SATA
[*]Yes, this is a UEFI computer
[/LIST]

---

### Post by papibe on 2016-06-07
> **makem2 said:**
> Which choice sounds about right?
I have done a similar procedure before.

The only thing I would do different is this: I would not touch the contents of the HDD until:
[LIST]
[*]Xubuntu is installed and booting on the SSD.
[*]Grub detects the 3 booting options: new Xubuntu on SSD, old X on HDD and Windows on HDD. This should be the default options after the installation as grup usually probes all present disks.
[*]Windows boots OK.
[/LIST]
Regards.

---

### Post by makem2 on 2016-06-07
Thank you. I may not have inserted the old HDD as I didn't know grub would find the old drive.

When you remove the old X does grub reflect this?

An OCZ drive comes with free cloning software but it may not cope with dual systems on the same drive. Have you any experience of cloning a dual boot system?

How did you go about shrinking? 

I can pare down /home to 9.02GB by backing up 154GB of data from it and windows to 72.09GB. I can also backup 226.44GB from a joint data partition.

That means a new 250 GB SSD is adequate with all data on the HDD.

Is it quicker if the data regularly accessed from X is on the SSD? I think it should be. I don't play games or do other heavy processor work regularly.

---

### Post by makem2 on 2016-06-08
Toshiba P50-C 12Z laptop

Bought without a DVD drive and Windows 10 on HDD

Laptop back is easily taken off after removing 10 screws and the DVD plastic filler.

Purchased a 9mm deep DVD bay caddy (must be the thin one, not 12.5mm)


                        OCZ 240GB SSD main drive which is 7mm thick (actually a Toshiba company) replacement for existing HDD


                        1TB HDD moved to dvd drive bay caddy


                        Operating systems:
            

                        On SSD: Xubuntu (new install from USB)


                        On HDD: Xubuntu and Windows 10
            

                        All three operating systems boot correctly.

---

