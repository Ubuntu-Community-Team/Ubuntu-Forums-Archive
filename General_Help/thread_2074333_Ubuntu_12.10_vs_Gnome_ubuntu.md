---
title: "Ubuntu 12.10 vs Gnome ubuntu"
date: 2012-10-21
forum: General Help
---

### Post by Chelidze on 2012-10-21
I love Ubuntu but i do not like one thing about it, system usage, i think it uses to much system resources, my windows 7 uses less resources then Ubuntu 12.10 
so what i want to know if any one knows, does [ubuntu]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10") with gnome on it takes less resources then ubuntu ??
I apologize about this question, it might sound silly for some users/people but i am new to linux and this question accrues if I install [ubuntu]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10") with gnome on it use the same terminal commands (apt-get, and if I am able to install ppa on it from launched ) 

and can I install gnome 3 on ubuntu 12.10 as I had the ability  on ubuntu 12.04

 Thank you for your time

---

### Post by Mark Phelps on 2012-10-21
> **Chelidze said:**
> ... my windows 7 uses less resources then Ubuntu 12.10 ... 

And you know this, how?

---

### Post by offgridguy on 2012-10-21
You might consider lubuntu for a lightweight system easy on resource.

---

### Post by Cheesemill on 2012-10-21
To install Gnome Shell on Ubuntu 12.10 it's just the same method as previously:
```
sudo apt-get install gnome-shell
```And yes, everything that works with Unity will work with Gnome Shell as well (PPA's etc).

I wouldn't say that it's really any lighter although I've not done any proper testing, they are both modern DE's designed for recent hardware.

---

### Post by Chelidze on 2012-10-21
> **Mark Phelps said:**
> And you know this, how?

started system monitor on ubuntu looked as how it uses memory cpu swap 

started task manager on windows looked at cpu usage ram and page file 

 I do not know if this [article]("http://mylinuxexplore.blogspot.com/2012/10/ubuntu-1210-vs-kubuntu-1210-vs-xubuntu.html") is true or not but shows how hungry is ubuntu/unity compered to other interfaces

> **offgridguy said:**
> You might consider lubuntu for a lightweight system easy on resource.

thank you for the reply but My system is not that week and (i want search function like dash or windows search) i just do not like when system uses too much performance when it does not need to, that is why i started using ubuntu from 9.10 i loved how it used minimum resources


> **Cheesemill said:**
> To install Gnome Shell on Ubuntu 12.10 it's just the same method as previously:
```
sudo apt-get install gnome-shell
```And yes, everything that works with Unity will work with Gnome Shell as well (PPA's etc).

I wouldn't say that it's really any lighter although I've not done any proper testing, they are both modern DE's designed for recent hardware.

 thank you for the answer it is really helpful 

but as i mentioned and i base my opinion on this [article]("http://mylinuxexplore.blogspot.com/2012/10/ubuntu-1210-vs-kubuntu-1210-vs-xubuntu.html") even kde takes less resources and as far as i know kde should be performance hog

---

### Post by Frogs Hair on 2012-10-21
I am using the Gnome Shell and the XFCE session along with Unity on 12.10. I have installed these from the official repository as I did in 12.04 .  The gnome shell doesn't use Compiz so may be less resource hungry . There is a Gnome Shell Ubuntu version at the link. [http://www.webupd8.org/2012/10/prefer-gnome-shell-download-ubuntu.html](http://www.webupd8.org/2012/10/prefer-gnome-shell-download-ubuntu.html)     

If resources are a problem Lubuntu and Xubuntu would be good choices, Lubuntu being the lighter of the two.  Both are more traditional style desktops. There is Gnome _Testing _PPA which includes the latest changes and I choose not to use it because of potential problems including compaibility .

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by sgage on 2012-10-21
> **Chelidze said:**
> I love Ubuntu but i do not like one thing about it, system usage, i think it uses to much system resources, my windows 7 uses less resources then Ubuntu 12.10 
so what i want to know if any one knows, does [ubuntu]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10") with gnome on it takes less resources then ubuntu ??
I apologize about this question, it might sound silly for some users/people but i am new to linux and this question accrues if I install [ubuntu]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10") with gnome on it use the same terminal commands (apt-get, and if I am able to install ppa on it from launched ) 

and can I install gnome 3 on ubuntu 12.10 as I had the ability  on ubuntu 12.04

 Thank you for your time

I do not believe that Windows 7 uses less resources than 12.10 by any possible metric. On my machine, it uses a LOT more, nearly twice as much RAM just to start up. What makes you think otherwise?

I find Unity uses more RAM than Gnome Shell, and Gnome Classic uses much less than either. Simply logging in and starting System Monitor, I see:

Unity - ~510 MB
Gnome Shell - ~450 MB
Gnome Classic - ~380 MB

This is obviously not a real scientific analysis or anything, but I run the monitor all the time, and this sort of ratio seems to hold for a similar mix of apps running on each desktop. Perhaps someone can point us to a slightly more formal study of the matter.

Windows 7 Home Premium 64-bit dependably uses ~900 MB just to boot.

---

### Post by offgridguy on 2012-10-21
> **Chelidze said:**
> started system monitor on ubuntu looked as how it uses memory cpu swap 

started task manager on windows looked at cpu usage ram and page file 

 I do not know if this [article]("http://mylinuxexplore.blogspot.com/2012/10/ubuntu-1210-vs-kubuntu-1210-vs-xubuntu.html") is true or not but shows how hungry is ubuntu/unity compered to other interfaces


Thank you for this Cheldize, you have helped me a lot .

---

### Post by sgage on 2012-10-21
> **offgridguy said:**
> Thank you for this Cheldize, you have helped me a lot .

The table showing Unity using 20+% CPU is absurd. They must have caught it running the tracker daemon or something.

That is not a particularly scientific comparison.

---

### Post by Chelidze on 2012-10-21
> **sgage said:**
> I do not believe that Windows 7 uses less resources than 12.10 by any possible metric. On my machine, it uses a LOT more, nearly twice as much RAM just to start up. What makes you think otherwise?

I find Unity uses more RAM than Gnome Shell, and Gnome Classic uses much less than either. Simply logging in and starting System Monitor, I see:

Unity - ~510 MB
Gnome Shell - ~450 MB
Gnome Classic - ~380 MB

This is obviously not a real scientific analysis or anything, but I run the monitor all the time, and this sort of ratio seems to hold for a similar mix of apps running on each desktop. Perhaps someone can point us to a slightly more formal study of the matter.

Windows 7 Home Premium 64-bit dependably uses ~900 MB just to boot.

 Yes from out of the box no doubt that ubuntu is using less memory then windows, but after personalizing both systems a bit windows uses 1.18 gb and ubuntu 1.34 gb this is when some apps are lunched like web browser video or image editor and so on so I know linux uses swap and ram differently from windows but still i feel it uses more recourse than ubuntu 12.04 did

---

### Post by Cheesemill on 2012-10-21
> **Chelidze said:**
> Yes from out of the box no doubt that ubuntu is  using less memory then windows, but after personalizing both systems a  bit windows uses 1.18 gb and ubuntu 1.34 gb this is when some apps are  lunched like web browser video or image editor and so on so I know linux  uses swap and ram differently from windows but still i feel it uses  more recourse than ubuntu 12.04 did

You can't really make a valid comparison like that. Linux and Windows handle memory in completely different ways.

Unused memory is wasted memory, it can be used to help speed up the system by caching regularly used files. Because Linux does this and Windows doesn't then you are bound to get a higher memory usage using Ubuntu. This is a good thing.

---

### Post by offgridguy on 2012-10-21
> **sgage said:**
> The table showing Unity using 20+% CPU is absurd. They must have caught it running the tracker daemon or something.

That is not a particularly scientific comparison.
Perhaps not, but this is not what I was thinking of specifically anyway.
Chaldize has helped make up my mind to buy a 4 OS cd install pack from ebay that
includes ubuntu,kubuntu , lubuntu and xubuntu,  Ubuntu I don,t need  as i already have it
but I wanted to try something else.

---

### Post by offgridguy on 2012-10-21
> **Cheesemill said:**
> You can't really make a valid comparison like that. Linux and Windows handle memory in completely different ways.

Unused memory is wasted memory, it can be used to help speed up the system by caching regularly used files. Because Linux does this and Windows doesn't then you are bound to get a higher memory usage using Ubuntu. This is a good thing.

Could you expand on this a bit for someone like me, not all that computer literate ?

---

### Post by sgage on 2012-10-21
> **Cheesemill said:**
> You can't really make a valid comparison like that. Linux and Windows handle memory in completely different ways.

Unused memory is wasted memory, it can be used to help speed up the system by caching regularly used files. Because Linux does this and Windows doesn't then you are bound to get a higher memory usage using Ubuntu. This is a good thing.

This is the point, really. More important to me than memory footprint is responsiveness. Some systems are better at caching and such, and are very snappy. Yes, the use more RAM.

Windows is rather agressive about using RAM adaptively. When you first boot Windows, it's a slug for a few minutes while it prefetches and runs scheduled tasks and such. The longer you use it, the faster it becomes as chunks of code and data are cached and ready for action.

So simple comparisons are really not that useful. Fairly benchmarking these sort of things is notoriously difficult.

---

### Post by Chelidze on 2012-10-21
> **sgage said:**
> This is the point, really. More important to me than memory footprint is responsiveness. Some systems are better at caching and such, and are very snappy. Yes, the use more RAM.

Windows is rather agressive about using RAM adaptively. When you first boot Windows, it's a slug for a few minutes while it prefetches and runs scheduled tasks and such. The longer you use it, the faster it becomes as chunks of code and data are cached and ready for action.

So simple comparisons are really not that useful. Fairly benchmarking these sort of things is notoriously difficult.

 But some times that is the problem for me I feels up ram and then it needs clean it and it takes time, 
back to the pint can you tell me how much ram does an x64 ubuntu uses out of the box ?? and if you can tell me how much other  flavors use??

---

### Post by sgage on 2012-10-21
> **Chelidze said:**
> But some times that is the problem for me I feels up ram and then it needs clean it and it takes time, 
back to the pint can you tell me how much ram does an x64 ubuntu uses out of the box ?? and if you can tell me how much other  flavors use??

I did in an earlier post. But the point is it doesn't matter 'out of the box'. What matters is how it adapts resource usage over the course of your using the machine with your collection of programs and work habits.

I have 4 GB of RAM on my machine. I want to see it used. Lots of RAM being used means lots of caching and prefetching and whatnot. I don't want to slowly load the same code off of disk over and over again - I want it to be stashed in RAM. I don't think I've ever seen my RAM usage go over 2 GB using any Linux. I've pushed 3 with Windows.

Right now, I'm running Gnome Shell. This session is probably an hour old. I've got Firefox running with 6 tabs, a couple of OpenOffice documents open that I'm working on, Rhythmbox playing some streaming music, nautilus open with 2 panes, and the System Monitor. I'm using 745 MB of RAM. 0 swap - I almost never see swap being used, and when it is, it's not because I'm anywhere near out of RAM.

Naturally, the optimum deployment of RAM by the memory management system will vary by use case - do you edit enormous videos? Do you play demanding games? Do you surf the web with an absurd number of tabs open on your browser? Do you... whatever.

How much RAM do you have? What do you mostly use your computer for?

---

### Post by Cheesemill on 2012-10-21
This might explain it a bit better:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by offgridguy on 2012-10-21
> **Cheesemill said:**
> This might explain it a bit better:

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Thank you Cheesemill, yeah this helps a lot.

---

### Post by Cheesemill on 2012-10-21
In case you are interested, I've just done a fresh install myself of Ubuntu 12.10 and added Gnome Shell. Here are my memory stats for Unity and Gnome Shell respectively:
```
rob@raring:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7723       1052       6671          0         31        567
-/+ buffers/cache:        452       7271
Swap:         7628          0       7628
```
```
rob@raring:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          7723        704       7019          0         54        286
-/+ buffers/cache:        363       7360
Swap:         7628          0       7628

```

So on a clean installation Unity is using 452MB and Gnome Shell is using 363MB.

---

### Post by Chelidze on 2012-10-21
> **sgage said:**
> I did in an earlier post. But the point is it doesn't matter 'out of the box'. What matters is how it adapts resource usage over the course of your using the machine with your collection of programs and work habits.

I have 4 GB of RAM on my machine. I want to see it used. Lots of RAM being used means lots of caching and prefetching and whatnot. I don't want to slowly load the same code off of disk over and over again - I want it to be stashed in RAM. I don't think I've ever seen my RAM usage go over 2 GB using any Linux. I've pushed 3 with Windows.

Right now, I'm running Gnome Shell. This session is probably an hour old. I've got Firefox running with 6 tabs, a couple of OpenOffice documents open that I'm working on, Rhythmbox playing some streaming music, nautilus open with 2 panes, and the System Monitor. I'm using 745 MB of RAM. 0 swap - I almost never see swap being used, and when it is, it's not because I'm anywhere near out of RAM.

Naturally, the optimum deployment of RAM by the memory management system will vary by use case - do you edit enormous videos? Do you play demanding games? Do you surf the web with an absurd number of tabs open on your browser? Do you... whatever.

How much RAM do you have? What do you mostly use your computer for?

How i use my operating systems is a bit hard on them 
for example

I have chrome browser opened with around 10 to 20 tabs but i try not to open more then 5 tabs that have flash content, i have couple of folders opened with multimedia on them I have either opened photoshop with wine or kdenlive or both,(sometimes video game running in wine) vlc app is opened mail client. so wean i do this i really do not want os to take much resources that is why i started using linux because it was easy on system.


> **Cheesemill said:**
> In case you are interested, I've just done a fresh install myself of Ubuntu 12.10 and added Gnome Shell. Here are my memory stats for Unity and Gnome Shell respectively:
```
rob@raring:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7723       1052       6671          0         31        567
-/+ buffers/cache:        452       7271
Swap:         7628          0       7628
```
```
rob@raring:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          7723        704       7019          0         54        286
-/+ buffers/cache:        363       7360
Swap:         7628          0       7628

```

So on a clean installation Unity is using 452MB and Gnome Shell is using 363MB.



you installed os wow what can i say thank you so much, really appreciated it 



can anyone tell me how kde compares to gnome ??

---

### Post by offgridguy on 2012-10-21
chelidze; My apologies, i just realized I have been misspelling your username.

---

### Post by sammiev on 2012-10-21
> **Cheesemill said:**
> In case you are interested, I've just done a fresh install myself of Ubuntu 12.10 and added Gnome Shell. Here are my memory stats for Unity and Gnome Shell respectively:
```
rob@raring:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7723       1052       6671          0         31        567
-/+ buffers/cache:        452       7271
Swap:         7628          0       7628
```
```
rob@raring:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          7723        704       7019          0         54        286
-/+ buffers/cache:        363       7360
Swap:         7628          0       7628

```

So on a clean installation Unity is using 452MB and Gnome Shell is using 363MB.

I have been using Gnome Shell for some time now as my preference. I should try Unity again and compare. Thanks for your post.

---

### Post by Cheesemill on 2012-10-21
> **Chelidze said:**
> you installed os wow what can i say thank you so much, really appreciated it
I didn't just do it for you, I was about to install anyway to set up my box for testing 13.04 :)

---

### Post by Chelidze on 2012-10-21
> **Cheesemill said:**
> I didn't just do it for you, I was about to install anyway to set up my box for testing 13.04 :)

any way thank you :)

> **offgridguy said:**
> chelidze; My apologies, i just realized I have been misspelling your username.

no problem :)

 Any ides how much kubuntu is using memory

---

