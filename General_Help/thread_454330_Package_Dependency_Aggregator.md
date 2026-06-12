---
title: "Package Dependency Aggregator?"
date: 2007-05-25
forum: General Help
---

### Post by xuancongwen on 2007-05-25
Hi,

I was wondering if there was a neat little web-app that I can use to download all the packages required to install a package (as in, download all packages when I type in "sudo apt-get install sun-j2sdk1.5").  The reason I ask this is because I am attempting to install a server on an offline Ubuntu 7.04 box, and at present, the organization I work is very strict on what goes onto the network (internet security is very, very tight here).  At present, there are no Debian or Ubuntu boxes connected to the network for me to do an aptitude download of packages so I can transfer them over.

If anyone can help me with this, it would be greatly appreciated.  Thanks!

-Sam

PS - Yes, I have mucked around at the package listing on the ubuntu website, and yes, I am aware that they list all dependencies and such there, but I'd like an easier way because I have quite a bit to install.

---

### Post by reacocard on 2007-05-25
I don't know of any apps, but you could take an Ubuntu livecd, boot it on a computer with internet, install the packages on it in live mode, then just copy the contents of /var/cache/apt/archives onto a flash drive or something. That'll get you all of them, then you can just copy the files into the same location on your offline box and install with apt as normal.

---

### Post by xuancongwen on 2007-05-25
Unfortunately, the network is set up in such a way that should I do that, it will set off so many warning flags that I may quite literally be arrested :P.  I did think of that, but I checked with a system administrator, and he said that unfortunately, the help desk had not analyzed the security of a liveCD OS just yet (since the liveCD is unable to receive updates from ubuntu updater), so I'm limited to either the dependency website at the moment.  I suppose if all else really fails, I would have to get the packages on my own Ubuntu box at home, but uh...this is embarassing, but I am on a 56k :(

Any other suggestions?  Thanks a lot!  I am actually pretty pleased at how active these forums are :)  it makes me so happy!

---

### Post by reacocard on 2007-05-25
> **xuancongwen said:**
> Unfortunately, the network is set up in such a way that should I do that, it will set off so many warning flags that I may quite literally be arrested :P.  I did think of that, but I checked with a system administrator, and he said that unfortunately, the help desk had not analyzed the security of a liveCD OS just yet (since the liveCD is unable to receive updates from ubuntu updater), so I'm limited to either the dependency website at the moment.  I suppose if all else really fails, I would have to get the packages on my own Ubuntu box at home, but uh...this is embarassing, but I am on a 56k :(

Any other suggestions?  Thanks a lot!  I am actually pretty pleased at how active these forums are :)  it makes me so happy!

So you can't get security updates for the livecd because it hasn't been updated? :-k

Apt is really the only way I know of to automatically handle the depends. You may just have to do it at home and let it run overnight or something.  Or ask a friend if you can use their computer for it. :p

---

### Post by Soybean on 2007-05-25
I believe Synaptic can use the Ubuntu CD as a repository. This will let you install a lot of things (I'm not sure how many things, but probably a lot of the dependencies you'd need, at least), although of course they wouldn't be the latest version in a lot of cases.

---

### Post by reacocard on 2007-05-25
> **Soybean said:**
> I believe Synaptic can use the Ubuntu CD as a repository. This will let you install a lot of things (I'm not sure how many things, but probably a lot of the dependencies you'd need, at least), although of course they wouldn't be the latest version in a lot of cases.

There isn't that much on the cd actually, just a few extras. The livecds are nearly useless for this, since the main stuff isn't available, only extras. 

You might be able to get some off the 'server' install cd, but then you'd have to download the whole cd and you probably wouldn't get everything you need.

---

### Post by christhemonkey on 2007-05-25
I am in the process of writing such an application.
At the minute it is just a python script, but it works, you can get the package and all its dependencies.

Im working on a graphical frontend, but its not going so well...
Im also planning to release it with a .exe for windows as well.

I shall post back when i make an initial release (even if it is just a python script)

---

### Post by xuancongwen on 2007-05-25
Hey Chris,

That sounds like a great idea.  What are you writing the frontend in?  I may be able to help you out with development in my spare time if you need it and have a CVS or SVN repo.

In any case, I will probably set this work aside for a little bit since I'm too lazy to manually go trudging through the repositories.

