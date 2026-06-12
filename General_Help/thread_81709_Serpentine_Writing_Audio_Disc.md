---
title: "Serpentine Writing Audio Disc"
date: 2005-10-25
forum: General Help
---

### Post by darkoptix on 2005-10-25
When I burn a music cd in Serpentine, the writing audio disc dialog box comes up and stays there despite me attempting to close. It continues to stay there after shutting down Serpentine. Anyone having these issues?

---

### Post by trigg on 2005-10-27
[QUOTE=darkoptix]When I burn a music cd in Serpentine, the writing audio disc dialog box comes up and stays there despite me attempting to close. It continues to stay there after shutting down Serpentine. Anyone having these issues?[/QUOTE]


Yes.  Same problem here.  Python problem?

---

### Post by ad noiseam on 2005-12-04
Same problem here.

Moreover, how do you kill the "Writing Audio disc" window? It just stays here, whatever I do. Which process is this, and how do I stop it?

---

### Post by Michel F on 2006-01-05
Same problem also. And the CD will not burn.

---

### Post by StefanoCole on 2006-01-05
Form me the same. The audio CD was not burned. I eventually succeded in burning the audio CD using "cdrecord" from terminal.

---

### Post by ad noiseam on 2006-01-05
I had this problem again and again, and eventually switched to K3b (well, I switched to KDE altogether anyway), which works perfectly.

---

### Post by Michel F on 2006-01-05
Thanks. Any other suggestion than "switch to K3b", because, you know, it works in windows, so I could also "switch to Windows"...

---

### Post by ad noiseam on 2006-01-05
Yes, I know, that's a pretty lame answer, but it's the only solution I found. :(

---

### Post by towsonu2003 on 2006-01-05
how about filing a bug and voting for it?

---

### Post by Michel F on 2006-01-05
Thanks again.

So far, the research I made within the forums leads me on the following tracks:
1/ try and use the terminal command cdrecord (thanks StefanoCole)
2/ check permissions on the cd drive
3/ update the kernel from 386 to 686

I am just wondering if there are:
1/ other things I should consider?
2/ in the three possibilities above, things that are irrelevant.

Also, beeing new to Ubuntu, Is this issue soething that was present in former versions of Ubuntu?

And, last, How do you file a bug ?

---

### Post by hobbit1983 on 2006-01-05
I don't know how to fix the serpentine pbm and perhapes this falls into the "switch to (insert ubuntu derivative or other OS) pond BUT

in Hoary I used gnome baker (available in the repos through synaptic) to burn audio CD's and that worked well.

Just another option

---

### Post by Michel F on 2006-01-05
I forgot to mention that I have a similar (?) issue with GnomeBaker. It starts to prepare the files for writing to disk but then freezes on the actual burn. The difference with Serpentine, is that I can stop the program and no windows stay open.

So I guess from that that the issue is not Serpentine-specific but rather general for cd-burning.

---

### Post by towsonu2003 on 2006-01-05
[QUOTE=Michel F]
And, last, How do you file a bug ?[/QUOTE] lol
check out this one: [https://wiki.ubuntu.com/ReportingBugs](https://wiki.ubuntu.com/ReportingBugs)

---

### Post by Michel F on 2006-01-05
Thank you. 

The "bug" is already reported as # 16296 and has many variants ... but apparently no resolution. Disappointing.

---

### Post by towsonu2003 on 2006-01-05
[QUOTE=Michel F]Thank you. 

The "bug" is already reported as # 16296 and has many variants ... but apparently no resolution. Disappointing.[/QUOTE]
if you didn't do so already, first try their suggestions, anf if not working -> then vote for it (or post a comment indicating you have the same thing) to the variant most similar to yours... more the voters / commenters -> more attention bug would get from devs ;) ...

good luck... it seems you're gonna have to switch o something else...

---

### Post by Michel F on 2006-01-07
OK. some time after and some CDs burnt, this is the situation.

1/ Serpentine. I have exactly the same symptoms as bug # 16296 reported in bugzilla. What I did is to try to use directly the cdrecord command as suggested in this thread.

The cdrecord device=/dev/hec *.wav command did not complete with an error message telling that the wav files have a size not exactly fitting the record size on a CD and suggesting the -pad option.

So probably the reason of the Serpentine and Gnome baker failure was due to this partivcular situation.

The cdrecord device=/dev/hec -pad *.wav command completed successfully. However this process introiduces a 2 second gap between the tracks, which is not desirable for me.

So I guess that the bug in Serpentine is that it is not able to burn audio files with a size not the size of a CD record, and that it has no fall-back procedure such as using the -pad option. I will document that in Bugzilla some time.

2/ in the meantime I installed K3B and ... it worked very well. So it is able to handle this size issue correctly (i.e. it has a fall-back procedure).

3/ I returned to Gnomebaker. I installed the backport Breezy version (0.50). And it worked well with two remarks:
- It displays a message saying that the cd-writer is not mounted. However, clicking on the message lets the process go on and complete.
- with no indication, it inserts 2-second gaps between tracks. to avoid this I found that one has to use the dao burn mode (and not tao or default).

So for Gnomebaker, you have to use the 0.50+ version and depending on your usage play with the tao/dao option.

BTW, the Gnomebaker site lists the following fix in the 0.50 release : "Fix Bug #1273910 0.4.2 > Xlib: unexpected async reply", which is the type of messages I had before.


Hope this helps the forum users ;)

---

### Post by Michel F on 2006-01-08
Ok, thinking about Serpentine, I did the same, that is UPGRADE TO THE LAST VERSION, namely 0.6.4 in Breezy Backports vs 0.6.3 out of the box.

and it works well FOR MY PURPOSE. :p :p :p 

So, as newbie, I must recognize many things:
1. turn your tongue seven times in the mouth before speaking. Do some research before.
2. when asking for help, be precise : versions, specific purpose, logfiles,...
3. relax, people are working hard on their projects to make them better and solve little headaches.

---

