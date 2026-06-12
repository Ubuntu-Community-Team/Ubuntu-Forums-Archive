---
title: "Edgy Permission Problems, Firefox Problems, More..  Help!"
date: 2007-03-16
forum: General Help
---

### Post by Unoone on 2007-03-16
I have been getting more and more problems ever since I installed Edgy on my new Conroe PC's. I'm using Edgy 32bit. I'ved used Ubuntu since Hoary. I don't know if it's that Ubuntu Edgy incompatible with major hardware like Maxtor drives, newer intel cpu's etc in some areas.

The new problem is that Firefox downloads files from sites like Source Forge with 0 bytes. This could be a problem that is connected with my fat32 hard drive write permissions problems. Or maybe the reason why some of the cd, DVD data that I back up with K3b only is readable in Ubuntu and not Windows. I'm wondering if there are some hoodooguru Ubuntu tricks that rid systems from this kind of evil stuff. Other than the basic install settings or linux terminal commands for drives, folders, etc. in manuals I don't know what to do . 

It's seems that every time I bring these problems up in a thread the response is that the basic Ubuntu Edgy features are working for other users. 

I dumped another machine that had Ubuntu edgy running and installed PCLinuxOS, Mephis, Fedora, etc. on it to test for similar errors. I saved data to my fat32 hard drive from Firefox fine. No -0- byte files. I used K3b to back up data from a ext3 storage drive to my fat32 drive fine without any read problems in Windows. 

I'm not a Linux expert who can analyze everything via terminal commands and instantly setup a perfect system.  I'm not trying to be funny here.  I love using Ubuntu more than any other operating system. In fact, I dumped the other error testing Linux installs from the other computer and replaced them with Windows 2k.:)  It's either Ubuntu or Windows for me on a stable mission critical PC. I only test out other Linux distros on my test PC's.

I'm hoping that someone went through what I'm going through right now and found a solution. Please share it with me. I don't want to move some of my PC's back to an older version of Ubuntu or Windows. Thanks.

---

### Post by spin2cool on 2007-03-16
This sounds like a problem with firefox, not with Ubuntu (I've heard of similar problems).  Go to a command line and type "firefox -p" to get the profile manager.  Create a new, clean profile and try saving the same file.  If that works (and I suspect it will), it means that some of your extensions aren't playing nice.

---

### Post by Unoone on 2007-03-17
> **spin2cool said:**
> This sounds like a problem with firefox, not with Ubuntu (I've heard of similar problems).  Go to a command line and type "firefox -p" to get the profile manager.  Create a new, clean profile and try saving the same file.  If that works (and I suspect it will), it means that some of your extensions aren't playing nice.

Thanks, I'll do that. 

Other Ubuntu users who are way more experienced than myself are having issues with Edgy from what I read in other forums. I realize that the automatic Linux Distros like Ubuntu miss a thing or two. While it doesn't make Ubuntu unusable it does tend to get on your nerves at times. Like now.:)  But you can accept it because tweaking an issue in Ubuntu here or there is so much better that dealing with viruses and unexplainable system (registry) issues. No matter where my Linux journeys take me I will always love Ubuntu for changing my mind about Linux.

I haven't tested Feisty out much lately. I'm trying to stay productive with my web work and all.  I would love to do a fresh install of a newer Ubuntu system and see all of my troubles go away.:) 

I like using Synaptic to install things. Someone once told me to never use gui package managers. I may just use Apt from the terminal for everything with my next Ubuntu full install. I don't know if that will fix everything but it may just improve my user experience.

---

### Post by Unoone on 2007-03-17
Well, well, a new profile with the "firefox -profilemanager" command did nothing at all to fix this issue. I have never had any problems like this with Firefox until Ubuntu Edgy. I know it's Ubuntu Edgy that at issue as a system here in connection to the way it runs Firefox. It's probably something in the kernels connection to the hardware that lousing things up. Maybe it's some unknown kernel issue connected to a dependency issue . As far as my Firefox install it was done with Synaptic. Then I installed Flash from inside of Firefox without any issues. It's a pretty clean setup.I didn't notice this issue until I needed a bunch of modules for my CMS engine from Source Forge. I haven't downloaded these files in ages. In the past I never had any issues getting these files with Firefox in Ubuntu.

Well the files downloaded with Opera. I just had to relocate and redownload about 20 files from a listing of hundreds of files. I had causally picked out these files during about 2 hours of searching the links. It was not fun to have to do that all over again. The problem here is the fact that I was caught off guard here thinking everything was working ok in Firefox. Big loss of productivity here. 

Like I said I may just have to downgrade to and older more stable Ubuntu version. This is sad.

---

### Post by spin2cool on 2007-03-17
I think you'll find more instability, not less, if you downgrade to Dapper.

I recommend doing a complete uninstall of firefox.  (sudo apt-get remove firefox  -- or do iot through Synaptic).   Also be sure to remove your profile folder in ~/.mozilla/firefox 

Then, reinstall.

---

