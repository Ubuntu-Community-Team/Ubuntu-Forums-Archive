---
title: "Help Quick Please - No Login - Despair"
date: 2007-05-30
forum: General Help
---

### Post by cosbear on 2007-05-30
Hey Guys:

I have a little problem, I was reconfiguring user Login and must have made a truly stupid blunder.  Now when I boot up there is no login screen, just a little spinning disk in the middle of the screen.  I can access the disk, is there a file I can just edit to get a login screen so I can get in.  I would hate to have to reload everything, I spent the better part of yesterday loading and configuring it.  I can get all the data I need to save off of the Ubuntu Feisty drive but I don't know how to access the data stored in the Winxp virtualbox virtual drive I had on there.  I have searched through the directories looking for a config file for the login to see if I could edit it and get myself back in but haven't had any luck finding it.  I hope one of you bright guys can give me a clue or two to help me get back in, I need to work.  Thanks in advance, I'll be waiting for replies.  Respectfully yours, cosbear

A little bit of knowledge can be truly dangerous sometimes--oooops #-o

---

### Post by benmoreassynt on 2007-05-30
Can you remember precisely what you did before the problem arose?

---

### Post by cosbear on 2007-05-30
Thanks for the response.  I had been in the login utility under the administation menu changing a user login.  I think the last thing i did was to turn off automatic logging.  I am not sure pricisely however.  Then I rebooted and it comes up a black screen with a spinning disc in the middle, no login screen.  I have tried everything I could think of and tried all the keys and there is no response.  I had to push the power button to get out of there.  Have any ideas.  cosbear

---

### Post by benmoreassynt on 2007-05-30
If you can get to the shell prompt, can you type the following and let me know the results?

#id#

#id root#

To check if something is messed up with the user names and groups.

---

### Post by benmoreassynt on 2007-05-30
Sorry that should have appeared as:

```
id
```
```

id root
```

---

### Post by cosbear on 2007-05-30
When the hard disk boots there are no shell prompts.  Grub runs and then just the spinning disk. I've tried putting in usenames and passwords and every key on the keyboard and none of it changes anything just a spinning disk on a black screen.

---

### Post by cosbear on 2007-05-30
I have Freespire on another hard drive on the same computer so I'm pulling all the  files I need off the Ubuntu drive I need in anticipation of wiping and reloading and reconfiguring the whole disk if necessary.  It's a big waste of time, but I just did it all yesterday so if I have to I could do it pretty quickly.  I just hoped someone might know a way to save me the effort.  I probably deserve it though.  Seems like I learn the most from making stupid mistakes and having to correct them.  Word taught me spelling and grammar--such as it is--because I couldn't stand a computer correcting me.  Ha Ha.  I need to get Ubuntu back up though so if I have to I'll just wipe the drive and start over.  Hope I find out another way to do it though, just so I know how.  Even if I have already wiped the drive and started over.  I am depressed unless I'm learning.  cosbear

---

### Post by benmoreassynt on 2007-05-30
At the moment I am as clueless as you, however, you should be able to get to the shell.

When the computer boots, when you see the Grub notice, quickly hit the Esc key (you have a 3 sec window).

You should get something like this:
```
Linux kernal blah blah blah
Linux kernal blah blah blah (Recovery Mode)
```

Use the keyboard to select the first line which says recovery mode and hit enter. This wil lboot without any grahical shenanigans, and you should be prompted for your root/admin password. Enter it and you should end up at the shell.

Try that, and see if you have sucess, and we can take it from there.

---

### Post by cosbear on 2007-05-30
benmoreassynt:

Thanks a million for the help I will try it as soon as I can reboot.  I'm copying some big files over to the Freespire drive right now in case I have to reload the Ubuntu drive.  I'll try it as soon as the file transfer is complete.  Sounds like it is worth a try.  I never would have thought of that.   cosbear

---

### Post by cosbear on 2007-05-30
Hey Buddy:

Brilliant.  When it said grub I hit escape and it gave me a small menu which led me to a prompt.  After id root it asked for the password and I entered it and got a root prompt.  Unfortunately I'm still a baby when it comes to Linux so I didn't know where to go from there.  I'm nearly cli illiterate.  Is there a way to bring up the gui from there or the login script so I can edit it?  I'll await your answer, your my newest hero.  cosbear

---

### Post by benmoreassynt on 2007-05-30
No problem. ;-) I'm not an expert with login stuff - (there must be someone out there who is!)

However. Once you have logged into the cli, type

