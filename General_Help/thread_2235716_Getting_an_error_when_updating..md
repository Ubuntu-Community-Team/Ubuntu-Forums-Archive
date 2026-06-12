---
title: "Getting an error when updating."
date: 2014-07-22
forum: General Help
---

### Post by grier-devon on 2014-07-22
So I was getting an error when trying to update either through the GUI or "sudo apt-get update && sudo apt-get upgrade"
> The following NEW packages will be installed:  shotwell
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/7,879 kB of archives.
After this operation, 39.1 MB of additional disk space will be used.
Selecting previously unselected package shotwell.
(Reading database ... 221142 files and directories currently installed.)
Preparing to unpack .../shotwell_0.18.1-1~trusty1_amd64.deb ...
Unpacking shotwell (0.18.1-1~trusty1) ...
dpkg: error processing archive /var/cache/apt/archives/shotwell_0.18.1-1~trusty1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/shotwell/icons/one-tag.png', which is also in package shotwell-common 0.18.0-0ubuntu4.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/shotwell_0.18.1-1~trusty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




So I thought maybe I should remove shotwell and reinstall, I removed it with "sudo apt-get remove shotwell" but when I go to reinstall I get this,
> devon@MrTux:~$ sudo apt-get install shotwellReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  shotwell
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/7,879 kB of archives.
After this operation, 39.1 MB of additional disk space will be used.
(Reading database ... 220490 files and directories currently installed.)
Preparing to unpack .../shotwell_0.18.1-1~trusty1_amd64.deb ...
Unpacking shotwell (0.18.1-1~trusty1) ...
dpkg: error processing archive /var/cache/apt/archives/shotwell_0.18.1-1~trusty1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/shotwell/icons/one-tag.png', which is also in package shotwell-common 0.18.0-0ubuntu4.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for menu (2.1.46ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/shotwell_0.18.1-1~trusty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be appreciated, thanks.

---

### Post by Bashing-om on 2014-07-22
grier-devon; Hi !

Try this:
```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade

```
'clean' command clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.

'autoremove' removes files that the system no longer needs.


[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by grier-devon on 2014-07-22
Hello,
Thanks for the response. I did all this just now, but still cannot install shotwell, what I notice when watching the processes I noticed that shotwell is trying to pull from my yorba ppa which I put on there for geary. I removed the yorba ppa and can now install shotwell, my question is there a way to keep the yorba ppa for updates to geary but not shotwell? I believe this is what was messing everything else up.

---

### Post by Bashing-om on 2014-07-22
grier-devon; Well, well ..

The package 'geary' is available in the software repository, is there an over-riding consideration that induces you to depart from the package manager's protection; and resort to a 3rd party application  ?

As I have no experience with 'yorba' I can not say further.

[INDENT][INDENT]3rd party software
[INDENT][INDENT][INDENT]the disclaimer do apply
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grier-devon on 2014-07-23
Bashing-om,
Thanks for all the great input. I just looked and seen that the repositories are using the latest version of geary, I only like to have the latest if there is a must have feature the older versions in the repositories don't have. In geary's case when I was using Ubuntu 13.10 was offering an older version of geary which did not allow you to delete emails from the trash.

For bug purpose I try to use minimal ppa and stick to the official packages, but when I do need a ppa for security purpose a ppa must pass three criteria

1. Must be listed as a official ppa from the developers website

2. When looking at who is uploading the packages it must be a developer I recognize (yorba is the maintainer of geary and I am going to look into if he is now building shotwell)

3. The new packages must have a "must have" feature I cannot live without.

Thanks again for everything.

---

### Post by Bashing-om on 2014-07-23
grier-devon; Hello,

Yep, ya know what you are doing, for a fact. Good head on your shoulders.

I expect presently all is good in your ubuntu world;
 Please mark this thread solved;
 aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on 
[INDENT][INDENT][INDENT]keep'n on[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Briga on 2014-10-30
Well yes yorba provides you a newer version of shotwell. 

Your solution is fine and I am happy you sorted it out. 

In any case if you DO want to install shotwell from the PPA (like I did) you are stuck with the issue. 

The solution for me was to force installation in this way. 

1) Try to install via the ppa, the apt-get will finish with an errorr 
2) run the following command (checj and adjust if necessary):
```
sudo dpkg --force-all -i /var/cache/apt/archives/shotwell_0.20.1-1~trusty1_amd64.deb
```

Basically you are using the deb apt-get downloaded and through the --force-all switch tell dpkg to go all the way no matter what. I had a bunch of warnings on the screen but the installation went well and shotwell is running just fine on my system. Hope it helps, but as usual be careful of what are you doing. Playing with sudo and installations can always be tricky.

---

