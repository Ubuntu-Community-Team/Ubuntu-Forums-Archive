---
title: "Dual boot, Windows 8.1"
date: 2014-10-05
forum: General Help
---

### Post by Aurivus on 2014-10-05
I've installed ubuntu for a month or so, but it sometimes it keeps on freezing. It's kinda annoying. Tho that being said ubuntu is better then windows(really! not being sarcastic). But am I able to get some help on how to install windows on my ubuntu to dual boot? I'm trying to install ArcheAge to play with my friend but it doesn't work out on wine. I've a flash drive/thumb drive with windows 8.1 but ubuntu doesn't seem to read my flash drive/thumb drive in the boot options screen. Uhmm justt another question/problem what does it actually mean I used sudo apt-get update and after the updates, this few lines that kinda looks like an error is my ubuntu gonna be fine? :( :
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_SG                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 1,994 kB in 27s (72.4 kB/s)                                            
W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

--Thanks alot! Sorry if I've bad english and ze amount of questions >.<, first time using forums, forgive me if I broke any rules or made any mistakes--

---

### Post by oldfred on 2014-10-05
Have you edited sources or added ppa?
It looks like the ppa.launchpad.net entries either are not correct or just do not exist.
If you manually added those, I would comment them out.

       # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

But now ppa are usually in /etc/apt/sources.list.d folder not in the main sources.list.
I have not edited nor removed a ppa from sources.list.d

---

### Post by yancek on 2014-10-05
> I've a flash drive/thumb drive with windows 8.1 but ubuntu doesn't seem  to read my flash drive/thumb drive in the boot options screen.

I'm not sure what you are trying to do here.  You need to set the BIOS options from setup when you initially boot the computer to boot from the flash drive.  It's possible to put an entry in the Grub boot menu to do it but it certainly won't be there by default and would be more complex than the standard method.

---

### Post by Aurivus on 2014-10-05
> **oldfred said:**
> Have you edited sources or added ppa?
It looks like the ppa.launchpad.net entries either are not correct or just do not exist.
If you manually added those, I would comment them out.

       # Edit Sources
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksu gedit /etc/apt/sources.list

But now ppa are usually in /etc/apt/sources.list.d folder not in the main sources.list.
I have not edited nor removed a ppa from sources.list.d

I'm pretty sure that I didn't edit the sources, since all I did was sudo get updates and sudo install, and for light coding learning purposes. This is my source list: [ATTACH]256975[/ATTACH]

> **yancek said:**
> I'm not sure what you are trying to do here.  You  need to set the BIOS options from setup when you initially boot the  computer to boot from the flash drive.  It's possible to put an entry in  the Grub boot menu to do it but it certainly won't be there by default  and would be more complex than the standard method.

I tried to go into the BIOS options but I don't see my flash drive from the boot options, the boot options for 1 & 2 is ubuntu for my laptop in the BIOS options screen

---

### Post by Aurivus on 2014-10-09
-bump- >.<

---

### Post by oldfred on 2014-10-09
You only can boot from flash drive from UEFI/BIOS. How is Ubuntu installed BIOS or UEFI. You then have to install Windows in the same mode. And flash drive does have to be bootable.
[http://ubuntuforums.org/showthread.php?t=2246751&p=13137145#post13137145](http://ubuntuforums.org/showthread.php?t=2246751&p=13137145#post13137145)


Did you resolve the errors in your sources list with bad ppa? Commented out or removed the incorrect ppa?

---

### Post by Aurivus on 2014-10-11
> **oldfred said:**
> You only can boot from flash drive from UEFI/BIOS. How is Ubuntu installed BIOS or UEFI. You then have to install Windows in the same mode. And flash drive does have to be bootable.
[http://ubuntuforums.org/showthread.php?t=2246751&p=13137145#post13137145](http://ubuntuforums.org/showthread.php?t=2246751&p=13137145#post13137145)


Did you resolve the errors in your sources list with bad ppa? Commented out or removed the incorrect ppa?

Thanks for the solution, I'll give it a try and hope it works, I have an flash drive with windows inside and it's locked. I'm not sure if it's bootable but I'm sure I used the same flash drive to install ubuntu.

I haven't resolve the errors yet, I'm still trying to look for the incorrect ppa. 

Nonetheless, thanks for the help you have provided. :D

---

