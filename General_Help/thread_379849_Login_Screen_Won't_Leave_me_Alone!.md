---
title: "Login Screen Won't Leave me Alone!"
date: 2007-03-08
forum: General Help
---

### Post by cheesybobman on 2007-03-08
Hi people.

So a few months ago I installed Ubuntu 6.10 i386 Version and everything's been working great, except for one thing (which I know many people have had trouble with): wireless cards. That's not my problem, I finally got the internet to work a couiple of nights ago. What I did was install NDISWrapper (the right way this time :) ) and it worked. 

My real problem is, now, when I start Ubuntu:

a. The login screen comes up fine; no resolution problems or anything
b. I insert my username
c. I press ENTER
d. I insert my password
e. I press ENTER
f. A black DOS-like screen comes up with a blinking cursor
g. The MAC-like circular waiting thing like the Windows hourglass comes up on the orange Ubuntu screen
h. The login screen comes up again
i. Repeat steps 1-8 a few times
j. Eventually get frustrated and shutdown computer, switching to uber-virus-prone Windows

I was wondering if maybe something I did with the wireless card made this happen, since this started happening the time after I installed NDISWrapper; or maybe someone out there just has an answer to my plea:

HELP!! I love Ubuntu very much and would like to make the switch from Microsoft :) 

Just need some help along the way :confused:

But like I said: this just started happening. I've been using Ubuntu for several months for word-processing and such without any problems (except the wireless).

Hope somebody knows something I dont know :)
~Cheesybobman

---

### Post by tribble222 on 2007-03-09
Try logging into a failsafe gnome session

---

### Post by zvacet on 2007-03-09
Try choose safe gnome (or something like that) from sessions.Terminal window will pop up.
```
sudo /etc/init.d/gdm start
```
If that doesn´t help try 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cheesybobman on 2007-03-09
Thanks I'll try these later and post if they worked or not.

---

### Post by Pikestaff on 2007-03-09
I had a similar problem once (not exactly the same, but close) and I had to reconfigure xorg and select some different drivers to get it to work.  I don't know if that will help you because yours seemed to happen all of a sudden, but maybe you might  give it a shot if nothing else works.

---

### Post by cheesybobman on 2007-03-10
Well, I've hit another dead end. I tried switching to every other session on the menu but I stil can't do anything. Whenever I log in it just goes through its routine again. Here's the items on my sessions menu:

1) Last Session
2) *
3) GNOME
4) Failsafe GNOME
5) Failsafe Terminal

I can't remember #2 right now, so I'll have to go look it up later. I'm pretty sure it says 'Terminal', but I'll have to go see. 

Thanks again,
~Cheesybobman

---

### Post by tribble222 on 2007-03-10
Press ctrl-alt-f1 to get to the terminal (ctrl-alt-f7 will get you back to the normal login screen).  Then try entering the commands zvacet mentioned above.

If that doesn't work, see if you can post your /var/log/Xorg.0.log (called something like that probably) here and maybe it will show what the problem is.

---

### Post by cheesybobman on 2007-03-10
Thanks tribble222, I'll try that and post back in about 15 minutes.

---

### Post by cheesybobman on 2007-03-10
OK, so I'm making progress:

I pressed Ctrl+Alt+F1 and typed:
```
sudo /etc/init.d/gdm start
```
The terminal then displayed this:
```
* Starting GNOME Display Manager...                                           [ok]
```

Then, after I typed my name password, a splash came up with this:
```
GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator
```

I'm the system administrator.

I'm going to try the second code right now. Thanks for everybody's help so far.

~Cheesybobman

---

### Post by cheesybobman on 2007-03-10
OK, so I typed ```
sudo dpkg-reconfigure xserver-xorg
``` and did some reconfiguring but that didn't work either. I still got the same text as in the post above when I tried to logint to the GUI. By the way I have no trouble logging into the terminal.

Hope someone has something else I can try.

~Cheesybobman

---

### Post by cheesybobman on 2007-03-11
If nobody has an answer then there's always the option of reinstalling Ubuntu. It wouldn't be such a hassle since I haven't really had the chance to customize much yet.

---

### Post by tribble222 on 2007-03-11
You don't need to reinstall, this is probably a simple problem of permissions or disk space.

Okay it is possible you are out of disk space.  This happened to me once because a log went crazy and filled up my drive.  You can check your space by typing

df -h

Look at the "Avail" column and report back :-)

---

### Post by cheesybobman on 2007-03-11
OK so this might actually help:

I typed ```
df -h
``` and looked at the 'Avail' column. Lo and behold, every column was less than 3%, with the exception of my Ubuntu partition, which was at 100%. If this is the root of my problem, how can I fix it? Should I just resize the partition?

~Cheesybobman

---

### Post by tribble222 on 2007-03-11
Do you know what could have filled up your drive?  If it's not something you did then it could be something like a runaway log file like I had.  To find the largest files type the command

sudo du -ah /var | sort -n -r | head -n 10

This will return the 10 largest files or directories in /var and give their location and size.  If nothing seems out of order, then search your entire root partition instead of just var by running

sudo du -ah / | sort -n -r | head -n 10

Hopefully this will give us a clue as to what took up all the space

Edit:  If nothing shows up that you want to delete, then I guess resizing the partition would be an okay solution, but you should back everything up before you do that (don't ask me how I learned).

---

### Post by cheesybobman on 2007-03-11
Well, I tried tribble222's 2 commands above. The first one produced a meaningless answer (the biggest file was 1004k), but I need a little help with the second one:

It showed me a list of all the biggest files, but many of them were cut off. Is there any way to slow down the 'viewing'? (Like the Windows/DOS dir**/p** command)

~Cheesybobman

---

### Post by tribble222 on 2007-03-11
You can pipe the output to more so that it doesn't scroll off the screen:

sudo du -ah / | sort -n -r | head -n 10 | more

---

### Post by cheesybobman on 2007-03-11
Thanks, I'll try this. I wish I was more fluent at Unix. This would be a lot easier.

---

### Post by cheesybobman on 2007-03-11
No dice. My biggest file is 1020k.
Any other suggestions?

~Cheesybobman

---

### Post by tribble222 on 2007-03-12
1020k?  Can't be.  Something must have gone wrong in the find.  Maybe you mean 1020M?  Your root partition HAS to have files larger than 1020k

Okay first things first.  I just thought of this.  Run 

sudo aptitude clean

This should free up some space, maybe enough to log in!  If this doesn't work, and your /home isn't on a separate partition, run

du -ah ~ | sort -n -r | head -n 10 | more

Just to check for large files in your home directory.  If that still doesn't show any large files, then maybe you should boot your install cd, mount your root partition, and poke around with nautilus.  Then you'll be able to look for large files or files you wish to delete using a gui.  Could run baobab in the live cd too.

If you are able to login after the aptitude clean command then empty your trash (if /home is on the root partition) and try to free up some space so it doesn't run out again.

---

### Post by cheesybobman on 2007-03-12
Nope. It said 1020K, but I'll try what you said when I get home later.

---

### Post by cheesybobman on 2007-03-14
Well, my Ubuntu is finally up and running again. I ended up resizing the partition from 2.89GB to 4.89GB and it worked. My guess is that installing NDISWrapper for my wireless used up the last of my free space.

So thanks for all your help, guys. I may just call on you again someday :) 

Thanks again,
~Cheesybobman

---

