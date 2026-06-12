---
title: "Timevault Questions"
date: 2007-12-17
forum: General Help
---

### Post by jlacroix on 2007-12-17
I installed Timevault on my test machine, I'm thinking about using it to back up my wife's computer. I want it set up so that if her hard drive fails she'll still have her files. (We both use Ubuntu).

My hard drive is larger so the backups will probably be stored on my hard drive. 

I have some folders on my hard drive shared with Samba already, (/home/jeremy/Shared).

So I guess here is what I want to know about Timevault:

1.) Is it a good choice for what I want to do?

2.) Would it work okay for my shared drive to be shared with Samba? I've never in my entire career got NFS to work, so that's why I use Samba. She has MP3's with special characters in some of the file names so I don't know if that will be a problem.

3.) If her hard drive does fail, and the backups are on my machine from Timevault, how would I restore them?

4) Could I use this trick to set up roaming profiles between our two Ubuntu PC's? What I mean is, if I create her user account on my computer, and I set up Timevault to back up her home directory to the home directory on my machine, would that work?

---

### Post by syxbit on 2007-12-22
if space is a problem, you probably won't want timevault, as it does the approach that it keeps variations of the same file
you could try 'sbackup'
or, better still, just write a really simple rsync script, and have crontab back it up.
i know for sure that you can easily have crontab run an rsync script that'll work over networks (with ssh w/o a password)
i don't think any will work with samba though, as samba isn't available to the termianl, just gnome.
the best bet for you is to just have the rsync script backup the home profile directory. then you could easily restore it (minus installed programs, that are easily reinstalled anyway)

---

### Post by pyronaut on 2007-12-22
i have use simple backup .. it works well... but check the first set of backups to make sure that it is backing up properly****.... its basically an rsync script.... if she is using ubuntu then you can save it directly to ur drive ....i dont know why you want a samba share. Also.. i have tried the recovery from simple backup... doesnt seem tow work properly... but it doesnt matter since it stores the backups as .tgz and when i open them up the files are there. So in case of a disaster i can rsync it all back after unzipping

---

