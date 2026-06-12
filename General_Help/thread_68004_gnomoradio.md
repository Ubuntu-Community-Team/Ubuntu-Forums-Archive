---
title: "gnomoradio?"
date: 2005-09-21
forum: General Help
---

### Post by gat on 2005-09-21
A few weeks ago I stumbled across gnomoradio in synaptic.  This looks like a very cool "creative commons" licensed music sharing program... but I can't get it to work.  Interestingly, it seems to pull down and install fine from synaptic, then seems to locate and start downloading a "playlist."  

However, I can't actually find any downloaded files anywhere on the system (default location or otherwise).  Also, when I press "play" no sound is played, but the cursor flies through all the songs in the playlist, as if each were there, but silent and zero-seconds long (instead of their apparent lengths).

Has anyone else seen this?  Does anybody have any idea what's causing it?

BTW I'm running Kubuntu 5.04.  I'm new to linux but I've been able to get almost all other sound, audio, etc. working fine (usually by following the ubuntuguide.org details).

Thanks.

---

### Post by jmcnaught on 2005-10-03
The same thing is happening to me in breezy.  It also won't play any of the files I already had.  The program looks really cool though.  According to the website [http://gnomoradio.org/]("http://gnomoradio.org/") it is being re-written using Mozilla as a foundation.

I haven't tried figuring out what's going wrong yet.  I'll post back here if I figure it out.

---

### Post by gat on 2005-10-16
I'm sorry you're having trouble, but it's at least nice to know that somebody else encoutered the same problem.  Yes, I agree that the gnomoradio site looks very cool -- I think the whole concept is great (I'd love to really try it).  I'll post back here also, if I find a solution.

Best of luck :)

---

### Post by gat on 2005-11-12
I've still had zero luck with gnomoradio.  However, I've just lately had some success with iRate radio.  So far it seems roughly like the description of gnomoradio.  All the songs are legal to download, but, beyond that, most don't seem to have much license info.

The interface itself is like a stripped-down version of yahoo launchcast (you rate songs and that affects what you hear next).  However, you don't just get streams -- the mp3's download, then play.  This means it takes a while before the first song starts, but, after that, the songs you have just loop until newer ones get downloaded.

You have to install java (kinda unpleasant currently), there are some instructions here (except you should be sure to get the latest version Sun is offering):
[http://ubuntuforums.org/archive/index.php/t-76702.html](http://ubuntuforums.org/archive/index.php/t-76702.html)

Then Java Web Start should run the irate app from the irate site:
[http://irate.sourceforge.net/download.stable.html](http://irate.sourceforge.net/download.stable.html)

I wasn't able (yet) to figure out how to get my browser to launch java web start directly, so I copied the link to the irate app, then ran it in a terminal:
javaws [http://irate.sourceforge.net/webstart/stable/irate-client-swt.jnlp](http://irate.sourceforge.net/webstart/stable/irate-client-swt.jnlp)

Anyway, I'm pretty happy to have some decent, legal music playing and downloading it's way to my 'puter.  I'll come back and re-post if I ever get gnomoradio running, but right now I have to say I'm enjoying iRate.

Stay well

---

### Post by eric0919 on 2005-11-12
iRATE sounds very interesting but I can't figure out how to install it.  I went to the website and fount a link that i guess is a repository link so I put that in my sources file and did 
sudo apt-get install irate 

and it said to try irate-client-gtk  
but that gave some errors too.

any sugestions?

Thanks Eric.

---

### Post by eric0919 on 2005-11-13
i got it I was making it way to hard

---

### Post by radimvice on 2007-06-22
I'm still having the same problem as these people in Feisty. Gnomoradio seems to be working fine, but whenever I try to play any songs (whether fetched or in my local directory) it skips through the playlist without actually playing anything. Any other music player programs work perfectly fine, so it's not a sound setup or mixer/volume problem. Has anyone found a fix for this, or is this program just useless?

---

### Post by starcannon on 2007-07-15
> **radimvice said:**
> I'm still having the same problem as these people in Feisty. Gnomoradio seems to be working fine, but whenever I try to play any songs (whether fetched or in my local directory) it skips through the playlist without actually playing anything. Any other music player programs work perfectly fine, so it's not a sound setup or mixer/volume problem. Has anyone found a fix for this, or is this program just useless?

Same exact problem here, I have iRate working, but it's lacking features, is buggy, and development is very slow or at a standstill not sure which.
Gnomoradio looks great, but for the fact its wiggin out.

---

