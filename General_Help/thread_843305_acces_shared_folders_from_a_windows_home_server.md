---
title: "acces shared folders from a windows home server"
date: 2008-06-28
forum: General Help
---

### Post by Blackprint on 2008-06-28
Hi,

linux n00b here. I am looking to use my linux box as a media center and access all my videos from a windows home server. I have downloaded and installed samba but have no idea what settings i need to put in. I tried editing the conf file but it said i didnt have permissions to save it. So I tried to login as root after setting a root password but it said I am not allowed to login from this screen.

Could someone please help with what settings i need to use to access windows shares. I have the GUI installed or could I run commands?

I should mention that I can see the computers on my network but when I click on them there are no folders displayed.

Thanks

---

### Post by wagb278 on 2008-06-28
Hi, I am still learning too, so take what I say with a grain of salt.

You should be able to edit the smb.conf file from the command line (Terminal) using:
sudo gedit /etc/samba/smb.conf
- and supplying the password for your first user. gedit is my editor of choice, use your editor of choice on that line.
I suggest that you first copy the smb.conf file using 
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf-backup. 

If you would like to use it - there is a SMB config file editor (SWAT) which you can install. Use the Package Manager and search on SWAT.  SWAT is a browser-based tool. SWAT includes good help for all the settings in smb.conf. To use SWAT open the browser and set the address to: [http://localhost:901](http://localhost:901)
and login as the root user that you established. SMB.CONF is writable only by root, unless you change file permissions. Logging into SWAT as another user will only allow you to inspect the settings, not edit them.

You will want a [Share] configured for the files you want to access over the network.  

Don't forget to establish SMB user accounts. From the Terminal enter smbpasswd -L -a username

Make life easy by using the exact username / password in SMB as you did for the Linux account(s).

I am diagnosing a problem accessing one of my shares that was working and suddenly stopped. I suspect a recent Ubuntu Update changed something that broke my configuration. I found your post looking for help with my problem.

Good Luck

---

### Post by Blackprint on 2008-06-28
Hi, 

Thanks for the info, theres a few tips there that I'm sure I'll use in the future. I managed to get it working by downloading the smb client. it seems i had only downloaded the server to share the linux folders. Can see them all ok. just need to solve my ketring problem now so it will save the windows access password!

---

