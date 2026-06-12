---
title: "Private PPA Not Updating - how to fix?"
date: 2017-09-19
forum: General Help
---

### Post by AwaitingUserInput on 2017-09-19
OS: Kubuntu 16.04

I have added a PPA to my sources to keep up with the most recent version of RawTherapee, a photo editor. I'm currently running version 5.0-r1-gtk3 and version 5.2 has been out since July. Still, my computer is not updating to the most recent version.

I have limited bandwidth at home, so get my software updates with [apt-offline]("https://launchpad.net/ubuntu/+source/apt-offline"). I use apt-get when at home to apply updates.

A [blog post]("http://rawtherapee.com/blog/linux-repositories-updated") from March on the RawTherapee site says that they changed the names of some packages and to make sure I'm using the correct package. Here is the blog post:> 
All Linux repositories have been updated and the naming of the  RawTherapee packages has changed. Check the information for your  distribution on our [Downloads]("http://rawtherapee.com/downloads") page to make sure you're using the correct package.

Here's the [instructions from RawTherapee]("http://rawtherapee.com/downloads") about how to use their PPA:
> 
This repository is kindly run by [Dariusz Duma]("https://launchpad.net/%7Edhor"), and all questions should be directed to him.

  To install RawTherapee follow these simple steps:

 Open the terminal and paste this code into it:

```
sudo add-apt-repository ppa:dhor/myway
sudo apt-get update
sudo apt-get install rawtherapee
```



If you want a [development version]("http://rawpedia.rawtherapee.com/Getting_Started#Installing_RawTherapee"):         sudo apt-get install rawtherapee-unstable


  RawTherapee should now be installed and ready for use.



Here are the relevant PPAs from my computer:
```
$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ xenial main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ xenial-security main multiverse restricted universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main multiverse restricted universe

```

Also...
```
$ ls -1 /etc/apt/sources.list.d
...
dhor-ubuntu-myway-xenial.list
dhor-ubuntu-myway-xenial.list.save

```

Here is the PPA that I'm trying to pull packages from: [https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=xenial](https://launchpad.net/~dhor/+archive/ubuntu/myway?field.series_filter=xenial)

**Question: **How do I troubleshoot this and make it so apt-offline keeps me up to date with the latest version of my software? Do I need to remove the PPA from the sources list and add it back in, or something else?

Thank you!!!!!

---

