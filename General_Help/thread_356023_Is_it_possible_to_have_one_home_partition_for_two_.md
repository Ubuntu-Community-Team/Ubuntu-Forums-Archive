---
title: "Is it possible to have one home partition for two Linux system?"
date: 2007-02-07
forum: General Help
---

### Post by shellhrs on 2007-02-07
I have an IBM TP 600e installed with Windows 2000 and Fluxbuntu. This machine is basically a test machine, so I want to install several flavor of Linux here.

I found an instruction to create a separate home partition [here]("http://www.psychocats.net/ubuntu/separatehome"). I followed the instruction to create the home partition, and it worked perfectly.

Now if I am to install another Linux flavor, say Dreamlinux will I be able to use this home partition? This way, I will be able to have my documents in the home partition, and share them between both Linux system.

My Windows 2000 partition is formatted as FAT32, so I can share files between Linux and it easily, but if Windows 2000 can access the home partition it will be great. I prefer not to use the Windows partition to share files between all three system. Any suggestion?

---

### Post by bodhi.zazen on 2007-02-07
To access ext2/3 partitions from windows : [http://www.fs-driver.org/](http://www.fs-driver.org/)

To access ntfs from Ubuntu : [http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)

If your windows partition is FAT it is even easier.

Yes, you can share /home but I would advise making a /data partition and allowing each OS it's own home.

You can use links like this :

ln -s /mnt/data/music /home/user_name/music

And **Welcome to Fluxbuntu** :p

---

### Post by vigleik on 2007-02-07
It is possible to share the home partition between installs, but it's not advisable. The reason is that linux also puts lots of config files in your home directory (the hidden files, starting with .) and unless you install exactly the same version of every program there might be conflicts. So like bodhi said, it's better to use one data partition, or link things.

---

### Post by shellhrs on 2007-02-09
@ bodhi.zazen:

Thanks for the links.

I'm trying to limit WIndows access to Linux partitions, while maintaining Linux' full access to Windows partition. That's why I didn't install the Windows drivers.

I've read about NTFS-3G when it was still in beta stage (Oct 2006). It was quite stable then. Is NTFS-config stable?

@ vigleik:

So I'm supposed to have a home partition for each Linux installation, and one data partition to share files between them?

Don't you think it'll be better if I don't set a home partition, just a home directory for each installation. Then I can have the data partition separately to share files.

---

### Post by bodhi.zazen on 2007-02-09
> **shellhrs said:**
> @ bodhi.zazen:

Thanks for the links.

I'm trying to limit WIndows access to Linux partitions, while maintaining Linux' full access to Windows partition. That's why I didn't install the Windows drivers.

I've read about NTFS-3G when it was still in beta stage (Oct 2006). It was quite stable then. Is NTFS-config stable? 

You are most welcome. ntfs-config is a gui / front end for ntfs-3g ;)

As far as qulity, yes it is considered beta and I can not vouch for it personally (no ntfs dreve :D )

but I have not heard of any problems. with that said I'm sure there is someone out there who lost data and I am reminded me of what a guru once told me:

It is not a matter of if hardware will fail, but when ...

Back up any critical data you may have, but not "just because" you may try ntfs-3g ;)

Here is a link re : quality - [http://www.ntfs-3g.org/quality.html](http://www.ntfs-3g.org/quality.html)

> @ vigleik:

So I'm supposed to have a home partition for each Linux installation, and one data partition to share files between them?

Don't you think it'll be better if I don't set a home partition, just a home directory for each installation. Then I can have the data partition separately to share files.

LOL I hope I did not confuse you too much :p

You get the general gist of it. 

First make a data partition, iether FAT or ext3 would be my advice. FAT can be read by both OS without any additional drivers, ext3 is better if the data partition is for linux only ...

OK then make 1 swap partition, RAM X2, mak 1 Gb ...

OK now each Linux disrro will need it's own home partition (swap and the data partition will be shared)

When you install each distro will create it's own /home automatically if you do not specify a /home on a separate partition ...

The only things you will need to specify are :

1. / or root partition.

2. swap

3. mount point for your data partition. You may mount it anywhere you like, but I would use a creative name in /mnt or /media. /mnt is used for internal dirves and /media for removable devices, although you can use either with no problem ...

As you install, you should format / but NOT your data partition. Format swap with the first install, then you do not need to although some distro's will format /swap automatically ;)

After the install, make your links in /home/user_name:

ln -s /mnt/data/music /home/user_name/music 

...


HTH 8)

---

### Post by vigleik on 2007-02-10
> **shellhrs said:**
> @ bodhi.zazen:

So I'm supposed to have a home partition for each Linux installation, and one data partition to share files between them?

Don't you think it'll be better if I don't set a home partition, just a home directory for each installation. Then I can have the data partition separately to share files.

Yeah, you might as well not make a separate home partition for each install if you keep your data on a separate partition. It's mostly a precaution to protect your data in case you have to reinstall, so if you don't have anything you need to keep in /usr/home, then there's no reason to.

---

### Post by dcstar on 2007-02-10
> **vigleik said:**
> It is possible to share the home partition between installs, but it's not advisable. The reason is that linux also puts lots of config files in your home directory (the hidden files, starting with .) and unless you install exactly the same version of every program there might be conflicts. So like bodhi said, it's better to use one data partition, or link things.

Exactly, if you are using something like Gnome of both systems, and they happen to be different Gnome versions, then using a common home partition can cause all sorts of issues as there could well be config files that will work on one but not the other - and even crash one of the systems!

---

### Post by katiad on 2007-02-10
I have installed on the same /home partition. The key here is to use the same /partition/, but not the same usernames, so that all the home folders stay unique to each distro.

Hence:
I installed Kubuntu first. My username was katia. My home folder was /home/katia.
Then I installed openSUSE. Set the same /home partition, but made the username: katia_suse. 
I edited both to be sure that I had the same user and group IDs on both distros, to ensure that I could just 'walk in' to either user folder and edit all the files without any permissions problems. (I have been told that this can be a problem... and I have been told it makes no difference. I chose to err on the side of caution, and have had good luck.) 
Set up links to make quick access to both folders.

But having a separate data parition for all the shared stuff would be a simpler process to keep files all in the same place. I didn't, because frankly, I only use the Kubuntu 99.5 percent of the time anyway. But if you were going to have a /data partition, I'd probably make sure to set your GID and UIDs the same in each distro, or else just give very lax permissions allowing anyone to read/write access to those files.

---

