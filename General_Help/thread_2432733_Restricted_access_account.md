---
title: "Restricted access account"
date: 2019-12-07
forum: General Help
---

### Post by mangonels on 2019-12-07
Hello, can someone help me with configuring a restricted access account on Ubuntu 18.04?

Requirement: Remote sftp access is needed through an Ubuntu user ONLY for a specific directory, contents, and subfolders, in an Ubuntu 18.04 system.
The user shouldn't be capable of executing any commands (for example by logging into the OS through ssh)... Files should simply be modifiable and transfered to and from a specific directory, subdirectories, and file contents (no parent directories).

Basically a user with access to the account should not be capable of doing anything else on the system except transfering and editing/overwriting in specified directory and subcontents.

Concern: That the produced user may have access to anything else except the required file operations, in the specified directory scope.
In order to do this, I imagine I must modify a user's permissions. But I know next to nothing about permissions for users.
Any guidance and ideas for achieving this is very appreciated. Thank you for your time. Any further information required for such purpose will be provided and added to this thread's description.

---

### Post by TheFu on 2019-12-07
Don't use plain FTP.  Use sftp.  Plain FTP should have died out by 2002.  There are so many reasons for this.  

Every networked OS has great sftp clients.  Use ssh-keys if you can for authentication, they are 1,000,000x more secure than passwords.  Every Linux file manager supports drag-n-drop sftp connections.  Just use sftp:// in the URL. This assumes the ssh client is installed.

The commands for sftp match exactly the commands for plain FTP, so if there is another program making the calls, you just need to link or alias sftp into ftp.

Google found this:
[https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-16-04)
[https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-18-04)

File permissions are the center of all Unix security.  You'll need to learn those, ASAP!  Web search of "*unix permissions*" will find a number of tutorials for file & directory permissions across all Unix-like OSes.  Every popular OS in the world uses this model except 1.

To setup ssh-keys between 2 Unix computers is just 2 commands total, run on the client:
```
ssh-keygen -t ed25519
ssh-copy-id -i ~/.ssh/id_ed25519.pub userid@remote
```
swap out the userid@remote for your username on the server and "remote" for either the DNS name or IP address of the server.  Nobody is hacking ed25519 today that has been reported anywhere.  These keys are used for every ssh, scp, sftp, rsync, sshfs, rdiff-backup, and 50 other ssh-enabled tools.  
To reuse the same key with a different server, run the ssh-copy-id command at the new server.

---

### Post by mangonels on 2019-12-07
Hey, thanks for the answer, but I'm already using sftp for all file transfers. The fact I said "ftp" was just as a generic file transfering term, but I'll change it in order to avoid any confusion.

I only need 1 account with such a set of permissions, and I highly doubt I'll have to get into permissions again, so if I could avoid having to do a master on them it would be a real time saver.
Unless you can guarantee me I can learn this in just a few hours, in which case I'd be more than happy to learn something new. Something tells me this may not be the case, and I may have to spend days.

Also, if you guys insist on me watching some sort of information source, I might as well ask here too, I wouldn't want to commit any mistakes by following any wrong information.

---

### Post by TheFu on 2019-12-07
I updated my answer above.

FTP isn't a generic term.  Glad I didn't attempt to answer that question, since it is completely different than the sftp solution. Completely different.

If you don't learn most of the permissions, then it will be easy to miss mistakes or create mistakes in how-to guides for any Unix-like OS.  That will cost you hours, days, weeks, months of frustration.   I'm actually trying to save you time with the suggestion to work through a permissions tutorial.  Watching something is not what I suggested.  If you don't work through the tutorial, using 3 userids, 2 groups, mix and match which group each userid is in, and do it in 3 different terminals, you won't get the learning necessary.

Learning Unix file & directly permissions is 45 minutes to get 90% of it. That assumes:
* 15 min reading a tutorial and working through the examples.
* 30 min more with 3 accounts, 2 groups, in 3 terminals trying every possible permission from 0-7 for ugo, then seeing with each different setting, which accounts have what sort of access and which do not.  

You will not MASTER permissions in this time, but you will understand about 80%, which should be enough for most people.

---

### Post by mangonels on 2019-12-08
Thank you for your detailed answer.

