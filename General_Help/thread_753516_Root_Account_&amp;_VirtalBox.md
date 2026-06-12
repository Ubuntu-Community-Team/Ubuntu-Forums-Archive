---
title: "Root Account &amp; VirtalBox"
date: 2008-04-12
forum: General Help
---

### Post by dpsguard on 2008-04-12
Hi All,

I have Ubuntu 7.10 on my laptop. I have installed VirtualBox but I am running into some permissions issues to access /dev/scd0 (which I have tried to fix by sudo chmod 666 /dev/scd0) but I still get the same error that my account is not authorized to open this device and hence virtualBox can not start the virtual machine.

So I thought to login as Root. By default Ubuntu does not let login as Root as there is no password created. When I try to do "sudo passwd root" instead of getting prompt to set up a new password for the user root, I am back to the prompt in the shell and hence I am not able to set up password to be able to then use the root account.

Another issue, I find is that under system > administration, I do not have login window enabled so that I can try GUI way of setting password for Root. So I tried to enable this from system > preference > administration, and in there I do see option to check in login window, but as soon as I check in this, or any other unchecked option, it becomes unchecked soon after I try to check in. I have also tried to create a new application item ( called it Login Screen) and copied the command from the properties of Login Window, and then I am successful in creating this new item and it remains checked in, so it will have the same function. But when I come back to System > Administration > Login Screen, I get an error message:

Failed to run /usr/sbin/gdmsetup as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I have tried becoming root via sudo -i as well, but my problems remain.

I also need to be root as I am not able to delete some files on my  desktop as that complains that only root can do so.

Please help.

Thanks

---

### Post by p_quarles on 2008-04-12
What you've done so far is not recommended, and it sounds as though it may have already messed up permissions settings. 

To run Virtualbox, you need to add users to the correct group:
```
sudo adduser *username* vboxusers
```
To delete the files on your desktop, run the filemanager with root privileges:
```
gksu nautilus
```
If your installation is broken, you may need to back up your current data and reinstall.

---

### Post by dpsguard on 2008-04-12
Thanks for your prompt support.

Yes, I had added my username to be member of vboxusers group via

sudo useradd -G vboxusers

and looks like that has created all this problem and my user has been reduced to only a member of this group.

when I do, groups dpsguard, I get in response
dpsguard : dpsguard vboxusers

I believe I have to be member of lot other system devices / resources.

When I issue gksu nautilus, I get similar error message as I had indicated in my previous post.

Could you do me a favor and let me know by pasting the output of groups username command and I can then try adding my username to those system groups?

Thanks again

---

