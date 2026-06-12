---
title: "Is it possible to turn my system into Mint without reinstalling"
date: 2014-05-31
forum: General Help
---

### Post by josephellengar2 on 2014-05-31
Hi there!

It is no longer possible to install a stable version of my favorite DE (Cinnamon) on Ubuntu. Therefore, I am going to transition to Mint. Since Mint is based on Ubuntu, is there a way to do this without reinstalling? I don't mind breaking things-- I can reimage my system after a failed attempt, but I don't even know where to start. Would I remove all of my sources.lst and then add Mint repos? If so, does anyone have a list of the addresses for the Mint repos? 

Anyway, I'd appreciate any ideas the community might have.

Thanks!

---

### Post by tgalati4 on 2014-05-31
It would be quicker to perform a clean install of Mint.  Yes, in theory, you could change the repository pointers and try installing the bits and pieces that make Mint.  If your system is not stable, then you could spend hours trying to troubleshoot and fix.

To figure out what you need, go the the correct package tree and make a list of all of the files that need to be installed:  [http://packages.linuxmint.com](http://packages.linuxmint.com)

The Agony Units of an in-place conversion are not worth it in my opinion.  But Mint is a solid distro and worth the time for a fresh installation.

---

### Post by LastDino on 2014-05-31
Certainly possible but not advisable, it is not as simple as installing just different desktop environment, it will take you to do *considerable* neat picking and at the end there is no sureity that it will work perfectly.  

Fresh install is the way to go.

---

### Post by Joel_Ross on 2014-06-01
You could use the mintbackup script which backups current packages and home directory. See deatils here [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html) about installing mintbackup on Ubuntu

Then do a fresh install of Mint (Mint 17 was just released with a LTS until 2019, so I would recommeded installing Mint 17).

Once you have a fresh install of Mint run the mintbackup script and try restoring.
[B]
Please note:[/B] *I have never done this before from Ubuntu, but it seems to work OK moving between Mint versions. *

Keep us posted I would be interesred in knowing if it works.

> **josephellengar2 said:**
>  I don't mind breaking things-- I can reimage my system after a failed attempt

**Definitely recommended**

---

### Post by josephellengar2 on 2014-06-01
Hi everybody! Thanks for the replies!

> **tgalati4 said:**
> It would be quicker to perform a clean install of Mint.  Yes, in theory, you could change the repository pointers and try installing the bits and pieces that make Mint.  If your system is not stable, then you could spend hours trying to troubleshoot and fix.

To figure out what you need, go the the correct package tree and make a list of all of the files that need to be installed:  [http://packages.linuxmint.com](http://packages.linuxmint.com)

The Agony Units of an in-place conversion are not worth it in my opinion.  But Mint is a solid distro and worth the time for a fresh installation.

:) Agony units. I like that. Do you have any advice on the best way to comb through the packages if I happen to try this method?

> **LastDino said:**
> Certainly possible but not advisable, it is not as simple as installing just different desktop environment, it will take you to do *considerable* neat picking and at the end there is no sureity that it will work perfectly.  

Fresh install is the way to go.

I really want to keep my current DE. It's how I have my workflow set up and I'm familiar with it, been using it since Gnome 3 went off the deep end.

> **Joel_Ross said:**
> You could use the mintbackup script which backups current packages and home directory. See deatils here [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html) about installing mintbackup on Ubuntu

Then do a fresh install of Mint (Mint 17 was just released with a LTS until 2019, so I would recommeded installing Mint 17).

Once you have a fresh install of Mint run the mintbackup script and try restoring.
[B]
Please note:[/B] *I have never done this before from Ubuntu, but it seems to work OK moving between Mint versions. *

Keep us posted I would be interesred in knowing if it works.


Thanks for this! I'll try it today. I'm guessing that it won't work but no harm in trying, right? One of the reasons why I didn't want to do a fresh install is because I have changes in so many deep config files that I don't even know everything I've changed.  I would guess that Mint Backup won't pick all of that stuff up but, again, no harm in trying.

---

### Post by LastDino on 2014-06-01
Please make sure you've clones the current installation then. Clonezilla is quite handy in these situations. :3

---

### Post by Joel_Ross on 2014-06-01
> **josephellengar2 said:**
> One of the reasons why I didn't want to do a fresh install is because I have changes in so many deep config files that I don't even know everything I've changed.

Most config files for Desktop Applications are stored under your home directory e.g Firefox ,but services like Apache are store under the /etc directory. Because your wanting to use Cinnamon you may have desklets etc installed these configs should be restored if you copy over your whole home directory (make sure you copy the .filename hidden files very important, this is where all the config files sit).  

If you do have services running .e.g Apache etc, it might be worth backing up your current Ubuntu /etc/ directory and dumping in a safe place on the new Mint install (but **DONT** restore to Mint's /etc/) then you can reference it when things aren't working as they did on your Ubuntu install.

> **josephellengar2 said:**
> I'm guessing that it won't work but no harm in trying, right?

Only time will tell .... one of the best things about Linux is the tinkering. Just make sure you have that image ready just in case :) 

> **josephellengar2 said:**
> I would guess that Mint Backup won't pick all of that stuff

Just make sure you backup the hidden files in your home directory as this is where all your config files are for Desktop Apps including your Cinnamon configs

---

### Post by tgalati4 on 2014-06-01
I always recommend dual boot.  Keep your working distro and put the new distro on a new partition.  They can share the swap (if both are 64-bit) and you have a data backup and can always go back to your working distro when things aren't quite working with 14.04.  Because several updates will be flowing into 14.04, there is a good chance for regressions over the next couple of years.

Because Mate and Cinnamon have different package names so that they don't conflict with gnome2 and gnome3 packages, it is quite tedious to figure out the correct packages that you need to build the complete distro.  The advantage is that you can have 4 different evironments installed and pick which one you want to run that day--all without interference.

---

