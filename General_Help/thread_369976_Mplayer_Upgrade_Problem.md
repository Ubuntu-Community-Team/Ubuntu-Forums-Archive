---
title: "Mplayer Upgrade Problem"
date: 2007-02-25
forum: General Help
---

### Post by CheeseQueen452 on 2007-02-25
I saw the update for Mozilla-Mplayer this morning, & although it appeared to install, Synaptic still says it's upgradable. It's also greyed out in the update manager. I tried marking it for upgrade in Synaptic, but it didn't work because of dependencies on libfontconfig1 & libpango1. It said they needed to be installed, but they are. HELP!!

---

### Post by CheeseQueen452 on 2007-02-26
Anyone?

---

### Post by CheeseQueen452 on 2007-02-26
Can someone help?

---

### Post by CheeseQueen452 on 2007-02-26
*bump*

---

### Post by CheeseQueen452 on 2007-02-27
Any help would be appreciated!

---

### Post by daemonfly on 2007-02-28
I had issue with 4 different things, mplayer being one of them. The way I fixed it was just manually search for "mplayer" in Synaptic, right-click it and "mark for upgrade", then apply. You'll probably see that it wants to remove something, then possibly upgrade whatever it removed. For me, it was libgii0 & libgii0-target-x wanting to be removed, and libgii1, etc.. installed.

Similar for checkinstall, which was one of my other problem programs.

---

### Post by CheeseQueen452 on 2007-02-28
As I said in my original post, marking for upgrade doesn't work. I would remove the mplayer plugin, but I'm afraid it won't re-install.

> **daemonfly said:**
> I had issue with 4 different things, mplayer being one of them. The way I fixed it was just manually search for "mplayer" in Synaptic, right-click it and "mark for upgrade", then apply. You'll probably see that it wants to remove something, then possibly upgrade whatever it removed. For me, it was libgii0 & libgii0-target-x wanting to be removed, and libgii1, etc.. installed.

Similar for checkinstall, which was one of my other problem programs.

---

### Post by CheeseQueen452 on 2007-02-28
Just as I thought, the mplayer plugin won't install after removing it. Now I'm stuck. I can't play streaming videos. HELP!!!! Can someone PLEASE clue me in on what I can do, if anything, to fix this? I started this thread 3 days ago & nobody answered me(except 1 that was of no use). PLEASE HELP!!!!

---

### Post by CheeseQueen452 on 2007-02-28
Somebody? Anybody?

---

### Post by CheeseQueen452 on 2007-02-28
I managed to install the older version of the mplayer plugin via a script someone posted in another thread, but the new version still won't install. If anyone knows how to get around this, I'd appreciate it! I think the powers that be should look into this problem, & hopefully resolve it soon!

---

### Post by ruffneck on 2007-03-15
bump...I'm having the same issue.

---

### Post by CheeseQueen452 on 2007-03-17
Is this problem EVER going to be fixed? I still can't upgrade the mplayer plugin. Is there anything I can do?

---

### Post by CheeseQueen452 on 2007-03-29
I still can't upgrade. If anyone can help, please clue me in!

---

### Post by CheeseQueen452 on 2007-03-31
Can someone PLEASE help me? I've tried everything I can think of, but to no avail. I deleted the plugins, but that didn't work. What am I missing? Add/Remove says there's a conflict with other software, & it tells me to switch to the "advanced mode" to resolve the conflict. What "advanced mode"? How do I get to it? Synaptic says the mplayer plugin has a conflict with... itself? How am I supposed to install the new version if it doesn't let me? What do I do? HELP!!!!!

---

### Post by CheeseQueen452 on 2007-03-31
Here are some screenshots of the errors I'm getting....

