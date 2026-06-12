---
title: "Trying to switch to Ubuntu, just need to be walked though one thing"
date: 2007-04-22
forum: General Help
---

### Post by JeffH on 2007-04-22
I have a 200GB drive and a 160GB drive. I want to take all of the files from that 160GB drive (formatted as NTFS) and transfer them to my now blank 200GB drive (haven't formatted it yet), and then partition and install Ubuntu.

However, the catch is I need to do it with nothing but the Ubuntu Live-CD. Knoppix won't boot on my machine, neither will GParted. How can I go about mounting this NTFS drive with the 7.04 Live-CD, copy all of it's contents to my 200GB drive (and how should I format my 200GB drive), etc.? I'm finally making the big switch to nothing but Ubuntu but i'm having a horribly hard time getting these files to what's going to be my new storage drive.

---

### Post by rocknrolf77 on 2007-04-22
Here you go : [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only) :)

---

### Post by jediborger on 2007-04-22
You can mount the NTFS partition with the guide above. but first you'll want to format the new 200 GB hard. So with the live cd you'll need to start gparted, either in the menus's or hit alt-f2 and type it in. Then select the drive and create an ext3 partition to put everything in. Then it's a simple copy and paste between the hard drives.

---

### Post by JeffH on 2007-04-22
I mounted the NTFS partition and everything went well, and formatted the 200GB drive as EXT3 (though QTParted, but for some reason I couldn't do it with GNOME Partition Editor, I have to use System Rescue CD to do it, GNOME Partition Editor would format it but fail to give it a label, and would error out when I tried to give it a label and the volume would show up as "unknown").

Anyways, so I mounted the EXT3 volume and my NTFS volume, but trying to drag and drop inbetween them, it tells me that I don't have the permissions. I think the permissions for the EXT3 volume aren't set to me being able to write to it, how do I do that?

---

