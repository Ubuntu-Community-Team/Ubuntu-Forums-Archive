---
title: "Samba, Kubuntu, Virtualbox, shared folder success"
date: 2007-07-08
forum: General Help
---

### Post by Gary.M on 2007-07-08
I've been through the process of setting up access to a shared folder on the host machine for my Windows XP virtualbox machine.

I wanted to try a different way to the virtualbox shared folder guest additions capability as that seemed sluggish and at times marginally stable.

I am running virtualbox 1.4 under Kubuntu Feisty.

All of the guides I read said you needed to enable a bridged network interface.

I saw one reference to Virtualbox 1.4 being able to do this even with the NAT network interface that is the default.

I tried and succeeded.

I'm new to this, but have good hands on experience with Windows and Windows networking.

I installed samba thus

sudo apt-get install samba samba-doc smbclient smbfs

then configured as per 

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

after samba setup I used dolphin file manager properties on the chosen folder to set shared folder access

I found I still needed to edit smb.conf file. Find section detailing the share created and then make it readwrite (readonly=no)

after this I was able to see the host machine samba server from the virtualmachine and map the network shared folder as a drive letter in the virtual machine.

Using this seems more stable and responsive than the virtualbox shared folder approach which I have been using.

Note. If you run kcontrol and use the samba setup in there it has a bug. It doesn't allow you to add samba users and a share I activated with that was buggy. Launchpad has this problem logged going way back to a much earlier release of Kubuntu. I'd avoid kcontrol.

---

