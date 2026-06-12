---
title: "My dad has some worries about upgrading from Dapper, help?"
date: 2007-09-27
forum: General Help
---

### Post by rainwalker on 2007-09-27
Okay, my dad is still running Dapper because he wants to stick with LTS releases because he uses his computer for work, so he can't afford to risk anything breaking.
I think the biggest worry he has is VMware breaking, because he needs it to run XP for all of his work stuff. I'm not sure what version he's running, but it's from a little before VWware was added to the repos. 
I also know that he hardly ever installs updates (or he checks closely which ones he installs) because he's so worried about things breaking, so I don't know what he's lacking besides kernel updates.

I really don't know what I'm getting at here, I guess I'm just wondering if anyone has advice as to how he should handle upgrading.

---

### Post by overdrank on 2007-09-27
> **rainwalker said:**
> Okay, my dad is still running Dapper because he wants to stick with LTS releases because he uses his computer for work, so he can't afford to risk anything breaking.
I think the biggest worry he has is VMware breaking, because he needs it to run XP for all of his work stuff. I'm not sure what version he's running, but it's from a little before VWware was added to the repos. 
I also know that he hardly ever installs updates (or he checks closely which ones he installs) because he's so worried about things breaking, so I don't know what he's lacking besides kernel updates.

I really don't know what I'm getting at here, I guess I'm just wondering if anyone has advice as to how he should handle upgrading.

Hi if its not broke then don't fix it. He needs it for work and it would probably be a great hassle. Just my two cents. :)

---

### Post by rainwalker on 2007-09-27
Yeah, but what about when support for Dapper ends? And the next LTS comes out?
He's going to have to update eventually

---

### Post by shae on 2007-09-27
When the next LTS comes out (8.04 April 2008), he should reformat and start anew.

---

### Post by strabes on 2007-09-27
Hardy Heron is the next LTS release. He should do a fresh install of it when it comes out.

---

### Post by dasunst3r on 2007-09-28
If your Dad wishes to stick with LTS, then please respect his wishes.  The next LTS is coming out in April 2008.  If you are afraid of breaking his current installation, just pop in a different hard drive to his machine, do the install, and if everything works fine, migrate.

---

### Post by trippinnik on 2007-09-28
I'd got with the others and even say why bother upgrading when the new LTS comes out.  It's not like he's running a server (thus worried about intrusion) or needs some hardware to work.  Why do you want him to upgrade?

---

### Post by overdrank on 2007-09-28
All the posters have great points and when the nest LTS comes out he and u can set aside a time to backup the system and set up the new one and that will give you time to set all the programs he needs to get his work done. Good luck! :guitar:

---

### Post by FuturePilot on 2007-09-28
I'd say just leave it alone now. It works and he's happy with it. Perhaps when the next LTS comes out in 2008, you can find a time to do a backup and a fresh install. For now though I would just leave it as is.

---

### Post by Neobuntu on 2007-09-28
Backup, backup, backup. Carefully.

Leave the old system installed!

When the new LTS comes out, wait a while longer. Then, if reports are not negative, do a clean install (NOT OVER YOUR OLD SYSTEM) by a new partition (remember your backups), another drive or another computer.

Use your new system for six months before deleting your old system install.

Find native, open applications instead; as you can. The progression is swift!

No one has said that one can't simply use a dual boot with Windows. Windows is just more hassle and upkeep than only one main Kubuntu. 

vmware is more complicated than a simple dual boot. It's your choice. There are pros and cons.

What's the status of your target windows apps under WINE? I've notice about one year old Win app versions tend to be working with WINE. So don't be to quick to upgrade an app (tier) with Windows.

May Windows continue to become less and less significant.

---

### Post by psusi on 2007-09-28
1) Make a full backup
2) Shrink the existing partition to free up space for the new install ( assuming disk is large enough )
3) Install new release to the new partition
4) Dual boot for a while
5) Finally, delete the old install and expand the new partition

After messing with the partitions, you will need to reinstall grub.

---

### Post by Tucatts on 2007-09-28
Ok I am a self employed old guy who needs his computers to work just like your Dad. I have two machines in my office ( built them almost 4 years ago) Both computers are dual booted with windows XP( separate hard drives). One computer has Dapper and XP and the other Feisty and XP. X- org breaks quite often on the Dapper updates but I have written down the fix for that and it takes me about 10 minutes to fix all that and get back up and running. Do a search for that process here in the forum and you will get all the info you need. You should be doing the updates in my estimation. I use Ubuntu 98% of the time now and only use XP when I want to play a game or use one scanner I have that will not work with Ubuntu. I have a Epson all in one machine CX5000 that works like a charm with Feisty so I am using Ubuntu for almost all of my business needs. Both Dapper and Fesity have been stable and when 7.10 is released I am going to do a new install over my current Dapper install. I have an external HD that works great with Ubuntu and XP and so I am backed up.
Good luck!
Tucatts

---

### Post by cslfasgard on 2007-09-28
if he is running windows in a shell vm then all he has to do is backup all the vmware files (vmdk, vmx, vmsd)... the whole directory all that stuff is in.  I would do it when the shell isnt running so that you get everything.

once the linux and vmware is back and up to date just open the windows shell again that you backed up and it should load right up.


you could test it now by backing everything up..  copying that backup to a different machine with the latest and greatest on it... and firing it up.

Thats the beauty of vmware shells.     It can be easily moved.

I created some vm's in vmware workstation for windows then copied them to an ubuntu with vmware server install.  They fired right up.

---

