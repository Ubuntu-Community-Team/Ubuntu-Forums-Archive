---
title: "Stuck in Perpetual Login"
date: 2007-04-04
forum: General Help
---

### Post by JacktheHomeless on 2007-04-04
Ok heres a brief overview. I am running Ubuntu Edgy. Earlier tonight, while fiddling around I got a mesage to update. A little while after the update I restarted and now I can't login. Every time i login, i type my name and pass, the screen goes blank, then returns to the login screen. If i Ctrl+Alt+Backspace to restart x, I get an error message about the greeter program appearing to crash. It then gives me an alternate login window. I then try to login through that, and it does the same thing and returns me back to the default login. 

The only way i can get back in to ubuntu is via the recovery mode. I searched and searched and all i can seem to find is something on turning off accessibility features. First off, I cannot figure ou thow to do that in recovery mode. Second off, I have done nothing that could've caused this.

Please, give me a hand here. This is extremely frustrating.

---

### Post by bapoumba on 2007-04-04
Hello, from recovery mode, please run **df -H**. One of the directories may be full. MAke some room ;)
**sudo aptitude clean** can help you clear some space and start a regular X session. Then you can move out some of your files.

---

### Post by Co.Sinecure on 2007-04-04
Try running:
> sudo dpkg-reconfigure xserver-xorg
from the command line (Ctrl-Alt-F1)

---

### Post by rdelbru on 2007-04-04
I have the same problem since I have updated.
I have tried the command:
sudo dpkg-reconfigure xserver-xorg
but it says that xserver-org is not installed ?

Thanks.

---

### Post by rdelbru on 2007-04-04
I fixed the problem by reinstalling the official nvidia driver.

---

### Post by bazcor on 2007-04-04
I am in the same boat, my nvidia driver loads OK (I've done a reinstall just in case), but I can't get ubuntu screen to load.(black screen, nvidia screen followed by login screen as described). This came after installing a few XORG updates this morning, now I'm completely stuck!

I have beryl installed which may or may not be connected to the problem.

I really love Ubuntu but this could be about the last straw for me :-( 

Any suggestions would be gratefully received, I'm  sick of windows already.

---

### Post by JacktheHomeless on 2007-04-04
Its not a disk space problem. I have around 90 gigs free on the partition. 

I'm gonna go ahead and give reinstalling the nvidia drivers and shot. Hopefully that may fix it.

And as for reconfiguring the X, i tried that from recovery but it doesn't run. Hopefully i can get this sorted out as soon as possible.

---

### Post by bazcor on 2007-04-04
I found a cure for my problems in a thread on the beginners forums:

cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1.0.9746 libglx.so

hope it helps....

---

### Post by defishguy on 2007-04-04
I was able to get back into my normal (sans beryl) session by switching to a different console Ctrl Alt F6 and uninstalling beryl (sudo apt-get remove beryl) and going back to Ctrl Alt F7

---

### Post by cmost on 2007-04-04
I can confirm that reinstalling nvidia's official driver solves the problem.  The reason this works, I might add is because during the reinstallation, it essentially does what 'bazcor' suggested as a solution.  The xorg updates replace the symbolic link (link to libglx.so.1.0.97xx) created by the nvidia driver with a hard file (new copy of) libglx.so.  This breaks the X server for those running the nVidia driver and using ARGB Visuals for Beryl.  It may break AIGLX as well, but I cannot confirm.

As an aside, this is the sort of issue that will send newbies scrambling for their Windows installation CD's.  Updates should NEVER break the X server, regardless of the reasoning.  An intelligent update should be able to detect the presence of the proprietary video driver and either work around it or present the user with some information whereby s/he can make a decision as to go ahead with the update or stand down.

---

### Post by Nachimir on 2007-04-05
Thank you very much, both for the fix and the explanation (Directed from [here](http://ubuntuforums.org/showthread.php?t=402185)).

That was an awkward update, which meant today was a bad day. It's only the fact that XP makes me scream bloody murder that prevented me from scampering for my windows CDs. Glad I could find so much help here though, thanks again.

(Edit: [Solution](http://ubuntuforums.org/showpost.php?p=2411230&postcount=11) for anyone who has reinstalled the nvidia driver but can't get Beryl working again)

---

### Post by roddyread on 2007-06-13
Talking of newbies....and scardie cats...
I will give that fix a go then thanks for the post

---

