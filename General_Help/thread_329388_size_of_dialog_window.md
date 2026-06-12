---
title: "size of dialog window"
date: 2007-01-01
forum: General Help
---

### Post by nicc9 on 2007-01-01
hello, all.

this has become very frustrating.

basically I need to make dialog windows bigger by default (in particular popup windows for "open file..").

are the default dimentions taken from a text file that i can change?

what app takes care of deciding this? X, metacity (or other window manager), Gnome or what?

I need to do this because I open files with bluefish every 2 mins and every time I have to reside the window, and the app (and I think metacity in general) doesn't remember the last size i used.

thanks!!!
:mrgreen:

---

### Post by nicc9 on 2007-01-01
anybody? :-|

---

### Post by greggus on 2007-06-14
I have the same problem.
How can I change default size of dialog window e.g. save / open file ?

---

### Post by startling on 2007-07-18
I have the same problem! This is not very good UI design IMHO. To have to resize a Save or Open dialog every time you use it is simply risible.

---

### Post by oomingmak on 2007-07-19
[http://ubuntuforums.org/showthread.php?t=428490](http://ubuntuforums.org/showthread.php?t=428490)

---

### Post by startling on 2007-07-19
> **oomingmak said:**
> [http://ubuntuforums.org/showthread.php?t=428490](http://ubuntuforums.org/showthread.php?t=428490)

Thanks for the link, Oomingmak. I didn't see a solution in that thread, though. I'm new to Ubuntu and I'm amazed that it seems there's no simple solution to what is undoubtedly a problem. 'Save as' dialogs are such a fundamental part of any OS that to have them so totally broken is laughable, but to have them *broken by design* is absolutely* crazy*!

---

### Post by oomingmak on 2007-07-19
> **startling said:**
> Thanks for the link, Oomingmak. I didn't see a solution in that thread, though. I'm new to Ubuntu and I'm amazed that it seems there's no simple solution to what is undoubtedly a problem. 'Save as' dialogs are such a fundamental part of any OS that to have them so totally broken is laughable, but to have them *broken by design* is absolutely* crazy*!
Hi startling. 

I didn't mean to give you the impression that my link had an answer to your problem, it was more to point out why they problem persists and why there still isn't an answer to it (and probably never will be).

I absolutely agree with you that it is ridiculous to have such obvious and fundamental flaws in an OS (but I find it even more bizarre when people extol these shortcomings as if they were some kind of virtue).

File dialogs are a sore point for many users:

see here:

[B][http://ubuntuforums.org/showthread.php?t=403111](http://ubuntuforums.org/showthread.php?t=403111)

[http://ubuntuforums.org/showthread.php?t=413457](http://ubuntuforums.org/showthread.php?t=413457)


[/B]The closest thing that I have found to a "solution" is [**Devil's pie**]("http://wiki.foosel.net/linux/devilspie"),  but it means writing code to detect the presence of windows and then specifying geometry settings / values to determine size and placement. You then have to do this for every single window (and the code is not trivial if you are not a script expert or programmer).

I keep meaning to get round to giving Devil's Pie a try, but so far I just can't be bothered. Instead I just go and use an OS where my windows stay where I put them.

I much prefer the look of Gnome, but I'll see what KDE4 has to offer later this year.

---

### Post by cookies on 2007-07-19
.... I just resize the dialog and it stays that way the next time, but that's for GNOME apps in KDE....

---

### Post by startling on 2007-07-20
> **oomingmak said:**
> I didn't mean to give you the impression that my link had an answer to your problem, it was more to point out why they problem persists and why there still isn't an answer to it (and probably never will be).

Sigh. Here's me telling everyone how great Ubuntu is - one friend even asked me for an Ubuntu CD because he's going to dual boot - and then I run into problems like this. Perhaps I should have given it a month or so before becoming quite so evangelical about Ubuntu! I just know that that friend is going to ask me if I know how to get the Save as dialogs to be usable...

> **oomingmak said:**
> I absolutely agree with you that it is ridiculous to have such obvious and fundamental flaws in an OS (but I find it even more bizarre when people extol these shortcomings as if they were some kind of virtue).

It astounds me. I cannot understand how anyone who used these dialogs would think they're okay - or perhaps the people that designed them this way don't use them!

> **oomingmak said:**
> [/B]The closest thing that I have found to a "solution" is [**Devil's pie**]("http://wiki.foosel.net/linux/devilspie"),  but it means writing code to detect the presence of windows and then specifying geometry settings / values to determine size and placement. You then have to do this for every single window (and the code is not trivial if you are not a script expert or programmer).

Ah, that cuts me out then! Oh well. Perhaps I should ditch Gnome and give KDE a try? What do you think? (Actually that's just reminded me! Another friend, who has used Suse for yonks, and I were chatting a couple of weeks ago - he was chuffed that I'd switched this machine to Linux btw - and he said that maybe he should give Gnome a try. Oops, I better email him now...)

---

### Post by Incie83 on 2007-07-25
> **oomingmak said:**
> [...**Devil's pie**]("http://wiki.foosel.net/linux/devilspie"),  but it means writing code to detect the presence of windows and then specifying geometry settings / values to determine size and placement. You then have to do this for every single window (and the code is not trivial if you are not a script expert or programmer).

I have to disagree. Devil's Pie rules are logically structured and very easy to write, just check the wiki you've linked to. Devil's Pie is in the repos, so it is easily installed by typing:

```
sudo aptitude install devilspie
```

into a terminal window.

---

### Post by startling on 2007-07-25
> **Incie83 said:**
> I have to disagree. Devil's Pie rules are logically structured and very easy to write

I don't wish to seem cheeky but, if you're familiar with Devil's Pie and its methods, could you post a rule that would change the save as dialog in Firefox to a sensible size? 

I did look at the Wiki but I must say I found it a tad daunting and it looked like it might take me hours to work out! (I'm a graphic designer, not a coder...) So I left it as one of those jobs that I would look at when I have a spare afternoon (i.e. never!). 

Thanks for your reply.

---

### Post by oomingmak on 2007-07-25
> **startling said:**
> I did look at the Wiki **but I must say I found it a tad daunting** and it looked like it might take me hours to work out!
That is exactly the point I was making, and your statement comes as no surprise to me at all.

There are experienced Linux users posting questions in the comments section of that Wiki, who are trying to figure out how to get certain actions to work.

I am by no means saying that it is impossible to learn, but saying that it is "very easy" is not how _I_ would describe it.

---

### Post by Incie83 on 2007-08-03
> **startling said:**
> I don't wish to seem cheeky but, if you're familiar with Devil's Pie and its methods, could you post a rule that would change the save as dialog in Firefox to a sensible size? 

Hmm.. I can't post the exact code for you (I'm on a Windows box at the moment) but I can point you in the right direction, it should only take you 15 minutes to get there if you do the following:

1. Install Devil's Pie like I suggested in my last post
2. Read the wiki up to the point where it gets too scary, make sure to read about the configuration files in the YOURHOME/.devilspie directory
3. Create a file called 'debug.ds' in the .devilspie directory, it's content is just '(debug)' on line 1
4. Open a FF window and a 'Save As' dialog and keep these windows open
5. Go to the terminal and run 'devilspie &'
6. Look at the output in the terminal and see if you can identify the 'Save as' window (You will find 'application name: 'Firefox' and hopefully a 'window name/title' variable as well, make sure you mix up the FF main window and the dialog box)
7. You can identify the 'Save As' dialog box by its unique 'window title'. Create a file 'YOURHOME/.devilspie/firefox.ds' and input:

```
(if 
( and
  (is (application_name) "Firefox") 
  (is (window_name) "VALUEYOUFOUNDFORWINDOWNAME") 
)
  (geometry "LOOKTHISPROPERTYUPONTHEWIKI")
)
```

8. Delete 'debug.ds' or, even better, rename it to 'debug.ds_' so you can easily 'switch on' the debug function should you need it in the future.
9. Go into a terminal, type 'killall devilspie', then 'devilspie &' and test your rule
10. If you're satisfied with the result, just add 'devilspie &' to the start-up programs in System > Preferences > Sessions

I hope the values in capital letters speak for themselves... happy 'programming' ;)

EDIT: I found the 'window name' (or 'window title') to be 'Save As'. But, just for educational value, I'll leave the rest of the post intact (the (debug) option is quite useful for making Devil's Pie rules).

---

### Post by strabes on 2007-08-03
Just so you guys know, KDE's dialog boxes don't have this problem. It also has the ability to specify window sizes, locations, desktops, etc, just by right clicking on the windows' title bars.

---