```
id
```
```
id root
```

at the prompt and tell me what you see. It may be that something has screwed up your only user account, which would mean that Gnome can't find anything to let you log in. That might make it hang.

---

### Post by benmoreassynt on 2007-05-30
Also, you could try typing

```
startx
```

It may work and boot Gnome, but I would not be too confident that it will work. It's not like Windows where you used to be able to just type 'win' to get to the gui from DOS.

---

### Post by benmoreassynt on 2007-05-30
See:

[http://ubuntuforums.org/showthread.php?t=457509&highlight=login+problems](http://ubuntuforums.org/showthread.php?t=457509&highlight=login+problems)

You are not the only person with this problem. Did you update the Linux kernel around the same time? It may be some sort of bug that's beyond me to fix.

Another thing to try:

Type:
```
sudo dpkg-reconfigure gdm
```

at the shell. It may reconfigure the login for you.

---

### Post by cosbear on 2007-05-31
Hey benmoreassynt Buddy:

You are a lifesaver.  Sorry I was out, I do onsite repairs and had to solve a windoze server problem for a small business owner.  Tedious work but it pays really well.  I hate all things microlame, but I can't completly get away from it.

The  startx command was the next step to a solution.  I should have known that because I've used that command before, but couldn't remember it.  When I said startx I was logged into a X gui as root.  I tried to open the user login utility under the administration menu and got an error message saying that the gdm was not started.  GDM = gnome display manager.  So I looked in /etc and found the gdm directory and sure enough there was a file in there called gdm.conf.  Remember I had said that I thought the last thing I did was turn off automatic login.  That was the key.  I opened gdm.conf up in a text editor and found these lines:

 [ daemon]
# Automatic login, if true the first local screen will be logged in
# as user as set with automatic key.
AutomaticLoginEnable=false
AutomaticLogin=

I changed the last two lines to:

AutomaticLoginEnable=true
AutomaticLogin=cosbear

and rebooted Feisty and it came up to my desktop smooth as silk.  Everthing seems to be working fine now, so I'm assuming that was the whole problem.
I can't thank you enough for your invaluable assistance and patience.  You saved me several hour of repetitive work and I truly appreciate it.  I hope I can help you out sometime buddy.   cosbear :D

---

### Post by benmoreassynt on 2007-05-31
Really pleased to be of help. Seems you worked out 90% of it yourself, but my 10% maybe got you started!

Awesome. Have fun with Ubuntu. Those people on the other thread may be interested to see your solution.

ben

---

### Post by MrGrey1 on 2007-08-20
Hey guys, 
I had the same problem, switched off the auto login and the machine then sits at black screen with cursor just before login screen. Luckily I have shell access from my win box and logged in and edited the gdm.conf back to auto login. This fixed my access problem but still hasn't fixed my ability to turn off the auto login without killing my system. I need to turn the auto login off, just as a matter of principal, I hate knowing there's a problem and not having a solution. Does anyone know where the gdm log file is? I'm assuming there's some command in the gdm startup that is not being closed/started properly and that's what's causing the hang. Would love to figure this one out. Cheers.
ps. 7.4, been upgraded for a while, just never tried to turn off auto login.

Edit: I left this for a while, upgraded to 7.10 and the problem appears to have fixed itself in the upgrade. I can now turn of auto login and get to the gnome login screen without my system hanging. :)

---

### Post by cosbear on 2007-08-21
> **MrGrey1 said:**
> Hey guys, 
I had the same problem, switched off the auto login and the machine then sits at black screen with cursor just before login screen. Luckily I have shell access from my win box and logged in and edited the gdm.conf back to auto login. This fixed my access problem but still hasn't fixed my ability to turn off the auto login without killing my system. I need to turn the auto login off, just as a matter of principal, I hate knowing there's a problem and not having a solution. Does anyone know where the gdm log file is? I'm assuming there's some command in the gdm startup that is not being closed/started properly and that's what's causing the hang. Would love to figure this one out. Cheers.
ps. 7.4, been upgraded for a while, just never tried to turn off auto login.

Howdy MrGrey:

