---
title: "how to get updated software question"
date: 2015-01-20
forum: General Help
---

### Post by matt18 on 2015-01-20
I have a question that a few users want me to ask. I have been letting some people try out ubuntu and so far they like it, they just have a question about updating software

Here is the question.

We are running 12.04. In the ubuntu software center, the version of libreoffice is 3. The ersion of gimp is 2.8 but not the newest version as well. 

How do we get updated software from the software center with out updating to the newest LTS or using the funky commands to install stuff. (remember they are basic users and dont understand CLI)?

They also want to know, if you cant get updated software from the center, why is it built that way? why doesnt the ubuntu center offer current and up to date software? Does it not have a connection to the servers to get the newest updates?

thanks

They all so far like ubuntu and are excited to try it out, they just want to ensure they can get up to date versions of things like Pitivi, libreoffice, gimp and etc with out having to add the repos and then using the cli. Totally understandable from a users point of view.

thanks for the input guys

---

### Post by newbie-user on 2015-01-20
To get the absolute latest versions, you'd have to go to the software developer directly, as is the case with any operating system. Otherwise, at least get a newer version of Ubuntu, which will have newer versions of all software. 

Regarding adding repos, you can do this directly in the GUI, no need to use the command line. For basic uses, there is no need for the command line. Of course, if you want to tinker under the hood, the CLI is ready and waiting..

You might want to warn the users about using the absolute latest versions, as they might break things. It's generally a good idea to wait on upgrades until you know for sure that it's been tested thoroughly and works properly in your distribution of choice.

---

### Post by matt18 on 2015-01-20
Ahh, so the ones in 12.04 were considered stable. So while they were testing libreoffice 4.3 to make sure it was stable, it was not available until testing was complete. So upgrading to each new LTS allows the software center to get the newest stable releases? 

How do i find out what current version of a particular software is available in 14.04? such as pitivi. I have a few users who are wnating to test that app out but have heard horid stories of the verison(0.15) in 12.04

Thanks

---

### Post by fantab on 2015-01-20
If you are using 12.04 then the software you get from [Ubuntu Repositories]("http://with out updating to the newest LTS or using the funky commands to install stuff.") is the one tested to work with 12.04. 
12.04 is an LTS version, it is supposed to be stable not latest. However, most software on 12.04 will be latest, for instance, your browser.
LTS versions are released every two years... the latest is 14.04 released in April of 2014 (which should explain the version numbering)... however the latest ubuntu is 14.10.
14.10 has all the latest versions of software.

If you want to run the latest software on 12.04 then you can't do it wihout 'using the funky commands to install stuff'. In other words, you have to be more than a 'basic' user to manage running 'unofficial' versions.

The best option for a 'basic' user is to upgrade regularly to the latest Ubuntu, either LTS or otherwise, to have latest software versions.

---

### Post by kerry_s on 2015-01-20
some updated software can be gotten using ppa's

---

### Post by matt18 on 2015-01-20
Interesting. i just learned more about the word stable than i knew before haha. Ok, so with all that being said, why cant the ubuntu software center allow the newer versions of software to be added to it? I mean, if libreoffice 4.x is included in the LTS of 14.04 and works, should it not be able to work on 12.04? Dont most apps that work in 14.04 work in earlier versions of linux?

Ok, next question from someone else. If LTS is released every 2 years, how can they take advantage of the non LTS versions that come out every so offten? I mean the update manager does not say upgrade to 13.10 in 12.04. How can they upgrade to a newer version of ubuntu, that may have newer software? will they have to use the command line to do so?

Thanks for answering their questions. I am a network engineer and i dont always use the user stuff. I just need a basic gui and a cli haha. They are just used to windows and mac based software apps asking if they want to update their software to the newest version haha.

---

### Post by matt18 on 2015-01-20
> **kerry_s said:**
> some updated software can be gotten using ppa's

Interesting. Is there a general approach for this method? 

thnaks

---

### Post by fantab on 2015-01-20
In your update-manager in LTS looks only for next LTS release and will inform you when its available. You must change the settings in update-manager to look for 'all' versions and not just LTS.
Upgrading from 12.04 to 12.10 or 13.04 or 13.10 is not possible because ver. 12.10-13.10 have reached their [EOL -End of Life]("http://www.ubuntu.com/info/release-end-of-life")... no support anymore. 
The best is to install the latest version and keep upgrading it to the next release.