[http://img.photobucket.com/albums/v209/Sasafrass/MyPix/Screenshot.png](http://img.photobucket.com/albums/v209/Sasafrass/MyPix/Screenshot.png)
[http://img.photobucket.com/albums/v209/Sasafrass/MyPix/Screenshot-1.png](http://img.photobucket.com/albums/v209/Sasafrass/MyPix/Screenshot-1.png)
[http://img.photobucket.com/albums/v209/Sasafrass/MyPix/Screenshot-2.png](http://img.photobucket.com/albums/v209/Sasafrass/MyPix/Screenshot-2.png)

---

### Post by CheeseQueen452 on 2007-03-31
Can someone PLEASE help?

---

### Post by garybrlow on 2007-03-31
What version of Ubuntu are you using? You might be experiencing broken packages from unresolvable dependencies due to using an older version of Ubuntu. Newer packages/versions and libraries are usually available in the next higher version due to version freezes for each distribution. If you always want bleeding edge versions (latest and or next beta software versions) like me, you will find that the repos do not keep up with current software version. The only solution is either to upgrade your distribution of Ubuntu to the latest version and if that doesn't satisfy you, the only option is to compile the software from source yourself. 

By the way you can still watch streaming videos even with out the embedded Mplayer Firefox plug-in. Just copy the stream url and open it in Mplayer.

Cheers!!! :P


GaryBrlow :biggrin:

---

### Post by CheeseQueen452 on 2007-03-31
> **garybrlow said:**
> What version of Ubuntu are you using?
Edgy(6.10)

> The only solution is either to upgrade your distribution of Ubuntu to the latest version and if that doesn't satisfy you, the only option is to compile the software from source yourself.
As if I know how to do that.....

There must be a way. Why would I be offered an upgrade, only to be told I can't have it? Makes no sense..... I even uninstalled it & deleted the files, but to no avail.

---

### Post by Shmifty on 2007-03-31
Try these:

sudo aptitude -f

press 'b' when in aptitude, if any found press 'g' and then 'g' once more

quit aptitude

sudo aptitude update && upgrade

If mplayer is upgradeable this should fix all broken packages and upgrade mplayer.

---

### Post by CheeseQueen452 on 2007-03-31
Didn't work. Any other ideas?

> **Shmifty said:**
> Try these:

sudo aptitude -f

press 'b' when in aptitude, if any found press 'g' and then 'g' once more

quit aptitude

sudo aptitude update && upgrade

If mplayer is upgradeable this should fix all broken packages and upgrade mplayer.

---

### Post by Shmifty on 2007-03-31
My other suggestion would have to be to ask yourself if upgrading mplayer is really worth it (since there are better players out there).

---

### Post by kodoku on 2007-03-31
> **Shmifty said:**
> My other suggestion would have to be to ask yourself if upgrading mplayer is really worth it (since there are better players out there).

Nothing really beats MPlayer on linux..

As for CheeseQueen, could you try removing everything mplayer related in synaptic, purging the config files, and then reinstalling all of them (mplayer web plugin being the last one)?

---

### Post by CheeseQueen452 on 2007-04-01
It didn't work :( Now what?

> **kodoku said:**
> Nothing really beats MPlayer on linux..

As for CheeseQueen, could you try removing everything mplayer related in synaptic, purging the config files, and then reinstalling all of them (mplayer web plugin being the last one)?

---

### Post by garybrlow on 2007-04-01
Hmm It could be that some dependencies are not yet available in the repositories. The new version update may not yet be complete on the repo side. Forcing it may only lead to broken packages. Just wait for a few days or until they're ready.

Mplayer is currently the best one for playing videos in Linux in my opinion. Very much like Media Player Classic in Windows. It renders subtitles well with nice customizations unlike the other players plus other things. My only qualms is that it doesn't display DVD menus like the xine or gstreamer based players and the playlist is not your usual stuff But over all quality and features far outweigh the shortcomings.

To compile Mplayer yourself heres a nice guide/HOWTO [http://www.ubuntuforums.org/showthread.php?t=336706&highlight=mplayer+howto](http://www.ubuntuforums.org/showthread.php?t=336706&highlight=mplayer+howto) its a step by step. You can download the source directly from [http://ww.mplayerhq.hu](http://ww.mplayerhq.hu), you can also read the official installation instructions here which includes compiling and obtaining SVN versions. You can very much apply what you get in terms of compiling knowledge from trying out the howto to other software aside from Mplayer.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by CheeseQueen452 on 2007-04-01
Erm.... I've had this problem since feb 25th.

> **garybrlow said:**
> Hmm It could be that some dependencies are not yet available in the repositories. The new version update may not yet be complete on the repo side. Forcing it may only lead to broken packages. Just wait for a few days or until they're ready.

---

