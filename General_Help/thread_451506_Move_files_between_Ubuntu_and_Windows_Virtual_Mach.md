---
title: "Move files between Ubuntu and Windows Virtual Machine"
date: 2007-05-22
forum: General Help
---

### Post by paul2112 on 2007-05-22
Okay, I'm a Linux newbie.  I've successfully installed Unbutu Feisty. LOVE it thus far. 
I have followed instructions from this forum and successfully created a Windows XP VM with VMware server. 

My question:

How do I get files into the windows VM envrionment? I've got them sitting here on my desktop in Ubuntu, but I need them on the desktop in my Windows VM! 

Thanks!

Paul

---

### Post by rocket777 on 2007-05-22
I haven't actually done this with the combination you are using, but basically there are three ways.

1. get the vmware tools. You need an .iso and you install into the virtual machine - this file can usually be found inside the vmware server distro - i found it somewhere but can't remember. I did it with the vmplayer, I think server actually has a command to help do this. 

This provides smoother mouse use as well. There is a mechanism that lets you also drag/drop from outside the virtual windows to inside which causes a copy. I've only been sucessful doing this between a windows 2000 host and a windows 2000 virtual however. 

2. You set up a shared folder in the guest that can be seen by the host. Share your desktop folder from xp and then in ubuntu, go to places, network and you should see windows networking, then workgroup, then your xp virtual machine, and finally all shared folders, such as the desktop folder.

3. In a pinch, I've used a thumbdrive as well. (You can enable and disable usb connections between host and guest, so you attach to host, copy files onto usb drive, then disconnect and attach to guest).

---

### Post by paul2112 on 2007-05-23
Okay, I've got VMware tools installed, but I am not seeing how this "drag & drop" thing is working out. Whenever I try to drag a file from ubuntu desktop to my windows desktop in VMware, it won't "stick".

HELP! 

Thanks!

---

### Post by mdurham on 2007-05-23
You can use the network. Share a directory in Ubuntu and also in XP. Then you can go either way with the file manager.

---

