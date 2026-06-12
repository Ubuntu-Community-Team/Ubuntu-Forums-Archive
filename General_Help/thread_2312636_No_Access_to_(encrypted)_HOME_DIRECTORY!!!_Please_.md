---
title: "No Access to (encrypted) HOME DIRECTORY!!! Please HELP!!!"
date: 2016-02-06
forum: General Help
---

### Post by Alcidious on 2016-02-06
Hi all,

I made the transition to Linux about 5 or 6 years ago, and while I am becoming more knowledgeable and confident, I still occasionally make rookie mistakes... for instance, I didn't make a backup because of a lack of funds and memory. Although I knew it needed to happen, I put it off too long.

One day, I could no longer log in to my Ubuntu Home Directory from the main log in splash screen after GRUB. I was running Ubuntu 14.04 LTS, 32-bit, on a SAMSUNG laptop (not sure of the model number off the top of my head) that was a gift in 2012. To make a bad situation worse, during the most recent installation, I selected "encrypt my Home Directory" without understanding what all that entailed; now, I cannot find the correct keys to recover my encrypted passphrase when running Ubuntu through a Live CD terminal session.

I have tried everything ... I tried to recover the passphrase, I tried to hack in (although I don't know enough about cracking to actually have done that well); one time I got partial access, although I don't know how that happened (I swear that I used my regular passphrase for everything, because I didn't understand what I was doing), and I did back up a limited number of files to my External HDD. Most recently, I used the DD command to back up the partition via an image to my External HDD. Then I attempted to upgrade to Ubuntu 15.10 ... I thought that almost worked, I was attempting to keep the file system and partitions, because I really don't want to lose a year of my life (in data). But, alas, I still cannot log in through the splash screen.

I am really at my last legs ... I am about to just say goodbye.  PLEASE, if anyone can help me fix this issue, or even just back up my files where I can actually read them, I will have learned my lesson about encrypted home folders, regular backups, and thinking before I act.

Sorry for the lengthy, emotional, description. I am happy to provide any details necessary.

---

### Post by Alcidious on 2016-02-06
So, an update:

As I said, I've upgraded to Ubuntu 15.10, yet I still cannot login to the HOME through the GUI (the guest account works, however). I searched to see if there was anyway to access my home folder through a terminal, and then attempted to access it through a Virtual Console. Once I entered my password, I was allowed root access.

I then mounted my external hard drive, and attempted to use:

rsync -au /home/me /mnt/myExHDD

The rrresoponse was that "/home/me/.conf/dconf" failed: Permission Denied(13)"

rsync is now running, and looks like some, but not all, files were backed up. What does this mean? I feel like there is a way to get the files I really care about (letters, things I wrote, pictures, that kind of thing. I don't care about anything but my personal memories ... and I'm a little upset and about to give up. Any help is super appreciated!

---

### Post by dragonfly41 on 2016-02-06
I don't encrypt my home folder.
But I suggest that you search for users who have been in same position.
Here is just one thread I found ..

[http://ubuntuforums.org/showthread.php?t=2244896](http://ubuntuforums.org/showthread.php?t=2244896)

See advice in post #4

Also note that passwords are case sensitive so if your passphrase does not work there is a possibility that you had keyboard Caps Lock on inadvertently when typing one or more characters.

You wrote "one time I got partial access, although I don't know how that happened (I swear that I used my regular passphrase for everything)".

I don't know what you meant by "partial access" since either the passphrase is correct or it fails.

[COLOR=#b22222][later edit]
I remembered this recent thread where I posted a few links describing brute force attack on forgotten passphrase. 

[http://ubuntuforums.org/showthread.php?t=2308251&highlight=bruteforce](http://ubuntuforums.org/showthread.php?t=2308251&highlight=bruteforce)

If you use a regular passphrase I would try variants on each character in your regular passphrase.
Or perhaps leaving out characters or double typing characters or changing characters upper/lower case.

Just one mistyped character can prevent access.  

But the puzzling part is your reference to gaining "partial access"
and quote: "... I did back up a limited number of files to my External HDD".[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by dragonfly41 on 2016-02-06
Reading again the clues in your two posts above I'm getting the impression that you may have a problem which is not a wrong passphrase.

> The response was that "/home/me/.conf/dconf" failed: Permission Denied(13)"

I read in one thread that a user  experienced ownership  of /home/user/.config/dconf/user file changing to root:root during an upgrade leading to the error message you report.

I'm assuming that you mistyped "/home/me/.conf/" .. it should be "/home/me/.config/"

Can you check ownership (it should be user:user i.e. me:me)?

Have you tried grsync (GUI for rsync) and tried its "dry run" option?

---

### Post by Alcidious on 2016-02-19
Sorry for the much delayed response ... life is crazy with work and new issues with my PC (not the laptop concerned here). [-o<

I actually had tried the typing of every single combination and variant you mentioned. In fact, the other night, when I was setting up the encrypted home folder of my new Kubuntu Desktop (why do I keep doing this to myself?), by typing in my general Admin PW, I did obtain a passkey. That is the exact same thing that happened before, when I got "partial and limited access to files." So, I must have the ability to recover the encrypted passphrase somehow ..... and I am wondering if the issue keeping me from logging in to my home folder (gui) is the same that is preventing me from accessing the recovered ecrypt passphrase?

Additionally, those files that were "partially backed-up" --- I am thinking they must either be an entire backup, or just the backup the of the "hidden encrypted directory"? I am not sure the difference, b/c in another instance when playing around, I did manage to get some files that were non-encrypted and that i could look at. The difference in how I am viewing these files is because of the different directions I have followed .... (I will try to find the links), but in one instance I created a folder within the live session to back up to (that was the limited number of unencrypted files). The encrypted files from my "Partial access" backup are the files on my exHDD.

I would be very interested in what you think that means?? I will again be trying to fix all my issues this weekend, but fear it may take longer than I need it to. 

Would it be easiest to figure out the bug/issue plaguing my installation than trying to workaround a way to recover all the files and do a fresh install??

Thanks!

---

### Post by Alcidious on 2016-02-19
@ dragonfly41, I am going to attempt, this evening, redoing the option of > [COLOR=#000000] "/home/me/.config/" [/COLOR]

[COLOR=#000000]AND >  Can you check ownership (it should be user:user i.e. me:me)?[/COLOR]

[COLOR=#000000]Have you tried grsync (GUI for rsync) and tried its "dry run" option?[/COLOR]

---

