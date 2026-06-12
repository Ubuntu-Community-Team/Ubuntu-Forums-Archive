---
title: "accidently deleted etc folder"
date: 2008-04-19
forum: General Help
---

### Post by sn0board3r on 2008-04-19
i am new to linux, and i was screwing with some bash commands and i somehow deleted my etc directory. Now i am running off the ubuntu cd trying to fix it. My /home directory is on a seperate partition than all my other files. How should i go about restoring this etc directory?

---

### Post by dashnak on 2008-04-19
Truthfully, I don't really think you can do that.
You may have to reinstall, but don't take my word for it, let's wait a little longer to see if someone has anything else to say.

---

### Post by Zorael on 2008-04-19
Tagging for interest, would like to know if I ever end up in the same situation.

Perhaps you could make a straight copy of the etc directory on the live CD? Then again, chances are some files in there are locked and can't be read.

---

### Post by Tyke91 on 2008-04-19
etc contains a lot of config files from programs that you've installed, so a copy/paste from the live cd wouldn't do much good for the newly installed programs.

good news, you still have your home partition, and any file installed there has it's config files in the home part, not /etc... so you can do a reinstall of ubuntu without losing personal data


out of curiosity, did your rm -rf your /etc folder or did you delete it in another way?

---

### Post by sdennie on 2008-04-20
After you finish the re-install, I would recommend making a backup of /etc with something like:

```

tar cvf etc.tar /etc

```

And keep that somewhere on your home directory partition.  I normally do that so that I can have a reference of what the original files were at a later date but, in this case, it would have helped you just completely restore /etc as well.

---

### Post by koenn on 2008-04-20
how on earth did you manage to delete /etc ? you must have been running as root while you shouldn't be, right ? 

I think you *can* replace /etc with a copy from eg a live CD system but it will require a few tweaks. I'm not planning to reproduce this problem so the following recipe may be not completely accurate. Use your best judgment. No guarantees. Use at your own risk.

1- boot a Live CD and find where the partition that contains the broken system is mounted. I'll assume that's /media/sda1

2- become root to execute the next steps
```
sudo -i 
```

3- create a new /etc, set its permissions, and copy the live CD /etc to the hard disk
```

mkdir /media/sda1/etc
chown root:root /media/sda1/etc
chmod 755 /media/sda1/etc

cp -rp /etc/* /media/sda1/etc

```

4- blank the root password to be sure you can log in after reboot :
open /media/sda1/etc/passwd in an editor (eg gedit /media/sda1/etc/passwd ), and remove the 'x' placeholder for the root password, ie make the root record look like this :
```
root::0:0:root:/root:/bin/bash
```

5- edit  /media/sda1/etc/hostname and  /media/sda1/etc/hosts with the hostname of your computer

6- reboot your system (not the Live CD) and select recovery mode in the grub menu. Type root &Enter if you're prompted to login.

7- create a new account for yourself and give it sudo privileges
```
adduser youracccountname
usermod -a -G admin youraccountname
```

you may have some errors here if there's already a /home for that account name but with a different User ID (UID). You can change the ownership with
```
chown -R youraccountname:youraccountname /home/youraccountname
```

8- reconfigure all installed software. The following command should update /etc for all packages installed on your system
```
dpkg --reconfigure -a
```
accept the defaults where you're not sure what to put, and modify where needed

9- reboot and cross your fingers

EDIT: if all is well and you're up and running, don't forget the root account has no password. I'm not sure how to set it back to Ubuntu's default. maybe putting the x back in /etc/passwd is enough. If not, just set a strong password for root (run 'sudo passwd root')

---

### Post by Zorael on 2008-04-20
And report if it worked, please.

---

