---
title: "Ongoing issue, cant find fix.Need help"
date: 2007-12-10
forum: General Help
---

### Post by justinclark on 2007-12-10
In a nut shell this is my problem(s).  The symptom is like this: When I first turn on my laptop everything works fine.  If I open a browser and surf the web for 10 or so minutes everything slows down terribly.  The scrolling get VERY laggy and flash heavy sites are a NIGHTMARE.  Videos such as on you tube play so choppy its unbearable.  Im using a Dell Latitude D600, 1600Mghz Pentium M, 1gig ram, ATI Radeon 9000.  I have been trying to fix this for months and have searched around like crazy.  I have noticed that xorg uses an *** load of cpu % and am not sure why.  I have read through multiple threads with same issue but no fix for me.  I have tried many different browsers (firefox, swiftfox, swiftweasel, Opera) all the same issue.  I have generic driver installed for the graphics card but after lots of research I dont think I need special ones.  Though we tried and found them.  After installing I get ATI control center in apps but it wont open.  It says I dont have the right drivers installed.  
I have tried my hardest but I need some help.  I switched to Ubuntu because they say "it just works" but at this point the only benefit over windows is the way it looks.  I want to keep Ubuntu I really like it but I use the web so often I absolutely cant have browsing this slow.  Any suggestions for an aggravated new guy?  Thanks to anyone who may have a solution.
-Justin

---

### Post by blu3ness on 2007-12-10
are you opening a page with java applets? sometimes java_vm can take quite a bit of cpu to load up in firefox.

---

### Post by justinclark on 2007-12-10
Probably but the issue is deeper than that.  Just opening Firefox sends cpu to 100%.

---

### Post by justinclark on 2007-12-10
Anyone out there? Help before this thread falls to the dreaded lonely 2nd page!:)

---

### Post by oldos2er on 2007-12-10
What version of Ubuntu are you running? This isn't much to offer, but it really sounds like video driver problems.

---

### Post by justinclark on 2007-12-10
Gutsy

---

### Post by forestpixie on 2007-12-10
can you get the restricted driver installed - system >admin >restr driver - see if there's one for it

---

### Post by justinclark on 2007-12-10
Not that I can see.  only 2 there one for a modem not being used and one for family chipset that is being used.

---

### Post by forestpixie on 2007-12-10
it does sound to me like a video driver problem - what is xorg.conf using for a driver?

---

### Post by justinclark on 2007-12-10
How do I check that?

---

### Post by forestpixie on 2007-12-11
```
cat /etc/X11/xorg.conf
```

there's a 'driver' section, probably other ways to do it but I don't know

---

### Post by justinclark on 2007-12-12
under the drivers section it says 'ati'.

---

### Post by Dryw Paulic on 2007-12-12
What are you using for your swf player? You noted that flash heavy websites are a pain. Does this only happen when you visit flash-heavy websites? If so, what are you using for your swf player? I had tried gnash but found it was rather choppy and sometimes locked up my browser. I've since gone to Flash Player 9 directly from adobe and have had no problems since. 

You can get it from here: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux")

-Dryw

---

### Post by justinclark on 2007-12-12
I do use adobe flash.  It will happen even if I dont visit a flash site.  Literally if I surf the web, even just this forum, for a short time after I turn my laptop on, It just all of a sudden slows down.  It just seems to happen faster if I visit a flash site.  Then once it happens it just stays slow,  ctrl-alt-backspce wont fix it.  And in case youre wondering about my hsi speed,its very fast (10 Mbps) so no,its not an internet service issue.  I never had this problem with Windows.  Can anyone help me?

---

### Post by Dryw Paulic on 2007-12-12
Hi Justin,

Could you post a list of running processes before and after the slowdown as well as screenshots (or numbers) on the system load? That will help us figure out if you're system is being forkbombed.

Also, computer stats would be appreciated. 

-Dryw

---

