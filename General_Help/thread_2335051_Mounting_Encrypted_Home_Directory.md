---
title: "Mounting Encrypted Home Directory"
date: 2016-08-25
forum: General Help
---

### Post by absoluteterror on 2016-08-25
Okay, so here's what happened:
  I lost power, and now my computer crashes whenever I log in.
  I CAN get to the root prompt from GRUB, but it appears to be useless.  I enable networking from the main menu, but I still cannot try to  restore or redownload packages as this causes it to freeze. It's similar  to how another machine I had reacted when it couldn't load Nvidia  drivers, however this computer uses Intel Iris graphics. Would it be  possible to reinstall those if root prompt ever works?
  Whenever I browse to my /home/terror folder, I see a .txt readme and a  .desktop file which just runs the command "ecryptfs-mount-private".
  ```

[Desktop Entry] _Name=Access Your Private Data _GenericName=Access Your Private Data Exec=/usr/bin/ecryptfs-mount-private Terminal=true Type=Application Categories=System;Security; X-Ubuntu-Gettext-Domain=ecryptfs-utils
```

  I try to run this .desktop file but it opens a shell prompt which immediately closes.
  I tried this command as well, but the results vary from which  distro's live CD I try. Right now it is saying command not found, but I  have installed encryptfs.
  ```
sudo ecryptfs-setup-private '/media/ubuntu/DISKNAMEGOESHERE/home/terror'
```

  I'm in an Ubuntu LiveCD right now, but the output of this command is  not the same as it was when I first logged in because I have tried so  many things.
  When I tried to run this command, it said it was successful at  mounting it but there's nothing in this folder. I tried making it with  mkdir and also tried mounting it to different places.
  ```
sudo mount /dev/kubuntu-vg/root /mnt/disk
```

  I have a LUKS encrypted LVM volume / with a separately encrypted  home partition which I DO know the passphrase for. When I was setting  these up I didn't realise it was two separate things.
  Please help. I will provide whatever information that I can.

---

