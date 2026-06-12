---
title: "How to use rdiff-backup remotely whilst maintaining user/group/attributes etc"
date: 2024-01-17
forum: General Help
---

### Post by freeflyjohn on 2024-01-17
I am looking for guidance on how to use rdiff-backup to perform a remote backup over ssh, whilst maintaining user/group/attributes etc

I have an Ubuntu server machine and an Ubuntu client machine, both of which have been setup to use ssh keys and can connect succesfully without needing a password.

I am trying to perform a backup from the Ubuntu server HDD to the Ubuntu client HDD.

 However, the backup will only maintain user/group/attributes etc if I run rdiff-backup as 'sudo' on the client machine, despite using an equivalent-root user I created on the server.

The equivalent-root user was created on the server using the following guide [https://mhagemann.medium.com/how-to-create-a-user-with-root-privileges-on-ubuntu-93de0bec648c](https://mhagemann.medium.com/how-to-create-a-user-with-root-privileges-on-ubuntu-93de0bec648c)

i.e.

```

sudo adduser rembackup
sudo usermod -aG sudo rembackup

```

To simplify testing, I created a single folder containing a single file on the server HDD which is used for the backup...  

```

Folder called 'testroot' created with sudo....

drwxr-xr-x  2 [COLOR=#ff0000]root[/COLOR]      [COLOR=#ff0000]root[/COLOR]       4096 Jan 16 20:10 testroot

File called 'testdoc.txt' in 'testroot' folder created with sudo....

-rw-r--r--  1 [COLOR=#ff0000]root[/COLOR]      [COLOR=#ff0000]root[/COLOR]         0 Jan 16 20:10 testdoc.txt

```


On the Ubuntu client, I run the rdiff-backup command with sudo....

```

[COLOR=#ff0000]sudo[/COLOR] rdiff-backup --force ssh://rembackup@192.168.178.15::/media/storage/testroot /media/backup/testroot

Upon completion, the file user and group is root...

-rw-r--r-- 1 [COLOR=#ff0000]root[/COLOR]      [COLOR=#ff0000]root[/COLOR]         0 Jan 16 20:10 testdoc.txt

```

And without sudo...

```

rdiff-backup --force ssh://rembackup@192.168.178.15::/media/storage/testroot /media/backup/testroot

Upon completion, the file user and group have been changed to the Ubuntu client user (ubclient)...

-rw-r--r-- 1 [COLOR=#ff0000]ubclient[/COLOR] [COLOR=#ff0000]ubclient[/COLOR]    0 Jan 16 20:10 testdoc.txt

```

From the results above, despite the user 'rembackup' having equivalent-root privaleges, the user and group are changed unless I run rdiff-backup as sudo.

Eventually, I want to create a backup script for rdiff-backup so I don't want to have to enter the rembackup' user  password due to using sudo.

How can I get rdiff-backup to work remotely so that the user/group/attributes etc are maintained, without having to use sudo with rdiff-backup which then asks for the 'rembackup' user password ?

---

### Post by TheFu on 2024-01-17
If the output from 'id' for your *root-equiv* user isn't uid(0), then you didn't set it up correctly.  Being a member of the sudo group, doesn't make a user root-equiv.

There's no way to maintain user/group/permissions without uid(0) running both rdiff-backup processes on both the client and server system. How you get that is up to you.

If you insist on using sudo, there are ways to allow specific commands to be run without a password prompt. This is an advanced capability and fully documented in the sudoers manpage.  I don't know if we are allowed to explain it here, since it sort violates the RootSudo (or is that SudoRoot?) stance in these forums.

I've been trying not to get myself into trouble with your last 5 rdiff-backup threads. I hope you can appreciate that.

---

### Post by freeflyjohn on 2024-01-18
Thanks TheFu

I have limited understanding of users and groups, I have only ever used the default users (i.e. root and the user created during the Ubuntu installation).

On the Ubuntu server, the id of root is....

```

uid=0(root) gid=0(root) groups=0(root)

```

The id of the new user I created on the server is...
```

uid=1001(rembackup) gid=1005(rembackup) groups=1005(rembackup),27(sudo)

```


So is it just the matter of changing the uid of the user rembackup to 0, whilst also leaving the uid of root as 0 ?

And do I also need to create a user on the Ubuntu client machine with a uid of 0, then run the rdiff-backup command with that new user ?

I don't care whether I use sudo, I just used that as an example because its the only method I know which will maintain user/group/attributes etc

I just want the simplest, safest method run rdiff-backup remotely so that it maintains the user/group/attributes etc, preferably without having to enter a password each time the command is called in a back up script.

I didn't realise that you could get into trouble and I am not interested in doing anything to seriously compromise my server, so apologies for that.  

If its not possible to run rdiff-backup remotely and maintain user/group/attributes then I will have to leave it and forget about offsite remote backups.

---

### Post by dragonfly41 on 2024-01-18
I have followed this (and earlier) discussion with interest since I am weighing/learning how to keep more than one remote node in sync with backups. But my ideas often go against the grain.
Understanding the rules of sudo in a distributed node environment is like trying to join the Magic Circle.
I have a germ of an idea to try which requires only rdiff-backup differences to be sent.

This does add an extra burden of Node A and Node B each having local backup devices or partitions.  But passwords usage can be automated, not requiring human intervention at remote Node B.

After thought: in fact I realise that -dry--run option might be used to extract differences thus removing the extra burden of local backup storage in Node A and Node B (although desirable).


[https://docs.nginx.com/nginx/admin-guide/high-availability/configuration-sharing/](https://docs.nginx.com/nginx/admin-guide/high-availability/configuration-sharing/)

[https://ubuntuforums.org/showthread.php?t=2444949](https://ubuntuforums.org/showthread.php?t=2444949)

---

### Post by TheFu on 2024-01-18
I use 2-stage backups for critical files.

For backups to work correctly, uid/gid have to be maintained.  The only way for that to happen when multiple users are involved (since Linux/Unix is multi-user from the ground up) is for the backup tool to run as root at some level. There are many different ways to accomplish that.  

If the backups are only for 1 user, not for the system, then you don't need to use sudo or root. The same user can be used, since it will be the owner of all the files anyway - or at least it should be.

"Pull" backups using rdiff-backup from all the clients on the network and some remote sites to a centralized backup server. This doesn't seem too complicated, but it is. "Push" backups are much easier for most people to understand, but they bring a liability - the client system will have some level of access to the backup storage and will be able to wipe it if any crypto-ware or other malware makes it onto the client system.  "Pull" backups don't require **any** access to the backup storage and by having versioned backups, if cryptoware his one of the client systems, we will see huge size changes in the backups AND perhaps run out of storage on the backup disk on the backup server.

Without versioned backups, even using "pull" backups, malware and crypto-ware can completely destroy the backups. Versioned backups are mandatory to protect against those attack vectors.

The backup storage on the backup server can only be accessed by root on the backup server. The clients shouldn't AND cannot have direct access to that storage. If that is possible it undermines the reason for backups to protect against malware.

Subtle malware can still happen on clients, so the backup admin needs to pay attention to changed data amounts, daily and strive to not miss malware installations before their versioned backups run out.  For example, if you have 30 days of backups, then finding the malware before 30 days of versioned backups run out is critical to have any chance of recovery.  Otherwise, all program and data files become suspect and cannot be trusted. Higher risk systems need more versions, which converts into more daily backups held for longer.  Thanks to the efficiency of rdiff-backup, there isn't THAT much difference most of the time between keeping 60 days and 120 days of versioned backup. This can be optimized further by only backing up files that are needed to restore the system to a recent state with a fresh OS install and all current versions of programs.

Each "pull" script has a different number of versions, based on the needs and risks of that remote system.  More and more, I'm keeping a full year of daily backups.

Now we have the **rdiff-backup** data for 1 - 50 other systems centralized. It is stored on a system on the backup network accessed over the backup LAN.  We do all segment our networks, right?  There's a public-facing LAN and a management-backup LAN, to make it a little harder for attackers to gain access to the backup storage.  

>  I have a germ of an idea to try which requires only rdiff-backup differences to be sent.

The next step is to get our backups off-site. I want my off-site backups to be in a different region of the world that won't be impacted by the same regional disaster that would hit me.  If your onsite and offsite backups are too close and both areas are hit with a tsunami, earthquake, hurricane, snow storm, nuclear attack (I've lived near nuclear targets all my life), or other region-wide disasters, then those backups are useless.  That should be clear.  So, my off-site backups are are about 7 hrs away by car.  A nerdy relative there and I swap differences using rsync nightly.  Because **rsync** is efficient at sending differences over encrypted channels, we use that tool. Additionally, we can limit the bandwidth used by rsync, so we don't flood the other person's internet.  Again, we use root-equiv accounts for this, since **rsync** transmissions need root to maintain users, groups, and ACLs.  However, we each limit the command that our individual root-equiv accounts can run, so prevent access to other stuff on the system and to prevent mistakes.

BTW, if you are using passwords still for security, you've already lost the security war.  Keys and certs are the way.  Even better is to have an external unlock FOB to allow access to the security key for keys and certs.  Most people will just setup password-less ssh keys to be used for very specific needs. Nobody talks about this, but everyone does it.  Just be certain that the ssh key used in this way is for a single purpose.  This can require lots of details to be correct to get it working.

Using sudo with ssh used to be harder pre-20.04 since Ubuntu didn't set the HOME like many other distros to the new userid.  Since 20.04, Ubuntu does set the HOME to the location of the elevated account, so setting up keys under the correct account, in the correct location, is much easier.  Alas, there are 15 other details that need to be handled and I forget a few each time even though I understand it. Different uses of these accounts means the details change slightly for what is good to have and what is needed for security and what is mandatory for the specific use to actually work.

Much of this stuff can only be learned through trial and error, so it becomes fixed in your mind, for your specific use.  Rather than asking questions, try it. See what works. Look for security issues in the implementation and decide for yourself if there are any and if they are things you can mitigate.  When your system gets crack, nobody here will help. It will be too late. Only YOU are responsible. Not us.

One last thing.  People seem to think that sudo only works for elevating to root privileges.  That's just 1 capability. There are many others and most of the useful capabilities aren't using the root account at all, but in allowing 1 account to run specific commands, with specific options, under another account which may or may not be root.

---

### Post by dragonfly41 on 2024-01-18
@TheFu
Thank you again for your much valued words of wisdom. I try to distill nuggets of knowledge from your frequent posts. So we use both rdiff-backup and rsync?
But your remote backup plan still requires  "a nerdy relative". What if there is no such clone? Remote scripts must be invoked.  A robot to be invoked?
[https://en.wikipedia.org/wiki/Klaatu_barada_nikto](https://en.wikipedia.org/wiki/Klaatu_barada_nikto)
I aim now to experiment by firing up a cluster of nodes using a PaaS provider to test the approaches.
One added dimension is that in addition to considering the risks of floods, fire and the seven plagues there is the mortality of the coordinator.  That is, I am thinking about a &#8220;dead man's handle&#8221; scenario if the coordinator is ill or worse the "show must go on".
What guidance do the remote users follow when the teacher goes under an avalanche?
This scenario is not talked about too much.  Do you hand over a prebuilt app to your legal executor or deputy?
Same thinking applies to multiple credit card subscriptions in play.

---

### Post by dragonfly41 on 2024-01-18
Duplicate post due to dodgy mouse. Actually the mouse is not dodgy since it works in other OS.
But I digress.

---

### Post by TheFu on 2024-01-18
> **dragonfly41 said:**
> @TheFu
Thank you again for your much valued words of wisdom. I try to distill nuggets of knowledge from your frequent posts. So we use both rdiff-backup and rsync?


Local backups are rdiff-backup.  Off-site backups are rsync of the rdiff-backup data.

> **dragonfly41 said:**
> 
But your remote backup plan still requires  "a nerdy relative". What if there is no such clone? Remote scripts must be invoked.  A robot to be invoked?
[https://en.wikipedia.org/wiki/Klaatu_barada_nikto](https://en.wikipedia.org/wiki/Klaatu_barada_nikto)

I don't do cloudy services, hence the use of a nerdy relative. 

If you do use cloudy services, be certain to encrypt everything before transmission. It is a lack of trust thing for me.  I don't trust them. Might be easier to use a backup tool based on Duplicity (Duplicati / Deja Dup), but nobody says there's a dirty secret with duplicity-based backups.  At least monthly, a full backup is required to be performed.  rdiff-backup uses reverse-differential backups, so the most recent backup looks like a mirror, with older versions being gzip'd diffs from the prior version, only if there are changes.

> **dragonfly41 said:**
> 
I aim now to experiment by firing up a cluster of nodes using a PaaS provider to test the approaches.


Or you could use a few virtual machines or even containers for simple tests.  The problem with using a container is that putting that much storage inside a container breaks some of the security aspects of containers.  Just use a VM, until you decide to use real hardware for your backup server.

> **dragonfly41 said:**
> 
One added dimension is that in addition to considering the risks of floods, fire and the seven plagues there is the mortality of the coordinator.  That is, I am thinking about a “dead man's handle” scenario if the coordinator is ill or worse the "show must go on".
What guidance do the remote users follow when the teacher goes under an avalanche?
This scenario is not talked about too much.  Do you hand over a prebuilt app to your legal executor or deputy?
Same thinking applies to multiple credit card subscriptions in play.

If you are planning to die in the next 2 yrs, I'd seek out another option. OTOH, I figure I have 10 - 40 more years.  Additionally, rdiff-backup make the most recent version a mirror, just like rsync, which almost any slightly technical person can understand and use.  Perhaps I'm lucky, but there are 3 nerdy relative in my generation who won't have any issue figuring out what to do with backups.  I suspect nobody will really care, since anything really important isn't on HDDs.  

Important things are in a safety deposit box and the will executor already has their signature on file with the bank and can walk into it today or when I die to access it.  Wills still need to be on paper here and notarized. A list of 10 accounts for insurance and financial stuff is all they really need, besides their name listed as executor for the estate.  

People think their computer files are really important to their heirs. Trust me. Nobody cares and nobody wants them.  Family photos are about all people might be interested in seeing and they only are interested in photos of family and family in places of interest.  They don't care about all those Christmas tree photos, unless their is a family member in the photo too AND they know that family member.

When my Dad died, I took all his photos and slides, scanned them all and created a DVD that I gave to all members of the family.  We did 1 slide show of the photos, which Dad had labeled.
Just forward 20 yrs and Mom died.  She had many more photos. I scanned all of them and created another DVD for the family.  Mom's death was carefully planned. She'd been giving away her most valuable items and conveying the story behind each item to the recipient.  During a visit where I was taking the 7+ ft tall Grandfather clock home, we sat down and looked around the house to get oral histories for everything she though valuable.  I have those recordings and made them available to the entire family.  Specific items were to go to specific people with the intention that they would be passed down based on birth placement for all future generations.  2 of those wishes have already failed.  The grandkids who are supposed to carry on the family line won't have children by choice.  I'm not complaining, but each generation has different life goals, so the assumption that the eldest son of the eldest son gets item Y and the eldest daughter of the eldest daughter gets X doesn't always work out.

Our family bible, which lists every birth and death going back 2 migrations has been handed to the oldest son.  Alas, the next generation doesn't speak/read the language used in that bible, so I don't expect those records to be maintained after my generation dies out.

How important are some old DVDs on a HDD now?  Let's put it into perspective.  There are a few movies that my parents enjoyed from the 1950s and 60s.  Very few of those are liked by me, so I didn't really care.  Ditto for music. Almost none of my father's music collection (reel-to-reel) did anyone actually appreciate. I know I didn't.  My kid doesn't care at all about any of my music collection.  Different times. Different tastes.

The executor of the estate will only need to have the death certificate to gain access to your financial accounts.  Almost everything else in your home will be considered "junk" by others.  Mom tried to give away her silver service and all the silver utensils.  Nobody in my family wanted it.  She couldn't believe it.  It must have been worth $10-20K and nobody wanted it.  I explained that to us, all that silver had bad memories of being forced to clean it. Hours of polishing.  It wasn't happy memories.  About a year ago, one of the grandkids asked about it and got it.  I think she's been selling it slowly on ebay.  I'm too close to it, but she was distant enough for it not to be personal. For her, it was just a financial thing.  At least someone in the family is getting something good from it.

Maybe my family is different. We've never been about filling our homes with "stuff".  I know I prefer to have memories and perhaps some photos to help remember those memories. Stuff is just clutter and even without trying to accumulate it, we all have more stuff than we need.  I do have a decent die-cast aircraft collection on display.  I also understand that the time, effort and money I put into it, won't be appreciated by anyone in my family. It will be boxed up and sold like it was used toys - probably for $0.10 on the dollar.  To be clear, those die-cast models aren't toys. 

What were we talking about?  Backups?

---

### Post by freeflyjohn on 2024-01-18
Thanks all for taking the time to comment

I am at a complete loss and don't know how to proceed, therefore I think I will just have to accept defeat and stick to onsite backups only.

Its very frustrating as I have spent a lot of time and effort to get this far and its all working apart from one last bit.... i.e. files/folders that give permission denied due to not being able to run as root.

Out of interest, is there a way I can display the user and group of all folders/files ?  Similar to using "ls -la" but to show ALL files (including sub folders) so that I can see what users and groups are being used for the files/folders on the HDD ?

If so, I could indentify which files would cause an issue and see if its possible to change the user and group of those files/folders, then I wouldn't need to run rdiff-backup with root privalages.

Or is there another tool I could use that would make all this easier (even if its a paid for tool) ?

---

### Post by TheFu on 2024-01-18
"Pull" backups are 100x harder than "push" backups.  Have you tried those?

> its all working apart from one last bit.
Actually, I'd say that nothing is working until the permission work as needed. Permissions, groups, owners are CENTRAL to Unix security. They aren't an add-on that can be tacked on after the fact. They are integral to the entire OS.

>  Similar to using "ls -la" ...

```
find / -ls
```
You'll need to run that as root or with sudo, since there are parts of the OS that normal userids cannot see. It won't show all the ACLs, BTW. That's part of the reason your "one last bit" isn't truly *one last bit* too.  However, every file and directory has a specific reason for having an owner, group, permissions and ACLs.  Screw with those only if you want to reinstall.  

We see this about once a year here - someone will get frustrated and change the owner of the entire OS, or just some important parts of the directory tree, to their personal userid.  The system never boots again.

As for other tools, there are a bunch, but each has issues.  rdiff-backup has issues too, but not related to owners, groups and permissions. It actually handles them cleaner and better than nearly any other backup tool I've tried, including rsync.  rsync has flaws in that regard if it is used for versioned backups. Only the most recent owner, group and permissions are retained with rsync. They aren't versioned.  rdiff-backup applies versioning not just to the file contents, but to the owner, group, permissions, ACLs, and xattrs.  People don't appreciate that until they are screwed by having the wrong value for a file and the restore process doesn't result in a working system.

For rdiff-backup, 
"Pull" backups is an advanced skill.
"Push" backups are intermediate level.
Local backups for important parts of the system are pretty simple and even easy if only a user's HOME directory are backed up.

I say this all the time, Unix skills build on prior, easier skills.  Jumping to Advanced skills isn't really possible without learning the beginner, intermediate skills first.

"Simple questions" often don't have simple answers.  Often, the only good answer is "it depends."

---

### Post by dragonfly41 on 2024-01-18
[COLOR=#000000]> Or is there another tool I could use that would make all this easier (even if its a paid for tool) ?
[/COLOR]Based on reading the valued advice from TheFu my own thinking (which I admit changes daily) is to retain local backups in Nodes A and B and push the (smaller) diffs streams (per backup session)  into a zerotrust vault tresorit.com as an encrypted pushdown stack.  Assign url and password to your remote site Node B so that the rdiffs can be pulled.  This way the Node A and Node B need not be active at the same time and are asynchronous. Node B can pull the ridiffs from the encrypted stack and apply to the Node B backup using cron or  automation script.

Remember these are rough thoughts in my mind, not yet proven.  But the penny dropped when I understood from TheFu how rdiff-backup and rsync can be used in different context.

You have an easier task of orchestrating two nodes (100 miles apart). But tresorit vault is in Switzerland or Germany.

And remember that if you lose the tresorit.com prime password you are totally stuffed since it cannot be recovered or the content. You must be prepared to keep the account paid up. So keep that password in a sealed envelope somewhere safe for others to read if you fall under a bus.
    
This is only one developing thought I have. I do like the idea by TheFu to test this cluster approach in a testbed of virtual machines on you primary Node A or other test platform. You can dispense with tresorit.com idea and rsync diffs directly between Node A and Node B.  Or you might have an intermediary container to pull through rdiffs. That might be worth trying. The intermediary container might be launched at backup time to reduce costs.  The pulled rdiffs can be applied via running scripts to Node B to update the backup.

---

