---
title: "Hello and new new to linux."
date: 2007-04-29
forum: General Help
---

### Post by tabs on 2007-04-29
Hello All.

I havn't touched Linux until 7 days ago.
I found Ubuntu 7 and thought I'd give it a try.I have a few spare Pc's lying around and so I 
installed Ubuntu on a Dell t650r pc with 768 ram and an upgraded powerleap 1.4ghz celeron cpu.

I had a major problems with the installation which I wont go into right now.

Anyway Ubuntu is up and running nicely now (well sort of).My old ati 9200se card half works but 
the system freezes when I try and use a screensaver or try and run 3d games.I spent about 2 days 
trawling forums about how to fix this but have given up as of right now.There's really no need to point 
me to 'fix it' forums because I tried it all.The ati card half works so its acceptable at the mo.

So as a new bloke to Linux I have found certain aspects great about Linux Ubuntu over XP.
Internet browsing and downloading is certainly quicker.
I love the online installations 'apt-get' or via add/remove or Synaptic.They work flawlessly well.

So there's my introduction.

The only thing I really need right now is a solution to Windows Quickpar.I am a major user of newsgroups 
and those who use it will know what I'm on about.I've got a newsreader and rar from the repositories but 
need a solution  as to wether Linux Ubuntu has the equivalent to Windows quickpar.Again I've searched 
online but haven't found anything that works.

Any help would be appreciated.

May I add at this point that I am not anti windows (XP) - boo hiss I hear but I haven't found an alternative 
that totally does all the things I need.

Anyway - thanks for reading my post.

Love and peace.

---

### Post by dreadlord_chris on 2007-04-29
Well, there is **gpar2** - it's in the repositories. For some reason, though, it doesn't work for me (won't run)

I actually use Quickpar with **wine** - no, not the drinking kind [-X 

If you are not familiar with it - wine is a Windows compatibility layer. In other words, wine allows you to run many Windows applications from within Linux.

I'd try gpar2 first - if it works for you great, native apps are always better.
```

sudo apt-get install gpar2

```

If that doesn't work for you, or you like to continue using Quickpar (familiar apps can be nice too):
You'll need to make sure that the **Universe** repository is enabled:
Synaptic Package Manager > Settings > Repositories
Then search for **wine** and install.
You can then install Quickpar with the installer from the website:
```

wine quickparinstaller.exe

```

---

