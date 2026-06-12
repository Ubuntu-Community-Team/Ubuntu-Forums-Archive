---
title: "Ubuntu is slowly self-destructing on me &gt;.&lt;"
date: 2006-10-22
forum: General Help
---

### Post by Chake99 on 2006-10-22
My Dapper Drake is not crrently in the best of shapes. The first error I noticed was that when I ran a graphical restart (ctrl alt backspace) my sound would not work and I would have to reboot the comp to listen to music. 

Then my internet failed. It was during some network problems but now the connection is back up as I type from a different comp connected to the net from the same network.

A little bit later the game soldat which was being run through wine stopped working. It would take longer to start up to the options and start screens, and then would freeze when I tried to start a game.

Then after a few plays of wine-starcraft it too began to freeze at the load screen. 

I have no clue what to do. 

Does anyone have any advice for troubleshooting or fixing? Could upgrading to edgy somehow help? Is it possible to upgrade from a livecd?

I'm so confuzzled :S. Help.

Thanks in advance.

---

### Post by buttari on 2006-10-22
Ubuntu Dapper is becoming unstable for me too. Here's a list of problems that I have now (and I didn't have on a fresh install):
1) after the famous X upgrade that broke everything, my X some times restarts for no apparent reson when I'm using mplayer.
2) if I log out I can't log in anymore. Ctrl-alt-backspace works most of the times but sometimes breaks down too.
3) evolution has a bunch of problems. If I don't start it withing (say) a minute from the session start, I cannot start it anymore (I get some nonsense error message about system configuration). Filters stopped working: I can run them manually but not automatically. If there's no network I have to kill evolution from the command line with "kill -9" otherwise it hangs.
4) I always have to close ekiga with kill -9 otherwise it hangs (like evolution).
5) after the latest update firefox crashes continuously.

