---
title: "Help with software"
date: 2007-06-19
forum: General Help
---

### Post by golfy on 2007-06-19
Hi,

Can anyone help me with some software please. I would like to run LiarLiar [http://liarliar.sourceforge.net/](http://liarliar.sourceforge.net/) on ubuntu but have tried without success. I am using the live CD and would like to run it from the hard drive by loading up ubuntu first and then using the ubuntu browser to simply run the LiarLair program which is on the hard drive. I know nothing about ubuntu or how to use it so would anyone be willing to help me by emailing me the finished software from the LiarLiar website so I can simply put it on my hard drive and run it in ubuntu by clicking on it from the browser? I would be very gratefull if you could help.

If you would like a financial donation for your help then I would be willing to oblige. Please let me know what amount it would be.

Regards

golfy

---

### Post by Brucevdk on 2007-06-19
golfy, no offense but you might have more success with resolving your problem if you didn't start a completely new thread discussing the same exact issue every other day. If you have new information to add, add it to the original thread instead of starting a new one. You could probably even bump it once in a while so people know you're still having problems.

I can see people are trying to help you but if you go off and start a new thread they can't monitor what you're doing.

---

### Post by golfy on 2007-06-20
Hi,

I can see your point and will leave the post as is and see what happens for a few days but as no one has yet replied I don’t believe anyone is trying to help so far, in fact it looks like the exact opposite. You yourself could have possibly helped if you are an experienced ubuntu user but instead volunteered to make comments instead of offering assistance with the installation of the software. If it is so difficult to install the software then how is a complete novice supposed to do it. If it is easy for an ubuntu user with some experience then why the lack of help? I am in a bit of a pickle and if the software would even give a beyond probability result then it would be of great help in my life. 

I have put up the post 3 times and not one single person has offered any assistance, doesn’t look like help to me. I know moaning about it also discourages helpers but no replies is no replies.

I’ll leave it a few more days and then re-asses what to do.

Thanks for your time and comments.

golfy

---

### Post by Qu4k3R on 2007-06-20
could you install the program in a temp directory ?

I don't know if you have enough RAM memory.

Running non-installed software in a live-cd can be messy..

And golfy:
everyone has it's own bugs (even with windows)...

You might need to install ubuntu first and then run the software.
It would be easy.

If you install the program with the live-CD, 
It might not be installed on your HDD, unless you install the program on the HDD with the correct drivers (if you use windows, use ntfs-3g drivers to manipulate the windows partition)

PS:
Now can you help me with my bug ?
[http://ubuntuforums.org/showthread.php?t=477280&](http://ubuntuforums.org/showthread.php?t=477280&)

---

### Post by Brucevdk on 2007-06-20
> **golfy said:**
> 
I don’t believe anyone is trying to help so far, in fact it looks like the exact opposite. You yourself could have possibly helped if you are an experienced ubuntu user but instead volunteered to make comments instead of offering assistance with the installation of the software.


Actually I was hoping to help you, I grabbed the source from the Liar Liar website and tried to compile it. However because the source offered at the Liar Liar website is from early 2004 it requires several older development packages. Those packages are gtkmm-2.0, gthread-2.0 and gstreamer-0.6. 

Of those packages only libgtkmm2.0-dev is available through the repositories, I tried to find the other ones by Googling several times but I was unable to find the relevant packages. There is a file */usr/lib/libgthread-2.0.so* which seems to be the gthread library. I am not sure how I can get around this problem and so I personally cannot assist you any further.

Perhaps I should have informed you of this, but it would have made me feel very uncomfortable. I only have some limited experience compiling packages from source (the typical ./configure && make && make install) I have personally never encountered this problem.

> **golfy said:**
> 
If it is so difficult to install the software then how is a complete novice supposed to do it. If it is easy for an ubuntu user with some experience then why the lack of help? I am in a bit of a pickle and if the software would even give a beyond probability result then it would be of great help in my life. 


Installing software in Ubuntu is easy under certain circumstances. Those circumstances are: 1) the application is in the official or a third party repository 2) there is a binary package (such as a .deb) available somewhere else 3) the application is easily compilable from source.

From what I can tell this isn't the case for Liar Liar, though for somebody with more experience compiling programs it might be.

> **golfy said:**
> 
I have put up the post 3 times and not one single person has offered any assistance, doesn’t look like help to me. I know moaning about it also discourages helpers but no replies is no replies.


You simply cannot assume nobody is trying to help you, as I explained above I was trying to assist you but I felt uncomfortable in replying to the thread with this information. I personally am convinced that if you wish to receive help on forums the best way to proceed is:
[LIST]
[*]Create one single thread and bump it every once in a while if the thread goes dead (perhaps every week).
[*]Do not cross post, information concerning to your problem should be handled centralized so people can get an overview of what is happening. If you cross post or dupe threads people can't keep track of the thread.
[*]Even if there are no replies, do not assume that no one is trying to help you. Again you should probably bump your thread if it's been a while since anybody responded.
[/LIST]

I hope somebody else is able to offer a solution to this problem, I'll be keeping an eye out on this thread by subscribing to it. Something you could also do is contact the author of Liar Liar at gururise at users.sourceforge.net.

Good luck.

---

### Post by golfy on 2007-06-20
Hi to the guys who replied.

Many thanks for your information, I realy do appreciate it. As a complete novice on Ubuntu I have no idea on how to do anything on it apart from boot from the live CD.

I of course would be willing to help you with any problems you have but as an almost zero knowledge Ubuntu newbie then you would probably know far more than I do. Hope someone on here can help with your problem Qu4k3R.

I have only realy used Windows and when I found the software to my dismay I realised that it was meant to run on Linux so i bought a Live CD and then got stuck at that point. I thought it may be similar to Window when installing software, how wrong I was.

Thanks again for your efforts, like I said before, much appreciated.

I'll take your advice on board Brucevdk and go as you suggested. How do i bump my thread though?

I have sent a few email from the original website but have had no replies - I'll try again and see what happens and let you know of any progress on here.

Any one else out there able to shed some light on the problem? If installing Ubunto on a seperate hard drive helps for things to work then that is doable if it makes things easier for you guys as I have an old 10GB one I can add to my PC and install Ubuntu on that.

Looking forward to your replies.

golfy

---

### Post by Brucevdk on 2007-06-20
> **golfy said:**
> I'll take your advice on board Brucevdk and go as you suggested. How do i bump my thread though?

Excellent. Bumping means replying to a thread to get it back to the top of the forum discussions list, also see [Wikipedia]("http://en.wikipedia.org/wiki/Bump_(Internet):) for a description. You shouldn't do it that often since it isn't always considered good practice, perhaps once a week if necessary.

> **golfy said:**
> If installing Ubunto on a seperate hard drive helps for things to work then that is doable if it makes things easier for you guys as I have an old 10GB one I can add to my PC and install Ubuntu on that.

That probably wouldn't help you in getting Lair Liar installed, but hey there's nothing wrong with installing Ubuntu. I can certainly recommend it.

---