Not exactly sure I entirely understand your question, nor do i know of a command in the gdm startup that is not being closed/started properly.  I'm pretty much a beginner.   Honestly, I haven't gone back to look at the gdm config file.  I do know how I turned off the auto login, without the previous problem.  Go to the System/administration/login window and click the users tab.  Select the include all users from etc/passwd.  Type in your user name and click the + add button.  Go to the accessibility tab and deselect the enable accessible login checkbox.  Go to the security tab.  Under enable automatic login I opened the gadget underneath it where your user name goes and there was my user name and just a white space above it to choose from.  I selected the white space to clear my username.  Then deselected enable automatic login.  Select the Allow local administrator login checkbox.  Select save when you close the login window and the next time you login you will have to type in your user name, enter, password enter, and then the desktop comes up.  If you want to know the difference in how to edit the gdm config file, open it and note the differences, I guess.  I hope that answered your question.  It worked for me.  I'm not sure if all those steps are entirely necessary, or the only solution, it's just what I did.  I haven't experimented anymore with it, because it worked.  Maybe someone with more experience could tell you more.  Cheers mate, g'day.  Later... cosbear

---

### Post by MrGrey1 on 2007-08-21
Hey cosbear,
 Thanks for pointing out the user list. I obviously didn't look hard enough at the gui. It didn't fix my problem though. 
After reboot with auto login turned off, just before the login screen appears everything stops  except the spinning cursor. Keyboard completely unresponsive with black screen.
 Shell access from my 2nd pc and a reset of gdm.config-custom back to auto login again to recover the system from that point. I've also found a log you can turn on in the [ login windows preferences- security tab ]  so I'm going to see what that has to say.

---

### Post by HokkaidoHillbilly on 2007-08-21
Glad to know that I'm not the only victim of this annoying little problem, although I came to a a slightly different way.

I was playing around w/ gdmsetup trying to tweak my login screen and restarted X via ctrl-alt-backspace, but when I did, I got the dreaded spinning cursor and nothing else.  

Will try to edit gdm.conf via the console via your guys' instructions though, so wish me luck!

---

### Post by cosbear on 2007-08-21
> **MrGrey1 said:**
> Hey cosbear,
 Thanks for pointing out the user list. I obviously didn't look hard enough at the gui. It didn't fix my problem though. 
After reboot with auto login turned off, just before the login screen appears everything stops  except the spinning cursor. Keyboard completely unresponsive with black screen.
 Shell access from my 2nd pc and a reset of gdm.config-custom back to auto login again to recover the system from that point. I've also found a log you can turn on in the [ login windows preferences- security tab ]  so I'm going to see what that has to say.

Sorry Buddy:

Sounds like what worked for me just caused you more problems.  One question I have is, are your permissions for your user name set to administrator?  I only have a few minutes right now to think about this then I have to run.  I am sending my gdm.conf, factory-gdm.conf and gdm.conf-custom files in doc format as attachments to this post in case you want to compare them to yours.  I probably should have done that last night, but I was falling asleep at the computer.  I'll think some more about this today and I'm looking forward to hear what you figure out.  I can't stand mysteries either when it comes to computers.  Good luck.  Later... cosbear

---

### Post by cosbear on 2007-08-21
> **cosbear said:**
> Sorry Buddy:

Sounds like what worked for me just caused you more problems.  One question I have is, are your permissions for your user name set to administrator.  I only have a few minutes right now to think about this then I have to run.  I am sending my gdm.conf, factory-gdm.conf and gdm.conf-custom files in doc format as attachments to this post in case you want to compare them to yours.  I probably should have done that last night, but I was falling asleep at the computer.  I'll think some more about this today and I'm looking forward to hear what you figure out.  I can't stand mysteries either when it comes to computers.  Good luck.  Later... cosbear

I don't know how the attachments thing works on these posts.  I uploaded the conf files as docs like I said, but they don't show up in the post for some reason.  You can private message me, IM me or email me from my profile and I would be glad to send you the files if you think they would help.  Good luck with your problem in any case buddy.  Later... cosbear

---

### Post by joshbax on 2007-09-04
thanks cosbear! this solution worked for me too!

---

### Post by cosbear on 2007-09-04
> **joshbax said:**
> thanks cosbear! this solution worked for me too!

Hey Buddy:

I'm glad it helped.  It's a lot less mucking about than a reinstall even if it's a somewhat backward shell-shocked newbie sort of solution.  I'm getting over it though.  Me and the console are slowly becoming old friends.  Later... cosbear

---

### Post by joshbax on 2007-09-10
hey, yeh, it worked for me, then i went to undo automatic log on, as my lappy is used by a few people, and i dont want them loggin on as me, and then the problem came back again when it loaded up... i should never have touched it once it was working again!!!

hmm... i have another thread going, which may hold the answer for me.

but i will let you all know of progress!

---