It seems I was already familiar with how the file and directory permissions worked (allthough I just complemented my knowledge with some additional info I found).

But I have some questions:
Would it cause any issue to just deny permissions for everyone except owner, for all root folders? Would it work for all subfolders and files (except an allowed subfile)? What about newly generated files and folders, would those be affected by a parent folder too?

But just adapting folder and file permissions won't be enough. I'll also need to block the execution of any command for the specific user. (And possibly something else? Since all I want is for files to be moved and edited in directory and all certain subdirectories)

---

### Post by TheFu on 2019-12-08
Those are good things to test on a play system, in a temp directory.  Nothing teaches more or better than screwing things up.

Did you:
> * 30 min more with 3 accounts, 2 groups, in 3 terminals trying every possible permission from 0-7 for ugo, then seeing with each different setting, which accounts have what sort of access and which do not.
?

If you had, you'd know the answers.

As for how to setup sftp - the links provided explain that.  If only an sftp login is provided to a userid, I don't see how they can run any commands, do you?

---

### Post by mangonels on 2019-12-08
I'll give you the answer. Changing root folder permissions will deny me access with all accounts on both ftp and ssh. It's actually the second time I've fallen into this, so I doubt I'll learn anything from it.

The lesson is that I should have invested more time into investigating this propperly. Probably by setting up a local vm. And I will, since apparently you have shown me that there is no direct or simple answer to my very singular and specific need, so I'll have to do the master on it.

I'll have to use ovh's rescue to fix this mess.

I am not blaming anybody but myself, but I really do hope there isn't a simple answer to my questions.

---

### Post by TheFu on 2019-12-09
The steps to setup a restricted sftp account were provided.
[https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-enable-sftp-without-shell-access-on-ubuntu-18-04)
That alone should have been followed to answer the specific question asked - how to restrict an account to sftp-only.  

If you actually changed permissions to the OS, and not just in a temporary play area under /tmp/, I hope you kept very careful notes about the prior permissions, owner, group, and any ACLs first.  If you used **chmod -R** or **chown -R** - just reinstall now or restore that backup.  There is no way to recover from those commands.


> I really do hope there isn't a simple answer to my questions. 
Is that what you really meant to write?

---

### Post by mangonels on 2019-12-09
Yes, I meant to write that, of course. If there's a simpler answer to creating a limited access account, which is pretty much what I'm requesting, then you don't really need to give me so much information, rather more precise steps or ideas.

I must say I have various problems. Firstly, I'm starting to be unsure of the fact that I'm actually using sftp, all I do is select sftp from filezilla, but I've been doing this for so long that I started to accept it as functional and correct.
However, the key part really left me confused, I probably should have mentioned that. Also, various people connect to the system using filezilla, and you seemed to mention connections between unix systems using sftp. I use windows to connect, and others may probably connect the same way...
And I certainly didn't understand how sftp would restrict access to an account only through sftp. This really still confuses me.

On the other hand, I thought modifying file permissions would be harmless (or reversible at very least). I checked some documentation on it, and my first thought was I don't have a test ubuntu machine for this, all I have is my main ovh kimsufi. Aparently that's when my very big mistakes started, In the hopes of getting this done fast, I tried to modify the entirety of the system's file permissions by starting with the root folders. I did ask beforehand, but didn't interpret the fact that it would probably be better to test that specifically as a "don't do it" if that is how it was meant.

In conclusion, I'm 100 steps backwards from where I started. My 0S won't boot, and I'm going to have to reinstall it, not only that but somehow extract some files with ssh, and reconfigure everything from scratch, so talking about this won't do any good, at least right now...
When I get back to where I was I may start from the begining with following your instructions if it's not long from now, I asume you won't be answering for ever but I really appreciate the help until now.

---

### Post by TheFu on 2019-12-09
Since I've already failed to communicate effectively, causing all sorts of problems for you, I'm afraid to attempt any more help.  Your call, but I usually move on when a thread doesn't have any action for 5+ days.

And to be clear, I didn't create those instructions in the link, but I think they are accurate. I wouldn't want to take credit for hard work by someone else.  If I needed to setup sftp restrictions for a user, I'd follow those same instructions.

---

