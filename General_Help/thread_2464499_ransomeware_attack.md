---
title: "ransomeware attack"
date: 2021-07-03
forum: General Help
---

### Post by Old Jimma on 2021-07-03
Hello Forums:

Ransomware attacks are becomeing common. 

I use ubuntu on all of my computers at home.

What should I do to prepare and prevent a ransomware attack?

Thank you,
Old Jimma

---

### Post by TheFu on 2021-07-03
[LIST]
[*]Have a secure backup server. An old system or a raspberry-pi v4 are fine. Just needs to have fast enough networking (GigE) and sufficient storage connected.
[*]Create daily backups.
[*]Versioned - enough versions so you'll recognize corrupted files BEFORE the oldest versioned backup expires,
[*]automatic - manual backups just don't happen. Humans get lazy, forget.
[*]"Pulled" by the server, never pushed by the client.
[*]The client(s) systems should have no direct access to the backup storage. Definitely do not use shared storage or network storage.
[*]Backups need to be verified as restore-able. We've all heard stories about people doing backups for years that were corrupted because nobody actually tested the restore.
[/LIST]

If you want to be more secure, have the backup server be the only system with remote access (use the sshd_config to allow only specific IPs), and allowed only to run the few backup commands like creating snapshots, mounting the snapshot read-only, running the remote backup tool for the "pull", and cleaning up the mount/snapshot post-backup.  This should all be authenticated using ssh-keys.  This setup is how github works to allow git access to hundreds of thousands of people while limiting all other access.

As for prevention, that's mainly 
[LIST]
[*]being a smart human and doing all the normal stuff  in the most dangerous programs (email and browsers).  
[*]Run those programs under constrained environments.
[*]Stay on updated, patched, supported, OSes running updated, patched, supported programs.
[*]Don't allow javascript from most locations.
[*]Use network blocking to prevent the bad parts of the internet from having access to any of your high-risk systems (any desktop with a browser is high-risk). 
[*]Don't open unexpected attachments. 
[*]Don't click on unexpected links.  
[*]There are lots of "How to be safe online" lists.  [https://krebsonsecurity.com/2011/05/krebss-3-basic-rules-for-online-safety/](https://krebsonsecurity.com/2011/05/krebss-3-basic-rules-for-online-safety/)
[*]Do what the UbuntuForums "Security" Sticky threads suggest.

[*]And have daily, automatic, versioned, "pulled", backups that are validated.
[/LIST]

---

### Post by Old Jimma on 2021-07-03
Thanks, Fu.

I've an old huge desktop that neary went into the recyling bin yesterday. 

Now I know what it is for!

Many thanks!!!!

Old Jimma

---

### Post by Old Jimma on 2021-07-03
Hi Fu:

I studied your reply and have a further question.

In "pulling" backups, do I set up an nfs network that allowss the "backup computer" to read and pull data?

Is that all there is to it?

Thanks,
Old

---

### Post by TheFu on 2021-07-03
> **Old Jimma said:**
> Hi Fu:

I studied your reply and have a further question.

In "pulling" backups, do I set up an nfs network that allowss the "backup computer" to read and pull data?

Is that all there is to it?

Thanks,
Old

NO!!! Never use NFS or CIFS or SAMBA or any storage sharing method for backups!   Use a client/server backup tool that requires strong, key-based, authentication from the server TO the client.  There are many tools with that capability.

---

### Post by ActionParsnip on 2021-07-03
Offline backups of anything important to you. The OS can be reinstalled then your data restored

---

### Post by HermanAB on 2021-07-05
Ransomeware is mostly a Windows problem.  You are already using Linux, so make a backup of your data once in a while on a USB widget, chuck it in a drawer where no hacker can find it, then relax and enjoy your reasonably secure system.

---

### Post by Old Jimma on 2021-07-05
Thanks, HermanAB!!!

---

### Post by Old Jimma on 2021-07-07
HI TheFu:

I've studied your reply, and like it. I want to discuss it with you.

I like the idea of a separate machine doing backups and providing security for my stuff.

Also, I like the idea of the process doing it all by itself, without me arround to tend the process, screw it up, or forget all about it if I do it myself. 

However, it will probably be a long road and steep learning curve.... but I'd like another project and this one has obvious benefits.

So, I've got a few quesitons for you:

1. hardware: I sent my old computer to the city dump. Also, I loaded dacula on my pi 3b. It choked.  I'm thining about a used Lenovo desktop with an i7and 16GB ram that boots from an SSD and has 2ndary storage on a 14TB mechanical hard drive. 

2. software: dacula (because my web searches rate it highest).

3. connectivity: on my home network

Hope would might comment on whether those are good starting points.

I'm sort of concerned that the machine I'll choose will be connected to the internet because it is on my home network. I wondered if this is a fatal flaw. I'm very interested in your comment about that.

Thanks for pointing me in a good direction.

Old and Aging Even Further Jimma From The Old Country

---

### Post by ActionParsnip on 2021-07-07
Dacula? ...... do you mean Bacula?

---

### Post by rsteinmetz70112 on 2021-07-07
Tagging on to this thread about Ransomware on Linux.

Since all it would take to mount a ransomware attack on a Linux server is administrator access and some software has anyone ever documented such an attack? 
Access to a Windows client would allow any shared files to be encrypted. That seems the most common method.

---

### Post by TheFu on 2021-07-07
haven't been allowed to reply.  Forum issue.

---

### Post by TheFu on 2021-07-07
Haven't been allowed to reply.  Forum issue.  Seems related to using certain tags in replies.

---

### Post by TheFu on 2021-07-07
Haven't been allowed to reply.  Forum issue.  Seems related to using certain tags in replies.

> Forbidden

You don't have permission to access this resource.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443

Also ... editing a post creates a new reply.

---

### Post by scorp123 on 2021-07-07
> **rsteinmetz70112 said:**
> Since all it would take to mount a ransomware attack on a Linux server is administrator access and some software has anyone ever documented such an attack? 

Qnap devices, which are essentially Linux-based storage appliances, got hit time and time again by ransomware because e.g. people opened up TCP/IP ports towards the Internet without really understanding what they were doing ... "Yaaay, Cloud functions ... I can administrate my Qnap storage over the Internet with my mobile phone and listen to my music collection stored back home while I'm sitting on the train ... "  ](*,)

