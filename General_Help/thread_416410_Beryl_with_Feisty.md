---
title: "Beryl with Feisty?"
date: 2007-04-21
forum: General Help
---

### Post by phoenixankit on 2007-04-21
This is my first time with ubuntu, and i'm downloading Feisty right now, and I wanted to know...does beryl come with feisty? or so i download it separately? If separately, from where? :confused: 
Thanks in advance

---

### Post by NikoC on 2007-04-21
Feisty comes with Compiz, but [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29") link might help you on your way to install Beryl...

Good luck

---

### Post by vishnumrao on 2007-04-21
> **NikoC said:**
> Feisty comes with Compiz, but [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29") link might help you on your way to install Beryl...

Good luck

I saw a few beryl packages in Synaptic. Isn't beryl already there in the ubuntu repos?

---

### Post by MrPyro321 on 2007-04-21
Open a Terminal window (Applications, Accessories, Terminal) and enter the following command:

**sudo gedit /etc/apt/sources.list**

Add the following line to the top of the text file that comes up for editing:

**deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main**

Save the file and quit. Now back on the command line, issue the following four commands, one at a time:

**wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -**

**sudo apt-get update**

**sudo apt-get install beryl beryl-manager emerald-themes heliodor beryl-manager**

**beryl-manager**


[Source]("http://www.pcworld.com/article/id,130923-c,linux/article.html")

---

### Post by jagogo on 2007-04-21
thanks i can finally try beryl

---

### Post by GSF1200S on 2007-04-21
> **phoenixankit said:**
> This is my first time with ubuntu, and i'm downloading Feisty right now, and I wanted to know...does beryl come with feisty? or so i download it separately? If separately, from where? :confused: 
Thanks in advance

I say this having had NO problems with Beyrl, but I might suggest holding off on Beyrl until you get to know Ubuntu a little better, I have read some nasty problems that people have had, and as a new user that could put a bad taste in your mouth. 

Like someone else said, Compiz comes with 7.04.. its supposed to have a lot of similarities.

I have a question here though.. I dont have Compiz on my 7.04. This is weird because I havent uninstalled it. Maybe its because I use Beyrl and compiz didnt install?

I dont mean to start to start a compiz vs beyrl war, but would it be smart to switch over? I remember people metioning that compiz is harder to install, but im guessing its more stable than beyrl (once again, ive had no problems) since they included it with 7.04.

---

### Post by phoenixankit on 2007-04-21
I'll stick with you advice gsf.

btw, that's a nice laptop you've got there...

---

### Post by GSF1200S on 2007-04-22
> **phoenixankit said:**
> I'll stick with you advice gsf.

btw, that's a nice laptop you've got there...

Kudos for holding off.. Your expeirence will be better. Make sure when you do try to run Beyrl/Compiz you have your video card drivers installed and working.

Yeah, considering I paid $1700 for the laptop, Im pleased. Its kind of cool that its a 15.4 inch too.. small but powerful. I lucked out with it, because at the time I wasnt really considering Linux. It just so happens that all of my hardware works well (Nvidia, Intel, Atheros, etc) with Linux, so I have the luxury of a fully functional laptop.

Too bad it will be average in 6 months... lol

---

### Post by wgscott on 2007-04-22
Go for it.

[IMG]http://diablo.ucsc.edu/~wgscott/debian/screenshot_beryl.png[/IMG]

You can turn it on and off in the Beryl Manager.

---

### Post by russell.h on 2007-04-22
How do you take a screenshot of the cube? It never lets me take a screenshot while the cube is... cubeified

---

### Post by sarracenia88 on 2007-04-22
I have installed beryl just fine, but i don't see the top menu bars on the windows. I know that in edgy, I had to install xgl in order to see those menu bars. Do I need to do that in feisty too?

---

### Post by GSF1200S on 2007-04-22
> **sarracenia88 said:**
> I have installed beryl just fine, but i don't see the top menu bars on the windows. I know that in edgy, I had to install xgl in order to see those menu bars. Do I need to do that in feisty too?

Dangit.. I *THINK* I had to modify a few lines in my Xorg.conf file. I think once again it had to do with triple buffering. Do a forum search and maybe a google search for this...

---

### Post by megamania on 2007-04-23
> **MrPyro321 said:**
> Open a Terminal window (Applications, Accessories, Terminal) and enter the following command:

Thank MrPyro, I followed your instructions and installed Beryl in three minutes! Everything appears to be working flawlessly!

---

