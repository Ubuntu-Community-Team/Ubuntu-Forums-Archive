---
title: "I have changed my username and all my files gone :("
date: 2013-03-04
forum: General Help
---

### Post by bekir35 on 2013-03-04
Hi, 
I am new at Ubuntu. 
I have changed my username with these codes respectively;

usermod -d /home/newusername -m oldusername
  sed -i -e 's_oldusername_newusername_g' /etc/passwd
  sed -i -e 's_oldusername_newusername_g' /etc/group
  sed -i -e 's_oldusername_newusername_g' /etc/shadow

All my files are removed. 
How can I recover them. They are so important for me. 
Please help.

---

### Post by SlugSlug on 2013-03-04
They are probably under you old /home directory..

use 
```
ls -l /home
```

to show the home directorys you will hopefully have two now?

then 

```
sudo chown newusername /home/oldusername -R
```

then open file browser and locate that folder

---

### Post by grahammechanical on 2013-03-04
Our files/documents are in a folder called by our user name that is under the Home folder. If you set up another user with your old username then you will get access to those files. If you want to copy those files you will need to open Nautilus as administrator. ```
gksudo nautilus
``` The files have not been deleted. You are no longer authorised to access them. You are not the user who created them any more.

---

### Post by schragge on 2013-03-04
> **SlugSlug said:**
> They are probably under you old /home directory.Probably not as the OP used *usermod -m* (--move-home).

@**bekir35**
It wouldn't help you find your files, but I believe you also should rename /var/mail/*oldusername*, /var/spool/cron/crontabs/*oldusername* etc. Look at the output of
```

sudo find /var -name [COLOR=red]oldusername[/COLOR]
sudo find /home -name '*[COLOR=red]oldusername[/COLOR]*'

```

---

### Post by bekir35 on 2013-03-05
@**SlugSlug;**

I did these things. But at the /home/oldusername directory I found two files, one of them is a readme file. Another one is Access-Your-Private-Data.desktop. 
I have clicked on it but nothing seems. 

@**grahammechanical**;

I want to open Nautilus as administrator, it opens file browser and waiting for me do a selection but there are nothing to select. I closed file browser and it gives me an error like this: 
"(nautilus:3485): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:3485): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)"

@**schragge**;
After the code 'sudo find /var -name oldusername', it lists:
/var/lib/AccountsService/users/oldusername                   // I opened this directory and it is a text document which name is a oldusername
/var/lib/sudo/oldusername                                              // I want to open this directory it says permission denied. Than I opened it from the terminal as a root and found oldusername than I listed files under oldusername but there is nothing

After the code 'sudo find /home -name '*[COLOR=red]oldusername[/COLOR]*'', it lists
/home/oldusername
/home/.ecryptfs/oldusername // same as @SlugSlug methods found. 

:( 
Is there a solution ??

By the way, thanks for your answers..




[COLOR=red]
[/COLOR]

---

### Post by schragge on 2013-03-05
> **bekir35 said:**
> /home/[COLOR=red].ecryptfs[/COLOR]/oldusernameWait, your old home folder had been encrypted ([uhelp]community/EncryptedHome[/uhelp])? Or only a subdirectory of it ([uhelp]community/EncryptedPrivateDirectory[/uhelp])? That explains where all you data have gone. They are still there, just not visible to your new user.

---

