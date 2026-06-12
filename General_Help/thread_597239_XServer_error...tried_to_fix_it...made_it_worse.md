---
title: "XServer error...tried to fix it...made it worse"
date: 2007-10-30
forum: General Help
---

### Post by Hoosier205 on 2007-10-30
Alright, I will provide as much information as I can. It might be a bit limited however, because the problem is with my computer at home...it's unusable at this point.

I'll lay it all out:

I have a Sony notebook. I had Feisty installed before with XP as a dual-boot. I thought I was finally familiar enough with Ubuntu to make the jump. Wiping out XP and installing Gutsy...and fixing small quirks that came up along the way made me feel even more confident. Boy was I wrong! Ever have one of those moments where that little voice is saying, "Stop! Stop! Don't touch anything else! Just ask for help before you screw it up anymore!" Well, I didn't listen this time and it bit me in the...well you know. 

1. Everything had been working fine for days. I went to reboot gutsy and had done nothing that made me worry. Gutsy exits. Notebook begins to boot back up...

2. XServer problem...end up with a blue (I believe) box telling me this and allowing me to diagnose the problem. I select yes and I get the message about EDID not being installed. That I should install it and than try to start GDM. Hmm...ok, seems simple enough. I don't know what EDID is, but that's normal for me with linux. It says I need it...I don't question it. 

3. Attempts to install EDID do not change the problem at all. It still says I don't have it installed.

4. I thought...hmmm...I wonder if this is a problem with xserver. So, I install xserver-xorg. It says I already have it installed, which I knew. So, let's try xserver-xgl. Not installed....I installed it. This didn't help either.

5. I am thinking of everything that has been stored in my limited time only ubuntu-using mind. Last ditch effort on my part...I decided to remove xserver-xorg and xserver-xgl and reinstall both thinking they are both just variations of each other. The removal of both goes fine. Reinstall was a different story...

6. The reinstall starts off well...at least I used the right command and it understand what I was wanting to do. Problem is...it can't find anything from ANY of the dependencies (if that's what they are called...the places listed on the sources list). I don't know if this because I suddenly have no internet connection from removing xserver...since I'm an idiot and don't know what xserver is even for. Also, I can't install anything at all.

I am hoping there might be a simple fix for all of this. I just got this set up to where I wanted it. I don't want to start over. Thank you for any help you can provide.

---

### Post by bswilson on 2007-10-30
First off, xserver-org is the set of packages that creates the graphical interface you see on the screen.  Without it, you have only command-line access to your system.

If all you've been doing is removing/reinstalling xserver-org and related packages, your Internet access shouldn't be affected.  From the command line, you can test that by pinging your default gateway, etc.

I think the first thing I would try is simply reconfiguring xserver-org with a safe setup.  Assuming you still have it installed, issue this command:

```
sudo dpkg-reconfigure xserver-org
```

The tool dpkg-reconfigure is used to reconfigure an already installed package.  After you issue this command, I recommend rebooting, see where you are then.  I'm hoping that this will restore you to a working setup.

---

### Post by Hoosier205 on 2007-10-30
> **bswilson said:**
> First off, xserver-org is the set of packages that creates the graphical interface you see on the screen.  Without it, you have only command-line access to your system.
I'm without it now...I uninstalled it. :( I have command-line only access.

> If all you've been doing is removing/reinstalling xserver-org and related packages, your Internet access shouldn't be affected.  From the command line, you can test that by pinging your default gateway, etc.
What is the command for doing this?

> I think the first thing I would try is simply reconfiguring xserver-org with a safe setup.  Assuming you still have it installed, issue this command:

```
sudo dpkg-reconfigure xserver-org
```

The tool dpkg-reconfigure is used to reconfigure an already installed package.  After you issue this command, I recommend rebooting, see where you are then.  I'm hoping that this will restore you to a working setup.I did this before when I screwed up a graphics driver installation. I'll give a try again once I figure out how to reinstall xserver-org. Is the EDID error something that can be cleared up by doing this?

Thank you for helping!

---

### Post by Hoosier205 on 2007-10-30
Problem has been solved. I did not have a wireless connection to my router any longer. Once I plugged in my ethernet cable I was able to install xserver-xorg and do the reconfigure....now everything is just fine. Thank you for the help. Sorry for wasting your time. I should have just tried that in the first place.

---

### Post by bswilson on 2007-10-31
Hey, not a waste of anyone's time!  Remember, the community is here to help and although I didn't do anything, we all need a little helping hand or guidance from time to time.  Glad you got it all sorted out!

---

