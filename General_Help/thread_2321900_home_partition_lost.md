---
title: "home partition lost"
date: 2016-04-25
forum: General Help
---

### Post by ibr2 on 2016-04-25
Hello guys,
I have installed ubuntu with a home in a separate harddisk but the harddisk is lost (hw problem). I now have a new harddisk that I need to add it as a replacement for the home folder so basically I need to make a new home for an existing system (no copy or backup). I don't want to reinstall ubuntu from the beginning as there are some configurations that I like to keep. Could you please guide me through this process!
Many thanks!
Ibrahim

---

### Post by oldfred on 2016-04-25
While yours is not a move, unless from your backup.
But most of the commands you need are shown in detail.

Generally you just need to create a new ext4 partition, set ownership & permissions, and edit your fstab with new UUID.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving

[/URL]
 Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 

You may need to manually mount, set permission & unmount before rebooting so you have correct permissions. Or above may not work for rebooting. Change example sda5 to your new partition, sdb1? or whatever.

 sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data 

[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]
[/URL]

---

### Post by jim_deadlock on 2016-04-25
> **ibr2 said:**
> there are some configurations that I like to keep.

Sorry to break it to you but all your configurations were stored in your /home partition so they are all lost. When you start your apps with a fresh /home they will all be back to default settings.

---

