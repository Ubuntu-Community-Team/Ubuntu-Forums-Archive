---
title: "Xterm copy &amp; paste?"
date: 2014-03-15
forum: General Help
---

### Post by Rob Sayer on 2014-03-15
I'm trying to copy from xterm and paste into leafpad in lubuntu 13.10.

Nothing I've found works.  Ctl-shift-C just exits to a new command line.  Middle mouse button does nothing.

It seems just ridiculous to me that simply copying from the terminal to clipboard is so convoluted in 2014.  This is just one reason why I think lubuntu is unsuitable for noobs, and probably also those of us who don't give a flying frak about geek points.

The thing is, the time saved by the extra speed of lubuntu on my 1Gb netbook compared to kubuntu (KDE!) has been more than made up by all the extra time and effort involved in simple configuration such as this.  This is not a more efficient way to do computing.

Can someone suggest either how to actually do this, or suggest another terminal that doesn't bring in a gazillion dependencies that actually has a menu bar that will actually copy selected text to a terminal?

This *is* the 21st century ...

---

### Post by oldos2er on 2014-03-15
Marking text then pasting with the middle mouse button doesn't work for you?

---

### Post by bapoumba on 2014-03-15
[http://ubuntuforums.org/showthread.php?t=2210754](http://ubuntuforums.org/showthread.php?t=2210754)
Please have a look here. May not be of much use as the user got it magically fixed. But copy/paste within xterm with shift-ctrl-c and shift-ctrl-v works here. ctrl-v to paste in Leafpad.

---

### Post by The Cog on 2014-03-15
That's strange. I just launched xterm (from a bash shell in xfce4-terminal) and couldn't copy from it with Ctrl-Shift-C. 
But simply highlighting the text to copy and then middle(scrollwheel)-clicking in the destination window works perfectly. And it's so much quicker and easier than all that ^C,^V stuff.

---

### Post by Dennis N on 2014-03-15
If you are using Lubuntu as you state, use LXTerminal instead and you will have the keyboard shortcuts for copy and paste.
**Accessories > LXTerminal **
It has a menu too. For copy and paste, see the Edit Menu.

XTerm only works with highlight text to copy and then middle-click to paste (as far as I can tell)

---

### Post by bapoumba on 2014-03-15
Ah. maybe something. I can reproduce in UXTerm, works fine in LXTerminal. I may have been confused, sorry. It is specific to Xterm : [http://www.linuxquestions.org/questions/linux-software-2/copy-paste-in-xterm-130077/](http://www.linuxquestions.org/questions/linux-software-2/copy-paste-in-xterm-130077/)

---

### Post by walterorlin on 2014-03-16
If you want to copy the output fo the entire command you may want to learn about the xclip package. To use it in terminal you can type ```
foo | xclip 
```where foo is the command output you want to copy. To get it install it in synaptic, lubuntu software center or by entering ```
sudo apt-get install xclip
``` Clipit is another option that does something similar as well. Although I have only tested this with xterm in 14.04.

---

### Post by bapoumba on 2014-03-16
Oh thanks, did not know about xclip. Installed :)

---

### Post by Rob Sayer on 2014-03-17
I've found a solution, though it's not really elegant.

I installed kde-plasma-desktop from the ubuntu repos.  I had kubuntu previously on this thing, and while you can get that to run a lot better in a 1Gb netbook with Cedarview gma than you'd think, it has frustrating latency.  Running the base kde package in openbox is much faster, though there were some pains configuring it.  No worse than lubuntu in general though ... I may install kubuntu 14.04 later if I add some RAM to this thing or use lubuntu 14.04 with this kde desktop.

So since konsole actually has decent features, like kde in general, I don't feel like I need lubuntu terminals anymore.  So I'm going to mark this solved.

Thanks for all the responses.

---

### Post by bapoumba on 2014-03-17
Would you please then mark your thread as solved ? [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Thanks!

---

### Post by afc888ny on 2015-01-10
a@a-NC210-NC110:~$ sudo apt-get install xclip
[sudo] password for a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xclip

---

### Post by afc888ny on 2015-01-10
How to install xclip in Lubuntu 14.04 LTS?

---

### Post by Impavidus on 2015-01-10
xclip is in the official repositories, section universe, which is enabled by default. Check your software sources. If there is a problem with your package manager, better start your own thread, as this one has been marked as solved.

---

### Post by vasa1 on 2015-01-10
> **Impavidus said:**
> ... better start your own thread, as this one has been marked as solved.
+1.

Also this: [http://askubuntu.com/questions/572005/clipit-functionality-cant-paste-in-order](http://askubuntu.com/questions/572005/clipit-functionality-cant-paste-in-order) !!!

---

