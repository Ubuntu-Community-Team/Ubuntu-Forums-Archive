---
title: "Using Ubuntu 19.10 In 2023 - reinstall Samba via PPA or find package?"
date: 2023-08-19
forum: General Help
---

### Post by DJonsson2008 on 2023-08-19
I've  custom video mixing software that will not run on Ubuntu past 19.10, due to a complex list of dependencies.
Upgrading to 20.04 or 22 is out of the question.

I accidentality removed Samba from this workstation attempting reinstall and reconfig samba.
I was surprised that Samba was not on the 19.10 DVD I keep for a local repository for this machine, but of course it makes sense now.

Questions
Is there a repository anywhere that might have Samba for 19.10?

Where can I find a deb package for Samba that will work on Ubuntu 19.10?

Is there a ppa I can use to reinstall Samba on this  Ubuntu 19.10 distro?

Any suggestions, hunches or ideas appreciated.

---

### Post by TheFu on 2023-08-19
19.10 support ended 3 yrs ago, in 2020.  Sorry.  There have been a number of remote root exploits over networking since that time. It isn't safe to run 19.10 anywhere with networking enabled, so Samba isn't really an option.

You seem to be screwed.  If it were me and I wanted to reduce my liability, I'd put that custom software into a virtual machine/linux container, and upgrade everything else to a supported release.

BTW, you might be able to find an "archive.x.x.ubntu.com" repo somewhere. It will not have been updated since June of 2020, when 19.10 support ended.  Might be a good idea to clone everything in that archive until you can get the custom software updated to 22.04 or 24.04.  Heck, if the software supports 18.04, then you can get onto an ESM contract and at least the base Ubuntu stuff will be maintained and patched till April 2028.

Best NOT to run important software on non-LTS releases.

---

### Post by guiverc on 2023-08-19
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by MAFoElffen on 2023-08-19
But then: "18.04 LTS", if you have Ubuntu Pro with ESM enabled... (esm-apps & esm-infra)
[quote="Ubuntu Pro"]
Initial application  support coverage consists of over 30 upstream applications, including  many popular projects such as Kafka, Kubeflow, OpenJDK, PostgreSQL,  Telegraf, [COLOR=#ff0000]Samba[/COLOR], and Vault. We continue to add to the list based on  prioritised customer demand.
[/quote]
RE: [https://ubuntu.com/blog/ubuntu-pro-beta-release](https://ubuntu.com/blog/ubuntu-pro-beta-release)

To do that, you would have to migrate back to 18.04 LTS. But you said that your specific requirements go up to 19.10, and not past it, but did not mention that it did not work on 18.04. That would give you until 2028...

---

### Post by DJonsson2008 on 2023-08-20
Thanks for your constructive advice.

---

### Post by DJonsson2008 on 2023-08-20
Thanks to your responses, they gave me some ideas as to where to look around and find something. 

This video from July 2023
[https://www.youtube.com/watch?v=7rvcwAyfO9Q](https://www.youtube.com/watch?v=7rvcwAyfO9Q)

And these links
[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)
[http://old-releases.ubuntu.com/ubuntu/dists/eoan/](http://old-releases.ubuntu.com/ubuntu/dists/eoan/)

I&#8217;ll give these a try and then report back here.

It should be noted that this machine is primarily for offline. 
And when sporadically going online uses wifi only.

I like the idea of rolling back 18.04 as the software 
I'm using (GLMixer) does have earlier versions that were intended for 18.04, 
yet the software for 19.10 has more features and is more stable.  

In any case now though I'm going try the repositories listed above, 
and then clone & rotate my 19.10 OS SSD to avoid mishaps like this in the future.

---

### Post by TheFu on 2023-08-20
1 backup isn't sufficient. Look up _3-2-1 backups_.
In general, backups need to happen either daily or weekly, be automatic, versioned, and be tested to ensure a restore actually works.  I've showed up at client locations where they thought they'd have over a year of backups only to find all their backups were corrupted due to a setup mistake. They had ZERO backups, but had been spending over a year doing them.  That's a bunch of wasted effort for no results and more importantly, no safety.

---

### Post by DJonsson2008 on 2023-08-24
Sorry I meant to say clone & rotate.

Please keep in mind this workstation OS SSD is static, work files are stored on external drives and on NAS.
In this case when I say backup I should of said cloning the SSD and testing that it boots and works. 
Clone and rotate, and move clone offsite are part of this shops ritual.

---

### Post by DJonsson2008 on 2023-08-24
This issue has been solved by updating sources.list per instructions on item #6 in this thread.
NOTE: This is a unique one-purpose primarily offline Ubuntu eoan 19.10 workstation that uses legacy software

Sources list entries and the command line commands used in this process follow.

Sources.list entries
deb [trusted=yes] [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-proposed main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-security main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-updates main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-proposed main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) eoan-backports main restricted universe multiverse

# After updating sources.list to eoan old-releases 
sudo apt update 
# Verified packages update was successful then...
sudo apt-get remove --purge samba samba-*
sudo apt autoremove

# I had some issues with these package's versioning and removed them.
sudo autoremove libtdb1 --purge
sudo apt-get remove libwbclient0

# To test integrity of existing packages.
sudo dpkg --configure -a 
sudo apt-get update --fix-missing

# Install samba and related components
sudo apt update
sudo apt upgrade
sudo apt install samba 
sudo apt install smbclient
sudo apt install cifs-utils
sudo apt install gvfs-backends
sudo apt install nautilus-share

---

