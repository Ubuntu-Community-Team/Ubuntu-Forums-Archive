---
title: "Trying to access a Win7 PC on the network"
date: 2016-06-25
forum: General Help
---

### Post by datawrite on 2016-06-25
**&#8203;**Hello.
I made the switch from Windows 7 to Lubuntu last year. I have been using 15.10 since it was released without any problems. My PC is on a home network which accesses  a win7 PC, mostly  for the video content on it (other PCs and devices also access the Win7 pc too - but I'm the only one who does with a linux OS). I have just installed Lubuntu 16.04. When I try to access the win7 PC a box pops up and asks for a password to access the WORKGROUP. The problem is that the win7 pc has NOT been set up with a password - so I have no password to enter. Version 15.10 never required a password it just accessed the win7 pc without any problems. So, I reinstalled 15.10 and that was fine - no password required. Installed 16.04 a second time - password required!. I have tried Ubuntu and Ubuntu Gnome 16.04 - same password problem. So, I'm back on Lubuntu 15.10. Any ideas why the new version wants a password  I don't have? The only password I have is my Lubuntu password (I've tried that and it doesn't do the trick). 
* I also have the same problem with MX-15
Thanks.

---

### Post by gsahli on 2016-06-25
samba password is separate from your login password. Read here:
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

---

### Post by datawrite on 2016-06-25
> **gsahli said:**
> samba password is separate from your login password. Read here:
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

Thank you for replying. 
This worked, thanks - I thought it hadn't..but after rebooting it worked and I can access the win7 pc.--thanks again.

---

