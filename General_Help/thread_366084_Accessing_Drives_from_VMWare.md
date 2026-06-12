---
title: "Accessing Drives from VMWare"
date: 2007-02-20
forum: General Help
---

### Post by Raptor45 on 2007-02-20
I got windows 2000 set up in VMWare, and now I would like to be able to access the ntfs partitions from my real windows xp install. How can I go about doing this?

---

### Post by capdog on 2007-02-20
Ok, but this sounds like a Windows support question... where does Ubuntu fit in with this setup?

Please elaborate on what you've got...

---

### Post by Raptor45 on 2007-02-20
Its an Ubuntu question because its quite a bit easier for a linux user to use a VM of windows than to restart the computer every time there is a need to use a windows only program. There are quite a few questions and howto's for VMs here on the forums because of this, so I don't think asking help on how to set it up is entirely out of place.

---

### Post by Raptor45 on 2007-02-20
So can anyone help me here?

Just want to be able to see NTFS partitions from my Windows 2k VM running on Ubuntu!

---

### Post by aragorn2909 on 2007-02-20
Are you using vmware player or workstation?

---

### Post by Raptor45 on 2007-02-20
I'm using vmware server.

---

### Post by aragorn2909 on 2007-02-20
I don't believe shared folders is an option in server, for that, you need workstation.

AB

---

### Post by Raptor45 on 2007-02-20
Lame if thats the case! Well thanks anyway.

---

### Post by aragorn2909 on 2007-02-20
If you set up, or already have, a samba share, you could share files that way.

AB

---

### Post by veloce on 2007-02-21
If you can see the ntfs drive in Ubuntu then you can share it with your virtual machines running under vmware server.

You will only be able to provide the same level of access to the virtual machines that Ubuntu can get.  That is, if you only have read access to the ntfs drive then that's all you can give to the virtual machines. I understand that there is experimental access to ntfs drives from linux available.  I haven't used it and know nothing more than that. 

Once you've got access from Ubuntu sorted, set up the directories you want to share as Samba shares.  

You need to have some sort of networking set up for your vmware.  Under linux, this can only be done using vmware-config.  I would suggest using host only networking.  Once this is set up on both host and vm you should be able to "see" the share on the vm.

---

