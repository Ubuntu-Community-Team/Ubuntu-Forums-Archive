---
title: "Deleting/Creating Logical Volumes"
date: 2024-01-29
forum: General Help
---

### Post by Quarkrad on 2024-01-29
I have been creating and deleting logical volumes on my SSD using them for both my live system and testing using the commands **sudo lvcreate.... **and **sudo lvremove ......**  (for testing I have been using qemu VMs within the LVs).  At the moment my LVs look like:



```
.....
/root             0 to 10239                        40
/home            10240 to 23039         12799       50
/workspace       23040 to 87039         63999       250
/swap            87040 to 89087         2047        8
/briant          89087 to 96767         7679        30
unallocated      96768 to 99327         2559        10
/win10           99328 to 112127        12799       50
unallocated      112128 to 119807       7679        30
/ubuntu2204vm    119808 to 132607       12799       50
unallocated      132609 to 238415
```

where the order of the above columns is:   name of lv,  physical extents, logical extent size, size in GB

My 'live system' is  /root, /home, /workspace, and /swap.  The rest of the LVs are used for VMs i.e. /briant, /win10 and ubuntu2204vm.  

For some reason the way I have created LVs has left a 10GB unallocated space between /briant and /win10 and a 30GB unallocated space between /win10 and /ubuntu2204vm.   The unallocated space at the end, 132609 to 238415 is the rest of my SSD free space (approx 413GB).  I would like, if possible, to either delete these 10G and 30G unallocated LVs or allocate them as actual LVs.

So far I have not been to find a way/command to create an LV in position 96768 to 99327 and another in 112128 to 119807.

note:  I have other HDs in my PC but not detailed them as the only HD that has LVM is the one detailed above.

---

### Post by Quarkrad on 2024-01-30
I have had a look at two gui apps - blivet and kde partition manager.  Both these gui's show the LVs continuous and lump the free space s together as one 453GB lump.  I appreciate these are GUIs and perhaps not representing the actual reality (i.e. where the free space areas are physically) but I'm wondering whether my original question/trying to tidy up is wrong.  Perhaps I should not be concerned about where the physical free areas are but just 'see' them as 'free space'.

---

### Post by TheFu on 2024-01-30
All SSDs are virtual. We don't actually know anything about the physical use.  Additionally, there's ZERO performance impact or difference in having fragmented blocks on SSDs.  They are solid state, no moving parts, and the internal controller handles how the block lookups to make a file happen. It is a closely guarded secret by each SSD maker.  

In short, relax. Don't worry about it.  LVM is doing what you want and the details don't matter.

---

### Post by Dennis N on 2024-01-30
> Both these gui's show the LVs continuous and lump the free space s together as one 453GB lump.

When you first create an LV in a new VG, the extents are likely to be one segment (of many extents). A segment is a set of continuous extents. Later, when extended, it may have several segments.

Use lvdisplay to see the situation with any LV. This is my separate data LV. lvdisplay shows it has 5 (discontinuous) segments. This happens because it has been extended several times after creation.

```
--- Logical volume ---
  LV Path                /dev/os_vg/Common
  LV Name                Common
  VG Name                os_vg
  LV UUID                yU18kC-YYN7-1jpk-A9qn-XHka-7QyK-OAT79Q
  LV Write Access        read/write
  LV Creation host, time Tyana, 2018-11-02 12:09:42 -0700
  LV Status              available
  # open                 1
  LV Size                <216.80 GiB
  Current LE             55500
  [COLOR="#FF0000"]Segments               5[/COLOR]
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:5

```

Use **vgs**, **lvs**, and **pvs** commands to see the status of your LVM components.


How did you get **blivet** installed in Ubuntu? I have seen it in Fedora, and I quickly decided that the terminal is a better way to manage LVM.

---

### Post by Quarkrad on 2024-01-30
Thank you **TheFu** and **Dennis N**.  Up to now I have always used the terminal and will continue to do so.  I was just interested what a GUI made of my set up.   I used these commands to install blivet-gui:

```
# Ubuntu 22.04
echo 'deb http://download.opensuse.org/repositories/home:/vtrefny/xUbuntu_22.04/ /' | sudo tee /etc/apt/sources.list.d/home:vtrefny.list
curl -fsSL https://download.opensuse.org/repositories/home:vtrefny/xUbuntu_22.04/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/home_vtrefny.gpg > /dev/null
sudo apt update
sudo apt install blivet-gui
```

from this website [https://unix.stackexchange.com/questions/583639/how-to-edit-resize-an-lvm-partition-graphically-with-a-gui](https://unix.stackexchange.com/questions/583639/how-to-edit-resize-an-lvm-partition-graphically-with-a-gui)

---