> If LTS is released every 2 years, how can they take advantage of the non LTS versions that come out every so offten?
You will have to pick a side (LTS or Regular) and commit. 
I upgrade my LTS every two years, though an LTS is supported for 5 years since its date of release.
I also have 'Regualar' Ubuntu on another partition (a lot of us here do) and dual-boot.

LTS means Long Term Support.... and its not from Debian 'stable'. Ubuntu is built from Debian 'testing', LTS or otherwise.
Latest and stable don't always go together. Also its not just the individual apps, there are a loads of dependent libs and dependencies to satisfy to install a latest software, if it depends on latest library versions.
If one version of an app depends on, say Qt4 then the latest version of the same app may need Qt5. If 12.04 has, say Qt4 then the latest app will not work, if you change Qt4 to Qt5 then apps depending on Qt4 will not work and so on...

---

### Post by kerry_s on 2015-01-20
> **matt18 said:**
> Interesting. Is there a general approach for this method? 

thnaks

you just google for the ppa for the software you want, example: libreoffice ppa
first 1 in search results:
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)
gimp first 1 in search results:
[https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp](https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp)
etc...

add the ppa & you can update those software just the same as before.

---

### Post by newbie-user on 2015-01-20
> **matt18 said:**
> Interesting. i just learned more about the word stable than i knew before haha. Ok, so with all that being said, why cant the ubuntu software center allow the newer versions of software to be added to it? I mean, if libreoffice 4.x is included in the LTS of 14.04 and works, should it not be able to work on 12.04? Dont most apps that work in 14.04 work in earlier versions of linux?
The software center is set to look for a specific Ubuntu release. In your case, Ubuntu 12.04 Precise Pangolin. If you look at your repository list, you'll see that it looks for precise. For example: *deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main*. If you change the release, for example from precise to trusty, you'll pull newer software meant for the newer release. With that said, the newer software may have dependencies (other required software packages) that do not exist in the older release or require newer versions of the dependencies. It's best to understand dependencies before trying to install the latest and greatest software on an older release (kinda like how some Windows 7/8 software won't work on XP).

> Ok, next question from someone else. If LTS is released every 2 years, how can they take advantage of the non LTS versions that come out every so offten? I mean the update manager does not say upgrade to 13.10 in 12.04. How can they upgrade to a newer version of ubuntu, that may have newer software? will they have to use the command line to do so?
Generally, LTS will only upgrade to a newer LTS unless you change some settings. See the following link.
[ http://askubuntu.com/questions/203184/upgrade-to-12-10-from-12-04-not-available-in-update-manager]("http://askubuntu.com/questions/203184/upgrade-to-12-10-from-12-04-not-available-in-update-manager")

---

### Post by matt18 on 2015-01-21
hmm, ill have to let them know. ill give it a shot to. 

I know that my update manager doesnt like some ppas cuz then it says partial upgrade available and what not. haha

---

### Post by deadflowr on 2015-01-21
Did you ever fix the debian.scribus repo error you were getting?
[http://ubuntuforums.org/showthread.php?t=2261398&p=13210513#post13210513](http://ubuntuforums.org/showthread.php?t=2261398&p=13210513#post13210513)

Busted repository entries tend to make the update manager turn quickly into an update mangler...

---

### Post by lisati on 2015-01-21
It was always my understanding that "S" in LTS referred to "Support", as in "Long Term Support" meaning that support for the LTS releases have always been supported longer. :D

---

### Post by coffeecat on 2015-01-21
> **lisati said:**
> It was always my understanding that "S" in LTS referred to "Support", as in "Long Term Support" meaning that support for the LTS releases have always been supported longer. :D

Indeed it does. :)

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

> The Long Term Support (LTS) version of the Ubuntu operating system for desktop PCs and laptops

---

### Post by matt18 on 2015-01-21
> **deadflowr said:**
> Did you ever fix the debian.scribus repo error you were getting?
[http://ubuntuforums.org/showthread.php?t=2261398&p=13210513#post13210513](http://ubuntuforums.org/showthread.php?t=2261398&p=13210513#post13210513)

Busted repository entries tend to make the update manager turn quickly into an update mangler...

Yes and no. If i take out the libreoffice ppas in update manager, then all is fine, but if i want to update libreoffice each time a new stable release is out, i cant use those ppas. when i try to hit install with only the libreoffice updates checked, it is grayed out and wont let me haha

im still trying to get this to work.  haha

thanks

---

### Post by matt18 on 2015-01-21
also on a side not, they asked how to change the folder color from orange to something else, i said i dont think you can unless you install something. What do they have to install to change folder colors and menu colors and what not? thanks. Oh it might help to know that i installed gnome and cairo dock haha

---

