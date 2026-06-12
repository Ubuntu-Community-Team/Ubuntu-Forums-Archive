---
title: "Firefox Keeps Crashing"
date: 2005-09-03
forum: General Help
---

### Post by EnderTheThird on 2005-09-03
Several times every session, Firefox will just keep crashing apparently for no reason.  I'll use my back button, click a link, or go to a bookmark, and then Firefox just closes with no warning or error message.  These sites work fine with Firefox under XP, so it's not something wrong with the site(s) that's making Firefox close.  Any ideas on what I can do?  I'm really getting sick of this!

---

### Post by numberexhaust on 2005-09-03
You know, I think it may be a problem with Flash or some other plugin.  I still have the problem, but I'm too lazy to fix it  :???: .

Try installing flash, etc, and see if it works.

---

### Post by Adam Lee on 2005-09-03
I have the exact same problem.
One day FF would crash 3 times, and on the other day FF works just fine.

And I have no idea why it's acting that way...

---

### Post by numberexhaust on 2005-09-03
Tell you what... let's work on this problem.  Next time your firefox browser crashes, try opening the same web page in a different browser (i tried Mozilla, but.......ya and it crashed as well).  I'm gonna see if I can get a hold of some other browsers and try those.  In the mean time, see if you guys can come up with some other ideas.

---

### Post by Kjell on 2005-09-03
Yes, it apears to crash whenever a plug (flash) is used.
I think Firefox, mozilla and Epiphany uses the same "engine", as they all crashes.

I'm trying Opera  to see if there is a diff - not a crash so far.

But I want Firefox.

---

### Post by danhm on 2005-09-03
[QUOTE=Kjell]Yes, it apears to crash whenever a plug (flash) is used.
I think Firefox, mozilla and Epiphany uses the same "engine", as they all crashes.

I'm trying Opera  to see if there is a diff - not a crash so far.

But I want Firefox.[/QUOTE]
 My mplayer plugin sometimes causes Firefox to crash. I'm willing to bet it's related.

---

### Post by dducko3 on 2005-09-03
I seem to be haveing this problem also, it developed after I installed the Nvida-gtx drivers through Synaptic.  The first and only place I have did it so far is on [www.imdb.com](www.imdb.com) and searching for Xenia Seeberg.  Also another place I have crashes is in Neverwinter Nights... several places last night if I was near certain people I would  crash.  As long as I didnt warp near them (I was on as DM) I was fine.

*edit* Trying to connect to a movie crashed it, also just going to Nvidia's site also crashed it.  I have Flash and Totem-Xine installed.

---

### Post by d1337 on 2005-09-03
Have you installed java and flash as per the [unofficial guide?](http://www.ubuntuguide.org) What version of FireFox?

---

### Post by EnderTheThird on 2005-09-04
Firefox version:  1.0.6
I installed Flash player when I installed Ubuntu, but I forgot to install Java.  I just finished that.  I'll try to pinpoint at least one specific webpage that keeps crashing Firefox and let you guys know what it is, to see if it's a universal issue with Firefox or something.

---

### Post by dducko3 on 2005-09-04
[QUOTE=dducko3]I seem to be haveing this problem also, it developed after I installed the Nvida-gtx drivers through Synaptic.  The first and only place I have did it so far is on [www.imdb.com](www.imdb.com) and searching for Xenia Seeberg.  Also another place I have crashes is in Neverwinter Nights... several places last night if I was near certain people I would  crash.  As long as I didnt warp near them (I was on as DM) I was fine.

*edit* Trying to connect to a movie crashed it, also just going to Nvidia's site also crashed it.  I have Flash and Totem-Xine installed.[/QUOTE]

Ok thanks to everone in the IRC channel.  I got my Repos worked out (thanks ompaul) and got the right flash plugin and then my Nvidia drivers installed (which was my issue) Firefox works fine once again for me.

---

### Post by numberexhaust on 2005-09-04
[www.imdb.com](www.imdb.com) works fine for me... the one that gets to me is [www.geminidj.com](www.geminidj.com) : note this site has a big flash intro thing, which is why i related it to the plugins in the first place.

---

### Post by dducko3 on 2005-09-04
[QUOTE=numberexhaust][www.imdb.com](www.imdb.com) works fine for me... the one that gets to me is [www.geminidj.com](www.geminidj.com) : note this site has a big flash intro thing, which is why i related it to the plugins in the first place.[/QUOTE]

That one works for me just fine.  What program did you install as flash?

---

### Post by numberexhaust on 2005-09-04
I tried using the ubuntuguide, but it couldn't find that package... so I went into synaptic and found libflash-mozplugin.  I think that's flash player.  If it isn't, where do I get it from??

---

### Post by gw90se on 2005-09-04
Mine crases when I hit the back button while on Google, or if I right click and save link as... Somedays it's fine, some days, arghhh!!!!

---

### Post by numberexhaust on 2005-09-04
What are some good linux browsers that are not mozilla based?  I would be perfectly willing to test one or two out for a while.

---

### Post by d1337 on 2005-09-05
Did you change your repositories as instructed in the ubuntuguide prior to looking for the flashplayer?  The correct flashplayer is flashplayer-mozilla which is iirc not in the stock repos.

d1337

---

### Post by numberexhaust on 2005-09-05
[QUOTE=d1337]Did you change your repositories as instructed in the ubuntuguide prior to looking for the flashplayer?  The correct flashplayer is flashplayer-mozilla which is iirc not in the stock repos.

d1337[/QUOTE]
 lol ya, i'm not THAT Much of a noob.  But it is strange, because I do seem to have a lot of other things missing from my list in Synaptic.... any ideas for that?

---

### Post by Skatox on 2005-09-05
I had those problems too, but i fixed with just changing the firefox's plugin directory to a link to mozilla's plugin directory

rm /usr/lib/mozilla-firefox/plugins -r
ln -s /usr/lib/mozilla/plugins /usr/lib/mozilla-firefox/plugins

Try this. :razz:

---

### Post by numberexhaust on 2005-09-05
[QUOTE=d1337]Did you change your repositories as instructed in the ubuntuguide prior to looking for the flashplayer?  The correct flashplayer is flashplayer-mozilla which is iirc not in the stock repos.

d1337[/QUOTE]
 oh I feel like an idiot now... i didn't have multiverse added in the repositories.  I had it before, but then I had to reinstall.

---

### Post by numberexhaust on 2005-09-05
Big Break here guys.... I solved the problem apparently.

Even after installing Ubuntu's mozilla flashplayer, it still didn't work.  I had to go to the macromedia site and install their linux flash player manually, and now everything seems to be working fine.  I'll test it out for a while and make sure that fixed the problem.  But until then, that's what I recommend.

---

### Post by y2kprawn on 2008-05-04
Yea, I have this problem as well, but not related to additional packages, sometimes I go into gmail and click a link in my email to a html page and BANG firefox vanishes. 

I am more inclined to think this is more to do with the default install on Ubuntu being in Beta 5.

---

