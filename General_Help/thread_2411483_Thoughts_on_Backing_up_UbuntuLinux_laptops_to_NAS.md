---
title: "Thoughts on Backing up Ubuntu/Linux laptops to NAS"
date: 2019-01-30
forum: General Help
---

### Post by barddzen on 2019-01-30
[SIZE=2]Hello,

I've recently setup our household with some refurbished laptops running Ubuntu and Linux Mint MATE and thus far it's working out pretty well.  But one thing still has me on a fence of sorts and it's regarding backups.

With my MacOS systems I had the following:

- Time Machine backups to my NAS (MacMini, Macbook Pro)
- Carbon Copy Cloner backup of my main machine (MacMini) daily as a bootable backup to an attached USB 2.5" HDD.
- I still have the Macbook pro running TM to the NAS
- The MacMini is just TM to the NAS (I moved it to function as a Plex server sitting in my rack in the basement)

I now have two laptops, one running Ubuntu and the other running Linux Mint MATE, latest versions of both.  I've been playing around with various software:

- Ubuntu Backup:  This seems to work well enough, but I can't exclude any folders nor run different sets, pick a folder, back it up, works fine.  Not much for options.  Creates proprietary files in destination NAS folder.
- FWBackup: Allows me to create backup sets and run on multiple schedules creating single compressed files.  To me this is the cleanest and easiest to work with.
- GRsync: This works to not only help me learn rsync command line syntax, but allows me to use rsync to my NAS, however, I'm still debugging a lot of errors and issues with the script.
- Rsync: See GRsync, still debugging script.

With rsync, I find it tends to get hung-up on certain folders so I have to use --exclude-from to keep it running smoothly, but this doesn't give me a "total" backup, but does get most of it.

This bring me to another question:  what folders to backup?  I've settled on the ones below and again, with fwbackup I setup two sets, one for home and one for everything else.  This gets me two compressed files per run and I have it set to keep up to 7 backups before rotation.

[/SIZE][FONT=Verdana][SIZE=2]/home[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]/usr[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]/etc[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]/var[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]/opt[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]/srv

So to wrap this up, here are my specific questions:[/SIZE][/FONT]
[SIZE=2]
- Based on the web research, rsync seems like a great, powerful solution but it takes a LOT of debugging to get just right and work without errors, locally and on the NAS.  My question is, is it worth the time and effort to get rsync working smoothly, despite the up front sweat time to get it right?
- Does having a bootable backup really have any advantage in Linux-based systems?  I've had a few instances with MacOS where having a bootable backup saved my bacon.
- Is there some other backup solution that will give me better options? Better recoverability?
- Am I backing up the right folders?
[/SIZE]

---

### Post by CatKiller on 2019-01-30
Déjà Dup, which I'd imagine could be branded as "Ubuntu Backup" if you're using Gnome, certainly lets you exclude folders from your backup.

Your Home folder contains all your settings and data. You don't need to back the rest up. That's all simply an apt install away.

You already have a live system ready to go at a moment's notice: any Linux install image from the past decade-and-a-half. 

The files that duplicity (the backend to Déjà Dup) creates aren't proprietary.

rsync was the standard way to back up prior to duplicity. Whether it's worth you learning it is entirely dependent on how interested you are in learning it.

---

### Post by HermanAB on 2019-01-31
On Linux, it is generally best to only backup your data.  

The OS is free and evolves rapidly.  One day when your system joins the great computer in the sky, you can download and install a new system with the latest and greatest version of Linux in minutes, so backing up the system itself is just a waste of time and resources.

---

### Post by SeijiSensei on 2019-01-31
At a minimum, I back up /etc and /home.  On machines where I care about preserving log files, or ones used as a server, I back up /var as well.  I have nothing in /opt or /srv. I do store local admin scripts in /usr/local/sbin and back up the /usr/local hierarchy as a result.  But for most users, /usr/local will be empty.

As Herman says, It's not really worth backing up the operating system files.

---

### Post by barddzen on 2019-02-02
Thank you!

This really helps.  Most of the articles and posts here are for far more advanced setups than what I'm really using linux for.  I have 3 laptops that I've moved to Linux and for what the family uses these laptops for, basic browsing, some documents, spreadsheets, presentations -> basic office kind of usage, some games:  the gist here is fairly basic kind of usage.

In my case, sure it's becoming a bit more than that but to start, it sounds like a couple of directories are all that I need.

This really helped, thank you.

What I've settled on is the following:

- For my main desktop, I have Deja-Dup to my NAS as well as fwBackups to my NAS.  Deja-Dup is drop dead simple and fwbackups, though I had to compile from source, is much more functional.  I can create backup sets with tons of options.  I also plan to use Timeshift to a second local drive once it arrives. At some point I'll probably drop either fwBackups or Deja-Dup, but for now I'm still in the evaluation stage. On my main daily use machine I like to have multiple backups on multiple media just in case, a bit paranoid but I've had machines/drives die on me over the years and this has kept me running for several decades.

- For my other laptops/machines, I have Deja-Dup.  I don't need anything fancy just a backup of the home folders if something goes bad.

I still play around with terminal and rsync which is quite powerful but has a steep learning curve.  I've been playing around with Grsync which is a GUI for rsync and let's me play with the options, test the command (without execution), and actually see what the command is.  This has helped me learn a lot of the complex syntax of rsync.  I'm not ready to put anything into action yet, but it's interesting to learn and have in my back pocket.

---

