---
title: "Upgrade button"
date: 2012-12-19
forum: General Help
---

### Post by Zane Pepper on 2012-12-19
How reliable is the upgrade button? I have heard it often breaks the system or have the fixed this issue? I am tempted to use it so I can have the latest version as soon as it comes out.

---

### Post by zombifier25 on 2012-12-19
The upgrade button, or any upgrade methods actually, has about a 50-50 (or 75-25, if [this poll](http://ubuntuforums.org/poll.php?do=showresults&pollid=7399) is correct) chance of upgrading successfully or messing up your system, so you should probably back up your home folder before going with the procedure.

---

### Post by Zane Pepper on 2012-12-19
> **zombifier25 said:**
> The upgrade button, or any upgrade methods actually, has about a 50-50 (or 75-25, if [this poll]("http://ubuntuforums.org/poll.php?do=showresults&pollid=7399") is correct) chance of upgrading successfully or messing up your system, so you should probably back up your home folder before going with the procedure.

I don't like those odds. I will just stick with 12.04 LTS until the next LTS version comes out I guess.

---

### Post by 3rdalbum on 2012-12-19
> **zombifier25 said:**
> The upgrade button, or any upgrade methods actually, has about a 50-50 (or 75-25, if [this poll](http://ubuntuforums.org/poll.php?do=showresults&pollid=7399) is correct) chance of upgrading successfully or messing up your system, so you should probably back up your home folder before going with the procedure.

I've only had one failed dist-upgrade, and that was to a version still in heavy development. However I do tend to do clean installs these days as they actually seem to take a shorter amount of time and effort. ("These days" being since 2009).

I've never heard of a failed dist-upgrade causing loss of data in your home directory. I don't believe it's likely enough to be a concern. However it's certainly a great idea to take the opportunity to back up your data; nobody backs up their data often enough.

---

### Post by snowpine on 2012-12-19
Most users who succeed with their updates read this link first (paying particular attention to the "we recommend" statements):

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Most users who fail it's for 1 of 3 reasons:

1. A bug beyond their control
2. Not test-driving a live DVD/USB of the new release to make sure it runs on their hardware and **that they like it!!!**
3. 3rd party repositories/PPAs

A fresh reinstall is foolproof with 100% success rate. Having a separate /home partition makes this easy.

---

### Post by Zane Pepper on 2012-12-19
> **3rdalbum said:**
> I've only had one failed dist-upgrade, and that  was to a version still in heavy development. However I do tend to do  clean installs these days as they actually seem to take a shorter amount  of time and effort. ("These days" being since 2009).

I've never heard of a failed dist-upgrade causing loss of data in your  home directory. I don't believe it's likely enough to be a concern.  However it's certainly a great idea to take the opportunity to back up  your data; nobody backs up their data often enough.
I have not backed up my data in over a year. I don't have a HDD big enough to back up my internal HDD and I never have the money to buy a new one :(

> **snowpine said:**
> Most users who succeed with their updates read this link first (paying particular attention to the "we recommend" statements):

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Most users who fail it's for 1 of 3 reasons:

1. A bug beyond their control
2. Not test-driving a live DVD/USB of the new release to make sure it runs on their hardware and **that they like it!!!**
3. 3rd party repositories/PPAs

A fresh reinstall is foolproof with 100% success rate. Having a separate /home partition makes this easy.

I have a separate /home partition because I was always told it was a good idea to have it, but I am not sure what to do with it when I reinstall. Do I set the mount point to /home, but won't the write over the existing data? I useally just format it because I don't have anything too important in there, I have a separate "data" partition for my files.

---

### Post by snowpine on 2012-12-19
> **Zane Pepper said:**
> I have a separate /home partition because I was always told it was a good idea to have it, but I am not sure what to do with it when I reinstall. Do I set the mount point to /home, but won't the write over the existing data? I useally just format it because I don't have anything too important in there, I have a separate "data" partition for my files.

I will let an Ubuntu user answer this for you, as I am unfamiliar with the current installer.

I will point out, however, that if you make a user error at this stage (or if there's a bug in the software, not unheard of with Ubuntu) then you risk overwriting your data partition. Therefore I cannot advise doing a clean reinstall until you have straightened out your backup situation. If you calculate how many hours it would take you to recreate that data (even if you only value your time at minimum wage) then you'll see that a $99 external hard drive is a good investment. :)

---

### Post by zombifier25 on 2012-12-19
> **Zane Pepper said:**
> I have not backed up my data in over a year. I don't have a HDD big enough to back up my internal HDD and I never have the money to buy a new one :(



I have a separate /home partition because I was always told it was a good idea to have it, but I am not sure what to do with it when I reinstall. Do I set the mount point to /home, but won't the write over the existing data? I useally just format it because I don't have anything too important in there, I have a separate "data" partition for my files.

When installing, choose "Something Else" (which means advanced partitioning). Then choose your previous /home partition, choose to set it as /home **WITHOUT** ticking to format it. Do the same to /, but this time tick to format it.

---

### Post by Zane Pepper on 2012-12-19
> **snowpine said:**
> I will let an Ubuntu user answer this for you, as I am unfamiliar with the current installer.

I will point out, however, that if you make a user error at this stage  (or if there's a bug in the software, not unheard of with Ubuntu) then  you risk overwriting your data partition. Therefore I cannot advise  doing a clean reinstall until you have straightened out your backup  situation. If you calculate how many hours it would take you to recreate  that data (even if you only value your time at minimum wage) then  you'll see that a $99 external hard drive is a good investment. :smile:
I am going to get a new external HDD as soon as I can, I am starting to get really paranoid about my data.

> **zombifier25 said:**
> When installing, choose "Something Else" (which means advanced partitioning). Then choose your previous /home partition, choose to set it as /home **WITHOUT** ticking to format it. Do the same to /, but this time tick to format it.
Thanks, I will do that next time I upgrade.

---

### Post by 3rdalbum on 2012-12-19
> **Zane Pepper said:**
> Thanks, I will do that next time I upgrade.

Just a note, to get the word out there: Even if /home is on the same partition as /, you can still do a clean install without losing your existing data.

Either choose the "Upgrade" option in the installer, or if not available go to Something Else and choose your existing / to have the mount point "/". But do NOT format the partition.

The installer will give you a message about replacing existing system directories. Click Continue. Your clean install will continue, but it will preserve your /home and reinstall new versions of your existing packages.

---

