---
title: "How to upgrade Beryl"
date: 2007-01-19
forum: General Help
---

### Post by mrwooster on 2007-01-19
Hi,

I am currentl using beryl 0.1.1 but have seen that there are other versions out - how do I upgrade?

Thanks

Guy

---

### Post by Billquinn1 on 2007-01-19
This is not a great time to update to the newest version. If you look around the forums there was some showstopper bug in the newest release. Wait a day or 2 then go to:

[http://ubuntuforums.org/showthread.php?t=279456&highlight=beryl](http://ubuntuforums.org/showthread.php?t=279456&highlight=beryl)

Add those keys and repos and apt-get update apt-get upgrade.

---

### Post by igknighted on 2007-01-19
> **Billquinn1 said:**
> This is not a great time to update to the newest version. If you look around the forums there was some showstopper bug in the newest release. Wait a day or 2 then go to:

[http://ubuntuforums.org/showthread.php?t=279456&highlight=beryl](http://ubuntuforums.org/showthread.php?t=279456&highlight=beryl)

Add those keys and repos and apt-get update apt-get upgrade.

The update today appears to have corrected this issue, I am no longer having troubles with it.

As far us upgrading to newer versions of beryl, check out [www.beryl-project.org](www.beryl-project.org) to stay up with the latest news.  There are several 3'rd party repo's you can add to get newer versions of beryl in .deb form as well.  Beryl 0.2 is due out soon, so you might want to hold out for that if you aren't going to use the (rather volatile at times, but updated daily) SVN version.

---

### Post by jabzwnein on 2007-01-22
So, how do you upgrade exactly (for the stupid among us)?  Step by step with code, if anyone could be so nice? :)

I'm having the standard problem with the titlebars missing and it seems nothing I have done can fix the problem, so I thought maybe updating would work.  I've tried everything else in all the forums and wikis.  Maybe someone out there has another solution?  The only one I haven't tried in to change the rendering path to copy, but I can't do this since I don't have the menu option "Advanced Beryl Options".

sigh.

---

### Post by tito2502 on 2007-01-22
Just add the Beryl repository listed in numerous beryl guides on this forum.

---

### Post by jabzwnein on 2007-01-22
Thanks, but how do you do that?

---

### Post by cmost on 2007-01-22
You simply add the repository to your /etc/apt/sources.list file.  I find it hard to believe you got Beryl up and running in the first place without knowing how to add a repository to your sources.list file.  But, anyway.  Open a terminal and type (without the "$" which represents the prompt.)

$sudo gedit /etc/apt/sources.list

When the file opens, copy and paste the Beryl repository for Edgy into your file.  Save it, then close gedit.

Next, type into the terminal:
$sudo apt-get update
$sudo apt-get dist-upgrade

If there are newer Beryl packages, then they will be upgraded.  If you wait a few minutes after doing an apt-get update, Ubuntu's update manager will pick up whether or not there are any upgrades to packages and you'll be able to see graphically the updated Beryl packages and install them from there if desired.  Good luck.

---

### Post by CowzRule on 2007-01-22
> **jabzwnein said:**
> Thanks, but how do you do that?

When you first installed Beryl, you had to add a repository to your sources.list file. Now you just need to change that to a more up to date repository. First```
sudo gedit /etc/apt/sources.list
```then replace the one you used with> deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy mainThen put
```
http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```Then do```
sudo apt-get update
```Then ```
sudo apt-get upgrade
```
If you need more help, post a copy of your sources.list file and I'll point out what line to change.

---

### Post by jabzwnein on 2007-01-22
I appreciate the help!  Trying that stuff now.  As for the comment that I couldn't have installed beryl without knowing about the packages or how to do it, well, it seems that I'm always being mistaken for being smarter than I am in these forums! :)  I just follow instructions, what code to put in, etc., I don't really know what all the processes are called.

---

### Post by mrwooster on 2007-01-22
> **jabzwnein said:**
> I appreciate the help!  Trying that stuff now.  As for the comment that I couldn't have installed beryl without knowing about the packages or how to do it, well, it seems that I'm always being mistaken for being smarter than I am in these forums! :)  I just follow instructions, what code to put in, etc., I don't really know what all the processes are called.

Its worth learning a bit about using the command prompt - it is not too difficult to master, and it makes using linux a lot easier.

---

### Post by jabzwnein on 2007-01-23
YAY!  I got Beryl working.  Was trying to run it under Dapper but ended up upgrading to Edgy and voila!  Thanks for all your help!

---

