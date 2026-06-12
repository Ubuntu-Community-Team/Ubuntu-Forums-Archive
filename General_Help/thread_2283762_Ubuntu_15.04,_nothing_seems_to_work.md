---
title: "Ubuntu 15.04, nothing seems to work"
date: 2015-06-24
forum: General Help
---

### Post by fuser312 on 2015-06-24
I am coming back to Ubuntu after 2.5 years and it is being a very unpleasant experience. First time I installed and updated the system, my Internet connection (mobile broadband) kept getting disconnected for every 1-2 minutes (other distros were doing fine on the same system) and shutdown button directly logged me out instead of asking for shut down or restart. There were various other annoyances too, some solved (Internet, trial error) and some not but anyway I reinstalled the system and didn't updated this time (I was thinking that may be some update is the problem) but no system kept behaving unpredictably. 

Now I have reinstalled it a third time and my problems are still here. The "shut down button" problem and the Internet connection problem, this time its simply unable to connect whereas the live version of same os i.e. Ubuntu 15.04 is working fine. I am posting this from live version of 15.04 where I can connect to my Internet using same setting and software that I am trying to use in the installed system but its not working there.

Is 15.04 in general a buggy release or is it just me? Should I fall back to more stable 14.04? 

Thanks.

---

### Post by dino99 on 2015-06-24
i have not met such issue with my vivid installation running gnome-shell

---

### Post by branau on 2015-06-24
That's interesting, I wonder if you have a corrupted or incomplete installation somehow. What did you use to install it? I run Vivid Velvet with little to no problems at all. [This thread](http://ubuntuforums.org/showthread.php?t=2276023) has a running list of bugs and how to get around them, you could check there. I'd also recommend getting the updates, as they typically fix the bugs. What machine are you running it on? And what are it's specs?

---

### Post by Bucky Ball on 2015-06-24
Try 14.04 LTS. As a long-term support release it has support for five years, until 2019. 15.04 is supported until end of January next year.

---

### Post by mbott on 2015-06-24
> **fuser312 said:**
> 
Is 15.04 in general a buggy release or is it just me? Should I fall back to more stable 14.04? 


Quite the opposite for me. I'm currently running 15.04 on both my inexpensive laptop **and** my home brew desktop. I felt comfortable enough with 15.04 to replace the desktop's very stable 14.04.2 LTS installation.  I do have a Clonezilla image of the 14.04.2 system that I could drop back to, but don't see the benefit of doing so at the moment.

-- 
Mike

---

### Post by wildmanne39 on 2015-06-24
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. You can run it from the live version.
Thanks

---

### Post by RobGoss on 2015-06-24
I'm thinking maybe it's a bad ISO file you might have gotten have you try a different download?

I think [COLOR=#000000]14.04 LTS. is a great choice I'm currently using it and love it..[/COLOR]

---

### Post by MikeMecanic on 2015-06-24
Get an Internet connection on a RJ-45 cable.  **Ubuntu 15.04 is not a buggy release**.  Upgrade to Willy Werewolf after: [http://ubuntuforums.org/showthread.php?t=2277831](http://ubuntuforums.org/showthread.php?t=2277831)
> Life would be so much easier if we only had the source code


The source code is a mkusb flash drive of the Vivid Vervet iso image.
[http://releases.ubuntu.com/15.04/](http://releases.ubuntu.com/15.04/) 
[https://help.ubuntu.com/community/mkusb/v9](https://help.ubuntu.com/community/mkusb/v9)

sudo add-apt-repository ppa:mkusb/ppa
sudo apt-get update
sudo apt-get install mkusb

---

### Post by Zoidmaster on 2015-10-05
Sorry people, but I am having the same problems with Ubuntu Studio 15.04:  One of my sound cards detected by Linux with the ALSA drivers for it in place, but not installed (it works in KXStudio). Some applications don't launch including the "Report problems" app, my Firefox profile suddenly completely wiped out, every time i right click with the mouse on something the top menu item is chosen before i even get to pick something from the pop up menu.... it's a long list.

As more and more people find out that Windows 10 is worse than spy ware (it's police state ware) these forums will be buzzing like never before with newb's like me who have a hard time using the terminal with the lack of graphical interface apps.  Finding help is not that easy, and although with Windows, Microsoft was the last place to look for help, it was always easily found through the hacker community.  Linux is open source, but getting help is tougher than nails.  More often than not I get partially through a tutorial or procedure description, only to end up faced with gibberish only someone with Linux experience would know, so then you end up searching for an answer to this, an explanation for that, a few dead links, links going to the wrong information, and the ever popular links to even harder to understand stuff, that just raises even more questions!!!!  When you finally got that rogue application or piece of hardware working, something else in the chain fails!

But I can not blame anyone for giving up their time for free to help.  I love the open source community for what it stands for, and I am not going to give up on it!  As a matter of fact I would love to help, but my knowledge of computers is limited to a soldering iron.

Now I am going to look for a linux guru to move in with me!

---

### Post by sudodus on 2015-10-05
Welcome to the Ubuntu forums, *Zoidmaster* :-)

Please make *an own thread with a good title describing your problem*. Best is to ask for and solve one problem in each thread. That way other users, who might be able to help will find your question. (It is not likely, that they find your post here (buried in an old thread with a general title.)

---

### Post by Zoidmaster on 2015-10-05
Thanks for the worm welcome Sododus, ):P

The general title is what got me here, and with all that seems to be not working right, and the possibility that it may all be related to one thing, it is hard to narrow it down to one starting point or question.  I have searched for individual answers on some topics, the one with the sound card being a real doozy, that there is a solution for at the ALSA site, but it is written in a way that leaves some open questions, and raises new ones, that the person who wrote it could answer best, but they have no venue to be contacted through.  It would be great if I could ask them to not only give me answers, but include them in their troubleshooting steps, to lessen confusing others.

I will pop the question in a new thread as soon as I figure out the least dumb sounding way to ask it!

---

### Post by Bucky Ball on 2015-10-05
> **Zoidmaster said:**
> Ubuntu Studio 15.04:  One of my sound cards detected by Linux with the ALSA drivers for it in place, but not installed (it works in KXStudio). Some applications don't launch including the "Report problems" app, my Firefox profile suddenly completely wiped out, every time i right click with the mouse on something the top menu item is chosen before i even get to pick something from the pop up menu.... it's a long list.

... is fine. Just add more detail and leave the rest of your original post out as it has nothing to do with support and belongs in a non-support area if you intend posting it in future. Good luck. :)

---

