---
title: "Do PPAs conflict?"
date: 2012-11-15
forum: General Help
---

### Post by Bluebearbevis on 2012-11-15
Hello all,

I have a question stemming from my recent attempt to get sound working through hdmi from my nvidia geforce g105m.  I didn't quite understand all the instructions in an "hdmi audio on nvidia cpus" link I found here, so finding another possible solution, I installed the latest nvidia and pulse audio stuff through ppas.  No sound icon in panel, nothing on any tab in "sound!" Another fresh install to fix.  Now my question, is it possible that ppas for computers are like prescriptions for humans and packages can conflict and even kill you (your computer)?  Thanks for listening,

Richard

---

### Post by ratcheer on 2012-11-15
In my opinion, yes, PPA's can cause serious conflicts. I found this out when I kept experimenting with the Gnome 3 PPA's for Ubuntu 11.10 and 12.04. YMMV, but when you install a PPA, you are straying from the "approved" sets of software, often including special libraries and drivers.

Tim

---

### Post by Bluebearbevis on 2012-11-15
Hello everyone and thanks ratcheer,

How is one to know?  Short of trying them and if they don't work and you're a terminal guru, fixing your system.  Or, most often in my case, doing a fresh install and starting over from scratch.  For example, when installing all the stuff I had on my computer before this latest fiasco, I was using the Faenza Icons.  I installed them again from the ppa.  They never appeared in my choices, then when I'd try to run update manager, synaptic, or Ubuntu Tweak I'd get some weird error about a source file from tiheum that had the word "lude" in it.  Learned how to navigate to and remove this file (thanks all), and everything is well again.  I don't know if it's a new day and this was fixed or what, cause I installed Faenza through Ubuntu Tweak this morning and there they are by God!  Guess I'll have to take a look at the new file.  Again thanks for listening,

Richard

---

### Post by Frogs Hair on 2012-11-15
PPA package conflicts are usually discovered  during installation. I try to stick with only PPAS that are well maintained and well known. If you go to Launchpad and discover no new builds for 50 weeks you may want to think twice about using that PPA. This is true especially if there are new versions of Ubuntu recently released and you know the PPA has not been updated.

---

