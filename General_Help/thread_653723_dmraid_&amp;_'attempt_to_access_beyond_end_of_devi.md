---
title: "dmraid &amp; 'attempt to access beyond end of device'"
date: 2007-12-30
forum: General Help
---

### Post by dupondje on 2007-12-30
Hello

I sucessfully installed Ubuntu 7.10 on my RAID0 array with DMRAID.
But there are a few things that doesn't work.

1) I'm getting flooded in dmesg with messages about 'attempt to access beyond end of device'
This is because it reads the parition table from /dev/sda, but it should read the parition table from the dmraid /dev/mapper/nvidia_fbajhgaf

2) In /dev/
 /dev/sda1 /dev/sda2 are created !!! While /dev/sda is just a part of the dmraid and should have partitions created in /dev/ ...


3) I was getting a 18gb disk in my locations (in the ubuntu gui) wich was a symlink to /dev/sda1 ... wich is ofc unmountable. I got it fixxed with adding the following lines to /etc/hal/premount/11-dmraid.fdi

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="scsi.model" string="WDC WD3200SD-01K">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
</deviceinfo>

4) For the dmraid partitions there is no symlink created in /dev/disk/by-uuid etc ...
   I think u can fix with changing rules in udev, but don't really know what ones etc
If u change the udev, so it doesn't create partitions for the disks that are part of a dmraid, the other problems will be solved also I bet :)


If u know some solutions for my problem :) Feel free to answer !

---

### Post by darwid on 2008-03-15
Actually I'm having the exact same problem.

However I also installed Fedora 8 and it doesn't have this problem but since I prefer Ubuntu 7.10 I've been trying (unsuccessfully) a few things, so I share them to avoid others the burden to explore those failing ways.

1. Compile a Vanilla Linux Kernel (2.6.24.3) which is greater than Ubuntu (2.6.22-14) and Fedora (2.6.23.1); It doesn't change a thing. Same message flood.

2. I found a message pointing to a bug that seems to describe our exact situation:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/106177/](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/106177/)

Now one last observation:
Fedora 8 uses dmraid-1.0.0.14 while Ubuntu uses dmraid-1.0.0.13, could that be that the issue was fixed in the new dmraid (eh, I'm a complete noob so I could be totally wrong here)

---