### Post by justinclark on 2007-12-12
I have my laptop info in my first post if thats what you meant.  As soon as I get home I will get some screen shots and try and post them here.  I use the TOP command for that correct?  Thanks

---

### Post by Dryw Paulic on 2007-12-12
Hi Justin,

Ah, sorry, missed the specs in the first post:

Dell Latitude D600
1600Mghz Pentium M
1gig ram
ATI Radeon 9000

Grabbing the output of ps -aux and a screen shot of the graphs in the system monitor would likely be sufficient :).

-Dryw

---

### Post by justinclark on 2007-12-16
Ok sorry it has taken so long but here we go...
/home/justin/Desktop/Screenshot-justin@justin-laptop: ~.png

/home/justin/Desktop/Screenshot-System Monitor.pngfile:///home/justin/Desktop/Screenshot-System%20Monitor.png
file:///home/justin/Desktop/Screenshot-justin%40justin-laptop%3A%20~.png


Hmmm, I obviously dont know how to post the actual pic... HOw do I do that?  I tried copy/paste and just dragging th image.

---

### Post by forestpixie on 2007-12-16
use post reply rather than quick reply

in the post toolbar there is an icon like a paperclip - tht's the attach button - then navigate to the folder, upload and it should be in your post

---

### Post by justinclark on 2007-12-16
Alright and as of now I am not currently experiencing the slow browsing issue.  After the problem kicks in I will post the sreenshots again.

---

### Post by forestpixie on 2007-12-16
If all's well at the moment I would mark this solved - and do another thread when and if it returns

---

### Post by justinclark on 2007-12-16
If you read the rest of the post will will see that this is how the problem always is.  After browsing for a bit (especially flash sites) It slows down significantly.  Nothing yet has been solved.

---

### Post by justinclark on 2007-12-16
And here are those screenshots after the problem has kicked in (Slow typing, scrolling, mouse movments, video so choppy its not watchable)

---

### Post by forestpixie on 2007-12-16
yea realise that - thing is if you add to this post and it goes past page 1 - none will know - if you start a new thread, you can reference to this - and it'll come up as unanswered on a search, people search for unanswered posts

---

### Post by Dryw Paulic on 2007-12-16
The load averages on the system monitor are fairly normal. That being said, load averages are a bit hard to read. For Example:

megatron@STARSCREAM:~$ uptime
 11:29:42 up 14:42,  2 users,  load average: [COLOR="Lime"]0.29[/COLOR],[COLOR="Orange"]0.29[/COLOR], [COLOR="Red"]0.17[/COLOR]

Load average is a time-dependent average of the load on the system. The above example shows green, orange and red loads. This correlates to the load averages over the last 1, 5 and 15 minutes respectfully. The actual measurement of the average is the sum of the number of processes in the queue and the jobs currently running on the CPU. Thus Load is not equivalent to CPU load.It's more or less equivalent to the number of processes on the system.

It's also a moving average with smoothing, which means that your not quite getting the instantaneous load on the system. Typically, if you are seeing spikes in the load they won't show up in the load average (or at least not blatantly) as the rest of the data will smooth out the spikes in the long run.

Anyway, long story short - - when you look at the load averages you should interpret them more on the side of "The number of processes running" rather than the CPU load. You should also take into account that since it is a smoothed average, it can take a few minutes before your average hits what the system is actually experiencing. Finally a high load average could potentially mean that the system will be sloggish and unresponsive. However the interpretation of that number depends on your system, as bigger systems can handle more processes at once. 

Feel free to let me know if you experience the same sloggish behavior you were before and take care when using load averages to determine how busy your computer is! When in doubt, look at the CPU, memory and swap utilization as well. If you find that the system is indeed under a lot of load (either by interpreting numbers or by system responsiveness) look for processes that are eating a lot of resources.


-Dryw

---

### Post by Flare183 on 2007-12-16
Bring up the system monitor sort the list by cpu usage and then you will find the program that is slowing you down.

---