To this I have to add (and I'm sad to say this) that even if I ask help on this forum I never get an answer. I hope upgrading to Edgy will fix my problems. This said, emacs works and that's almost all I really need to survive.
Regards

Alfredo

---

### Post by podunk on 2006-10-22
It makes me sad to see posts not replied to also.

I read a couple of your posts in the past &#8211; you've been very kind and helpful to others. Unfortunately I don't really know how to fix the problems you 2 are having. In particular I don't know how to help you, I mean you not only know how to use emacs &#8211; you like it. :-) You're a much more knowledgeable user than I.

I got caught by the kernel upgrade too. It was like 3 days after I installed. I was just starting to get a working system. I was also in the middle of installing compiz at the time with no luck. I can't say for sure it was all the updates fault &#8211; you had an alpha user installing beta software &#8211; not a very stable combination! :-)

The more I  fixed the worse the problems got &#8211; and I just started over. I formatted to partitions and loaded in the live DVD an started from scratch. This particular set up went much better, it was much longer lived &#8211; but I ended up trashing it in the end and started over again.

This time I had quite a bit more experience and had learned my lesson about beta software and alpha users. For instance I installed, then did all the updates then installed my video card. Once  I had a stable set up I backed it up (insanely easy in Linux), and do a fresh back up every week. Then and only then did I start moving my data from Windows.

I no longer install software updates the first day they come out. :-D There are some updates I just won't do period. For instance it took forever to get wine to run the one program I really want from the windows world. I'm not going to do a thing to change it now. It will just have to be a little insecure &#8211; the program I use it for doesn't go on the net so it should be ok.

One thing I've done is carve out a separate partition for /home. This way if the OS gets hosed (excuse me &#8211; if I break it) my data and most settings will be doubly protected, first by being on a separate partition second with weekly backups.

Personally, if I were having the troubles you 2 were having I'd backup my data (there is simple backup installed by default and hubackup in the repositories) and start over. Theres a chance that all your instabilities stem from the bad kernel update and there is no way to recover from them. And of course, that's why no one else has said anything, an awful lot of folks here are like me, and we don't know what to do either.

I've read many nice things about Edgy, but once again it's beta software and an I'm still an alpha user here &#8211; I'm on release 0.0.0.1 so I'll hold off on that upgrade for a year or so I think. :-)

---

### Post by buttari on 2006-10-22
Well,
don't get me wrong...I don't blame anybody for not answering my posts especially users; maybe developers can/should make the effort of investigating a little bit more problems that are posted on the forum but it's not right to expect anything even from them because they are doing it for free. I've been a gentoo user for three years and the forums were just great: whatever problem you had (and people that knows gentoo may imagine what kind of problems you can have with such a distribution) could be solved searching/posting on the forum. Anyway I think ubuntu is far more stable than any other distro and all the minor problems I have are well worth to have a nice/cuttingedge/justworks system.
Regards

Alfredo

---

### Post by bsussman on 2006-10-22
I may be way off base here...

The problems you are reporting are odd, catastrophic and feel like they are going to be very hard to fix by 'repairing'.

Thousands of serious folks are running thousands of systems and the reports of this level of decay are not many.  This tends to support a theory that your problems are not due to the basic quality and reliability of standard ubuntu.

I assume you have been using the system updating facilities to remain current.

So...

1.  Have you installed anything using methods other than the 'plain old' package installers?  Special packages, builds from source, changes to the standard management tools, parameters, settings, etc?  Non-standard repositories?  Monkeying with permissions on files that belong to the system?  Manually editing configs that were automatically generated?

2. Have you studied your logs to liik for screwy events at the same times as your failures?

3. Is it possible your hardware is marginal?  Memory and disk problems are at the top of my suspect list.

Frankly, if it were my system, I'd put another hard drive in it and re-install.  If you have been VERY careful to record all changes and do only things you understand, I'd not recommend this - it is too Windows-like, but sometimes you just gotta do it.

If you upgrade to 6.10 and your problems go away, I am absolutely sure I have listed your problem above - 6.06 is very reliable and 6.10 is  only marginally better, probably in code improvements and not in bugfixes.  Your re-install would merely repair the damage and I would expect to hear the same question in 6 months.

---

### Post by buttari on 2006-10-22
> **bsussman said:**
> I may be way off base here...

The problems you are reporting are odd, catastrophic and feel like they are going to be very hard to fix by 'repairing'.

Nothing catastrophic...if firefox crashes I restart it. Actually what happens with evolution (especially the non-working filters) is pretty boring.

> 
Thousands of serious folks are running thousands of systems and the reports of this level of decay are not many.  This tends to support a theory that your problems are not due to the basic quality and reliability of standard ubuntu.

I assume you have been using the system updating facilities to remain current.

So...

1.  Have you installed anything using methods other than the 'plain old' package installers?  Special packages, builds from source, changes to the standard management tools, parameters, settings, etc?  Non-standard repositories?  Monkeying with permissions on files that belong to the system?  Manually editing configs that were automatically generated?


nope. Always used apt with usual repositories and neve installed any exotic software. Whatever I build from source I build it in my home directory so it never affected the rest of the system.

> 
2. Have you studied your logs to liik for screwy events at the same times as your failures?

Actually I didn't (laaaazy) :-)

> 
3. Is it possible your hardware is marginal?  Memory and disk problems are at the top of my suspect list.

Well this can be. I'll go for a memtest. Anyway most of my problems just come after a sw update and this just makes me think that it's a software problem. I mean, if I upgrade firefox and it starts crashing it can't be my hard disk... and the same happened for X.

> 
Frankly, if it were my system, I'd put another hard drive in it and re-install.  If you have been VERY careful to record all changes and do only things you understand, I'd not recommend this - it is too Windows-like, but sometimes you just gotta do it.

If you upgrade to 6.10 and your problems go away, I am absolutely sure I have listed your problem above - 6.06 is very reliable and 6.10 is  only marginally better, probably in code improvements and not in bugfixes.  Your re-install would merely repair the damage and I would expect to hear the same question in 6 months.

I'll tell you what I'll do: after (say) a couple of weeks from the release of edgy I'll back up my disk and go for the upgrade. If I'm not happy with the results I'll go for a clean install.
Anyway I've been a linux user for a long time and I'm perfectly used to all this kind of problems so, as I already said, I'm not blaming anybody and I'm not complaining about the quality of ubuntu.
Regards

Alfredo

---

