---
title: "Cannot install avidemux"
date: 2005-05-05
forum: General Help
---

### Post by giorgosc61 on 2005-05-05
Hello.
I have Ubuntu Hoary v5.04
I tried apt-get and synaptic and avidemux cannot be installed
After sudo apt-get install avidemux i get:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avidemux: Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libvorbisenc2 (>= 1.1.0) but 1.0.1-1 is to be installed
            Depends: libxvidcore4 (>= 1:1.0.0-rc4-0.0) but it is not going to be installed
E: Broken packages

I tried sudo apt-get libxvidcore4 and I get:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxvidcore4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

I noticed ** libc6 (>= 2.3.2.ds1-21)** . Is this from debian and possibly the problem.

I hope someone from the developers sees this and corrects the problem.

---

### Post by giorgosc61 on 2005-05-06
Did anyone was succesfull in installing avidemux in ubuntu via apt-get or synaptic?
Does anyone know a solution to the problem?

THank you in advance.

---

### Post by rwabel on 2005-05-08
have a look here to get around the libc6 problem
 [http://ubuntuforums.org/showthread.php?t=548&page=3]("http://ubuntuforums.org/showthread.php?t=548&page=3")
 
 it worked for me too and haven't had any problems. I know it's not the best solution to do that. I guess the differences are so minor that it's safe to do that. But no guarantee from my side

---

### Post by belovedconsole on 2007-06-18
This thing is a joke.  I have been trying and trying to find an audio editor so that I can edit multi-track audio files like I used to do in Windows, very easily.

Everything I download doesn't work, most of them don't even recognize mp3's, and then when I look for a solution, I get all these pointers to download this and un-tar that, and whatever.

All I have to do now is spend $350 for Windows ($250 + various anti-virus software and subscriptions) and I can have a plethora of audio editing software.

Even if I spent $350 on Linux, I wouldn't get it, am I right?

I can't begin to describe how incredibly disappointing this is.  I've been happy with Ubuntu Linux up to this point, and I accepted that I might not be able to edit video, but I can't even edit audio easily like I did with Windows.

Linux is not appealing to artists-- the Mac and PC are doing that.

Linux is appealing to tech-heads.  I would much rather spend the money than follow all these goofy links telling me how great a piece of software is that doesn't even work when I install it.

Hate Windows, I hate Microsoft, but hey-- you press buttons, it installs, and it works.

You people have a long way to go.

When I can't get one audio program to work, that's pathetic.  Sure, you can say it's pathetic of me.  But do a scientific experiment.  Put a person on Windows online next to a person on Linux online and tell them to download and use a free audio multi-tracker/editing program, and guess who will get the demo done first?

The Windows people will have it downloaded and working within the hour.

The Linux people may have something working in a few days.

I finally got .avi's and other formats to work, by using "automatix"-- this was a big plus.

I thought that since I did that, hey, maybe I'd take a grand leap and actually consider doing audio work on my Linux piece like I used to do on Windows.

Oh well.

So much for artists, right?  "When SysAdmins Ruled the Earth," great story by Cory Doctorow... I'll come begging for help to you when the world ends... until then, I just want to edit my audio like I've always done.

Too bad I, and other performers, can't.  Cite me one great thing made on this crap.

I am totally disappointed and pissed.

Oh, here's an idea, since that was so inappropriate, point me to some downloads where Ubuntu, the supposed king of easy Linux, can download and operate a multi-track audio recorder as easy as Windows can.

Hey, I'll make it easy.  Point me to a tracker.  I'm going to research Linux trackers right now, let's see what happens...

---

