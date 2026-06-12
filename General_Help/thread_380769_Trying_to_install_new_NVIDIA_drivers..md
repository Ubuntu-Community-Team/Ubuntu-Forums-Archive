---
title: "Trying to install new NVIDIA drivers."
date: 2007-03-10
forum: General Help
---

### Post by KevinAlaska on 2007-03-10
I am very very very SORRY if I didnt find this in the forum.  I can't barely think right now and feel that I am about to have a break down.  But this has nothing to do with my computer issue.  I just want ONE thing to go right today and I would love it if this was it for me.  Again sorry if I am too lame to find the help needed online.  I TRY not to post anything with out researching it first.  But researching is just NOT going to work for me it seems.

But I am new to the Linux world,  I have messed with FC 6 and enjoy it.  I had on that disro setup to just load into a run level 3 with /etc/inittab set to 3 (god I hope I do not have 5 and 3 turned around).  so then I loaded in root and ran the command 'telinit 5' to boot into X.  

This allowed me to load the drivers etc when I needed (not that I have the experience in loading all kinds of drivers).  Being in as root did at let me do the 'sh NVIDIA-Linux-blah blah blah' to install the nVidia drivers.

So what is different here with ubuntu?  I just wish there was more standardization.  I know there are good reasons for this.  Just makes it hard for a newbie like myself.

Well I hope this is an easy one to solve.  I need to go lay down and take a nap for a few.  My head feels like its about to burst.

thank you again everyone and I hope everyone is doing VASTLY better then I am now.

Cheers,

Kevin in Alaska

PS I hope this all was easy to understand.  sorry if not.  best wishes.

---

### Post by aa.ivanov on 2007-03-10
Sorry if my answer is useless for you, but I had some problems trying to figure out what your post was about.

First. Ubuntu should work out-of-the-box on nvidia cards. When you need 3d, tv-out and such extras - you can follow this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Fedora is a puristic distro and does not provide any non-FOSS software. That's why you need to use the nvidia-installer for installing nvidia's drivers. Ubuntu's policy is to provide non-FOSS software if no open source alternative exists. Furthermore Ubuntu has a much bigger collection of apps in it's repositories compared to Fedora.

Starting in text terminal is not needed if you intend to use a graphical desktop most of the time. Leave it to boot in graphical and if anything bad happens with the X window system you'll be dropped to text mode.

Second: If you mean 'unification' by what you're calling 'standardization', I should disappoint you - that's NOT a good thing. One of the most exciting things about the many linux distros is the variety and the freedom to choose.

---

### Post by Famicommie on 2007-03-10
I think I understand most of what you're getting at, Kevin.

Ubuntu, by default, has the ability to log in as root turned off. This is mostly for us noobs own good :)

When you need to run root commands, begin the command with "sudo". If you have to type "sudo" to do something, it's like telling the system "don't worry, I know what I'm doing".

An excellent program that I have had a lot of good experience with is [Automatix](http://www.getautomatix.com/). One of its features is an automated nVidia driver install. There are also many other useful applications that Automatix can install, and in some cases I find that the Automatix installs work better than repository installs. Azureus, for instance, seems to work much better when installed via Automatix.

I agree with you that linux needs some more standardization between distros. It is *very* frustrating when what seems like a simple task on one distro simply doesn't work on another. Linux is still maturing to that point, I think.

Standardization is different from unification aa.ivanov, because it means that things should work well together, not be combined.

I sincerely hope that you feel better after your nap, Kevin :D

---

### Post by al1b1 on 2007-03-10
also you might want to try the envy script made by alberto milone (google it)

---

### Post by jem7v on 2007-03-10
I believe I know what you're talking about.
In order for the NVidia script to work properly you have to have your X server turned off, eh?  Well, sadly the telinit method won't shut if off in Ubuntu.  Instead, you run the following command:
```
sudo /etc/init.d/gdm stop
```
...and then run the NVidia install script.  Afterward, to restart your X server, do this:
```
sudo /etc/init.d/gdm restart
```

If the installer gives you heck about dependencies, try using Alberto Milone's Envy script because it does a good job installing all the dependencies for the driver to compile.  It usually does a good job installing the driver too, except on a few older NVidia cards like the Geforce2 MX, for which it chooses the wrong driver. :) [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


P.S. And oh yes.  Any time you want to run a command as root in Ubuntu linux, you just preface it with **sudo**, as you can see in the example above.  That way you don't have to log in as root and you don't run the risk of doing something that might ruin your system without realizing it while you're root (because if you don't know it's going to be dumb to do, you probably won't have run the command with sudo).

