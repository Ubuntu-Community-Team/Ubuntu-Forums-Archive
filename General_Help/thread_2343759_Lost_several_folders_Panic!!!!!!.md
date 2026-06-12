---
title: "Lost several folders Panic!!!!!!"
date: 2016-11-18
forum: General Help
---

### Post by Sammy_boy on 2016-11-18
I've lost several folders in my home drive, I've searched the machine and cannot find them. Can I recover this data? Or am I screwed?!

Yes I know I should have backed up more often, but been working on a project non stop for several weeks and it slipped my mind. Started machine up last night and it looked like Unity had failed. Stupidly tried to fix it and now several folders (not all, but several) on my home drive are gone. Is there ANY way to recover this data?! 


Really bloody panicking any help would be appreciated!!!

---

### Post by howefield on 2016-11-19
Perhaps knowing what you did to fix the issue might help others to help you ?

---

### Post by Sammy_boy on 2016-11-19
Hi Howefiled,

I'' try and give as detailed account as I can. I started up my machine and the side bar and terminal was gone. I didn't notice anything missing at that point. I attempted to fix it. For example

sudo apt-get update
sudo apt-get update
[COLOR=#111111][FONT=Ubuntu]I've also tried[/FONT][/COLOR]
sudo service lightdm restart
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop [COLOR=#111111][FONT=Consolas]sudo apt-get install unity

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I've also tried[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]sudo apt-get install compizconfig-settings-manager[/FONT][/COLOR]

I belied that it was something trivia and stupidly did not make a backup. I followed a few bits on-line that suggested that it may be my /config

I tried to reset my unity using 

[COLOR=#111111][FONT=Consolas]rm -f ~/.conf/dconf/user; unity

[/FONT][/COLOR][FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]Though I ,may have accidentally hit

[/COLOR][/FONT][COLOR=#111111][FONT=Consolas]rm -f /.conf/dconf/user; unity
[/FONT][/COLOR]
[FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]and attempted to reinstall it. Nothing worked, I kept looking and someone else noted that its best just to reinstall. At that point I though, OK I'll transfer everything across to my other machine and do a quick reinstall. I moved everything over (haven't done the reinstall) but noticed that some files were missing in my home directory, checked the machine and they are not there! Also other folders are gone like Pictures and My Documents instead I get the error message [/COLOR][/FONT][COLOR=#111111][FONT=Ubuntu]"Underhanded error message: Error when getting information for file '/home//Pictures': no such file or directory" - can this be recovered?!  Desktop is still there. 

I've tried to use find -name <Project>, but the computer can't find anything!? I've also checked trash ect. Is it gone? What I don't understand is why 7/10 of the folders in home are still there and working fine. Are the other files gone for good? I've shut down the computer as I'm worried that if the data is still there I'm overriding it by using it.

 Is there anything I can do? 



[/FONT][/COLOR]

---

### Post by howefield on 2016-11-19
Can we get a look at what is in the user-dirs.dirs file, just as an easy starter for 10 ?

```
cat ~/.config/user-dirs.dirs
```

---

### Post by HermanAB on 2016-11-19
First do a recursive search over the home dir or over the whole disk for a known file.  You may have moved one directory into another.

find . -name whatever.doc

---

### Post by Sammy_boy on 2016-11-19
Hi HermannAB,

[COLOR=#000000]many thanks for your response. I tried that and unfortunately nothing.

A quick question for both of you before I try [/COLOR][COLOR=#000000][FONT=Ubuntu Mono]cat ~/.config/user-dirs.dirs .

[/FONT][/COLOR][COLOR=#000000]The machine is off at the moment, by starting up the machine do I run the risk of overriding any data of its been removed viva rm? I want to stress that I did not use rm on anything other than the ~./config file, should I attempt to boot from live cd to be on the safe side? My apologies I'm not trying to be a pain, I just don't want to make things worse![/COLOR]

---

### Post by HermanAB on 2016-11-19
OK, then search again, this time over the whole disk, starting at the very root of the tree:

find / -name whatever

---

### Post by howefield on 2016-11-19
> **Sammy_boy said:**
> .. should I attempt to boot from live cd to be on the safe side? 

If you feel you have actually deleted the files then yes, it would be safer to work from a copy of the disk/partition or at least a Live media.

---

### Post by dragonfly41 on 2016-11-19
I look for any clues in what the OP has written so far ...


In post #3
> I tried to reset my unity using 

rm -f ~/.conf/dconf/user; unity

Though I ,may have accidentally hit

rm -f /.conf/dconf/user; unity

But looking into my Ubuntu 14.04 I do not see any such ".conf" files.

I do have ~/.config/dconf/user

Also I read ...

> error message "Underhanded error message: Error when getting information for file '/home//Pictures': no such file or directory"

But '/home//Pictures' is not a valid path.
It should be '/home/<yourusername>/Pictures'.

So I would explore why is OP username missing in the path?

...

Of course these might be typing errors.

...

This thread describes similar symptoms to the OP.

[http://askubuntu.com/questions/633451/downloads-directory-not-opening](http://askubuntu.com/questions/633451/downloads-directory-not-opening).

...

If OP is to progress to trying to recover lost data, using Live USB, remember that 
spare space is needed on an external device to actually save all files identified in a forensic scan.

---

### Post by dragonfly41 on 2016-11-20
In my post above I should have added a suggestion to print out your recent command line history so we can see exactly what commands were run.  
This eliminates the possibility of typo errors in posting commands to the forum.
e.g. the last 15 commands are found by running this in terminal.

history | tail -n 15

Or use grep filters such as

history | grep "apt-get" | tail -n 15
or
history | grep "rm" | tail -n 15


More discussion here .. 
[http://askubuntu.com/questions/358867/how-to-view-the-bash-history-file-via-command-line](http://askubuntu.com/questions/358867/how-to-view-the-bash-history-file-via-command-line)

Perhaps the effects of some historical commands might be reversed.

---

### Post by ra7411 on 2016-11-20
Using your file explorer, you've looked in Trash, right?
Using Ctrl H in file explorer, you've looked through the hidden files, right?

---

### Post by dragonfly41 on 2016-11-20
OP wrote in post#3 > [COLOR=#111111][FONT=Ubuntu]I've also checked trash ect.  so we're all assuming that this is the case.[/FONT][/COLOR]

---

### Post by kingneutron on 2016-12-01
--Posting to get updates, but also to remind folks in general that a) backups are critical, and b) RM is _not_ your friend.  I use Midnight Commander to delete files for a reason.

--It sounds like your files may be gone, and you have my sympathy. In the future, I would advise copying important data to 3 different locations, and script automatic backups with cron or something if you don't run the backup script manually every day/week.

--If the data is vitally (job at stake // life/death) important, you could try taking the drive to a data-recovery service, but be prepared to pay $$$.

---

### Post by eric710 on 2017-04-06
There are a number of other file recovery tools that will do what you want, and automatically move recovered files to a different disk/folder. A search for file recovery tools to find the feature you require, would probably be the best...Normally, the way you work a forensics case, you work a forensically-correct image of the original disk.  You recover the information there, and then transfer any files of interest to a third disk for presentation. This way the original disk is never harmed, as all work is done  on the second disk, and anything that gets touched by people after the fact is on third disk. recommend article [https://www.cleverfiles.com/howto/computer-forensic.html](https://www.cleverfiles.com/howto/computer-forensic.html) described here is a best application to restore files

---