By the way, I know it sounds silly (that I can't get updates because it won't allow my un-updated machine onto the network), but these are the kinds of paradoxes one lives by when working for certain organizations.  Another good example is that at present, I am unable to log onto the exchange server to change my username and password because I haven't taken a quiz to certify I have taken training.  However, in order for me to access that quiz online, I need to provide my exchange server username and password.

I swear to you, I couldn't make this stuff up if I tried.

-Sam

---

### Post by christhemonkey on 2007-05-25
I am writing frontend in pygtk+glade, but there are just a couple of things that seem to escape my grasp.

Such as;
why when i have a callback connected to a signal and 2 actions in the callback 
(one to update the frontend and *then* one to run a part of the backend)
does it not run them in the order they are written in?! 

(So it should update GUI then run backend but it just freezes until backend has finished running and then updates)

Very frustrating...


Anyway, i am just awaiting sourceforge approving my project then i should upload the command line alpha release.

---

### Post by xuancongwen on 2007-05-25
I've never used pygtk by I know that in c gtk libraries and gtkmm, you have to manually create ways to make your application thread safe.  In any case, good luck with that and I guess when you have your project up, pm me with the URL and I will try to join your project!  Thanks!

---

### Post by reacocard on 2007-05-25
> **christhemonkey said:**
> I am writing frontend in pygtk+glade, but there are just a couple of things that seem to escape my grasp.

Such as;
why when i have a callback connected to a signal and 2 actions in the callback 
(one to update the frontend and *then* one to run a part of the backend)
does it not run them in the order they are written in?! 

(So it should update GUI then run backend but it just freezes until backend has finished running and then updates)
Probably what you want to do is run the backend in a separate thread. Take a look at python's threading module, it's not hard. Also with them in separate threads you can give the GUI incremental updates on the progress.

---

### Post by christhemonkey on 2007-05-26
Ok, sourceforge hasnt got back to me yet, so hosting the files on my home server.

Single windows executeable is here:
[http://software.chrisbeagles.ath.cx/wubdependsv4/Single_Executable/wubdepends3.exe](http://software.chrisbeagles.ath.cx/wubdependsv4/Single_Executable/wubdepends3.exe)

With the source python+glade files here:
[http://software.chrisbeagles.ath.cx/wubdependsv4/Source/](http://software.chrisbeagles.ath.cx/wubdependsv4/Source/)

Enjoy!

(im aware that the application can look unresponsive, dont exactly know where the problem is, if someone wants to then they can advise)

Any comments or feedback appreciated.

---

### Post by xuancongwen on 2007-05-29
Hmmm, thanks for the links but they appear to be dead.  Can I get confirmation on that?

---

### Post by reacocard on 2007-05-29
> **xuancongwen said:**
> Hmmm, thanks for the links but they appear to be dead.  Can I get confirmation on that?

They work for me.

---

### Post by christhemonkey on 2007-05-29
They only work when my home server is online (although it has been on for the last week an a bit....?!), so if anyone wants to mirror... (hopefully will get a page on sourceforge soon so it wont matter)

Anyway please let me know any feedback/issues you have with the program.

---

### Post by xuancongwen on 2007-05-29
I'm sorry, I know why.  The network is blocking that particular site because it doesn't appear on the trusted domains server *sigh*.  Any luck with sourceforge?

PS - Like I said, security is tight.

---

### Post by christhemonkey on 2007-05-29
Not yet im afraid, they said it can take up to 2 business days to approve a project with today being the 2nd...
I shall let you know as soon as i find out.

In the meanwhile will putting a download on another host help?

---

### Post by christhemonkey on 2007-05-29
Ok there on mediafire.com hope that's approved for you:
[http://www.mediafire.com/?f1kzbgmmjj3](http://www.mediafire.com/?f1kzbgmmjj3)

And for the source:
[http://www.mediafire.com/?bpgz2oowiiz](http://www.mediafire.com/?bpgz2oowiiz)

---

### Post by christhemonkey on 2007-06-10
Sourceforge finally got back to me...

[http://sourceforge.net/projects/wubdepends/](http://sourceforge.net/projects/wubdepends/)

Enjoy!!

---

### Post by tonderai on 2008-07-02
This looks like a fantastic utility.

I am trying to use the .exe on a library Win2k computer to download packages for an offline ubuntu. However, whatever package or distribution I enter, wubdepends goes to "initialising" then after 4-5 minutes returns "package not found".

Any ideas?

---