### Post by Dryw Paulic on 2007-12-16
Thanks for the update Justin. Looks like something is hammering the system in terms of CPU utilization. Your memory/swap utilization looks fine.

Use the command "top" from the terminal to see the processes which are taking the most resources.

-Dryw

---

### Post by justinclark on 2007-12-16
According to TOP its that darn xorg.  It idles around 15% and jumps around to even 40% (as of now) though I have seen it up to 70 or 80% while bowsing flash and such.  Also if it helps to know, restarting does not fix it.

---

### Post by Dryw Paulic on 2007-12-16
Hi Justin,

I would recommend turning of Beryl/Emerald to see if that brings xorg to normal levels of CPU usage. There was a reported issue in the mailing list regarding Radeon 9000 series cards (specifically 9600) a few months back that seemed to cause high CPU usage. It looks like no one was able to reproduce the problem though.

That being said, one lister had mentioned that it seemed to be related to the transparent cube feature, so I would try turning just that plugin off. If that works, you may want to try his fix - - turning up the inactive_opacity gconf key to a value of 100. 

More info on his post can be found here:

[http://readlist.com/lists/lists.freedesktop.org/xorg/2/13403.html](http://readlist.com/lists/lists.freedesktop.org/xorg/2/13403.html) 

-Dryw

---

### Post by justinclark on 2007-12-16
Thanks for the sugestion, how do I look at/change  /apps/compiz/plugins/cube/screen0/options/inactive_opacity ( Im still new).

---

### Post by Dryw Paulic on 2007-12-16
The "inactive opacity" key should be equal to "Opacity When not rotating", so you should be able to do:

System -> Preferences -> Advanced Desktop Effects Settings -> Desktop Cube -> Transparent Cube and turn the "Opacity When not rotating" to 100.

If you want to do it from the command line, do:

```
cd ~/.gconf/apps/compiz/plugins/cube/screen0/options
```

You can then open up the %gconf.xml file and change the inactive_opacity manually. Crtl-Alt-Backspace to restart X after the change.

-Dryw

---

### Post by justinclark on 2007-12-17
Well I tried that but it didnt fix, it was already set to 100.

---

### Post by justinclark on 2007-12-19
Anyone else have any ideas?  Perhaps my video drivers?  Radeon RV250 [Mobility FireGL 9000] is what I have, not sure what drivers I need or how to install them:confused: .  I cant help but think I wish I could afford a macbook right now, I wouldnt have to worry about any of this crap....

---

### Post by Dryw Paulic on 2007-12-20
Hi Justin,

If you turn off all the desktop effects (e.g turn off compiz) does the problem go away? You can do this through Preferences -> Appearances.

Cheers,

Dryw

---

### Post by justinclark on 2007-12-20
Yes, when I turn off the visual effects the problem does go away.  What does this mean?  As silly as it may seem the visual effects was a big part of me switching to Ubuntu.

---

### Post by justinclark on 2007-12-20
Well it doesnt completely go away, but it does help.  Flash is still a little slow but significantly better.

---

### Post by Dryw Paulic on 2007-12-20
Hi Justin,

I think this may be a driver issue then. I would run through the following tutorial:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

That particular tutorial is for fiesty, however it should lend it self well to gutsy. You can safely ignore the page where they go over how to install beryl though, as that has been replaced with compiz. To install compiz on gutsy (you should already have it) do:

```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```

Let me know how it goes!

Cheers,

Dryw

---

### Post by justinclark on 2007-12-20
I keep geting this (justin@justin-laptop:~$ glxinfo | grep vendor
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual
)
when trying to remove and replace the drivers.

---

### Post by justinclark on 2007-12-22
Alright well when I made changes to the xorg.config file (according to the above tutorial) and saved I lost my screen.  When I turn it on I get the Dell screen, then the ubuntu loading screen, then it just goes black.  So here I am at the public library.  Help?

---

### Post by justinclark on 2007-12-25
So I fixed the xorg.comfig file.  That tutorial didnt work for me.  Can anyone help me with these drivers?

---

