---
title: "Ubuntu no longer boots up into GUI; boots up terminal-like."
date: 2008-04-06
forum: General Help
---

### Post by AquaStreak on 2008-04-06
Ok, today is still technically my first day of using Ubuntu. It has been nothing but problems. I've asked my friends for help with many, and when they can't help me, I ask here.

Today alone, I've had these problems:

[http://ubuntuforums.org/showthread.php?t=746870](http://ubuntuforums.org/showthread.php?t=746870)
No sound

[http://ubuntuforums.org/showthread.php?t=747123](http://ubuntuforums.org/showthread.php?t=747123)
Black screen

[http://ubuntuforums.org/showthread.php?t=747558](http://ubuntuforums.org/showthread.php?t=747558)
No sound... again

As you might imagine (and know if you've read my last topics), Ubuntu is made me nothing but furious. I'm trying really hard to be fair with it and adapt to using it, but the harder I try, the more that screws up.

Now, I have a new problem. It's like the second problem, but this time, I can't boot into the GUI. Instead, after the Ubuntu logo with the progress bar, I get a terminal like boot.

I asked my friend, and he swore it was my graphics drivers screwing up. He said if it doesn't boot into the GUI, it's my drivers. I told him it wasn't, but I tried it anyway. So, just a few minutes ago, in that terminal thing, I typed

sudo dpkg-reconfigure -phigh xserver-xorg

I reset my drivers, but it still boots into the terminal thing. Grrr.

**This is a picture of what's going on now:**
[http://travisipodstore.com/ubuntuload.JPG](http://travisipodstore.com/ubuntuload.JPG)

I have no idea how to fix this. I don't understand what went wrong. It was working fine, I reboot, and.... now it won't boot up again.

Please help... :confused:

---

### Post by hyrule_man on 2008-04-06
Your friend is right, its that GFX card of yours, no question. <.<

---

### Post by haggus on 2008-04-06
check here

[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)

If your using nvidia 

gksuo gedit /etc/X11/xorg.conf

check the drivers section make sure it says nv or nvidia then reboot

---

### Post by AquaStreak on 2008-04-06
I'm using an ATI Radeon X1300 Pro.

But I'm 99% sure it ISN'T my graphics card.

---

### Post by p_quarles on 2008-04-06
Off topic silliness removed. Please keep this on topic.

---

### Post by WoosterB on 2008-04-06
One thing I've noticed is that you were dabbling with sound.  May I ask what sound driver/card you are using?  

I ask because I have the exact same problem after installing a sound driver and for some reason it killed off my graphics driver.  I'm currently in a similar state of affairs and would very much like to fix the problem and find out why a sound driver would overwrite a video driver.

-W

---

### Post by AquaStreak on 2008-04-06
I'd like to answer your question, but I really don't know.

See, the problem is, I have a SoundBlaster Audigy 2 ZS that I don't believe works. Therefore, I use onboard sound (Signatel) for my Windows installation.

I'm not sure if Linux tries to use my SoundBlaster or my onboard sound.

---

### Post by WoosterB on 2008-04-06
Well Aquastreak, I owe you one.  I tried out the command line you had posted and resetting the resolution solved my problem and I'm back to the GUI. :)

Now I have a SB X-Fi.  There are several methods to get it to install (that I've found) but each one upon reboot will kill off the video drivers and I have to re-install them.  I use Envy for my graphics driver (nvidia 8800 gtx) and it does a great job.  Now it COULD be the devil is in how Envy installs that driver.  I don't know.

However I've pinpointed that the main problem with the video drivers (for me and possibly for you) is the installation of the sound card since NOTHING changes between installation, reboot, and then terminal problem.  If anyone of greater Linux intelligence than I reads this, please take this into account.

-W

---

### Post by dchurch24 on 2008-04-07
I can offer no help (apart from bumping this post), but I would just like to say "hang in there" - it's worth it in the long run.

I had all sorts of problems when starting out - but I soon realised that it was my lack of knowledge that was at fault in part. When I think back, I used to have all sorts of errors with Windows - but after many years of using windows I knew where to look for the answers.

I've been using Ubuntu for the past 12 months, and now when I encounter problems (and there have been fewer than if I'd been using Windows), I find that now I am starting to know where to look once again.

It was never going to be a fast learning process, but I think you will find eventually that the pros outweigh the cons. 

I finally deleted my Windows partition last week as I found I hadn't booted into Window for over 6 months.

I find now that I can do most things I ever wanted to do that I could do in Windows - only know, I find I can do them quicker and with a lot less hassle.

Stick with it.

---

### Post by AquaStreak on 2008-04-07
Its kind of odd, when people wanted me to try Linux they did nothing but praise it. Now that I try it, everyone says they had problems when they started out.

---

### Post by Nameless_one on 2008-04-07
Transitions are always a problem, praise has nothing to do with a problematic beginning. 

On topic, let's check wether even though you end up with a command line, graphics work. 

In the prompt, type: 
```
 sudo /etc/init.d/kdm start
```

That should start KDE (I assume you have kubuntu because of your command line output - if you have ubuntu ie Gnome, substitute kdm with gdm). If not, post your output.

---

### Post by AquaStreak on 2008-04-07
That didn't work. I have Ubuntu (not Kubuntu) so I substituted gdm for kdm and typed:

sudo /etc/init.d/gdm start

It gave me an error.

---

### Post by AquaStreak on 2008-04-07
Bump..

---

### Post by jocko on 2008-04-07
> **AquaStreak said:**
> That didn't work. I have Ubuntu (not Kubuntu) so I substituted gdm for kdm and typed:

sudo /etc/init.d/gdm start

It gave me an error.

What error did it give you?

---

### Post by AquaStreak on 2008-04-07
[http://travisipodstore.com/ubuntuerror.JPG](http://travisipodstore.com/ubuntuerror.JPG)

Thats a picture of the error it gives me.

"sudo: /etc/init.d/gdm: command not found"

---

### Post by Nameless_one on 2008-04-07
I have been reading at your posts and tried to understand what is going on, but I can't. However, it seems you did a lot of things between posts that you haven't mentioned, and these might have broken stuff. 

I recall you have an Audigy sound card, which you said was buggy under Windows, however, you also have sound problems, and correcting them broke your GUI. I suggest you remove the sound card completely, and deleting and reinstalling Ubuntu. 

Now, I guarantee nothing. This might work, and it might not. Or maybe I have forgotten something you have already done. Whatever you try, please be more descriptive of what you do, so that we can help you.

---

### Post by AquaStreak on 2008-04-07
Well, the only thing that could have caused this was a program called "Timidity". Ubuntu loaded fine until I tried to install that, and now it won't boot (my current problem).

Is it possible to remove this from the terminal?

---

### Post by jocko on 2008-04-08
> **AquaStreak said:**
> [http://travisipodstore.com/ubuntuerror.JPG](http://travisipodstore.com/ubuntuerror.JPG)

Thats a picture of the error it gives me.

"sudo: /etc/init.d/gdm: command not found"

That means you have managed to uninstall gdm (and probably some other important packages).
type this command to fix it:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Nameless_one on 2008-04-08
Plus, you can uninstall timidity from the terminal (as you can with any other program):

```
 sudo aptitude remove timidity
```

(you can use either aptitude or apt-get, if you are interested in the differences, google it)

---

### Post by Tomatz on 2008-04-08
You can use envy at the command line to install and configure the latest ATI graphics drivers. Just write down (or print) the following ant type it at the command line:

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb
```

then

```
sudo dpkg -i envy*.deb
```

and finally to run envy type

```
envy
```

Hope this works for you ;)

---

### Post by jocko on 2008-04-08
If you guys could [read his post]("http://ubuntuforums.org/showpost.php?p=4673400&postcount=15"), instead of posting solutions to other problems: When he tries to start gdm, he gets the message that gdm is not found.
The problem is NOT with any ati drivers or timidity or whatever, the problem is that he has uninstalled gdm and needs to reinstall it (and probably some other essential gnome packages).

The solution is still this:
First make sure gnome and gdm is installed by installing the package 'ubuntu-desktop'.
Then try to start gnome again by this command:
```
sudo gdm
```or:
```
sudo /etc/init.d/gdm start
```

---

### Post by jimbo99 on 2008-04-08
I read everything before replying and I to have expressed frustration in the past where people post responses without first reading and those responses ended up sending me in odd directions ultimately having no bearing on my problem.

His screenshot shows no gdm installed.  There are a few times when you try to remove this or that application it will be dependent on gdm and that will uninstall gdm.  I've posted to bug reports and various other places indicating that this should NEVER ever happen but unfortunately it does.

I would also like to point out that the creative drivers for sound, as far as I know, don't work unless you are in a 64bit environment, but I have a RL friend that says he is able to get them up and running using the creative drivers.  I doubt this and I doubt it was done without issues.

I also would like to support the post that said--reinstall.  Hopefully with as little time he has spent using it he didn't create any content that has to be backed up.

I would also like to support the post that said that transitional times can be tough.  For the most part, in my experience, the installs generally go well.  It is when someone tries to tweak things without having knowledge that it tends to let them down.

Most Windows installs are done by the factory for the pre-fab computers (dell, HP/compaq, etc).  Well, the bottom line is that you have far less problems but if you had to install those by hand you would have the same sorts of problems--missing drivers, tweaking, applications installation.

If someone generally sets up linux for you then the experience is generally very positive.  Even if you have to do it yourself, can you say that Microsoft's text based installer is better than booting from the live CD and running a graphical installer that asks far fewer questions and installs significantly more product (software)?

I would suggest one thing:  version 8.04 is due out in short order.  The way it works is that if you get the beta, then you do the regular updates to it, by the time that the official release is gold and you can download it for yourself, your beta install will no longer be beta, it will be the official release.  Rarely will someone have to reinstall from a beta to get the full official release--it does happen though.

I am recommending you download and try the 8.04 release of ubuntu and see how that solves your problem.  I would also say to hold off on the creative drivers.  If you follow digg.com you'll note that there was a guy that was fixing the creative drivers that were INTENTIONALLY bugged to keep features from working--and there was this guy who was debugging those drivers and re-enabling the features (he thought he was just fixing them).  Creative stated this was a licensing issue with various companies that they license technology from--meaning they don't invent everything that goes into their product--but then again many others don't either--such as nVidia (they purchase or license technology).  That's one of the reasons that nVidia won't open their drivers to Open Source.  It is also a reason there are issues with other hardware manufacturers producing drivers for Linux.

My point is that your issue with sound drivers is moreover an issue with Creative than it is with linux and some of that pain that you are experiencing is fully their fault.  Unfortunately we don't have the genius of this guy working in the Linux world helping us resolve the same issues.  It would be nice.

So, download the 8.04 beta.  Do the updates.  Then try working through the sound driver or just use the onboard sound.

---

### Post by Tomatz on 2008-04-08
> **jimbo99 said:**
> 
His screenshot shows no gdm installed.  There are a few times when you try to remove this or that application it will be dependent on gdm and that will uninstall gdm.  I've posted to bug reports and various other places indicating that this should NEVER ever happen but unfortunately it does

It isn't the fact GDM isn't installed. The problem is that X isn't starting. GDM won't start without X.

Maybe you should research xorg and what it does/is ;)

---

### Post by Tomatz on 2008-04-08
Login at the "black screen" and do this:

```

wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb
```

then

```
sudo dpkg -i envy*.deb
```

and finally to run envy type

```
envy
```

Then follow the prompts

It should defiantly fix your problem. In my opinion it is borked graphics drivers stopping X from starting ;)

---

### Post by jimbo99 on 2008-04-08
Totally disagree.  He'll be chasing his tail.  My recommendation is to download and install 8.04 and go from there.  Envy, at least in part, is used to automatically install the video drivers.

His system didn't say that gdm was unable to start it said that gdm was MISSING.  GDM is the gnome desktop manager.

---

### Post by jocko on 2008-04-08
> **Tomatz said:**
> It isn't the fact GDM isn't installed. The problem is that X isn't starting. GDM won't start without X.

Maybe you should research xorg and what it does/is ;)

Wrong. When the terminal says "/etc/init.d/gdm: command not found" it means the startup script that will start gdm is** missing** (most likely because gdm is uninstalled, but it could also be caused by deleting or changing permissions on the startup script in /etc/init.d/ either way a reinstall of gdm will fix it).
If Xorg doesn't start you get a different error. And Xorg is actually started from gdm, not the other way around (or rather xorg is started as a consequence of starting gdm, as the command to start xorg is run from the scipt that starts gdm).
Maybe YOU should do some research...

---

### Post by Tomatz on 2008-04-08
[beer and ubuntu dont mix]

---

### Post by Tomatz on 2008-04-08
> **jocko said:**
> Wrong. When the terminal says "/etc/init.d/gdm: command not found" it means the startup script that will start gdm is** missing** (most likely because gdm is uninstalled, but it could also be caused by deleting or changing permissions on the startup script in /etc/init.d/ either way a reinstall of gdm will fix it).
If Xorg doesn't start you get a different error. And Xorg is actually started from gdm, not the other way around (or rather xorg is started as a consequence of starting gdm, as the command to start xorg is run from the scipt that starts gdm).
Maybe YOU should do some research...

[beer and ubuntu dont mix]

---

### Post by Nameless_one on 2008-04-08
@Tomatz
Maybe you should edit/delete the last couple of posts.

EDIT: ;) great

---

### Post by Tomatz on 2008-04-09
> **Nameless_one said:**
> @Tomatz
Maybe you should edit/delete the last couple of posts.

[beer and ubuntu dont mix]

---

### Post by Tomatz on 2008-04-09
Try this:

**sudo apt-get --purge remove gdm**

**sudo apt-get install gdm ubuntu-desktop**

You have probably damaged gdm this should reinstall gdm and startup scripts ;)

---

