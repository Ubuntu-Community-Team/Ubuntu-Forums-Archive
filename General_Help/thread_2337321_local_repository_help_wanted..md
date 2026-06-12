---
title: "local repository help wanted."
date: 2016-09-16
forum: General Help
---

### Post by mintmag on 2016-09-16
Hi guys. So I've been using apt-mirror to create a local repository I seem to be half way to getting it to work. I've read a lot of tutorials on how this is done but I'm still not sure what I'm doing wrong.

I thought I got most of the local repository working but Ubuntu doesn't seem to want to use it.

Also my antivirus alerted to some of the files in the repository. Weird   

I’ll send a few screen shots of what I’m doing. I seem to be able to create the local repo but I can’t seem to get ubuntu to pull resources from it.

This was done in a virtual machine.

Here is the directory structure 
[https://drive.google.com/file/d/0B5PLItq4rD2jVzlzM0d2WUpDbGc/view?usp=sharing](https://drive.google.com/file/d/0B5PLItq4rD2jVzlzM0d2WUpDbGc/view?usp=sharing)

 Mirror List
[https://drive.google.com/open?id=0B5PLItq4rD2jQkRLOHBJNjU5Vlk](https://drive.google.com/open?id=0B5PLItq4rD2jQkRLOHBJNjU5Vlk)

Sources
 [https://drive.google.com/open?id=0B5PLItq4rD2jakthdXRkLXlqWDg](https://drive.google.com/open?id=0B5PLItq4rD2jakthdXRkLXlqWDg)

Terminal error 
[https://drive.google.com/open?id=0B5PLItq4rD2jeTEwSEhNSmRjWVU](https://drive.google.com/open?id=0B5PLItq4rD2jeTEwSEhNSmRjWVU)

---

### Post by T.J. on 2016-09-16
Your repository is not configured properly. I'd check that you have your paths set up correctly.

The terminal error is the result of not being able to retrieve the Packages index file inside of the repository.  You need to generate this if you are hosting your own personal packages, or do a complete mirroring instead of a partial, if they are official packages.

An easy way you can generate your own indexes is by installing the dpkg-dev package and using dpkg-scanpackages. However, all packages have to be signed with a valid signing key that you have on your keychain.   Without it, you will get a security warning every single time.

Also, just a comment, it looks in the screenshot as if you are using a Windows drive for storage.  If that is the case, I recommend against it vigorously.  Windows and NTFS do** not** respect UNIX file conventions.  It can and **will** mangle files.  For example, UNIX systems (like Linux) are case sensitive, Windows is not.  If you must use a Windows machine, I recommend a drive image or a native EXT4 partition for storing the files from the mirror.

---

### Post by mintmag on 2016-09-16
I've learned that the hard way yes. So what I'm trying to do is a complete mirror of the repositories. I'm not sure if EXT 4 will work with a virtual machine but it's worth a try. As for the configure. Isn't scan packages for downloaded .debs? Also I'd like the repo to be protable so I can take to any ubuntu based system and use it.  Would apache2 be better for this?

---

### Post by ian-weisser on 2016-09-16
Creating your mirror isn't a big deal. Maintaining and updating the mirror can become cumbersome without a bit of planning.

I'm not sure how portability helps you, unless you are working with offline machines.
The problem of installing and updating to offline machines has been solved several times: aptoncd and apt-zip are both excellent, safe, secure solutions.

---

### Post by mintmag on 2016-09-17
I simply prefer it for control. I also have an offline machine. What methods would be good to maintain the entire repo and keep it portable? apache2?

---

### Post by ian-weisser on 2016-09-17
Look at the apt-mirror package for mirroring all or part of the Ubuntu repositories across a network to your online server. (You said you did this part already)
Look at the apt-zip package for installing and updating offline systems from whatever mirror you prefer.
Neither requires Apache.

---

### Post by mintmag on 2016-09-17
So how do I make the system use the local repo?

---

### Post by ian-weisser on 2016-09-17
Change a system's /etc/apt/sources.list to point to the new mirror. (You did this part already)
Did you generate an index file like T.J. pointed out in post #2?

---

### Post by mintmag on 2016-09-17
I type dpkg-scanpackages /mnt/hgfs/repo/mirror/archive.ubuntu.com/ubuntu so far it just seems to hang there.

I don't know I can't seem to get this to work I don't know why it isn't working.

---

### Post by mintmag on 2016-09-17
> **T.J. said:**
> Your repository is not configured properly. I'd check that you have your paths set up correctly.

The terminal error is the result of not being able to retrieve the Packages index file inside of the repository.  You need to generate this if you are hosting your own personal packages, or do a complete mirroring instead of a partial, if they are official packages.

An easy way you can generate your own indexes is by installing the dpkg-dev package and using dpkg-scanpackages. However, all packages have to be signed with a valid signing key that you have on your keychain.   Without it, you will get a security warning every single time.

Also, just a comment, it looks in the screenshot as if you are using a Windows drive for storage.  If that is the case, I recommend against it vigorously.  Windows and NTFS do** not** respect UNIX file conventions.  It can and **will** mangle files.  For example, UNIX systems (like Linux) are case sensitive, Windows is not.  If you must use a Windows machine, I recommend a drive image or a native EXT4 partition for storing the files from the mirror.


The scanpackges didn't work for me I'm not sure why I typed dpkg-scanpackages /mnt/hgfs/repo/mirror/archive.ubuntu.com/ubuntu


I'm not sure what to do here. Half the tutorials I find say to create a symbolic links with apache2 but that's just not working either

---

### Post by ian-weisser on 2016-09-17
> **mintmag said:**
> The scanpackges didn't work for me I'm not sure why I typed dpkg-scanpackages /mnt/hgfs/repo/mirror/archive.ubuntu.com/ubuntu

Was there an error message?
If so, what (exactly) did it say?

---

### Post by mintmag on 2016-09-18
Oh hey guys with a directory like this [https://drive.google.com/file/d/0B5PLItq4rD2jVzlzM0d2WUpDbGc/view](https://drive.google.com/file/d/0B5PLItq4rD2jVzlzM0d2WUpDbGc/view)


when it comes to adding the repo to sources.list is it necessary to add the pool and dists to the address like this [https://drive.google.com/file/d/0B5PLItq4rD2jVzlzM0d2WUpDbGc/view](https://drive.google.com/file/d/0B5PLItq4rD2jVzlzM0d2WUpDbGc/view)

This is the part that really confuses me

---

### Post by mintmag on 2016-09-19
Hey guys after downloading the repository I get this error message can't open postmirror.sh" What does this mean

[https://drive.google.com/open?id=0B5PLItq4rD2jTEdYRlptUjNjU1U](https://drive.google.com/open?id=0B5PLItq4rD2jTEdYRlptUjNjU1U)

---

### Post by T.J. on 2016-09-19
> **mintmag said:**
> The scanpackges didn't work for me I'm not sure why I typed dpkg-scanpackages /mnt/hgfs/repo/mirror/archive.ubuntu.com/ubuntu



I'm not sure what to do here. Half the tutorials I find say to create a symbolic links with apache2 but that's just not working either


If the repo is being stored on a non-native Linux partition, please do not expect any of the tools to work properly.  That said, here is an example script to update an archive directory: 

```
#! /bin/bash


cd /usr/local/dists
dpkg-scanpackages .  > Packages

```

You can then add a simple line to your sources:

```
deb  file:/usr/local/dists ./
```

This presupposes a very simple setup where all the packages are dumped into a single folder.  If you want better management, you will need to do some appropriate reading.

---

### Post by T.J. on 2016-09-19
> **mintmag said:**
> Hey guys after downloading the repository I get this error message can't open postmirror.sh" What does this mean

[https://drive.google.com/open?id=0B5PLItq4rD2jTEdYRlptUjNjU1U](https://drive.google.com/open?id=0B5PLItq4rD2jTEdYRlptUjNjU1U)


This means that the postmirror script is either not installed, does not have the proper permissions, or is otherwise unusable.

Please do not consider my terse responses an unwillingness to help.  I want to help you, but I haven't much information about the specifics of your setup, and when managing your own mirrors sometimes it is best to learn by trial and error.

---

### Post by mintmag on 2016-09-20
Okay I managed to run the dpkg-scannpackges but I'm still getting this and it's still not finding the main packages. 

[https://drive.google.com/file/d/0B5PLItq4rD2jUWNQbjhReDdyYnc/view?usp=sharing](https://drive.google.com/file/d/0B5PLItq4rD2jUWNQbjhReDdyYnc/view?usp=sharing)


Again this is not on NTFS this is now on EXT4

---

### Post by mintmag on 2016-09-21
Bump

---

### Post by mintmag on 2016-09-22
Bump

---

### Post by T.J. on 2016-09-28
Still having problems?

---

### Post by mintmag on 2016-09-29
> **T.J. said:**
> Still having problems?

Yes though I have made some breakthroughs. This was done with Mint since I find it a bit easier to use. Here's a link to the latest info [https://forums.linuxmint.com/viewtopic.php?f=47&t=230611&p=1221504#p1221504](https://forums.linuxmint.com/viewtopic.php?f=47&t=230611&p=1221504#p1221504) feel free to post either there or here. I'm so close to getting this to work. I just need to find out why it's not seeing the files. They are there but apt isn't seeing it.

---

### Post by mintmag on 2016-10-04
I found something that kind of works but also kind of doesn't. I added the lines dir::cache::archives /mounted/partition/repo; dir::state::lists /mounted/partition/lists; This seems to work for installing debs from the archive. But when I take it to a brand new installation of Ubuntu or Mint it doesn't

---

