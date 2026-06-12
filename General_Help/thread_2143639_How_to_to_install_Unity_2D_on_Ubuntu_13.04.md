---
title: "How to to install Unity 2D on Ubuntu 13.04"
date: 2013-05-09
forum: General Help
---

### Post by leon_chame on 2013-05-09
Google and some searches here on the forum didnt produce any how to install unity 2d in Ubuntu 13.04, so I will ask here.

How should I do this in 13.04?

Apparently from what I read, the Unity 2D Dummy package doesnt actually run or install Unity 2D.

I use Ubuntu on a work computer where I give presentations hooked up to projectors.  I noticed while running 12.04, I almost always had to log in using Unity 2d to get the projector to recognize my computer.  I just upgraded to 13.04 and noticed and read unity 2d is removed so I am concerned about what to do now.

---

### Post by grahammechanical on 2013-05-09
Unity 2D was removed from 12.10 onwards. We now have something called llvmpipe which has the purpose of providing Unity 3D on lower specified PCs. I think we also get it when we enter Recovery Mode Resume. I have not tried deactivating the video driver to see if llvmpipe steps in.

Regards.

---

### Post by sdhengsoft on 2013-05-27
> **grahammechanical said:**
> Unity 2D was removed from 12.10 onwards. We now have something called llvmpipe which has the purpose of providing Unity 3D on lower specified PCs. I think we also get it when we enter Recovery Mode Resume. I have not tried deactivating the video driver to see if llvmpipe steps in.

Regards.

  I can see why you may want to remove 2D when running on the console, but what about the rest of us that use Ubuntu as a Server and log in remotely via XDMCP over a LAN. I don't want compiz running over a network. The interface is just way too slow for that. Could someone please consider returning the 2D interface so that network logins are possible with good speed. At present Unity is unusable over a network in 13.04. I'm keeping all my servers at 12.04 until this is fixed. Thanks.

---

### Post by mtroutman on 2013-05-29
Removing support for unity 2d is a mistake. You are ignoring any user that uses a remote desktop. I do my daily development on a remote virtual machine running 12.04. The only thing fast enough to do this is nxserver with unity-2d.  If I upgrade I won't be able to do this anymore. 

I stupidly upgraded my home machine to 13.04 only to discover the hard way that I can't get a unity remote desktop anymore from my laptop because you decided no one needed to be able to do this anymore. VNC is not an option, it's too slow. I also see that the only alternative I have left from this machine (gnome-fallback-session) is deprecated for removal too. 

If I can't get a fast remote desktop then this will kill ubuntu for me or I'm stuck at 12.04 forever. I actually really like Unity too. 

If you have a work around that gets me a responsive Unity remote desktop on a 13.04 host I would love to hear it.

---

### Post by Frogs Hair on 2013-05-29
2D is not independent of 3D   in 12,04 , they share folders in the file system. Attempting to install  Unity 5 on 13.04 which uses Unity 7 would most likely end up broken dependency hell. With Unity likely/possibly moving  Mir I don't think there will be interest in resurrecting 2D development .  

[http://en.wikipedia.org/wiki/Mir_(display_server)](http://en.wikipedia.org/wiki/Mir_(display_server))

---

### Post by kansasnoob on 2013-05-29
Before I get started please understand that I was also disappointed with the demise of Unity-2D, but that's beyond my control so please don't shoot the messenger. I'm only making the following comments in an attempt to be helpful :)

So, first of all, it's now more than ever preferable to use LTS releases on production machines because:

(a) Beginning with Saucy (13.04) the support cycle for interim releases was reduced to nine months rather than the typical 18 months:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

(b) The LTS releases will be supported for 5 years, and the LTS point releases will include kernel and "x-stack" updates in order to support the latest hardware:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Second you should know that Unity-2D used the Metacity window manager just like the Classic/Fallback (no effects) session which Edubuntu uses to support LTSP installs:

[ATTACH=CONFIG]243244[/ATTACH]

And Edubuntu dev will continue to support the fallback session going forward:

[http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/](http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/)

I made more notes regarding that here:

[http://ubuntuforums.org/showthread.php?t=1966370&page=20&p=12665934#post12665934](http://ubuntuforums.org/showthread.php?t=1966370&page=20&p=12665934#post12665934)

Now I know this is not a direct answer to the question posed but it rather leaves you with two possible choices:

#1: Reinstall and stick with 12.04 (currently 12.04.2), or:

#2: Use the "fallback" session in either 12.10 or 13.04.

---

### Post by bmullan2 on 2013-08-15
Folks don't forget that just because Ubuntu 13.04 doesn't support Unity-2d any longer it does NOT mean you can't use remote desktop software any longer with 13.04.  All you have to do is install a different desktop that your remote Desktop software does support like LXDE or XFCE etc.

Also, if you have not tried x2go... do so.   It does work with Unity and it is by far the best remote desktop solution I have worked with and I've tried a LOT including commercial applications.

see: [www.x2go.org](www.x2go.org)

The server side installation of x2go is simple and takes only minutes.

There are native clients for windows, mac and linux.

There is a python version.

If you use Ubuntu there is even a browser plugin that lets you just use your browser to acccess the machine with the x2goserver installed on it and get your remote desktop.

x2go supports - remote printing, remote audio/video (video depends on b/w & server cpu etc), remote file shares w/client, screen sharing and more.... its just really good software and I use it all the time with servers I have running on Amazon's cloud where I want a desktop instead of just a server terminal prompt to work with and its just like working on a machine at home.

---

