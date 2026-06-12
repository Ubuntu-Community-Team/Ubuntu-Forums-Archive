---
title: "Reversing rm /usr/lib command"
date: 2014-09-09
forum: General Help
---

### Post by Trad_dog on 2014-09-09
Hi,

I have inadvertedly issued the following command:
```

sudo rm -r ../usr/lib

```
While trying to reverse it, I get an error:
```

sudo mv -r ~/.local/share/Trash/files/lib .
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so: No such file or directory
sudo: fatal error, unable to load plugins

```
Can some experienced OS reader of the forum help not to make things worse at this stage ?

Thanks and best

Trad.

---

### Post by steeldriver on 2014-09-09
What directory were you in when you issued the command? 

Assuming you have actually removed /usr/lib, then even if you could 'fix' the sudo error (and all the other likely errors once you get past that one) it's not going to help you since rm does not use the trash mechanism (unless you have aliased it?). Realistically you are going to need to reinstall. If you don't have a current backup of all your data, you can use a live CD/USB to recover your files first.

---

### Post by Trad_dog on 2014-09-09
Hi steeldriver, 

I was in /usr before issuing the unfortunate command. 
I hear what you say about rm. However, I am not sure why I can see "lib" in ~/.local/share/Trash/files/lib.
Re-installing is a untasteful option as my system is heavily customised.
I was thinking to move lib to a safe area without the need of sudo and boot from a live cd and reinstall it under
/usr but deemed it heavy handed. 
Maybe someone will have an better idea. 

Best

---

### Post by sandyd on 2014-09-09
> **Trad_dog said:**
> Hi steeldriver, 

I was in /usr before issuing the unfortunate command. 
I hear what you say about rm. However, I am not sure why I can see "lib" in ~/.local/share/Trash/files/lib.
Re-installing is a untasteful option as my system is heavily customised.
I was thinking to move lib to a safe area without the need of sudo and boot from a live cd and reinstall it under
/usr but deemed it heavy handed. 
Maybe someone will have an better idea. 

Best

That means your /usr/lib is gone.
If your in /usr, going to ../ means your now in / - basically deleting everything in /usr/lib

---

### Post by Trad_dog on 2014-09-09
Hi, 

I deleted inadvertedly /usr/lib. The directory seems to be in the Wastebin located at ~/.local/share/Trash/files/lib.
To move it back I need admin rights, which seems to have been affected by the manipulation. 
I am wondering how to bring  my system back to a correct state. 
I have not enabled the super-user account (this is a case where it would come handy). 

Is this the right forum to post this sort of request ?

Best

---

### Post by Impavidus on 2014-09-09
**rm**, unless modified by you, doesn't move things to trash but simply deletes them. If you are sure the lib directory in your trash can is the lib directory from /usr (which seems unlikely to me), you can restore it using recovery mode (or a live disk). But I think you have to reinstall almost every package on your system, which is easiest if you reinstall the entire system.

Most of your customisations will be in your home directory. Using your live disk you can make a backup and simply restore them. As to reinstalling all your applications, ```
dpkg --get-selections >packages.txt
``` may get you a list of all installed packages,```
sudo dpkg --set-selections <packages.txt
sudo apt-get dselect-upgrade
```can reinstall them after you reinstalled the system. This is assuming dpkg still works, I'm not sure it relies on /usr/lib. Maybe (hopefully) dpkg only depends on libraries in /lib.

Edit: If you really want to solve this without reinstalling the entire system, you could boot a live disk, chroot in your installation and use apt-get to reinstall every package:```
sudo -i
for package in `dpkg --get-selections | awk '{print $1}'` do apt-get -y --force-yes install --reinstall $package ; done
```

(Source: [http://ubuntuforums.org/showthread.php?t=735693](http://ubuntuforums.org/showthread.php?t=735693))

Edit 2: Still I think reinstalling is best. Use backups of your settings to restore all your customisations. The above method is rather advanced.

---

### Post by Trad_dog on 2014-09-09
Hi,

It seems that there is a convergence of opinion in favour of the re-install. 

Is there a reason why booting from a Live OS, mounting the root partition and moving the lib 
directory back to its original place would not work then -- assuming I am not mistaken on the fact
that the lib I see in the Wastebin is indeed the one I deleted ? It would seem slightly less involved
to me ?

Best

---

### Post by ian-weisser on 2014-09-09
For most /usr/lib files, it would work just fine.
However, moving to the trash may have broken links (lot of links in /usr/lib) and lost permissions. Those would need to be repaired by hand as you discover breakage. It's a question of how many hours you wish to expend upon such manual diagnosis and repairs.

---

### Post by Trad_dog on 2014-09-09
Hi 

This is fairly convincing. 

Re-install it will be then. 

Cyril

---

### Post by Trad_dog on 2014-09-09
@Impavidus,

For information. 

I tried your no-reinstall option in a simpler way. Copied the /usr/lib from a live CD OS into /usr and then tried to reload my packages. 
It did not really work for some reason. 
So I re-installed.

Best

---

### Post by Trad_dog on 2014-09-09
Hi,
 actually
```

sudo dpkg --set-selections <packages.txt
sudo apt-get dselect-upgrade

```
fails. 
Any idea why ?

---

### Post by Bashing-om on 2014-09-09
Trad_dog; Hello ;

> **Trad_dog said:**
> Hi,
 actually
```

sudo dpkg --set-selections <packages.txt
sudo apt-get dselect-upgrade

```
fails. 
Any idea why ?

did you do:
```

dpkg --get-selections > ~/packages.txt

```
1st ?
[INDENT][INDENT]Just what pops to mind[/INDENT][/INDENT]

---

### Post by Trad_dog on 2014-09-09
Thanks for checking. Yes I did.

---

### Post by steeldriver on 2014-09-09
What exactly is the nature of the failure - can you be more specific (any error messages etc.)?

---

### Post by Trad_dog on 2014-09-09
In the file that I attached, there is an very long list of:
dpkg: warning: package not in database at line ....:

---

### Post by Trad_dog on 2014-09-09
And none of the application would be re-installed.

---

### Post by ian-weisser on 2014-09-09
"package not in database" usually means the dpkg database is empty or incomplete.

Check your /etc/apt/sources.list.d to see that you actually have valid repositories listed, and that you have all the sections: Main, universe, multiverse, restricted, security, updates, etc.
Run apt-get update to build the package database from those sources.

---

### Post by Trad_dog on 2014-09-22
Tried the suggested solution but I could not make it work. 
Actually, re-installing nowadays goes a long way to keep your data. 
Following the above advice and saving your /etc directory as well as your home directory 
should cause very little data, functionality and customisations loss. 

Best

---

