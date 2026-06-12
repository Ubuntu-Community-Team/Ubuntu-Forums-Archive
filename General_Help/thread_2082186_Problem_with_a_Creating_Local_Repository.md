---
title: "Problem with a Creating Local Repository"
date: 2012-11-08
forum: General Help
---

### Post by soccerevolution on 2012-11-08
Hey all,

I have been trying to create a local (offline) repository to install applications without using the online repositories, where I'm basically using my USB stick as the local repository.  

-- QUESTION: Does anyone have an idea of what is happening and more specifically, what is this ***Meta-index file (malformed Release file?)*** ??  This can be seen below.

I have already generated the GPG key to create a "Trusted" repository and generated the proper hierarchy.  Basically, when I try to run **sudo apt-get update**, I get the following:

user@user:/media/7C9B-0F86/local_repository/localrepository$ sudo apt-get update
Ign file:/media/7C9B-0F86/local_repository/localrepository/  Translation-en_US
Get:1 file:  Release.gpg [316B]          
Get:2 file:  Release [220B]                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
***W: Failed to fetch file:/media/7C9B-0F86/local_repository/localrepository/Release  Unable to find expected entry  Packages in Meta-index file (malformed Release file?)***

The ***/media/7C9B-0F86/local_repository/localrepository/ ***is the USB stick I'm using for my local repository.  

My system architecture is **amd64** and the release is **Ubuntu 10.04 LTS - the Lucid Lynx**.

Thanks much.


Al

---

