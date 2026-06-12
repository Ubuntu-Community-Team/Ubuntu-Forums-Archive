---
title: "Possible to / Easiest Way to Strip Ubuntu...."
date: 2024-07-04
forum: General Help
---

### Post by rebeltaz on 2024-07-04
I installed a full desktop version of Ubuntu 22.04 LTS on a mini computer that is only being used as a local network file / media server. Is it possible to (and if it is, what is the easiest way to) strip this down to just the bare necessities. The things I know I need are ssh, and probably the GUI. 

I had installed this system as a headless OS, but for some reason (and I don't remember why) I needed the GUI, so I reinstalled. I REALLY don't want to have to rebuild / reinstall this AGAIN.

---

### Post by vanadium on 2024-07-04
Ubuntu works with a package management system. Thus, it is a matter of removing packages you do not want.

The easiest way to start could be to remove the entire graphical stack (remove Xorg, Wayland). This will automatically remove any graphical desktop environment, graphical applications and related libraries. Then you could add these GUI components that you need.

---

### Post by Rubi1200 on 2024-07-04
You could, in theory, strip things away. However, the potential for running into all kinds of issues with dependencies etc. is that much greater.

If it was me, I would make a backup and reinstall using a lighter version such as Lubuntu or Xubuntu and choose the minimal install option.

Then only add in what you really need.

---

### Post by dragonfly41 on 2024-07-04
Remember the other option. On rebooting[COLOR=#000000] you get to the login screen and before entering password there is a drop-down menu 'Sessions'. You can choose a lighter weight desktop environment session.[/COLOR]

---

### Post by ActionParsnip on 2024-07-04
I'd suggest installing Ubuntu server rather than the desktop OS, then run:
```

sudo apt update
sudo apt -y install lxde

```
This should install gdm (or lightdm) as well (If not, install lightdm) and you'll have a super light OS with a GUI. If you just want a file server you don't need a GUI for that and Ubuntu server will suffice. You can configure services using SSH easily

---

### Post by currentshaft on 2024-07-04
> **rebeltaz said:**
> I installed a full desktop version of Ubuntu 22.04 LTS on a mini computer that is only being used as a local network file / media server. Is it possible to (and if it is, what is the easiest way to) strip this down to just the bare necessities. The things I know I need are ssh, and probably the GUI.

It is Linux, so anything is possible, but is it necessary? What problem would "stripping" it solve for you?

---

### Post by TheFu on 2024-07-04
The easy way is to not load a GUI and use Ubuntu Server as your base system, but that isn't what you want to hear.

When you remove many of the GUI things from any "desktop" install, you'll likely break those little things that integrate with the DE like network controls. I suspect that's one of the main issues for you.  OTOH, learning to manage network connectivity is just a few commands and 1 config file (mostly), so having all the bloat of a GUI just to have network controls is a huge 5GB waste, in addition to the security ramifications that having a GUI at all causes.

All DEs are pretty bloated, IMHO.  They aren't necessary to have a GUI either.  Just something more to think about.

---

### Post by rebeltaz on 2024-07-04
> **vanadium said:**
> The easiest way to start could be to remove the entire graphical stack (remove Xorg, Wayland).
> **Rubi1200 said:**
> If it was me, I would make a backup and reinstall using a lighter version such as Lubuntu or Xubuntu and choose the minimal install option.
> **ActionParsnip said:**
> I'd suggest installing Ubuntu server rather than the desktop OS, then run:
> **TheFu said:**
> The easy way is to not load a GUI and use Ubuntu Server as your base system, but that isn't what you want to hear.

lol... yeah. I anticipated this being the most popular solution. I just REALLY hate having to rebuild systems. I either invariably forget to back something up or forget how I configured things before and wind up having to relearn everything all over again to get things running the way I want. Memory of a guppy and all ¯\_(&#12484;)_/¯ 

> **dragonfly41 said:**
> Remember the other option. On rebooting[COLOR=#000000] you get to the login screen and before entering password there is a drop-down menu 'Sessions'. You can choose a lighter weight desktop environment session.[/COLOR]

The problem with that solution is that I would have to physically be there to see it at every reboot (sometimes done remotely and sometimes due to power glitches) to select that option. I wasn't aware of the "light weight" option, though.

> **currentshaft said:**
> It is Linux, so anything is possible, but is it necessary? What problem would "stripping" it solve for you?

On the mini pc on which I am running this, the entire GUI is slow as molasses flowing uphill in winter anytime I need to access that. I am assuming, probably incorrectly, that that is being caused by unnecessary resources being used. 

I may wind up having to rebuild this anyway. I really appreciate all of the advice. Thank you all.

---

### Post by TheFu on 2024-07-04
> **rebeltaz said:**
> lol... yeah. I anticipated this being the most popular solution. I just REALLY hate having to rebuild systems. I either invariably forget to back something up or forget how I configured things before and wind up having to relearn everything all over again to get things running the way I want. Memory of a guppy and all ¯\_(&#12484;)_/¯ 

I remember what that was like decades ago.  I was afraid to wipe and start fresh.

Then I started making backups with a specific process that allowed selective restores so that in less than 45 minutes, even on completely different hardware, I can have my system back with all my settings, all my programs, and all my data.  If your backup/restore method doesn't support that, perhaps you need a better solution?  

If there's any issue and I've spent over 1 hour trying to fix it, I'll stop, wipe the system, and restore from the most recent backups.  The restore process begins with a fresh, minimal, install.  That minimal install can be the same version+flavor, a different flavor, or even a different version of the same OS.  I've migrated 18.04 systems to 20.04 using this method and again ... 20.04 to 22.04 with completely different DEs.  More and more, I just install Ubuntu Server to avoid all the GUI bloat.  Where there aren't any GUI programs, the number of config files is drastically reduced to about 15.

BTW, I don't backup most OS files/programs.  When I restore, I won't have an identical system, but I will have a system that is close enough AND "feels" the same.  In the end, isn't that all that matters?

To make backups easier, I use tags inside system config files with comments so I know exactly which ones I modified.  Takes 1 command to find them at restore time so I can merge any config changes into the new install.  I little pre-planning makes things trivial later.  Best to begin doing this after a fresh install.  However, you can go back into the files you remember modifying already and put the comment tags in to start the habit.

Just something to consider.  Knowing that something is possible is the first step.  Also, since a fresh install shouldn't take much over 15 minutes, that shouldn't be a very high barrier.

---

### Post by rebeltaz on 2024-07-04
Yeah... I'll be the first to admit that my backup solution, what there is of it sucks. I am by no means a computer novice, but that doesn't mean I necessarily always practice what I preach. I'd be open to any suggestions on the best back up strategies. 

You mention not backing up programs, etc.. The problem with that, for me, is that given the memory of a guppy that I possess.. I never remember what programs I installed/use or how I configured them to work together, etc... So every time I have to restore a system, I always have to start fresh and figure it all out again. Usually, it's been several years, so the chances of my remembering is near zero.

---

### Post by TheFu on 2024-07-04
Nobody remembers what they installed. Certainly not me either.  The computer knows, so we don't need to remember that trivia.

Well, if you stick with the Canonical repos, then you just need a list of the installed programs, nothing more.  dpkg or apt-mark can provide that list.  I include the results of a run to gather that information in my nightly backups.  You can create a text file with the list of snap packages installed too. Not hard.  Put these into your "pre-backup" script.

For manually installed programs, I put them into /usr/local/ and everything in /usr/local is backed up.  That is a very small number of programs.

I've posted in about 100 threads here for backups.  Perhaps reading a bit would make sense?  If you aren't willing to do that, no reason for others to waste their time.  In the last few years, I've updated some of my posts to have specific commands that are better then what I was using previously.  Backup tools sometimes change their options to mean different things AND I learn more.

As with any muscle, the more it gets used, the stronger it becomes.  Restoring from backups is a muscle.  Don't expect it to handle 1000 lbs needs when it has only been used for 100 lb work before.  When I first switched to my current backup method ... around 2010 ... it took 5 attempts to ensure I had everything needed.  Then, over time, I started adding key troubleshooting data to help with non-backup tasks and system information to make the manual parts of my restore process easier to accomplish.  About once a year, due to HW failure or personal stupidity (mostly stupidity), I get to test my restore process.

There's a law of nature - if you have backups that work and can be restored, you'll need them much less.  OTOH, when you do need them, you'll either discover flaws OR corruption OR that they've saved you.  I sleep really well at night.  When a disk has failed, it was a minor inconvenience, not a total data-loss event ... er ... since I've had backup religion.  Of course, I didn't always have backup religion and I've lost nearly all my data a few times, but those few problems were all over 20 yrs ago.  I started out making ZIP files. Then I got a cheap tape drive and used that for backups. Because those methods were a pain to use, I barely used them.  Eventually, HDD prices became cheap enough (and my income increased) that I could get storage specifically for backup needs.  Initially, I did weekly rsync backups (a straight mirror), which saved me once from a hacker attack.  The rsync backups were in a script, but I didn't automate running them.  Don't know why.  They always worked, so it didn't make sense.  Eventually, I'd forget or just be lazy and not bother running the rsync script weekly.  Life and work were busy. Other things took priority.  Soon, I'd find it was over 6 months since the last backup and I'd panic, run the script and swear I'd never let that happen again.  A year later, no backups made, I'd run the rsync script.  

That went on about 6 more yrs until I started supported 3 small companies systems.  At that point it would be embarrassing if I wasn't doing backups should something bad happen.  It was possible embarrassment that made me work out better backups. I used rsync with hardlinked versions, like the old-school UNIX backup books showed.  These were great for a single desktop, but I had 20 servers to backup and soon wasn't able to complete the backups within the allowed backup window overnight.  I needed a better solution and even/odd day backups (50% of the systems on even and the other 50% on the odd days) wasn't an answer.  I spent about a month trying all the best backup tools, finding the good and the bad about each.  I ended up with rdiff-backup and have stuck with it nearly 15 yrs now.   It isn't perfect, but it is really great compared to all the other alternatives.  The biggest negative - no GUI, so it isn't noob friendly.  There were a few noob-friendly backup tools that address most needs, but have some flaws that may or may not matter to you.  All the rsync+hardlink methods have this flaw, but there is one, with the flaw, that most people can use, back-in-time.  I set this up for my mother's computer and she used it a few years until her death.  It did almost everything automatically, so she didn't need to worry about anything.  The amount of storage used wasn't THAT bad, but it didn't make restoring a system particularly easy. For her, it was all about personal data. The applications she used were a small list.

If you want a backup tool that does system backups easy, Linux Mint uses something called Timeshift.  It works best if you choose btrfs as the file system, not ext4.  With btrfs, it can have the file system create snapshots before copying everything off to an external disk.  Timeshift doesn't recommend using it for personal data, just system stuff.  That's always bothered me.  OTOH, to have a system back to where it was before an issue happened, timeshift just needs a reboot and selecting the snapshot you want restored.  Volume manager snapshots like this are sub-second, nearly instant.  [https://www.linux.org/threads/how-to-restore-a-timeshift-snapshot-from-the-live-session-in-mint-cinnamon-21-1.46520/](https://www.linux.org/threads/how-to-restore-a-timeshift-snapshot-from-the-live-session-in-mint-cinnamon-21-1.46520/)  Looks like timeshift volume snapshots need an extra step to copy off to external storage. IDK. Perhaps someone else can explain.  

With LVM snapshots, the data isn't copied anywhere until we do that ourselves using a backup tool.  [https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/)

---

### Post by vanadium on 2024-07-05
> **Rubi1200 said:**
> You could, in theory, strip things away. However, the potential for running into all kinds of issues with dependencies etc. is that much greater.

I do not see this happening if you use the APT system to remove packages. It is designed to automatically handle dependencies.

> lol... yeah. I anticipated this being the most popular solution. I just REALLY hate having to rebuild systems. I either invariably forget to back something up or forget how I configured things before and wind up having to relearn everything all over again to get things running the way I want. Memory of a guppy and all ¯\_(&#12484;)_/¯ 
Your other option is to select a distribution that most suits you, or at least irritates you the least. This statement of you surprises me, because you asked a question about tinkering with a system. Either you take what is out there, or you get your hands dirty.

---

### Post by Rubi1200 on 2024-07-05
> **vanadium said:**
> I do not see this happening if you use the APT system to remove packages. It is designed to automatically handle dependencies.

Yes and no. I have seen many instances where users remove things without paying attention to what other packages are being deleted along with it.

On a well-maintained system there should be no need to strip anything away.

My formula is to start with a minimal install and only add what I really need.

---

### Post by rebeltaz on 2024-07-05
> **vanadium said:**
> This statement of you surprises me, because you asked a question about tinkering with a system. Either you take what is out there, or you get your hands dirty.

When I said I hate rebuilding systems, I didn't mean the "getting my hands dirty' part. I don't mind tinkering with existing systems. I meant that I hate wiping clean and starting over from scratch.

---

### Post by HermanAB on 2024-07-06
Trying to unscramble an egg usually doesn’t work.

---

