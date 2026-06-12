---
title: "Guitar amp"
date: 2007-12-11
forum: General Help
---

### Post by rkrash3423 on 2007-12-11
Hey all, not sure if this is the right place to post this. anyway, anyone know if there is a guitar amp program similar to Amplitube for windows on linux? I was using that for my guitar in windows and want to switch to linux completely but can't live without that prog. I tried installing it with wine with no success....

---

### Post by matthewcraig on 2007-12-11
This is a swell place to post the question.  Could you elaborate what you are trying to do?  Are you talking about a real guitar amplifier?

---

### Post by rkrash3423 on 2007-12-11
Well yeah kind of, go here [www.amplitube.com](www.amplitube.com) click on products and check out amplitube 2 you'll see what I mean.... It's a virtual guitar amp and effects modeling.

just want a prog like that in linux. I installed it with wine but when I click on the icon it just never opens...

---

### Post by matthewcraig on 2007-12-11
Sorry, I don't click on random links from forum messages any more.  I've seen too many mind-scarring images.  You'll have to explain the software here.

---

### Post by rkrash3423 on 2007-12-11
ok? just google amplitube then?! it's a legit link and prog, great prog actually, but don't take my word for it, google works great. better yet jsut type the link into your browser....

for description see previous post....virtual gutar amp with effects modeling....

---

### Post by Talos82 on 2007-12-11
I was just searching for something like this. I've found creox in the repositories, put I haven't been able to work with it. I gets me an error message.

Update: Creox also needs "Jack" to run. Install jackd from the repos.
You also have to run the jack server and creox as root.

According to [this]("https://answers.launchpad.net/ubuntu/+source/creox/+question/9018"):
>sudo jackd -d alsa& {This runs the JACK daemon in the background (don't forget the '&'),
                                              and 'hooks' it to the ALSA sound device}
>kdesudo creox& {Runs the creox application}

The error message is gone but I still get no sound..

---

### Post by rkrash3423 on 2007-12-11
Thanks for the info, I'll try it out and let u know how it goes for me....still no luck for me getting amplitube to run. really sucks cause it's a kick a$$ prog. it opens and says loading but closes right away, I have that problem with just about every windows program I try to load using wine, I've only had about 2 or 3  windows progs, out of probably 20, install and run successfully. I think I'm gonna try a virtual machine, but that was already pretty laggy on my machine last time I tried, so I highly doubt it's gonna run a virtual amp very well....we'll see. can't really expect to get much help with amplitube running here though as the prog is about $400, unless ur good like that....

---

### Post by rkrash3423 on 2007-12-11
Yep, so far I have the same problem. I can hear my guitar regardless through the input on my sound card, but thats a gimme, and obviously I want to be able to control the effects. I believe this probably has something to do with jackd. I also tried to install Adour since I saw it in ubuntu studio, but when I try to open it I get an error saying it cannot connect to "Jack" and lists reasons y, "jack may not be running or may be running as root", etc. So the question is, how do u run jackd under a normal user? I seem to be able to get jackd running as root, but get the same error in creox and adour regardless of running under normal user or root. idk, maybe I'll just give ubuntustudio a try since it seems to be already set up for that.... Any thoughts?

---

### Post by rkrash3423 on 2007-12-11
y does everything in linux have to be so difficult? I wish it wasn't so pretty!

---

### Post by Whiffle on 2007-12-11
you should need to run either one of those with sudo. 

[http://ubuntuforums.org/showpost.php?p=706654&postcount=16](http://ubuntuforums.org/showpost.php?p=706654&postcount=16)

---

### Post by rkrash3423 on 2007-12-11
Sweet! thanks, hope this works.

---

### Post by rkrash3423 on 2007-12-11
nope doesn't work for me :( I think thats way out of date....

---

### Post by rkrash3423 on 2007-12-11
Yesssss! Well I finally went and installed ubuntu studio. Absolutely awesome. I was about to give up on linux. It appears to have everything I was looking for installed by default, creox, adour, hydrogen, jack, etc. awesome, awesome, awesome. Highly recommended. Wish I hadn't waited so long on this one. Props to the ubuntu studio team. Just hope it's not a pain to set up compiz since it's not installed by default like the standard ubuntu 7.10....

---

### Post by rkrash3423 on 2007-12-11
Well compiz setup was as easy as can be. I have an ati card so I just installed xserver-xgl, compiz, compiz settings manager, enabled the restricted driver, reboot, and in appearance settings on the effects tab set effects to custom....bingo bango ready to go. I would go as far as to say that ubuntu studio is a better alternative to standard ubuntu regardless of what type of desktop environment u want. u can do a fresh clean install with minimal apps cluttering up your system, or select from an array of cool, useful apps, u have no options in standard ubuntu. the setup was faster and also had none of the problems I experience with standard gutsy like the long initial boot time due to the splash screen being set to the wrong resolution, which apparently is happening to the majority of people installing gutsy, (installing startupmanager after initial install and changing the splash resolution to 1024x768 is the easiest way to fix this), everything was working perfectly out of the box and I think it's packaged better, also the standard theme is nicer looking then standard gutsy even though I changed all that anyway, but nicer nonetheless. This is what I'll be using and recommending from now on, highly recommended!! if anyone cares that is!

---

