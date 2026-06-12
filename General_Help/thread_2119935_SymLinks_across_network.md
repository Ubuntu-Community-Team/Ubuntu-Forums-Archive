---
title: "SymLinks across network"
date: 2013-02-25
forum: General Help
---

### Post by aCeeDub on 2013-02-25
Hi Guys, I hope someone can help, I'll give as much background as I can.

I have an Ubuntu LAMP serving an Intranet (Joomla et al) that I will need to get the following to work on.

The domain is controlled by MS SBS 2011 in a 10.0.0.* address space

On my (Win7) desktop I have a development copy of the Intranet running WAMPSERVER.

Everything is fine....

However, I want to point to files that sit in different locations on the network (I do not want to upload them to Joomla - just not practicable) 

I am trying to achieve this (on the development system for now) using symlinks (which despite a lot of reading clearly I do not fully understand)

I have placed a folder in the same root as my test document, called **workdrive**

I have also created **c:/testfolder/testwork/**

my test document consists of
```
<a href="file:///workdrive/readme.txt" >file</a>
```I have a test folder as described below.
in the workdrive and the testwork folder I have a text file called readme.txt (with different text in them) - neither open from the test page.


I have the following for an Apache alias directory entry (WAMPSERVER runs okay with this entry)
 
```
Alias /workdrive "c:/testfolder/testwork/"
<Directory "c:/testfolder/testwork/">
Options Indexes FollowSymLinks MultiViews
    AllowOverride all
        Order Deny,Allow
    Deny from all
    Allow from 127.0.0.1
    Allow from 10.0.0.*
</Directory>
```What am I doing wrong? I'm I doing it right, but WAMPSERVER does not follow the rules? Once I get this working I need to test it with network shares and then implement it on the Ubuntu LAMP.

Kind regards
ACW

---

### Post by aCeeDub on 2013-03-06
I now have this working on a windows box, and Joomla is able to display files that are dotted across the domain.

I now need to transfer this to my Ubuntu LAMP.
Can anyone tell me how I can give Apache authorisation to access files and directories on  the windows domain?

Many Thanks
ACW

---

### Post by SeijiSensei on 2013-03-06
The easiest solution is to mount the remote shares on your machine with [CIFS]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").  Then you can create a symlink that points to the mount point of the share.

---

