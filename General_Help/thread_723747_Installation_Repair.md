---
title: "Installation Repair"
date: 2008-03-13
forum: General Help
---

### Post by TonyFordz on 2008-03-13
I have taken a look at other repair topics none of which have been useful to my problems & I have also searched the World Wide Web for other posts or topics that could have covered my problems but no luck in finding what I needed.

Aright this is what happened this time around as I have tried in the past to use Ubuntu & other versions of Linux in which I always end up pissed off or aggravated beyond end to the point of reinstalling Windows XP & saying the hell with Linux.

I installed Ubuntu on my 300GB HD & then did all the updates spent about 4 1/2 hours downloading all the software & programs of interest to me. After everything was done I clicked on the exit icon on the top right hand side of my Ubuntu desktop which gives you the options of logging off or shutting down. I figured that the suspend option was something like "sleep" mode in windows & chose it where it seamed to do the same as sleep would in windows & I went to bed. Today when I came back I was not able to come out of this mode I tried the ESC key, enter, and even pressing random keys & because I already know that CTRL+ALT+Delete is useless in Ubuntu or Linux I didn't bother trying that. Then I pressed the restart button on my computer in which rebooted & seamed to be fine till it was time to load the desktop & ask for my user & pass at which point the screen went black. I assume this black screen would be equivalent to the evil blue screen on windows operating systems but in any case it went no where.

Now I find there is no repair option or if there is I am unable to find it & because I have to put the CD in to even access the net or anything else it is useless to use the terminal screen because of the fact it isn't reading my hard drive because it booted from CD mode instead therefore I would be unable to even repair anything CD wise unless there is a special feature for that like in most Windows OSes. I find it hard to believe that someone made such a great free OS without the option to run a fresh install repair or at least add some option some where to fix any errors or problems as at some point in time someone will face & from what I have read in many online forms I am not the only one facing the Ubuntu repair nightmare.

I have tried the "sudo apt-get install --fix-broken" & it ended up giving the following "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." & you have to keep in mind I am not Linux minded as I grew up with Microsoft starting out in MS DOS all the way up to about Windows XP Pro as from what I have read it will be a cold day in hell before I ever buy or use Vista & windows honestly isnt much better in general.

So can someone reply with some useful information without making smart *** remarks because honestly I am here to seek help not be told I am a newb so respond with something useful or don't respond at all I don't have time for childish BS.

---

### Post by Rocket2DMn on 2008-03-13
Getting that black screen just means that X (the GUI) did not start up right because of incorrect video configuration.  Here is a guide on how to reconfigure X so you can get back to the GUI - [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

Because of your dpkg problem, during that guide, run
```
sudo dpkg --configure -a
``` at the start (when you first get to a terminal interface), then proceed normally with the guide.

Nobody here is going to tell you you're a "noob" or that you're stupid, this community prides itself on being helpful and inviting to everybody.  Nobody here is an all-knowing linux god, nor would anybody claim to be - we are simply here to help with any problems that come up, and to do so as professionally as possible.

---

### Post by TonyFordz on 2008-03-14
Thank you for the information but I gave up & reformatted into Windows XP think I will just stay in windows until Linux grows into the gaming community because I play so many games that none of which support Linux OSes so I don't have much of a choice otherwise unless I run a emulator & so far I am not impressed with any of them.

Thank you very much for the attempted help hope you have a great weekend,
Tony

PS: I couldn't get past the black screen no matter what I did & it even did that when I tried to reinstall over again & I have never in the past had those problems with Ubuntu & all system settings are the same as when I had it installed the many times before.

---

### Post by TonyFordz on 2008-05-09
I really want to swap to Ubuntu but every time I do there is something I just cant get past which leaves me with no options but to revert back to Windows XP Pro every time.

When I use Ubuntu I can surf the web freely with very little concerns of some crap be it hidden content or what corrupting my system files like in windows. In XP its just a matter of time & you can expect to get nailed with something nasty sooner or later which in most cases is sooner then later. I don't ever get this problem with Ubuntu ever nothing wants to attack it like Microsoft products & OSes. Plus there is so much free content in Ubunutu but I think most people are afraid of things they don't understand like me for example I know very little about anything Linux based so the first sign of trouble I reformat back into XP because even though there are so many bugs, errors, and glitches in it I understand it because I grew up on Microsoft products from DOS & QBasic up to XP Pro.

It it nice for a change to find some where I can go ask questions & not get some rude remark like "noob" its more common in  games but I swear it has to be the most annoying word out there. We all have to start out some where & most times at the bottom to work our way up & it would be nice if people were more helpful then not so I thank anyone who is nice enough to take some time to read & answer my posts & questions.

Thank you,
Tony

---

### Post by Rocket2DMn on 2008-05-09
Hello again.  Since your last posts, the next version of Ubuntu has been released called Hardy Heron, and it is an LTS release.  You might be interested in giving it a try again, esp. since Wubi is now an officially supported method of install.  It installs to your existing windows setup so you don't end up repartitioning drives.  I'm not clear on the details since I've never tried it, but I hear it is a nice gateway to Ubuntu - [http://wubi-installer.org/](http://wubi-installer.org/)
Enjoy, and don't be discouraged, you will learn a lot from troubleshooting problems.  Remember, we are here to help.

---