[https://www.qnap.com/static/landing/2021/qlocker/response/en-us/]("https://www.qnap.com/static/landing/2021/qlocker/response/en-us/")

[https://www.qnap.com/en/security-news/2021/response-to-qlocker-ransomware-attacks-take-actions-to-secure-qnap-nas]("https://www.qnap.com/en/security-news/2021/response-to-qlocker-ransomware-attacks-take-actions-to-secure-qnap-nas")

There are also several videos from frustrated users who got hit by that ransomware e.g. on YouTube. Because of excessive use of inappropriate vocabulary in those videos I shall not post links to those, but I am sure you could find them yourself if you wanted to.

All in all:  Just because your OS happens to be Linux-based doesn't mean you're automagically "safe" from such attacks. If you do something not so smart like opening up badly secured and/or insecure network services that are running on your Linux box via port-forwarding to the Internet then you still might get hit by something like this.

---

### Post by mastablasta on 2021-07-08
UrBackup is another option for pull.

Areca is push service (so theclient pushes the data). 

turn off internet access or use tools to harden and block access to unwanted parties.

---

### Post by Old Jimma on 2021-07-21
Hi TheFu:

I've got a rpi 4b now and 10GB of HD storage.

Should I use Bacula described at [https://serverspace.io/support/help/backup-ubuntu-server-20-04-with-bacula/]("https://serverspace.io/support/help/backup-ubuntu-server-20-04-with-bacula/") to do the backups? 

Old

---

### Post by TheFu on 2021-07-21
I've never used Bacula for a number of reasons. Mainly the way the backups are stored.

---

### Post by Old Jimma on 2021-07-21
Hi TheFu,

What software would you recommend for pulling backups from my laptop the the raspberry pi 4b that I'll use as a secure backup server?

Thanks,
Old

ps. Saw one of your comments in another thread. All members of my family had their data taken in the 2015 OPM data breach, also. When that happens to you, the need for privacy and security has special urgency. It's among the reasons for the project we are talking about now.

---

### Post by TheFu on 2021-07-21
I use **rdiff-backup** with LVM snapshots. That selection was made after testing many other options years ago.  I can see it has been used here since at least 2014.  
```
drwxr-xr-x  8 root root  4096 Apr 10  2014 rorlap/
```

I moved from using **rsync** with hardlinks after getting burned with some undesirable limitations of that technique where the backup sets lose the owner, group, permissions, ACLs and xattrs if those change. Only the latest metadata is retained. Boooo.  Backups that don't capture file metadata are a failure.  The actual data is only 50% of what we need.

There are lots of backup tools.  The one I chose isn't the best for every situation.  Do some testing your self with 3-5 different tools. Do some restores. See which work for the 3 types of restores we all need.  Check the performance for initial backups and for the versions.  And be certain to backup /etc/ in your testing, so you can easily validate that different userids are retained in the method picked.  Any backup that doesn't include at least 15-25 files from /etc/ is a failure in my book.  I grab the entire directory, though I only need 15-25 files which are specific to the system. Many files are just for reference later and won't actually be restored.

Are you planning to encrypt the storage under the backup location or will you be trusting the backup tool to encrypt for you?

---

### Post by Old Jimma on 2021-07-21
Hi TheFU:

I had not thought about encryption.

I can see from what you've written that perhaps the best thing for me is to try a few things to see what works for me. 

I thought Timeshift would be a good solution, but it wiped out my home directory. Then, ignoring my advice, a friend tried Timeshift, and it wiped out his home directory.

Malware? Geeze!

I think that in all my testing one main thing is to have a back or copy elsewhere if things really go wrong.

Getting Older

---

### Post by rbmorse on 2021-07-21
*** withdrawn ***

---

### Post by TheFu on 2021-07-21
Lots of people seem to love Timeshift, so there is probably something that you've missed.  Timeshift appears to work in very different modes depending on the underlying file system, so perhaps it isn't a great solution for everyone or for system-level backups?  IDK. Doesn't timeshift prefer btrfs?

The way I see it, if a backup solution recommends that some other backup tool be used for the system backups, then why use 2 different tools when there are lots of 1 tool, full solution, answers available?

I'm probably oversimplifying.  No tool is perfect and people tend to like what they get working without too much trouble.  In my testing, I got most of the backup tools working, but was disappointed with other aspects. Some were terribly slow, not just the first run, but the 2nd - 10th runs too.

rdiff-backup isn't perfect either. Encryption is outside the tool, which is a negative for kitchen-sink loving tool people.  I prefer to control the encryption used,  I WANT to know the details so I don't have to trust a single team who probably isn't expert at encryption.  OTOH, if I were pushing backups to storage that I didn't fully control - like Glacier or Box or some other cloudy service, then I'd probably want encryption in the backup tool.  I don't do that.  I have trust issues.

Between 20.04 and prior releases, the version of python changed from python2 to python3.  While the rdiff-backup code didn't change much and the backup storage areas are 100% binary compatible between the two python versions, the client/server architecture of rdiff-backup and python's serialization code vastly changed between python2 and 3.  They don't work together at all.  So, if you have all older systems, great.  If you have all newer systems (20.04+), great.  If you have a mix of systems - well --- er ... that's a problem.  I ported the older python2 stuff and rdiff-backup to 20.04 along with the required dependencies.  My 20.04 backup clients all run my rdiff-backup code.  When over 50% of my system are on 20.04 or newer releases, then I'll move the backup server to 20.04 and switch to the new python3 version.  
To support the older python2 versions, I may need to create a linux container with access to the storage for those older systems.
I suppose I could have created a linux container to support python3 for the newer systems. Hummmmm.

Maybe check out Borg Backup too?

Lots of options.  We like options, right?  ;)

---

### Post by Old Jimma on 2021-07-21
Yeah. I like  opinions. It helps people think. 

I'm gonna try a few things and see how they work out. I'll have another look at Timeshift. It is definately EASY.

Thanks for your thoughts. It'll be a fun project.

Old

---

### Post by TheFu on 2021-07-21
Just out: [https://www.howtoforge.com/how-to-backup-and-restore-files-using-deja-dup-in-linux/](https://www.howtoforge.com/how-to-backup-and-restore-files-using-deja-dup-in-linux/)
I didn't read it.

**Deja Dup** checks all the boxes for ideal backups, including encryption, except it isn't "pulled" and access to the most recent backups requires using Deja Dup to access.  Deja Dup is in the same family as **duplicity** and **duplicati** backup tools.

Probably worth searching for Deja Dup failures before deciding.  There seem to be a number of those.  No backup solution should be trusted until after the 3 types of restores have been fully tested. Don't believe what others claim online. Test the restores yourself BEFORE you need them.

---

### Post by Old Jimma on 2021-07-22
Hi The Fu:

Tx again for your advice. Completely agree with not taking anybody's word for it and verifying that restoring backups correctly is the only acid test for the adequacy of backup system.

Also, seem like everything on a backup computer should be encrypted.

In fact, I'm thinking about reinstalling 20.04 on my main computer ... with encryption. Not having it encrypted is where my headaches start, anyway.

However, how would I back up an encrypted system?

Old

---

### Post by Old Jimma on 2021-07-22
Here is ancient advice on how to backup an encrypted system at: [https://askubuntu.com/questions/115566/how-to-backup-restore-full-disk-encryption](https://askubuntu.com/questions/115566/how-to-backup-restore-full-disk-encryption)

plz see my reply below...

---

### Post by TheFu on 2021-07-22
LUKS encryption only matters when the system is powered off.  When powered on, with the LUKS container "open" there is no encryption, so it is just like any other storage for backup ... and attacks.

Encryption is about shipping a HDD in for warranty support or selling it to someone else used or if someone steals it, provided the system is completely shut down.  It keeps those other people out of the data.  When powered or in standby mode, encryption doesn't matter.

---

### Post by Old Jimma on 2021-07-22
WOW!  

That's pretty informative.  

For starters, I think I'll reinstall 20.04 with encryption, and then use crontab to schedule shutdowns each day.

Next, I'll use 7pzip to encrypt and zip files that I want to "totally: protect while the computer is on... and ship that data off to a server in Switzerland. 

Then, I'll work on the backup plan for to a secure server, and put a copy of my system in a safe deposit box once a month, rotating several cheap HDs to cover that process for a very long time.

The Cybersecurity and Infastructure Security Agency (CISA) has published an important article that provides me more to think about: [https://us-cert.cisa.gov/ncas/tips/ST19-001](https://us-cert.cisa.gov/ncas/tips/ST19-001)

Old

---

### Post by dragonfly41 on 2021-07-22
[COLOR=#000000]"and ship that data off to a server in Switzerland."

Tresorit? .. now, apparently, part of Swiss Post.
[/COLOR]

---

### Post by TheFu on 2021-07-22
If you already visit your safe deposit box monthly and the contents of the disk are encrypted using 2FA, then there is next to zero chance anyone would be able to crack it.  

Putting the weekly rotated encrypted HDD in a locked desk drawer or file cabinet at work is what I did. The data was secure. The HDD could walk off, but never did.

---

### Post by Old Jimma on 2021-07-22
Nope not Tresorit. Tresorit has servers in Hungary and they've signed the treaty with the US to allow access to data on serviers within Hungary.

---

### Post by Old Jimma on 2021-07-22
Maybe I'll do that, TheFu.

It is easy.

Pretty sure I'm gonna encrypt my computer, anyway. I won't have to hide it under the couch when I'm out walking the dog.

---

