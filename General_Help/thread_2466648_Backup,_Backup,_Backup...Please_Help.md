---
title: "Backup, Backup, Backup...Please Help"
date: 2021-09-01
forum: General Help
---

### Post by wyattwhiteeagle on 2021-09-01
128gb usb flash drive full install (the internal is dead)
2-6gb swap area
4gb RAM

Which backup strategy is best?
At first I thought scripting would be sufficient, but now I think scripting isn't enough.

Photo's, music, Household Records, etc are already backed up (stored on a different usb and on a different laptop)
I need to be doing backups weekly or daily.
These backups need to include the other important files and also customizations and stuff.

I'm thinking I need to have no less than 3 backup files and the most recent backup replaces the oldest backup.
I probably should keep closer to 8 or 10 backup files.

Timeshift, ZFS, CloneZilla, etc.
I need something light weight and low-resource use, that backs up more than just my stuff and able to produce backup files that aren't "married" to the CLI/GUI being used.

---

### Post by oldfred on 2021-09-01
Just about every thread on backup and then TheFu's posts.

Just some of them, search for more if he does not post.
simple rdiff backup script - TheFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)
[http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html)

What to backup TheFu
[https://ubuntuforums.org/showthread.php?t=2456011](https://ubuntuforums.org/showthread.php?t=2456011)
[https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507](https://ubuntuforums.org/showthread.php?t=2462752&p=14040507#post14040507)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
[https://ubuntuforums.org/showthread.php?t=2368992&](https://ubuntuforums.org/showthread.php?t=2368992&) 
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

---

### Post by Bashing-om on 2021-09-01
wyattwhiteeagle; Hello

My personal take on backups is: "why backup system files, as these are on the install media" ?

I only backup ( three places) my personal data with the rsync tool:
for an instance to a USB drive:
```

rsync -aiv --exclude=".*" --exclude uwn /home/sysop/ /media/sysop/store/

```
where I back up my /home.

I also keep a changelog of any changes I make to the default install.

[INDENT][INDENT]KISS :P
[/INDENT][/INDENT]

---

### Post by wyattwhiteeagle on 2021-09-01
> **Bashing-om said:**
> wyattwhiteeagle; Hello

My personal take on backups is: "why backup system files, as these are on the install media" ?

Good point

> I only backup ( three places) my personal data with the rsync tool:
for an instance to a USB drive:
```

rsync -aiv --exclude=".*" --exclude uwn /home/sysop/ /media/sysop/store/

```
where I back up my /home.

I also keep a changelog of any changes I make to the default install.[INDENT][INDENT]KISS :P
[/INDENT]
[/INDENT]


A few question's...

Does it backup the user's customized setting's?

Am I able to specify where the backups are NOT stored, but also where they ARE stored without manually moving the backups to those places?

Is it possible to have the backup produce a changelog that look's somewhat like this...
(Note: This is only an example. The applications and versions may or may not match any real scenario.)
> Lubuntu 20.04 LTS
08-01-21 15:57

Uninstalled...
Norton..........3.2.1
McAfee........4.3.2
Quicken.......5.4.3

Installed.......
Thunderbird...3.2.1
Stacer............4.3.2
Bleachbit.......5.4.3

Backup and Changelog stored at (with date in the file name for easy identification)...
Place 1 
Place 2
Place 3

---

### Post by TheFu on 2021-09-01
I'm guessing Oldfred's links to my prior posts likely cover everything.  Modern backup tools aren't copies. They are differences (forward or backwards) in time.  It doesn't take much storage to have 90 days of daily backups, so why would anyone settle for just 3?  In 3 backups, you probably won't notice corrupted files or malware infected files.

There are trade offs between the amount of storage used, the time and hassle it takes to get a clean backup and the complexity of the restore process.  Please do some reading, see what makes sense to you, and ask some questions.

There is no "best backups" - if you don't actually do them or if they are too much hassle. Backups that don't actually let you restore what you need are also failures.  No backup is "good" until it is tested through a restore.  It would be terrible to run backups for a year only to find that not all the stuff needed to restore was included.  Had a client do that.  Nobody had bothered to validate their backup processes could actually be restored.  They ended up trying to restore data from each of their 100 different desktops because the server backup hadn't worked for over a year.

---

### Post by wyattwhiteeagle on 2021-09-02
> **TheFu said:**
> I'm guessing Oldfred's links to my prior posts likely cover everything.  Modern backup tools aren't copies. They are differences (forward or backwards) in time.  It doesn't take much storage to have 90 days of daily backups, so why would anyone settle for just 3?  In 3 backups, you probably won't notice corrupted files or malware infected files.

There are trade offs between the amount of storage used, the time and hassle it takes to get a clean backup and the complexity of the restore process.  Please do some reading, see what makes sense to you, and ask some questions.

There is no "best backups" - if you don't actually do them or if they are too much hassle. Backups that don't actually let you restore what you need are also failures.  No backup is "good" until it is tested through a restore.  It would be terrible to run backups for a year only to find that not all the stuff needed to restore was included.  Had a client do that.  Nobody had bothered to validate their backup processes could actually be restored.  They ended up trying to restore data from each of their 100 different desktops because the server backup hadn't worked for over a year.

TheFu, I admire your advice, and thank you for it all.

Reading the above brings to my mind the thread I started about MyPaint.
I was trying to find something that very closely resembles mspaint.exe in Windows. (both inside and out)
Seems like the majority of tools that I was looking through resembles more to Paint.net rather than mspaint.exe.
Including what is in the repositories.
I got MyPaint installed through Wine on Ubuntu.
It wouldn't install outside of Wine.
That's as far as I got with MyPaint.
Any time I tried to open it, I had all kinds of issue's.
Any time I tried to uninstall it via CLI and GUI...I had more issue's and it was still on the system.
Some who were trying to help me there, seemed as though they believed I wanted MyPaint.
Why would I want something I can't use?

Same goes for "a years worth of backups ending up not being as thorough or as reliable as the user had believed."
So, yes...it is very crucial that the user validate and confirm that each backup is both thorough and reliable before they actually need it.
I believe that process involves a "throw-away machine" that is used only for testing such things.
Or other people's experiences.

When I said "best" here, I meant what is best for my current system specs and hardware setup that I'm having to resort to.
Most certainly I'm not the first to have encountered this particular scenario.
Because of that, it seems that some people (not everybody, but only those who have actually gone through what I'm going through) are purposely being reluctant to share any ensight.

Though this is important, I wasn't meaning it as in "What's best for the new user, or for the ease of use".

It's almost like some people don't believe it is actually possible to install to a usb flashdrive the way I installed to it.
Seems as though they are reverting to the belief that "That's not possible. He must be on a LiveUSB."
That is until they see "real proof" from details layed out by Gparted.
Of course, the "burden-of-proof" is on the person making the claims.

After using MKUSB, I thought..."this looks and acts like a descending product put together by someone who wanted their own personal prototype of something original".

Turns out, my thought was correct.
I learned it was correct by looking at the "something else" option in Ubuntu's installation procedure.

The installation procedure in both are very similar to each other.

---

### Post by ActionParsnip on 2021-09-02
Additionally, no backup strategy is best. It depends on what sort of restores you want to be able to do. In computing there is rarely a single best solution for.... Anything.

---

### Post by wyattwhiteeagle on 2021-09-02
> **ActionParsnip said:**
> Additionally, no backup strategy is best. It depends on what sort of restores you want to be able to do. In computing there is rarely a single best solution for.... Anything.

Following the same as in contraceptions..."No single thing or practice is 100%".

Even using a combination of things isn't 100%

Here's the catch..."Something is better than nothing. More than one of those something's is better than only one something."

I'm actually thinking of a "multi-strategy". A "Plan A, Plan B, Plan C, and so forth"...as well as a "multi-tier strategy", "this tool, this script, etc."

and eliminating those that don't work.

---

### Post by HermanAB on 2021-09-02
Only backup your data, since there are copies of Linux at every university and ISP, you don't need to keep one too.  Each time you reinstall Linux, it is easier and then you have the latest version.  In general with Linux there are no license keys to safeguard, so saving program settings is usually not helpful either.

As for your data, unless you are wealthy enough to have lots of storage, use a differential backup system.  You can easily keep three versions of all changed files, for very little more space than a single version.  It can be very simple: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by wyattwhiteeagle on 2021-09-02
> **oldfred said:**
> 
simple rdiff backup script - TheFu
[https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)


Re: Backup-Drive permissions/formatting --
Backing up HOME directories is bonehead simple.
a) use a real backup tool, not rsync or grsync.
b) run it from a crontab - root is the account.
c) when root runs a backup tool, permissions are handled. They will be retained automatically both when doing the backup and when restoring.
d) Be certain to backup /etc/ and the list of manually installed packages too.


