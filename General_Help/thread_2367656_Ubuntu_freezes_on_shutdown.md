---
title: "Ubuntu freezes on shutdown"
date: 2017-08-01
forum: General Help
---

### Post by adam-beddoe on 2017-08-01
Hello forums,

My Ubuntu freezes every time I try to shutdown my laptop (XPS 15 dual boot with windows 10). 
It is completely unresponsive, there is no cursor, and the only way to get out is through a hard shutdown.

I've tried doing the key-command rescues that I saw mentioned on another forum post (crtl alt f1 and alt f2), and on further investigation, have discovered that this also causes my laptop to freeze.

It also freezes occasionally some other times, then there is a cursor, but nothing else seems to work. If I've been watching a video at the time, the audio will continue to play for a bit but the video will freeze.
(I'm not sure exactly when this happens or if it's related to the shutdown freezing issue)

I also used to get a problem where it would almost shutdown, and I'd be left with a terminal that said something like "cpu2 stuck for 22s!" but this is not visible anymore as I do not make it this far. \\:D/

Thanks in advance for any suggestions, they will be greatly appreciated! 

I'm able to post logs and more information, but don't know too much about the workings of linux, so someone will have to tell me where what I'm looking for :p

---

### Post by RobGoss on 2017-08-02
Hello and welcome to the forum, You might want to share the specs for your machine it will help trouble shoot the problem, is this a older machine?

---

### Post by banancitron on 2017-08-03
I have the exact same problem. It started a week ago with the "cpu2 stuck for 22s! message at shutdown and now my computer just freezes the exact moment I try to shut it down. Both via terminal or GUI. 

My computer is a couple of months old Dell xps 15 with
 Intel (R)CPU label for Core(TM) i7 KBL
NVIDIA(R) GeForce(R) GTX 1050 with 4GB GDDR5

---

### Post by wildmanne39 on 2017-08-03
Welcome to the forum banancitron please start your own thread so you and the OP of this thread can get the help you need.
Thanks

---

### Post by adam-beddoe on 2017-08-18
Sorry about not responding, I have now managed to solve the issue myself. I hope it will provide some use for anyone else with this problem:

I followed the steps here:
[https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics?noredirect=1&lq=1](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics?noredirect=1&lq=1)

(I actually fresh installed version 16.04.2 and then followed the steps before upgrading to 16.04.3, but I think it should work without doing this)

Edit: I actually installed nvidia-current instead of whatever version that link suggests

---

### Post by jetson23 on 2017-08-18
Hi Adam. Thanks for your response, I think I'm having the same issue. I  posted it in this thread, but didn't get replies, probably not the right  place:

[https://ubuntuforums.org/showthread.php?t=2317843&page=17](https://ubuntuforums.org/showthread.php?t=2317843&page=17)

I'm  attached what Ubuntu looks like when I try to restart, I just want to  verify it's the same problem. I'll take a closer look at your link; at  first glance it seems more graphics related.

---

### Post by adam-beddoe on 2017-08-18
Hi Jetson,
This looks very similar to the initial error messages I was getting before it broke more. I was browsing various posts about this and put 2 and 2 together. 
I think it has something to do with the graphics processes not terminating (don't know anything about how it works so that's the best I can offer haha) so I was sceptical that it was going to work myself too but it did.

I'd be curious to know if it works for you

---

### Post by jetson23 on 2017-08-18
Adam-

Sorry for needing to be spoon-fed, but would you mind specifically saying what parts of the link you posted you did? There are many responses as well as comments, some of which have links to other threads. It's pretty confusing, seems like a lot of different paths to take to do some of the same stuff. The first one I chose did not fix the problem, which was basically remove all nvidia drivers, install intel microcode and gpa-tools, and install nvidia current.

Can you describe exactly what you did step by step?

Thanks in advance.

---

### Post by adam-beddoe on 2017-08-19
I followed the top answer, though it was from a fresh install of Ubuntu 16.04.2 
One symptom of my problem was that startx would also cause the system to hang, perhaps you can use this to work out if your problem is the same.

---

