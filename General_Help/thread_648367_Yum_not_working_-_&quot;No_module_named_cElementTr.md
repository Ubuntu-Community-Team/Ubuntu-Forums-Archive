---
title: "Yum not working - &quot;No module named cElementTree&quot;"
date: 2007-12-23
forum: General Help
---

### Post by ahfu on 2007-12-23
Hi all,

I am unable to complete the "yum" command. It gives error - "No modules named cElementTree". 

I am currently using Ubuntu v7.10 and is running it on my laptop - Acer Extensa 4260Z

As i am a first time linux user, I would appreciate if replies are kept at a newbie level.. Thanks!

Ah Fu

---

### Post by oldos2er on 2007-12-23
Ubuntu doesn't use yum; it uses apt-get or aptitude. Please see [https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

---

### Post by ahfu on 2007-12-23
Oh! Haha... Okie... Thanks! 

Ah Fu

---

### Post by CCNA_student on 2007-12-23
You should be using tar.gz

---

### Post by Animal Mother on 2007-12-24
> **CCNA_student said:**
> You should be using tar.gz

yeah, that won't scare him off of linux! 

you could try sudo apt-get install yum 

I like yum too, I am a fedora guy at heart :)

---

### Post by ubuntu27 on 2007-12-25
What program are you tryin to isntall? If it is infamous, it is most likely to be in the Ubuntu's repositories.

Open-up SYnaptic Package Manager [System menu/Administration/Synaptic Package Manager]

1) Click on Reload to update the list of available packages.

2) Click on Search, and type what you are looking for.

3) If you found it, click on the box in order to mark for installation. 

4) Click on Apply.

5) Enjoy

More info on ["How to install ANYTHING in Ubuntu!"]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Bart1345 on 2008-01-01
Hi I have same problem when I try to install YUM.

Why am I using YUM ?

There is a lot of updates to Adobe's Flash Player 9 plugin.

Adobe has set up a YUM repository installation (Option 3)
[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)

With YUM it is very easy to get the new updates.

Is there a way to make this work with apt-get ?

Is there another way to get Flash Player updates ?

/Bart

---

### Post by HuskyDev on 2008-01-04
I'm having the same issue, even after installing yum from source (v3.2.8).  Yum installed from source ( 'make' then 'make install' from a fresh untar) and then run produces this:

```
No module named yum
```

As far as I'm concerned, Yum is broken in 7.10, meaning my productivity has come to a screeching halt.  If this is not resolved soon, I will have to go back to 7.04.

Of course, I don't know anything about python, so maybe there is an easy workaround that someone could come up with?

---

### Post by HuskyDev on 2008-01-04
The following code downgrades the cElementTree and elementTree packages and is supposedly a fix.  I haven't tried it though.

```

sudo dpkg -r --force-depends python-celementtree
sudo dpkg -r --force-depends python-elementtree
sudo dpkg -i (your directory)/python-elementtree_1.2.6-10ubuntu2_all.deb
sudo dpkg -i (your directory)/python-celementtree_1.0.5-8ubuntu2_i386.deb

```

The .deb packages shouldn't be too hard to find.  If you try this, let me know how it goes.

---

### Post by kanalconsulting on 2008-01-13
I had the same problem.

I was trying to install adobe flash via their website because the non-free version available via adept manager downloaded but had mdsum mismatch no matter how manny times I tried to install it.

I tried rpm but it failed due an dependency error.  I got an error saying it needed /bin/sh.

So, I thought I'd try yum.  HuskyDev's suggested changes to ElementTree worked!  

However, I got the following errors now:  See below:

sudo yum install adobe-release-i386-1.0-1.noarch.rpm
Warning, could not load sqlite, falling back to pickle
Setting up Install Process
Setting up repositories
No Repositories Available to Set Up
Reading repository metadata in from local files
Parsing package install arguments
Examining adobe-release-i386-1.0-1.noarch.rpm: adobe-release-i386 - 1.0-1.noarch
Marking adobe-release-i386-1.0-1.noarch.rpm to be installed
Resolving Dependencies
--> Populating transaction set with selected packages. Please wait.
---> Package adobe-release-i386.noarch 0:1.0-1 set to be updated
--> Running transaction check
--> Processing Dependency: /bin/sh for package: adobe-release-i386
--> Finished Dependency Resolution
Error: Missing Dependency: /bin/sh is needed by package adobe-release-i386


I think the /bin/sh error is due to Ubuntu 7.10 created a sym. link from /bin/sh to dash vs bourne shell.  I am not sure why they died it but it seems to break rpm, yum , who knows what else.

As for the sqlite, it have it installed  according to apt but it doesn't seem to work with yum.

Any thoughts?

Thanks

Alan

---

### Post by reiserfs on 2008-01-19
> **HuskyDev said:**
> The following code downgrades the cElementTree and elementTree packages and is supposedly a fix.  I haven't tried it though.

```

sudo dpkg -r --force-depends python-celementtree
sudo dpkg -r --force-depends python-elementtree
sudo dpkg -i (your directory)/python-elementtree_1.2.6-10ubuntu2_all.deb
sudo dpkg -i (your directory)/python-celementtree_1.0.5-8ubuntu2_i386.deb

```

The .deb packages shouldn't be too hard to find.  If you try this, let me know how it goes.

I can verify that this works. The reason why I needed to use yum was because I have installed linux-vserver on my Gutsy system and have setup some Centos guests which requires yum to be installed.

---

### Post by warriorx99 on 2008-05-23
I can also confirm that this works.  It resolved problems I had with the default install of mach in both Gutsy and Hardy.  I had to apply this fix before the "mach setup build" would work correctly.  The problem wasn't with mach, but with yum.  After removing those packages and downloading the new one, everything worked just fine.  I found them at:

[http://archive.ubuntu.com/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-10ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/e/elementtree/python-elementtree_1.2.6-10ubuntu2_all.deb)

[http://archive.ubuntu.com/ubuntu/pool/universe/c/celementtree/python-celementtree_1.0.5-8ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/c/celementtree/python-celementtree_1.0.5-8ubuntu2_i386.deb)

Additionally, I had to hold these from upgrading to keep it from breaking:

sudo apt-get install wajig
wajig hold python-elementtree
wajig hold python-celementtree

---

### Post by ee99ee on 2008-06-27
I need yum to install a specific piece of software that requires it and "only supports" CentOS. Here is what I get after installing the elementtree and celementtree packages manually:

```
Traceback (most recent call last):
  File "/usr/bin/yum", line 27, in <module>
    yummain.main(sys.argv[1:])
  File "/usr/share/yum-cli/yummain.py", line 75, in main
    base.getOptionsConfig(args)
  File "/usr/share/yum-cli/cli.py", line 299, in getOptionsConfig
    self.parseCommands() # before we return check over the base command + args
  File "/usr/share/yum-cli/cli.py", line 47, in __init__
    yum.Errors.YumBaseError.__init__(self)
  File "/var/lib/python-support/python2.5/yum/Errors.py", line 25, in __init__
    self.args = args
TypeError: 'NoneType' object is not iterable
```

I don't know python. Does someone care to translate that to english?

-Chris

---

### Post by Marcianisto on 2008-07-01
Hi! I'm find the solution of "/bin/sh" error.

If the system doesn't use RPM for package management but you still want to install any package through rpm then do:
```
rpm -Uvih --nodeps *.rpm
```

---