Yes, using ext4 is a reasonable choice if you don't have any specific reason to use some other type.


```
#!/bin/bash


# Create the list of manually installed packages - use apt-mark showmanual and store that output somewhere that gets included in the backups.  I put it into /root/backups/
/usr/bin/apt-mark showmanual > /root/backups/apt-mark.manual
######[ to restore pkgs ]#######
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade


######
# Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.


# mount the backup disk as needed; best not to leave it mounted.
/bin/mount /Backups


# Ensure backups are by hostname, so multiple hosts can use the same backup storage
mkdir  -p /Backups/$(hostname)


# Run rdiff-backup  options sources  target
/usr/bin/rdiff-backup  --exclude-special-files --include  /etc  --include /root   --include  /home  \
                                            --exclude '**'    /       /Backups/$(hostname)


# Remove really old backup sets - say 90 days old.
/usr/bin/rdiff-backup --force --remove-older-than 90D    /Backups/$(hostname)


# umount the backup disk
umount /Backups

```

Simple. Put that into a file, make the permissions +x, then put that file /path/name into root's crontab to run daily.
More rdiff-backup examples: [http://rdiff-backup.nongnu.org/examples.html](http://rdiff-backup.nongnu.org/examples.html)


Ok, here is one area where I get confused about scripting...

> a) use a real backup tool, not rsync or grsync.
Is Timeshift considered a "real" backup tool?

> b) run it from a crontab - root is the account.
How exactly do I do that?

