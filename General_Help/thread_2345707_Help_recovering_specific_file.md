---
title: "Help recovering specific file"
date: 2016-12-07
forum: General Help
---

### Post by frazicm on 2016-12-07
Im relatively new to Linux so bare with me :) 
 
Everything  was going fine until one day i booted up my spare laptop running Ubuntu  14.04 LTS. Upon trying to login i would be presented with a blank  screen, although the guest account would work without any problems. 
 
I  looked for a solution on the internet and was told 'rm-rf ~/.config'  would fix the issue. It did fix the problem and i could logon fine  however now my files are missing.....I have since learnt the importance  of that command. I have also learned to make regular backups in future. 
 
I really need to recover virtualbox files, is this possible? If so, how? 
 
Some people have told me it isn't possible, some said maybe and some say it is....So its left me rather confused. 
 
Can anyone help?

---

### Post by dragonfly41 on 2016-12-07
Understand that the effort in time you are prepared to invest depends on how important it is to recover the lost data.
It seems that you have another laptop (not the "spare") so that will help you to prepare for the recovery process.

First rule: **stop now** using your spare laptop to avoid your lost data (which may be still in your disk) being overwritten by some other application.

Now with your other laptop prepare a Ubuntu Live USB on a USB stick (you might already have this ready). Ensure that you have adequate free space in your Ubuntu Live USB to save any recovered files.  Recovered data must not be saved into your spare laptop hard drive.

Now boot up your spare laptop launching not the internal Ubuntu (where the lost data may reside) but booting up your Live USB and clicking on "Try Ubuntu" button - not "Install Ubuntu".   You might have to switch your BIOS at bootup to boot from USB device first, and not the internal drive.

Once inside your Live USB Ubuntu you can look for the internal drive (Ubuntu) from where you hope to recover deleted data. 

If your data is very important you might consider at this point cloning the internal Ubuntu into some external backup device.  At this point you might find it helpful to purchase an external drive for such backups.

...

Now looking at your command which you posted above

```
rm-rf ~/.config
```

suggests that you deleted only your VirtualBox config files in ~/.config/VirtualBox and not the vm images.


VirtualBox.xml
xpti.dat - but this is a generated file.


The VirtualBox images might still be unscathed.
Search by using ...

```
sudo locate .vdi
```

To see if they are still in your spare laptop drive.

This is what I see from that search ...

```
~/VirtualBox VMs/Ubuntu-14.04/Ubuntu-14.04.vdi
```

Now it is some time since I used VirtualBox so I'm not sure if you can reconstitute deleted config files from .vdi files.  But I would try installing VirtualBox on your Live USB and copying your .vdi file from your spare laptop into your Live USB VirtualBox. You might strike lucky.

If that works then you would need to reinstall VirtualBox in your spare laptop. But first make sure you have a backup.

...

If the above process does not work you can try various tools to try to retrieve your lost data.

testdisk and photorec are two such tools which you can read about in this forum.

---

