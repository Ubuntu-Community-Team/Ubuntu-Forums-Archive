---
title: "Auto Mounting External HDD on Home Network"
date: 2013-03-14
forum: General Help
---

### Post by BCain on 2013-03-14
Hello All,
I am a Noob to Unbuntu and have been a Windows user for years. I decided to switch over to Linux and I am running Unbuntu 12.10 beside Windows Vista via a dual boot with GRUB. That said, I have spent weeks trying to mount a WD MybookLive 2TB External HDD without any luck. However, I was finally able to mount it using the code: 

```
blake@blake-HP-Pavilion-dv4-Notebook-PC:~$ sudo mount -t cifs -o username=blake,users,uid=1000 //192.168.1.15/Public /media/mybooklive
```
 
The HDD is attached to my router and acts as a home network storage drive. When I run the above code, the mount shows up in my Home folder under "Computer". I am able to read and write to this drive and it functions normally. However, my new issue is that I can not seem to get the drive to auto-mount at boot. I have read that PySDM would possibly work but is not in the repository for 12.10. I am fairly new but I have no problem trying to edit /fstab, I just do not know how to do so correctly. Any help would be appreciated. My system info is below. Some of it may be redundant but I did not want to leave anything out. Thanks

System Info:
HP Pavilion dv 4 Notebook 500GB Internal HDD
Windows Vista Home Basic
AMD Turion X2 Ultra Dual Core Mobile ZM-80
ATI Raedon graphics

OS: Unbuntu 12.10 (quantal)
GNOME: 3.6.0
Kernal: 3.5.0-25-generic

*EDIT* I should have noted that the IP address for the HDD is Static

---