> [COLOR=#000000]*d) Be certain to backup /etc/ and the list of manually installed packages too.*[/COLOR]
Are these defined in the above script, or is it something that needs to be edited into the script?

> [COLOR=#000000][FONT=&amp]Clean up garbage inside all the HOME directories before doing the backup.  No need for cache or trash files, for example.[/FONT][/COLOR][COLOR=#000000][FONT=&amp]
The script contains lines such as the above.
Is that something I need to do, or does the terminal or whatever do those for me?

[/FONT][/COLOR]> [COLOR=#000000]*Simple. Put that into a file, make the permissions +x, then put that file /path/name into root's crontab to run daily.*[/COLOR]
Make the permissions +x...are you talking about making the file executable (ie, chmod 700, or similar)?

How do I put that file /path/name into root's crontab?

Does it automatically run or do I have to manually run it?

---

### Post by wyattwhiteeagle on 2021-09-02
> **HermanAB said:**
> Only backup your data, since there are copies of Linux at every university and ISP, you don't need to keep one too.  Each time you reinstall Linux, it is easier and then you have the latest version.  In general with Linux there are no license keys to safeguard, so saving program settings is usually not helpful either.

As for your data, unless you are wealthy enough to have lots of storage, use a differential backup system.  You can easily keep three versions of all changed files, for very little more space than a single version.  It can be very simple: [https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

A "differential backup system"
Thank you for that

I get in one month what you probably get in one week.
I'm nowhere near "wealthy"

Only backup my data. Explain this to me please.
My personal data as in pics songs household records, or my system data which would include custom settings?
Other people are saying whatever I don't want to lose, but that answer doesn't really clarify.

So, why are other people saying that saving their custom settings are getting included into their backups?

[https://ubuntuforums.org/showthread.php?t=2441366](https://ubuntuforums.org/showthread.php?t=2441366)
Alot of info at that closed thread

You suggested that same link to me in the above closed thread
[https://ubuntuforums.org/showthread.php?p=13949311#post13949311](https://ubuntuforums.org/showthread.php?p=13949311#post13949311)

I had some questions in that thread concerning the info at your link
[https://ubuntuforums.org/showthread.php?t=2441366&p=13949327#post13949327](https://ubuntuforums.org/showthread.php?t=2441366&p=13949327#post13949327)

You never responded.
You suggested something, and then completely disappeared.
That's not helping, really.

Are you gonna bail on this one too?

---

### Post by TheFu on 2021-09-02
Seems you may be reaching beyond your current skill level.  Unix skills build on each other.  This is why many people dislike it. It requires knowledge that grows to get to a certain level before all the pieces start clicking. Prior to that point, people's eye gloss over and fairly simple things seem difficult.

I tend to avoid helping beginners because I'm terrible at answering "simple" questions and we both get frustrated. That doesn't help them and it doesn't help me.

You've listed a number of general knowledge items that are part of what I consider basic Linux/Unix skills.  This thread is about backups. Herman and I have provided links to fairly simple answers.

If you don't understand Unix permissions, that is the first skill to be learned.  It isn't hard and there is a simple elegance to how it works. There's no use avoiding this because you will waste hours, days, weeks, months, years until it is learned. Takes about 45 minutes of concentration to learn 90% of it.

If you don't understand cron and crontabs, that is how things get automated on Unix systems. It isn't hard either.  But that topic really belongs in a separate thread ... depending on what you want.

For how Unix system files are laid out, Google "Linux File system hierarchy."  There is a wikipedia article with a table. That is pretty much all that 99% of us need to know for which types of files go where.  From that table, you'll know what should be backed up.  Plus there are lots of threads here where people list what they backup.  Typical end-users need $HOME, /etc/ and a list of installed packages.  I'd bet that Herman's script gets that and I know that the one you pasted above does.

As for how to read a script ... well ... you actually need to read it.  My scripts are commented.  If you ask about 1 line you don't understand, someone will probably explain it.  For bash scripting, you'll want to understand a little bash.  [https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/)  ... this says "Advanced", but it starts from the beginning, so don't be fearful.

For normal, daily use, command line stuff, [https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php) is an easy introduction.

In the beginning, the learning curve is steep.

When we don't answer a specific question, usually that is because it is already answered OR we don't have experience in that area.  I've never used timeshift, but I have read about it.  It operates in 2 very different modes depending on the file system.  Everyone I know who uses it, has another backup tool they need to use for stuff that timeshift doesn't handle.  Should we all have 10 backup tools to get 1 system backup?  I say no.  1 tool that actually works, is what someone should use.

When I say not to use rsync for backups, that is because I used it for over a decade and found where it works great and where it fails completely.  For a remote server running in a VPS, using rsync is probably fine.  The number of files and size of the total backup are relatively tiny compared to what a desktop would have.  Most of my server backups are ~5G.  That's nothing.  For a desktop, 50G would be a typical "backup" if not 500G or 5TB.  rsync becomes impractical as the number of files increases. There are a number of other reasons rsync isn't the best tool, but everyone has different needs and different skills.

Almost all Linux backup tools are based on librsync, which is the library that rsync uses. I'm not anti-rsync. Heck, I use it 10x almost every day.  What I'm against is having to manually do things for backups that rsync isn't good at - like versioning.  rdiff-backup does the versioning of backups for us.  There is little extra effort needed to have 1 mirror (like rsync does) or 200 versions, which is what rdiff-backup can easily support.  The most recent rdiff-backup is just like an rsync mirror, so we keep that simplicity.  The second and later backups run much faster with rdiff-backup and use a tiny amount of additional storage, not a full copy of yet another mirror.  rdiff-backup isn't hard to script. See above. There are 2 commands. One creates a new backup version and the other trims really old versions off the end.  If you only want 3 versions, there's an option to do that, but if your backup storage has room, wouldn't more versions be better?  We never know when a file got corrupted until we try to use it.  I had a DB corrupted on a system due to a failed software upgrade. Most of the software was working, but not everything.  Then I needed to do some once-a-quarter work and found that the file had been corrupted 37 days prior.  If I didn't have 90 days of versioned backups, I'd have been screwed.  Do you see why more backup sets are useful?  What if I'd not noticed for the entire quarter - 90+ days?
And I can't say how many times I do dumb things on my systems and reach for the backup files to fix it. Usually it is a simple data files - like a spreadsheet. I know that every night a backup gets made automatically. Getting the file back from yesterday is just a copy out of the backup storage to the working storage area.

As for testing the restore process ... I use virtual machines for that.  You would use another USB stick.

---

### Post by QIII on 2021-09-02
@wyattwhiteeagle

> You never responded.
You suggested something, and then completely disappeared.
That's not helping, really.

Are you gonna bail on this one too?


We all get frustrated at times.  However, I would suggest that you remember that all of us here are volunteers giving our time as we have it to give.  We are not employees of Canonical, we are not paid to be here, we do not work on schedules.  People do have other things to do in life.  In the case of the thread you cited, oldfred stepped in to answer some of your questions.

Do not demand that specific community members snap to attention and, forsaking their own lives, immediately and fully divert their attention to address your questions.  This is a community:  If someone has to be elsewhere, another can step in.

Curb your indignation and cool your jets, please.

---

### Post by GhX6GZMB on 2021-09-02
[COLOR=#000000]@wyattwhiteeagle

Every user's backup needs are different as most people have pointed out.

Let me describe my scenario and why I backup the way I do as an example.

I use older HP business laptops (~2008, 2009, 2010) because they are cheap, perform extremely well and have all the hardware ports/interfaces that modern laptops miss. The keyboards are excellent, as opposed to the "designer" types today, and the screens are matte, allowing outdoor work. Upgrading RAM (2 GB and 4 GB work well) and using SSD is no issue. It just works. And Lubuntu gives them 4x the performance of the earlier Vista OS. They're really fast :)

I split my hard drive as follows:
[/COLOR]```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom 


```[COLOR=#000000]
Because I want to be able to reinstall/reconfigure my system without having to worry about my documents/pictures/videos etc. They are all on /home

Now for backup, there are two scenarios in my life:

1: backing up my data in /home. This I do on a weekly/daily basis, depending on activity. For this I use BackInTime, which was designed for this purpose. It can do system backups as well, but that's a bit kludgy.

2: backing up my system. Now, the argument that this is not necessary, beacuse I can reinstall it all again I regard as nonsense. Over time, you do so many installations, tweaks, modifications etc. that a reinstall/reconfiguration of it all will take at least a day. I do system backups when I plan on changing something on the system: new installs, tweaking a setting, fiddling with system files etc. It gives me a good feeling, and has saved my behind several times, when I've done something stupid, even to the point of a complete reinstall.
For this I use Timeshift, which is optimized for this task.

So for me, it's two completely different situations. Using two backup programs may seem quirky ("one or the other can do both jobs"), but it's a question of ease-of-operation. Once set up, each is just a couple of clicks.

Both programs are rsync-based incremental backups, so only the initial backup takes some time, every subsequent one takes a minute or two.

I don't know your situation, but this works for me.

Cheers.

[/COLOR]

---

### Post by wyattwhiteeagle on 2021-09-02
> **wyattwhiteeagle said:**
> 
You never responded.
You suggested something, and then completely disappeared.
That's not helping, really.


Are you gonna bail on this one too?


> **QIII said:**
> @wyattwhiteeagle


We all get frustrated at times. However, I would suggest that you remember that all of us here are volunteers giving our time as we have it to give. We are not employees of Canonical, we are not paid to be here, we do not work on schedules. People do have other things to do in life. In the case of the thread you cited, oldfred stepped in to answer some of your questions.


Do not demand that specific community members snap to attention and, forsaking their own lives, immediately and fully divert their attention to address your questions. This is a community: If someone has to be elsewhere, another can step in.


Curb your indignation and cool your jets, please.


I'll curb and cool.

---

### Post by wyattwhiteeagle on 2021-09-02
Thanks to all for the patient guidance. It is very much appreciated.

I believe no matter what I choose, it is only very temporary given my hardware setup and skill level.

> 128gb usb as my hard drive
2-6gb swap area
4gb RAM

It's looking to me as though my prioritized choices need to be...

> Timeshift
BackInTime
Bash Script Backup

Timeshift and BackInTime while learning Bash.

Rsync scripting may become an option, but I fear it will conflict with Bash. Especially during the learning process.

The link within the post here where I was indignant with hot jets presented to me that rsync uses the cloud, I realize now that using the cloud is only an option and not a requirement.
I know the cloud is a good thing, but I'm not a major cloud user.

I tried just opening root's crontabs folder, it said permission denied.
A bit of a revelation to myself that I need to be realistic about my skill level and not try to learn too much too soon.

The 1.0 TB internal hard drive suddenly not working sent me into a panic where all options of recovering, including backup, was catching my attention all at once.

---

### Post by TheFu on 2021-09-02
Back-in-Time does rsync+hardlink backups.  I think Timeshift does the same thing on non-BTRFS systems.  You don't need both.  Back-in-Time can make full and selected backups.

rsync has a target and a source.  Where those are located are up to you.  If you have a cloud provider that supports rsync, then you can point it there, but it isn't necessary.  rsync can be used for 100% local, same computer, backups.   I think using cloudy services is a bad thing for anything you don't expect to share with everyone on the internet.  _"Cloud computing is careless computing."_  This has been proven true over and over.  Don't put anything onto cloudy servers you don't want to share with the entire world.

> I tried just opening root's crontabs folder, it said permission denied.
A bit of a revelation to myself that I need to be realistic about my skill level and not try to learn too much too soon.
Probably a good idea, since you shouldn't be using any GUI to attempt this specific thing.  I'm afraid to provide any guidance, since you could end up harming your system doing this with your current level of knowledge.  

Download a copy of that book I linked above.  Ensure you don't skip over the early chapters that explain how different userids run with different euid and egid values.  That basic understanding leads into Unix permissions, which is the core of the entire OS security.

---

### Post by wyattwhiteeagle on 2021-09-03
> **ml9104 said:**
> [COLOR=#000000]
1: backing up my data in /home. This I do on a weekly/daily basis, depending on activity. For this I use BackInTime, which was designed for this purpose. It can do system backups as well, but that's a bit kludgy.

2: backing up my system. Now, the argument that this is not necessary, beacuse I can reinstall it all again I regard as nonsense. Over time, you do so many installations, tweaks, modifications etc. that a reinstall/reconfiguration of it all will take at least a day. I do system backups when I plan on changing something on the system: new installs, tweaking a setting, fiddling with system files etc. It gives me a good feeling, and has saved my behind several times, when I've done something stupid, even to the point of a complete reinstall.
For this I use Timeshift, which is optimized for this task.

So for me, it's two completely different situations. Using two backup programs may seem quirky ("one or the other can do both jobs"), but it's a question of ease-of-operation. Once set up, each is just a couple of clicks.

Both programs are rsync-based incremental backups, so only the initial backup takes some time, every subsequent one takes a minute or two.

I don't know your situation, but this works for me.

Cheers.

[/COLOR]

Timeshift vs BackInTime

Per the quoted guidance, I will try one and if it doesn't work for my USB install, I will try the other.

I seen a post where Timeshift was able to be configured to do what I'm wanting.
( [https://ubuntuforums.org/showthread.php?p=14011521#post14011521](https://ubuntuforums.org/showthread.php?p=14011521#post14011521) )

I will try Timeshift first.

---

### Post by HermanAB on 2021-09-03
The problem was that you were asking very basic questions about file paths and mounts, which means that you still had a lot to become familiar with. What I see in this thread, is that you are rapidly learning from TheFU and therefore I don’t need to say anything more - you’ll be a graybeard UNIX guru in another week or so! &#128561;

---

### Post by GhX6GZMB on 2021-09-03
> **wyattwhiteeagle said:**
> Timeshift vs BackInTime

Per the quoted guidance, I will try one and if it doesn't work for my USB install, I will try the other.

I seen a post where Timeshift was able to be configured to do what I'm wanting.

I will try Timeshift first.

I think they're already in the repository, just run muon to install either.

---

### Post by TheFu on 2021-09-03
> **ml9104 said:**
> I think they're already in the repository, just run muon to install either.

All the tools I've seen are in Canonical's repos.  Use whatever front-end to APT you like.

---

### Post by ActionParsnip on 2021-09-03
> **wyattwhiteeagle said:**
> Following the same as in contraceptions..."No single thing or practice is 100%".

Even using a combination of things isn't 100%

Here's the catch..."Something is better than nothing. More than one of those something's is better than only one something."

I'm actually thinking of a "multi-strategy". A "Plan A, Plan B, Plan C, and so forth"...as well as a "multi-tier strategy", "this tool, this script, etc."

and eliminating those that don't work.

Yes. I'm just highlighting the fallacy of this whole idea of "best" that people seem to like to use. It's nonsense

---

### Post by TheFu on 2021-09-04
> **ml9104 said:**
>  
2: backing up my system. Now, the argument that this is not necessary, beacuse I can reinstall it all again I regard as nonsense. Over time, you do so many installations, tweaks, modifications etc. that a reinstall/reconfiguration of it all will take at least a day. I do system backups when I plan on changing something on the system: new installs, tweaking a setting, fiddling with system files etc. It gives me a good feeling, and has saved my behind several times, when I've done something stupid, even to the point of a complete reinstall.
 

I agree. A backup that can get the system restored to how it worked is absolutely critical, but there are different techniques for accomplishing that without saving stuff that is trivially replaced.

Assumptions:
[LIST]
[*]Storage is expensive.  Having at least 5 versions to restore is the minimal needed to survive malware, software corruption, and bonehead user mistakes (that we all make)
[*]Backups that aren't convenient won't be done.  That means they need to be fast, encrypted, and automatic.
[*]Restores that aren't easy won't be done.  There is a trade off between 1-click restores and 5 step restores in convenience.
[*]Restore time should be ASAP, but never more than 1 hour. In that period, the system needs to be back, as it was, productive, and working with all critical data.
[*]The backup area shouldn't have funky storage formats that humans cannot understand.  80% of restores are for the *last version of a file*.  That can be 1 file, a full directory system, including all subdirectories, or everything in the backup for that time. Most restores should be a simple copy back of a file.
[*]A broadband internet connection is available.  If this isn't the situation or it isn't possible to download ~200MB as part of the restore, then 100% local restore is required.
[/LIST]

If a restore takes more than 45 minutes total, I'd be unhappy too.  System settings are stored in /etc/  Period.  If they are anywhere else, that is a failure of the packaging for that program.  Let's break down the restore time, Barney style.

Doing a fresh, minimal install is 10-15 minutes.

Restoring /home and /etc/ and /usr/local and the scripts I need in /root/ is no more than 15 minutes.  Total 30m so far.

Restoring any huge data areas that are controlled by the system is usually just for servers, not desktops, but that takes what it takes 5min - 5 days. Just depends on the number of TBs. On a blog server, I'd restore everything in /var/www and all the DBs in /var/lib/mariadb .... which is less than 5 min.  So skipping music, 40K photos, and video. Around 35 minutes total for our restore so far.

Feeding the list of manually installed packages (I back those up to /root/backups/ nightly), into APT takes 5 seconds, before the daily backups happen. It is part of my backup script. Then telling APT to install them and all dependencies will see your settings in your HOME and /etc/. APT will honor those 100% and install the packages as though they are a **sudo apt install --reinstall {package}** command.  Prior settings will be used.  How long this takes depends on the number of applications and network speed.  For me, it is 10 minutes or less.  For servers, it is much less.

So, there you have it - **45 minutes total time** to restore a system to feel like "_my system_" with all my settings, programs, and most of my data restored (if not all of my data).

There are some manual steps to this, but the payoff is vastly returned in
[LIST]
[*]total backup time; minutes or seconds.
[*]backup storage; 1.2x the source size for 60 days of daily backups.
[*]Flexibility at restore time to change out the entire storage architecture and the OS, if needed.
[/LIST]

Want to change from ext4 to ZFS, fine. Want to change from encrypted to non-encrypted storage, fine.  I've moved OSes using this. Last year, I restored a 16.04 desktop (32-bit) system into a freshly installed 20.04 64-bit system.  Took 45 minutes, until I was productive again.  That last example needed a bit longer for some non-core capabilities since different OSes ARE different.  My first 20.04 install was with experimental ZFS ... that lasted about an hour before I wiped it and reinstalled using LVM+ext4.  Every Sunday morning, I kick out a report about the backup sizes ... here's the report for that desktop which was converted:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Aug 29 01:15:03 2021         6.08 GB           6.08 GB   (current mirror)
Sat Aug 28 01:15:04 2021         2.09 MB           6.08 GB
Fri Aug 27 01:15:04 2021         2.88 MB           6.09 GB
Thu Aug 26 01:15:03 2021         3.27 MB           6.09 GB
...
Fri Jun  4 01:15:03 2021         27.2 MB           8.85 GB
Thu Jun  3 01:15:04 2021         2.66 MB           8.85 GB
Wed Jun  2 01:15:04 2021         2.69 MB           8.85 GB
Tue Jun  1 01:15:05 2021          237 MB           9.08 GB
```
So, I'm backing up about 6G - amazing how little is needed when you don't bother with the OS and things that are trivially replaced.  Looks like I keep 90 days of versioned backups ... which use a little over 9G in total storage.  So, for just 30% more storage than the source backup areas, we get 90 days of versioned backups.  Seems like a bargain to me.  Of course, YMMV based on the amount of churn you have on the system.

Backups are run daily at 1:15am and usually take less than 2 minutes.  From yesterday:
```
StartTime 1630646103.00 (Fri Sep  3 01:15:03 2021)
EndTime 1630646189.75 (Fri Sep  3 01:16:29 2021)
ElapsedTime 86.75 (**1 minute 26.75 seconds**)
TotalDestinationSizeChange 3418161 (**3.26 MB**)
```

Anyways, if it takes more than an hour to have a useful, functioning, system, I'd say the restore process is bad and needs to be reworked.  Of course, we aren't talking about restoring 4TB of data.  That restore would take many hours just to put the data back, but the OS, applications, settings and DBs should be ready to go in well under 1 hr.

I just setup a new email gateway server.  It doesn't have an data ... it is a filter. Just store-->forward for SMTP in and out.  It is using
```
$ df -Th
Filesystem           Type      Size  Used Avail Use% Mounted on
lxd/containers/spam1 zfs        13G  640M   12G   6% /
```
640MB of storage. How quick is that backup?  Seconds.  There are 180 days of versioned backups because it is a very high-risk system for being cracked.

I'm curious about Timeshift.  Could be very nice ... guess it doesn't work on a system without any GUI, like all Linux servers? Of my 15 systems, only 2 have GUIs. Also, I use "pulled" backups and consider that mandatory.  Seems timeshift doesn't support pushed or pulled backups between systems. If that isn't possible, it is not very useful for my needs.  Backups are not just about dead hardware, but also about security restores post-attack. That's the reason for requiring "pulled" backups.

As part of my research, I read both the great and the not-so-great about backup tools.  Seems that restoring the boot areas when restoring to new disks doesn't always work.  They actually recommend having another backup to handle the boot areas AND HOME directories.  That's 3 tools total for a system backup. Why not just start with a fresh install in that situation?  Is it just to avoid having to touch the fstab file?

---

### Post by wyattwhiteeagle on 2021-09-04
> **HermanAB said:**
> The problem was that you were asking very basic questions about file paths and mounts, which means that you still had a lot to become familiar with. What I see in this thread, is that you are rapidly learning from TheFU and therefore I don’t need to say anything more - you’ll be a graybeard UNIX guru in another week or so! &#128561;

With me being a 20+ years Windows user who wanted to do different things, I would agree with you.

I take my time learning because I don't want to run into the "uh oh, what did I do wrong and how do I correct this" type of routine.

I get impatient when I run into problems and trying to learn the absolute resolution to a problem

A lot of the problems I run into is due to my impatience

Most of all, I apologize for my indignant outburst towards you earlier.

---

### Post by mike.berkley@gmail.com on 2021-09-07
rsync + ZFS snapshots on an external disk work well for me.
backuppc is harder to setup, but it's good at space management, especially for multiple systems.
On the issue of backing up "system" files, I've found it useful to backup /etc, especially using ZFS snapshots to look back on old versions of config files.

---

### Post by TheFu on 2021-09-07
ZFS snapshots are not backups.  They are versions ON THE SAME physical DISK!  If that disk fails, you lose.

A ZFS snapshot + zsend to another system **is** a backup method that can work great. There are scripts written to make this easier.  
[https://github.com/jimsalterjrs/sanoid/](https://github.com/jimsalterjrs/sanoid/) from Jim Salter seems popular.  It includes **syncoid** to remotely replicate ZFS file systems.
```
#  syncoid data/images/vm root@remotehost:backup/images/vm
```
Those are ZFS storage locations, not exactly 1-for-1 maps to directories, FWIW.

Right now, the use of ZFS for boot storage under Ubuntu 20.04, is still highly experimental.

---

### Post by kevdog on 2021-09-07
I'm using zsnapzend ([https://github.com/oetiker/znapzend/](https://github.com/oetiker/znapzend/)) to send my zfs backups.  I backing up a homelab server with zsnapsend -- I get an email when the send starts and completes.  Clearly I don't generate a lot of data since the snapshots taken every 6 hours) take about 6 seconds to snap and transfer.  I'll be honest, I should probably practice the restore process a lot more than I do.  I've restored before from snapshot but like everytime it creates a "oh crap" moment and I have to sit down and start reading.  I make notes along the way but usually when I become frustrated that's when the note taking process ends for that episode.  With the snapshots -- its easy to either restore the entire volume -- or mount and cherry pick the files you really want or are missing.  I've done both depending on how "broke" the system is.

A shoutout to Jim Salter who was mentioned above -- I really like reading his articles on ArsTechnica.  They are usually very technical and straightforward.

---

### Post by TheFu on 2021-09-08
Attended a presentation Jim did at SELF a few years ago which convinced me to drop consumer routers and switch to an amd64-x86 router running constantly maintained firmware/systems.  I'd gotten frustrated by consumer (not necessarily cheap) routers only having 3 yrs of support.  Ended up buying a purpose-built, fanless, AMD box with 4 intel NICs to be my router ($140 all in) and loaded up pfSense.  About 2 yrs ago, switched that to OPNSense.  It is silent, easy to maintain, fast.  The latest release (less than 1 month old) of opnsense uses ZFS.  

I expect the hardware (PCengines APU2) to last 10+ yrs and still be supported by many versions of different firmware. I'm not trapped. opnsense patches every 2 weeks.  My prior tp-link router was lucky to get updates annually. Because it was unsupported, I'd actually dropped back to using an older router with dd-wrt on it instead.  pfsense and opnsense provide many more capabilities for solid routing that are a hassle with dd-wrt.

Anyway, I need to wipe my router and do a fresh install this weekend to get ZFS.  Older releases use ufs, with isn't exactly the best file system.
```
# df -Th
Filesystem       Type     Size    Used   Avail Capacity  Mounted on
/dev/gpt/rootfs  [COLOR="#FF0000"]ufs[/COLOR]       45G    2.1G     40G     5%    /
```

It is nice to have plenty of storage on a router for graphing and reporting too.

---

### Post by Paulgirardin on 2021-09-10
For what it's worth I use the same pattern as**[COLOR=#000000] M[/COLOR]**[URL="https://ubuntuforums.org/member.php?u=2127041"][B][COLOR=#000000]l9104
[/COLOR][/B][/URL] Backintime to save /home and my personal data drive (SDB) on a third storage drive (SDC)
Timeshift to save the system onto SDC ,this serves the same function as Windows restore points do. It has actually saved me on a couple of occasions. Timeshift is also supposed to be able to do a restore after a new install onto a different drive if the backups are accessible and therefore recreates all your personal settings - if I'm not mistaken.
I also back up selected  folders that are on my personal data drive (SDB) to Google Drive using an rclone script [https://rclone.org](https://rclone.org)
 and nearly all of SDB on my Mega cloud storage using the Mega Linux client (50GB free)

---

### Post by kevdog on 2021-09-10
@TheFu

Do you have 10G networking ports or sfp+ ports for your router?  I have a custom made "protectli" type box for my pfsense router (haven't yet switched to OPNSense), but I don't have any 10Gb routing.  I'd like however to make a self made box with sfp+ if that's possible.

---

### Post by Skaperen on 2021-09-11
i wrote my own rsync based backup tool two decades ago.  while it keeps a master tree in sync at the target, it also leaves positive reverse increment deltas for each time it is run.  i have not yet been motivated to write the part that makes the negative delta, but it would work from logs and listings, so it can be done much later in time if i ever need a negative delta, which is basically a list of files that were added since that increment and would be the list of files to delete to finish an accurate restore of an older date.  so far i've only had incidents where i needed to restore files just to get them back, not make an accurate tree that leaves out what it didn't have back then.  i can just discard old increments and can restore any date back to then, so i don't do a fixed number of increments.  i wrote a separate script to discard old increments to a specific file space usage percentage (i usually run 75%).  my script numbers things in a way that allows it to be run many times a day down to every minute (imagine up to 10080 increments per week) if the source and changes are small enough to be done in a minute.  logs and listings get compressed when done.

this tool has served me well enough over the years that i have not felt a need to really look at other tools.  please don't ask for a copy.  i don't have the time to support it in public or write documentation for it (there is none).  i didn't write it for the world.  i wrote it for me.  if you need reverse incremental backups, use *rdiff*.

---

### Post by TheFu on 2021-09-11
> **Skaperen said:**
> i wrote my own rsync based backup tool two decades ago.  while it keeps a master tree in sync at the target, it also leaves positive reverse increment deltas for each time it is run.  i have not yet been motivated to write the part that makes the negative delta, but it would work from logs and listings, so it can be done much later in time if i ever need a negative delta, which is basically a list of files that were added since that increment and would be the list of files to delete to finish an accurate restore of an older date.  so far i've only had incidents where i needed to restore files just to get them back, not make an accurate tree that leaves out what it didn't have back then.  i can just discard old increments and can restore any date back to then, so i don't do a fixed number of increments.  i wrote a separate script to discard old increments to a specific file space usage percentage (i usually run 75%).  my script numbers things in a way that allows it to be run many times a day down to every minute (imagine up to 10080 increments per week) if the source and changes are small enough to be done in a minute.  logs and listings get compressed when done.

this tool has served me well enough over the years that i have not felt a need to really look at other tools.  please don't ask for a copy.  i don't have the time to support it in public or write documentation for it (there is none).  i didn't write it for the world.  i wrote it for me.  if you need reverse incremental backups, use *rdiff*.

Back-In-Time does hourly rsync + hardlink backups.  Then, it selectively removes the backups over time.  It has the same flaw that all rsync-based, versioned-using-hard-links, backup tools have.

For 20+ yrs, lots of people and book authors have created scripts that use rsync + hardlinks for versioned backups.  This is extremely well-understood.
**rsnapshot**: rsync + hardlinks for versioned backups (requires Linux file system like ext4)
[Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](Https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](Https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/) 
[https://ubuntu.com/server/docs/backups-introduction](https://ubuntu.com/server/docs/backups-introduction) is sparse.  
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) has a long list of tools. 

The only one I'd say to avoid for most people is tar.  Tar was created when 20MB was considered huge.

I've never used rdiff. I use rdiff-backup many times, daily, across many different systems.

---

### Post by evinrude on 2021-09-13
I use 'btrfs' for all my backup devices . By doing this I can keep an arbitrary number of snapshots from which I can recover files or directories . See the script below .
To work the script needs at a minimum

1) a btrfs file system with a 'LABEL' of 'Daily'
2) a "/Daily" directory
3) a subvolume of 'Daily' named 'BackupRoot'
4) a directory  'rsync' with a file 'rsync.ex' in it (file may be empty) in your home directory (change 'your-user' in the script to your user)
5)'rsync' installed

you run the script as root like this "/usr/local/bin/rsync-btrfs.sh  Daily" (or where ever the script sits)

About 'btrfs' . Will lots of snapshots slow down the btfs volume ? Maybe , but who cares . Using this script I can save months or years worth of snapshots . The ability to recovery  a files,files or a home directory from a point in time days , weeks or months ago out weighs any performance hit (to me anyway) . 
This does not create backups from which you can do a cold metal restore . Its for preserving your data .

ZFS is perhaps a better solution than btrfs but given Linus Torvalds  recent comments about ZFS in linux I decided to use btrfs .

As with all  things linux your mileage may very .


```
[COLOR=#000000]#!/bin/bash [/COLOR]
# Dev=$(findmnt -l "$Which" --output SOURCE -n) 
Which="$1" 
NoCheck="$2" 
int() { 
   printf "%.0f\n" "$@" 
   } 

echo -e "\n--------------------------------" >>/var/log/rsync.out 
date >>/var/log/rsync.out 
echo      "--------------------------------" >>/var/log/rsync.out 

if [[ -d /$Which/BackupRoot ]] 
   then 
   echo -e "\n<<<<<< Backup Drive All Ready Mounted >>>>>>\n" >>/var/log/rsync.out 
   exit 
   fi 
mount /$Which 
if [[ ! -d /$Which/BackupRoot ]] 
   then 
   echo -e "\n<<<<<< Backup Drive Mount Failed,BackupRoot not found >>>>>>\n" >>/var/log/rsync.out 
   exit 
   fi 

Date=$(/bin/date +%Y-%m-%d-%b-%s) 

Need=$(Need=$(/usr/bin/rsync -an --stats  --no-human-readable --exclude-from=/home/your-user/rsync/rsync.ex / /$Which/BackupRoot\ 
       | grep "Total transferred file size" \ 
       | cut -f5 -d' ');Need=$(echo "$Need""*1.5" | bc);int $Need) 
test -f /$Which/full && rm /$Which/full 
btrfs subvolume list /$Which | tr -s ' ' | cut -d ' ' -f 9 | grep "snap@BackupRoot" | sort | while read Snap 
   do 
   Avail=$(Avail_blocks=$(df --output=avail /$Which | grep -vi avail);echo "$Avail_blocks""*1024" | bc) 
   echo "Need " $(echo ${Need} | sed ':a;s/\B[0-9]\{3\}\>/,&/;ta') \ 
        "Have " $(echo ${Avail} | sed ':a;s/\B[0-9]\{3\}\>/,&/;ta') >>/var/log/rsync.out 
   if [[ $Avail -lt $Need ]] 
      then 
      echo -e "\n<<<<<< delete Snap $Snap to make space $(date) >>>>>>\n" >>/var/log/rsync.out 
      touch /$Which/full 
      btrfs subvolume delete -C /$Which/$Snap >>/var/log/rsync.out 
      btrfs filesystem sync /$Which 
   else 
      rm /$Which/full 
      break 
      fi 
   done 
test -f /$Which/full && exit 
if [ -f /$Which/Rsynced ] 
   then 
   btrfs subvolume snapshot /$Which/BackupRoot /$Which/snap@BackupRoot-"$Date" >>/var/log/rsync.out 2>&1 
   touch /$Which/snap@BackupRoot-"$Date" 
   fi 
/usr/bin/rsync -aX --stats --exclude-from=/home/your-user/rsync/rsync.ex / /$Which/BackupRoot >>/var/log/rsync.out 2>&1 
touch /$Which/Rsynced 
umount /$Which

```

---

### Post by TheFu on 2021-09-13
evinrude thanks for sharing.

BTRFS has "real" snapshots, but just like other "real" snapshots, they are not backups because the data isn't moved to another storage device.  Just want to make that EXTREMELY CLEAR.  It is the rsync that creates the real backup.  Using snapshots on the target storage **is** unique (except with ZFS) IME. Still - it should work nicely.

Nice perspective.

It would help regulars here if you could wrap your script(s) in "code tags", so the entire script jumps out.  That's available in the Advanced editor using the (#) button, or use any other select-tag like quote/bold/italics and change the "quote" --> "code" leaving the  brackets alone.  Plus, it would retain the indentation formats which I'm sure is in the script - we just don't get to see it.  Code tags are best for anything you'd see or run in a terminal.  I try to be very consistent with code tags in these forums. Really helps with readability.

---

### Post by evinrude on 2021-09-13
Heres the script a little more readable I think

```
#!/bin/bash
# Dev=$(findmnt -l "$Which" --output SOURCE -n)
Which="$1"
NoCheck="$2"
int() {
   printf "%.0f\n" "$@"
   }

echo -e "\n--------------------------------" >>/var/log/rsync.out
date >>/var/log/rsync.out
echo      "--------------------------------" >>/var/log/rsync.out

if [[ -d /$Which/BackupRoot ]]
   then
   echo -e "\n<<<<<< Backup Drive All Ready Mounted >>>>>>\n" >>/var/log/rsync.out
   exit
   fi
mount /$Which
if [[ ! -d /$Which/BackupRoot ]]
   then
   echo -e "\n<<<<<< Backup Drive Mount Failed,BackupRoot not found >>>>>>\n" >>/var/log/rsync.out
   exit
   fi

Date=$(/bin/date +%Y-%m-%d-%b-%s)

Need=$(Need=$(/usr/bin/rsync -an --stats  --no-human-readable --exclude-from=/home/ajminson/rsync/rsync.ex / /$Which/BackupRoot\
       | grep "Total transferred file size" \
       | cut -f5 -d' ');Need=$(echo "$Need""*1.5" | bc);int $Need)
test -f /$Which/full && rm /$Which/full
btrfs subvolume list /$Which | tr -s ' ' | cut -d ' ' -f 9 | grep "snap@BackupRoot" | sort | while read Snap
   do
   Avail=$(Avail_blocks=$(df --output=avail /$Which | grep -vi avail);echo "$Avail_blocks""*1024" | bc)
   echo "Need " $(echo ${Need} | sed ':a;s/\B[0-9]\{3\}\>/,&/;ta') \
        "Have " $(echo ${Avail} | sed ':a;s/\B[0-9]\{3\}\>/,&/;ta') >>/var/log/rsync.out
   if [[ $Avail -lt $Need ]]
      then
      echo -e "\n<<<<<< delete Snap $Snap to make space $(date) >>>>>>\n" >>/var/log/rsync.out
      touch /$Which/full
      btrfs subvolume delete -C /$Which/$Snap >>/var/log/rsync.out
      btrfs filesystem sync /$Which
   else
      rm /$Which/full
      break
      fi
   done
test -f /$Which/full && exit
if [ -f /$Which/Rsynced ]
   then
   btrfs subvolume snapshot /$Which/BackupRoot /$Which/snap@BackupRoot-"$Date" >>/var/log/rsync.out 2>&1
   touch /$Which/snap@BackupRoot-"$Date"
   fi
/usr/bin/rsync -aX --stats --exclude-from=/home/ajminson/rsync/rsync.ex / /$Which/BackupRoot >>/var/log/rsync.out 2>&1
touch /$Which/Rsynced
umount /$Which
```

---

### Post by TheFu on 2021-09-13
BTW, could have "edited" the prior post to keep the thread cleaner.

---

### Post by wyattwhiteeagle on 2022-02-12
UPDATE:

TimeShift vs BackInTime

Both allow the user to configure (optimize).

TimeShift seems to be a "simple" tool euivalent to Windows system restore point.
Not exactly what I'm looking for.

BackInTime gives the user more configuring options.
Almost what I'm looking for.

How would I configure BackInTime to save the snapshot to a usb flashdrive?

---