---

### Post by Azakus on 2007-03-10
I would advise against Envy 9.X because I had massive problems with it (restricted modules didn't like the newest nvidia driver). Envy 0.8X works very well though. Follow the instructions on the site and it will work well. Basically, log out of Ubuntu, press Ctrl+Alt+F1 then sudo envy.

---

### Post by KevinAlaska on 2007-03-10
Well after much needed sleep and down time I feel a hell of a lot better thanks.

I want to thank each and everyone who posted here.  Lots of great information.  Not just great information but well written information.

I can not wait to try it out and see what happens.  I will post back what I did and what happened.

Well off I go to try it.  Wish me luck!  [-o< 

Sincerely,

Kevin in Alaska

---

### Post by r4ik on 2007-03-10
As advised go for Envy.

---

### Post by KevinAlaska on 2007-03-13
Well I ended up picking a solution that seemed easy and it was.  Well it was easy after I did a reinstall of ubuntu 6.10.  I ended up using Automatix2 for amd64.  It works flawlessly as said.  It was pretty cool because I just needed to enter the text in the terminal.  It didn't mention that I was supposed to enter the password but that was common sense I guess.  Below are the commands that it asked for in six steps.

1) echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/source.list

This is where the password was asked but they failed to mention that it might be needed.

2) wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)

3) gpg --import key.gpg.asc

4) gpg --export --armor 521A9C7C | sudo apt -key add -

5) sudo apt-get update

6) sudo apt-get install automatix2

that was it.  It installs an icon under "system tools" and when you run it, it also asks for a password to start.

But I have one question I hope someone here might know, where does the list of applications it lists for downloading come from and how does it differ from the "Add/Remove..." that is listed at the bottom of the applications menu in Gnome?

I selected the nVidia drivers listed and rebooted the system.  that was that.  Easy.  I know others here have suggested other methods of installing drivers...  Is there a reason for this?  I would really like to know because I really really wish to understand Linux as BEST as possible.

Thank you EVERYONE for your help and time on this issue.  Cheers!

Best wishes

Kevin in Alaska :popcorn:

---

### Post by jem7v on 2007-03-13
Some people don't like Automatix for a variety of reasons that sometimes conflict with each other.  I just don't use it because it seems extraneous to me.  You can find plenty of opinions about Automatix vs EasyUbuntu in these forums if you look.

The list of applications is basically a list of what the Automatix developers decided are the most popular, commonly installed applications in Ubuntu.  Most of the time, the packages are installed from the same places in the same way as they would be from the Add/Remove dialogue... it's basically just a shorter list of things lots of people commonly use instead of a complete list.

Hence why I use Add/Remove and Synaptic instead of installing yet another program to do it for me when I don't need to.  Also, the reason I install drivers manually is so I know How they're installed... if I let a script do it for me, I don't really know what it's doing.  (And my card is sort of fussy, so a lot of scripts choose the wrong driver for it.)

---

### Post by KevinAlaska on 2007-03-13
Well I think this thread is a closed deal.  thank you for that good information on comparing Automatix and other forms of updating.  Well for this stage in the ball game for me I think I choose the right format for the time being.  As in the Windows world (which I consider myself maybe upper intermediate levels) I am comfortable on how to fix MOST problems.  I read on here what someone wrote about being hard for some who is good with windows coming to Linux has a harder time then someone who does not know windows coming to Linux.  This is very true because of how I can get discouraged at all of a sudden NOT knowing how to do things.  Just because Linux has a monitor, keyboard and a mouse means that its NOTHING close to Windows (as I know you know already).  

I am thinking about doing that Linux From Scratch method to get used to Linux first.  Sounds like a good way to learn what Linux is on the inside.  I guess if you have any thoughts let me know but thank you EVERYONE again for the help.

Best wishes

Kevin in Alaska

---

