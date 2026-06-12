---
title: "Distro upgrade from local repo"
date: 2020-02-08
forum: General Help
---

### Post by daryl9 on 2020-02-08
I just created a local repo with the following distribution, Trusty, Xenial and Bionic.   I did a fresh install of Trusty, patched and updated it from the repo and now I want to upgrade it to Xenial.  I tried the **do-release-upgrade** command, but it came back with nothing available, or something like that (I don't remember the exact wording). 

The repo is on NAS storage and shared out as CIFS.  I mount the share on the machine that I want to upgrade and modify the source.list file to point to a file rather than HTTP, e.g. "deb file:/mnt/ubuntu trusty main restricted" etc....  The repo was created using apt-mirror, so it should be created just like the repo that is found on line.  Am I missing something? What causes Ubuntu to decide that an distribution upgrade is available?  Do I need something else in the repo?  

Any advice is appreciated.

Thank you.

Daryl

---

### Post by deadflowr on 2020-02-08
Check your release-upgrade flag in /etc/update-manager/release-upgrades.
Should be set to lts.
(Prompt=lts at the bottom)

Edit: If it is set to lts and doesn't work, you might try setting it to normal, since 14.04 to 16.04 can be considered a normal upgrade.
(Since there are no other upgrades between the two anymore. The only direct upgrade for it from now is 14.04 to 16.04)

---

### Post by daryl9 on 2020-02-08
I'll give that a try.  Thank you.

Daryl

---

### Post by daryl9 on 2020-02-08
Hello,

Sorry but that did not work. I just get back "The software on this computer is up to date".  

When update-manager runs, what does it look for that tells it that there is a new release?  Do I need to add something to sources.list to get it to look at Xenial?

Thanks

Daryl

---

### Post by daryl9 on 2020-02-23
Hello,

Its been a while since I updated this thread and it's dropped down the list a way's, but I'm still trying to get this to work and I thought that I would update it and see if anyone can help me figure out how to make this work.

So, just to recap, I am trying to setup a local repo with the following distributions:  Trusty, Xenial and Bionic.  I do a fresh install from Trusty, then I want to upgrade to Xenail, then to Bionic.  I'm actually using Edubuntu, which is Trusty v14.04.  Edubuntu hasn't been updated since 2015.  If the maintainers of Edubuntu were to keep it updated, then I really wouldn't have to do all of this, but it doesn't appear that the project has any life left in it, and I need to find a work around solution to keep the packages up-to-date on my end.  The way that I have this setup is I have a single device that is connected to an external WIFI which gives me access to the public repos.  That device is also on my little internal network.  I have a NAS device setting on the internal network exporting a cifs share for the repos.  So this one device can see both internal and external, however, the machines that I build can only see the internal network.  

I do a fresh Edubuntu install, mount the cifs share to the machine, update the sources.list file to see that mount and execute apt update.  I apt finds the Trusty repo and tells me there are 500+ packages that need to be upgraded.  Great.  Works as it should.  However, I can't get the upgrade from Trusty to Xenial to work.  No matter what i do, I just get "No new release found".  I feel that I must be missing something.  Perhaps a configuration somewhere? 

How does do-release-upgrade work?  Does it check the sources.list file for a new upgrade?   If I do a fresh install on a machine that has outside connectivity, then the sources.list points to an external repository such as [http://archive.ubuntu.com/](http://archive.ubuntu.com/).   If I follow that URL, it takes me to ubuntu, then to the dists directory and then this list of distributions.  Here I can pick from trusty, xenial, bionic etc...  do-release-upgrade must follow the same path.  My repo was created by apt-mirror, so I would think that the do-release-upgrade would follow the path the same whether its an external repo, or my internal repo.   Perhaps it does, but just isn't finding what it needs to recognize an upgrade is available?  

What does do-release-upgrade look for when deciding if an upgrade is available or not?  Perhaps apt-mirror isn't downloading everything, which I know that it doesn't, but that is another story.   Is there a specific file or directory that it looks for that it's not finding? I've been searching, searching and searching trying to find how the program works, but there just isn't any documentation out there, other than the help, which doesn't really help much.

Any ideas or suggestion on how to do a dist upgrade from a local repo?

Thanks

Daryl

---

