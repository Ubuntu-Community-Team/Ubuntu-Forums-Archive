---
title: "Problem Updating and Upgrading in 12.04"
date: 2012-11-20
forum: General Help
---

### Post by brantpadams on 2012-11-20
Hey all. I'll try and be as concise as I can with my problem. 

For about a month now, I have been unable to perform updates on my 12.04 system. Any time I try "sudo apt-get upgrade" I receive this prompt:
> E: Syntax error /etc/apt/apt.conf.d/70debconf:5: Extra junk at end of file

I also have a red dot in the top of my status bar that is saying my installed packages have unmet dependencies. It gives me the option to show updates in its dropdown menu, but won't execute any commands when I click on "show updates" or "install all updates."

Second part of my problem:

I've tried simply doing a fresh install of 12.10 on my system a couple of times now, but the install process never makes it past a certain point. It always stops progress at "saving installed processes." I've been told that it may be due to the iso image itself being corrupt or the burn wasn't good, but I've downloaded two different files and burned on 3 different discs and I can't seem to fix this problem. 

If there's any more information I can provide please let me know. I'd really just like to upgrade my system to 12.10 and I'd appreciate any help available. Thanks in advance!

---

### Post by cwsnyder on 2012-11-20
On your 12.10 installation media: Are they live media, or a minimum installation?

If they are Live media and you boot from that medium, do you go to a GRUB menu to select options like check the memory as well as go into Ubuntu?  Check to see if there is a selection to check the installation disk in that menu, and run that option to check the file you downloaded.

Just because you have downloaded it two different times does not mean you did not get two corrupted downloads.

---

### Post by brantpadams on 2012-11-20
Thanks for you response cwsnyder, but I'm not entirely sure how to do all that. Are you talking about checking the status of the file after it's been burned to a disk or checking the file itself before burning? 

Right now I've junked the disks that weren't working before, but I still have the .iso file for the install.

---

### Post by ibjsb4 on 2012-11-20
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

cat /etc/apt/apt.conf.d/70debconf

And please post the output.

Problem #2  Post #2

[http://ubuntuforums.org/showthread.php?t=2026566](http://ubuntuforums.org/showthread.php?t=2026566)

---

### Post by cwsnyder on 2012-11-20
On [http://releases.ubuntu.com/12.10/MD5SUMS](http://releases.ubuntu.com/12.10/MD5SUMS) , there are listings of the md5sum for each type of .iso file.  Check your download by opening a terminal and entering **md5sum nameofisofile.iso** then checking the result against the list from the above link.  If they are not identical for the file you (supposedly) downloaded, there was a problem with the download, and you must re-download until you can get a copy which DOES match the md5sum.  If you prefer you can use **sha256sum** instead of md5sum and the [http://releases.ubuntu.com/12.10/SHA256SUMS](http://releases.ubuntu.com/12.10/SHA256SUMS) listing of sha256sums.

---

### Post by brantpadams on 2012-11-20
> **ibjsb4 said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

cat /etc/apt/apt.conf.d/70debconf

And please post the output.

Problem #2  Post #2

[http://ubuntuforums.org/showthread.php?t=2026566](http://ubuntuforums.org/showthread.php?t=2026566)
Here's the terminal results:
> brant@brant-Inspiron-1525:~$ cat /etc/apt/apt.conf.d/70debconf
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
APT::Cache-Limit "100000000"

I'm checking on your link now. Thanks.

EDIT: I have no clue how a smiley face got in there.

---

### Post by brantpadams on 2012-11-20
I followed the link you provided and couldn't execute an "apt-get" command without the "extra junk at end of line" popping up. I think I need to fix issue #1 before I can upgrade Ubuntu.

---

### Post by ibjsb4 on 2012-11-20
In terminal:

sudo gedit /etc/apt/apt.conf.d/70debconf

That will open up your gnome editor and change:

APT::Cache-Limit "100000000"

to ..

#APT::Cache-Limit "100000000"

Save and close.

Thats the only difference I see between yours and my 70debconf.  So my guess is that will fix it  :)

---

### Post by cwsnyder on 2012-11-20
I would probably suggest opening a terminal and typing:```
sudo /usr/sbin/dpkg-preconfigure --apt | true
```If this completes without error, then type:```
dpkg --configure -a
``` and see if that fixes your problem by typing:```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by ibjsb4 on 2012-11-20
I think you should try cwsnyder's solution first

---

### Post by brantpadams on 2012-11-20
I tried the terminal solution cwsnyder provided and I got nothing after the first command. Should I have to wait for a while or does it normally execute right away?

Thanks again for the help you guys. I know this is kind of a weird problem.

---

### Post by cwsnyder on 2012-11-21
The first two commands may take as long as an hour, depending on conditions of your packages.

---

### Post by brantpadams on 2012-11-25
> **cwsnyder said:**
> I would probably suggest opening a terminal and typing:```
sudo /usr/sbin/dpkg-preconfigure --apt | true
```If this completes without error, then type:```
dpkg --configure -a
``` and see if that fixes your problem by typing:```
sudo apt-get update && sudo apt-get dist-upgrade
```
Hi again.

Just wanted to update on my progress. I was away for the Holiday weekend and didn't have computer access.

After using the top command and letting the terminal sit for several hours, I got zero results. I entered the command and all I got was a blank cursor. 

The problem also extends to ubuntu software center. I can't launch it. It seem to be anything having to do with installing new programs or upgrading simply won't function.

---

### Post by ibjsb4 on 2012-11-25
Just to make sure that nothing has changed, open a terminal and ..

sudo apt-get update

And please post.

Also this is my last post tonight.  Will check in tomorrow.

---

### Post by brantpadams on 2012-11-25
> **ibjsb4 said:**
> Just to make sure that nothing has changed, open a terminal and ..

sudo apt-get update

And please post.

Also this is my last post tonight.  Will check in tomorrow.
> brant@brant-Inspiron-1525:~$ sudo apt-get update
[sudo] password for brant: 
E: Syntax error /etc/apt/apt.conf.d/70debconf:5: Extra junk at end of file


No change.

---

### Post by ibjsb4 on 2012-11-25
Ok then, do post #8

---

### Post by brantpadams on 2012-11-25
Post #8 worked!

Updates are working again and ubuntu software center launches as well. I'm going to attempt to upgrade my distribution and let you guys know the results. Thanks again for the help!

---

### Post by ibjsb4 on 2012-11-25
And when finished and all is well  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by brantpadams on 2012-11-25
SOLVED.

Thanks again for all the help. 12.10 is installed and working well.

---

