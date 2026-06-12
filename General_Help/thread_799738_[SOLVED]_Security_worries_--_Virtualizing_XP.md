---
title: "[SOLVED] Security worries -- Virtualizing XP???"
date: 2008-05-19
forum: General Help
---

### Post by ZabiGG on 2008-05-19
Hi all ;)

I'm in the process of virtualizing XP using Virtual box (currently reading User Manual front to end). 

My question is, since XP is so full of holes, is there a specific way to ensure that the security layers of my linux shell remain on top and unaffected by the presence of XP on my system??

I know, I should not use XP. But I have no choice since some of the software I use for work on a daily basis and can't live without is currently not possible to install in Ubuntu (Antidote, SDLX), and wine just won't do for them.

Thanks in advance for keeping it simple to understand for a newbie.

Z.

---

### Post by HermanAB on 2008-05-19
Well, running Windows is always a risk. Therefore you have to take the usual precautions.  The best way to protect Windows is to disable networking.

---

### Post by bingoUV on 2008-05-19
Look at it this way : 
        XP
-------------------
      VirtualBox
-------------------
      Ubuntu

Since XP is full of holes, all your data inside XP is always at risk. Hence
1. Use the snapshot feature of VirtualBox frequently and whenever you get infected just revert to last known good snapshot.
2. Backup data from XP somewhere safe in Ubuntu (not system files, just your data).

VirtualBox **could** have some holes, or you may get late in updating VirtualBox after some vulnerability is found. This is much rarer than a hole in XP, but still. Hence
1. Run VirtualBox as a user that does not have write permission on your other data that you keep in Ubuntu. Including the data that is in virtual XP but backed up in Ubuntu.
2. Update VirtualBox frequently.

---

### Post by steviers on 2008-05-19
I am not an expert on Linux but have done extensive work with virtualzation in the Windows environment, and I am an expert with Windows, for whatever that's worth.

I feel about 95% confident and telling you that any security problems that you may encounter with your virtual XP will only affect the XP environment and not transcend into the Linux realm.

However since I don't know about the virtual technology being used, there is always a risk.

Here are a few things you can do to your XP session to keep it as secure as possible.

The first thing I do when I build a windows box, virtual or not, is to install anti-virus right away before I even plug in a network cable.

Unplug the network cable from you computer and install your anti-virus.

The best A/V you can get, which is 100% free is AVG from Grisoft.
The link is [www.free.grisoft.com](www.free.grisoft.com).

Download AVG 8.0 free edition, install it, and just before it asks you to do the online update, plug in your network cable, then run the update.  This keeps your exposure the the absolute minimum.

After you have installed AVG,

Download XP service pack 3, it's free, and it will save you a ton of time doing manual windows updates.

Download and install IE7.

After all reboots, run Windows Update.
From IE, Click on "tools" then "options" then "Windows Update".

When presented with the Windows Update page, click on the link for "Microsoft Update" which is an enhancement ot the normal Windows Update.

Downlaod and install Microsoft Update.  Rather than only using the "Express" or "reccomended" updates, always choose the "Custom" option, and install EVERYTHING.

Everytime you do this, you will have to reboot, and some updates require additional upates once they are installed, especially for things like ".Net frame work".

So go through this process several times until you finally see that there are no more updates available in the "Custom" option.

At this point your installation is going to be as bullet proof as it can be for windows, I would also suggest downloading and installing "Windows Defender" which is a free real-time spyware agent, you can get that, along with SP3 from [www.microsoft.com/downloads](www.microsoft.com/downloads).


Once XP is up and running, you can turn on automatic updates to download the monthly patches from Microsoft as per usual, and you should be good to go.

---

### Post by ZabiGG on 2008-05-19
Wow! I couldn't have asked for better info. Thank you all for taking the time to help me out, I really appreciate it.

:KS

Z.

---

