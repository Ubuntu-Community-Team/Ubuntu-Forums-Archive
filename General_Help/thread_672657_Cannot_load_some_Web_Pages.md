---
title: "Cannot load some Web Pages"
date: 2008-01-19
forum: General Help
---

### Post by Chessmaster on 2008-01-19
Hi there, 

Only been using Gutsy for a few weeks now and like it. EXCEPT, I cannot load some web pages. I have problems with Yahoo and Hotmail. I can log in (sometimes) but it is painfully slow and no images load - just text (if I am lucky) but I cannot access my emails. I have searched the web and forums and see that some people have similar problems although they have either found no solution or the solution they have does not work in my case.

So far I have tried Firefox, Epiphany and Opera. Same problem. I have uninstalled and reinstalled - browsers and Javascript (as I suspect it is a javascript problem as I get java script errors show in opera error consol - see screenshot attached - there are loads of errors!). I have disabbled/uninstalled all addons (such as adblockers / popup blockers).

As I said above, I suspect it has something to do with Java Script. I notice that all the images that will not load are those that are redirected images (i.e. when I look at the properties of the non-loading images they have an address different from that of the site). Could this be an encryption problem perhaps?

I have not noticed any problems with any other sites (only Yahoo and Hotmail)

Any suggestions / ideas would be greatly appreciated. I would love to be able to check my email from my computer! 

Cheers

---

### Post by erfahren on 2008-01-20
it probably has nothing to do with javascript - that's just bad coding on websites - it's common

I've heard of some people experiencing problems with ipv6 although I don't know much about it.

I can provide some links to other threads that you can look at

[http://ubuntuforums.org/showthread.php?p=3989760](http://ubuntuforums.org/showthread.php?p=3989760)
[http://ubuntuforums.org/showthread.php?t=373545](http://ubuntuforums.org/showthread.php?t=373545)
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)
[http://ubuntuforums.org/showthread.php?p=4132456](http://ubuntuforums.org/showthread.php?p=4132456)

hope that can get you started - good luck!

---

### Post by LaRoza on 2008-01-20
I use Opera 9.50b, and have no problems with it. Poorly designed sites cause trouble in any standards aware browser.

If scripts cause a problem, which is possible, disable them.

---

### Post by Chessmaster on 2008-01-20
Hi, thanks for you suggestions.

I have turned off IPV6 (and on again, and off agin) but it makes no difference. 

I am currently running Opera 9.50 at the moment and I still have the same problems. So, I assume that it is not a browser problem as the problem is in Firefox, Epiphany, and Opera.  

When I go to the Mozila diagnostics [http://forums.mozillazine.org/viewtopic.php?t=288184]("http://forums.mozillazine.org/viewtopic.php?t=288184") I cannot load image no. 4 - which suggests that some software is blocking it. BUT, I am not running any adblock or firewall software. 

Anyone got any other suggestions? 

Cheers

EDIT: I have also loaded up Firefox in SAFE mode and it makes not difference.

---

### Post by erfahren on 2008-01-20
that image was blocked for me too - with both Ffx and Opera - the page just may be a little dated and the blocking is standard now

I thought that maybe Flash might be causing some sort of problem - what version are you using - or do you have it working for Opera?

--- you could try using the OpenDNS addresses to see if that does anything - see the section here:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

---

### Post by Chessmaster on 2008-01-20
Tried the Open DNS changes as you suggested and it didn't make any difference unfortunately - thanks for the suggestion though. 

I am using the Java release installed from Synaptic, and I have no problems with pages displaying Java - [www.java.com](www.java.com) test page tells me I am running latest Java, version 6 update 3, and their Java applet works fine. 

Anyone got some other suggestions?

Cheers

---

### Post by Kevbert on 2008-01-21
You could try the Swiftweasel browser and Evolution email client at least to get Hotmail.
I installed Swiftweasel along with all codecs, plug-ins via Automatix [http://www.getautomatix.com]("http://www.getautomatix.com")
Install it via Apt (Terminal).
The Evolution install can be found at [http://ubuntuforums.org/showthread.php?t=200408&highlight=Hotmail]("http://ubuntuforums.org/showthread.php?t=200408&highlight=Hotmail")
Good luck.

---

### Post by sports fan Matt on 2008-01-21
Just in case you want it, here is the link to swiftweasel: [http://swiftweasel.tuxfamily.org/](http://swiftweasel.tuxfamily.org/)

Hope this helps:)

---

### Post by rosswmcgee on 2008-01-21
I have the same problem with loading my yahoo with firefox, but Epiphany does not have the problem

what could be the problem?

---

### Post by sports fan Matt on 2008-01-21
Considering they both run off a Gecko engine, I have no idea.  The only thing I know as was pointed out to me was you couldnt import ff extentsions

---

### Post by rosswmcgee on 2008-01-21
I removed adblock/installed adblock plus/ installed flashblock/problem solved.:)

---

### Post by rosswmcgee on 2008-01-21
I uninstalled adblock/ installed adblock plus/ installed flashblock/ Voila! problem fixed.

---

### Post by Chessmaster on 2008-01-22
Hey all, thanks for the suggestions. Unfortunately, no success. 

I have tried installed and uninstalled No Script, Ad Blocker, Ad Blocker Plus, Flashblocker.

Also downloaded Swiftweasle and all to no avail. 

I don't have this problem in windows XP, and I have used lots of different browsers (Firefox, Opera, Epiphany, Swiftweasle) so I am assuming that it is not a browser problem - most likely something to do with my Ubuntu settings?

What I have noticed is that the images that do not load are those from redirected or third party (?) websites: i.e. when I am trying to access [www.yahoo.co.uk](www.yahoo.co.uk), all images from uk.yahoo.com load, but those from uk.ard.yahoo.com   or   l.yimg.com will not load.  

On [http://login.live.com/login.srf](http://login.live.com/login.srf)... the images from [http://gfx1.mail.live.com/mail/w2/ltr/LoginImages/WLW2_signup.jpg](http://gfx1.mail.live.com/mail/w2/ltr/LoginImages/WLW2_signup.jpg) (I think this is where they come from) will not load.  

I am determined to get to the bottom of this (from what I can tell I am not the only one with this problem but have not seen any solutions that work for me).

Any ideas?

---

### Post by AnonCat on 2008-01-22
Could there be an MTU problem with your modem/router?  Some webpages/ISPs don't do well with the standard 1500 value for some reason.  Have you tried loading those web pages in Windows or another OS on the same machine?  If you have problems loading the pages there  you probably have a bad modem setting somewhere.

---

### Post by Chessmaster on 2008-01-22
I can load these pages in XP (dual booting) on the same machine using the same modem. I also tried changing my MTU settings (as was suggested in another thread on a similar topic) but no luck I'm afraid.

---

### Post by plucky on 2008-01-22
Chessmaster,

When the page fails to load, do you get the **Server Reset** page eventually?

 I have had a very similar problem with an old **2Wire** wireless modem router which I was sharing between two computers. Some webpages wouldn't load with Ubuntu on both computers but were ok with Windows. I have now reverted back to my Speedtouch modems until I can replace the wireless modem router. The webpages now load correctly. 

Do you have another means of connecting to the internet? This will eliminate the modem router as the possible cause.

Good luck..

---

### Post by Kevbert on 2008-01-23
Interesting... The plot thickens.
I've tried the UK yahoo page [http://uk.yahoo.com]("http://uk.yahoo.com") using XP IE7 on my laptop, and Ubuntu 7.10 , Swiftweasel on my desktop.  It seems that some l.yimg.com images may be blocked according to Adblock Plus (that comes with Swiftweasel as standard) and some aren't.  If you go to Tools - Page Info you can see the images (and sources) that either Firefox or it's derivative Swiftweasel does show but not the missing ones.
Could this be a java related thing as I notice Java does not seem to fully work ?

---

### Post by Chessmaster on 2008-01-25
Thanks for the suggestions! 

My problem has been solved, I can now load up hotmail and yahoo. How this was solved I don't know. It was solved indirectly - so I don't know if you can actually say that it was 'solved' - perhaps just 'resolved'. 

Anyway, I was connecting to my modem via the "Network" manager. I accidentally removed the icon from my task bar and the only way I could start up my modem was by writing "wvdial" in the terminal. Now, I have access to yahoo and hotmail but I don't know why??!! Very strange indeed. (Is this a bug? Should I report it on launchpad?)

To others that cannot load yahoo and hotmail, try connecting to the internet by typing "wvdial" in the terminal as opposed to the network manager / icon, it may just work.

This of course has raised other problems, as I don't want to have to run wvdial in the terminal. And I cannot get Gnome PPP working without playing around with file permissions.   Anyhow, I will post that as a new thread as it is a new problem. 

Thanks all.

---

### Post by fragos on 2008-01-26
Give us some offending URLs to try.  Sometimes images and videos are embedded with javascript or active-X envelopes.  There are also some variances in how HTML is executed.  Web pages will sometimes try to determine the browser and selectively execute HTML for them.  Windows IE is biggest offender.  There's no substitute for a webmaster debuging his web pages on multiple browsers.  Some web pages are coded in such a way that they only work properly on IE.

---

### Post by MarkX on 2008-01-29
> **fragos said:**
> Give us some offending URLs to try.  Sometimes images and videos are embedded with javascript or active-X envelopes.  There are also some variances in how HTML is executed.  Web pages will sometimes try to determine the browser and selectively execute HTML for them.  Windows IE is biggest offender.  There's no substitute for a webmaster debuging his web pages on multiple browsers.  Some web pages are coded in such a way that they only work properly on IE.

I have similar problems with google.co.uk and hotmail login on a friend's computer I just set up today. 
Google wouldn't load at all and no logos on the Hotmail sign-in page.
Fine with Firefox on XP but not on Ubuntu 7.10.
Interestingly, it all worked fine at my house with my ISP but not at theirs which has a much slower and noisier broadband line and different ISP.
Their ISP wants the MTU set to 1400 but I haven't done that on the router or  XP (it work fine there) and I have no idea of how to do it in Ubuntu either.

Another problem I had was that when I rebooted the router Ubuntu wouldn't find the internet afterwards and I had to reboot the computer too.

---

### Post by fragos on 2008-01-29
I accessed google in the UK and was even able to login to my iGoogle but served from the UK instead of the US.  I tried hotmail.co.uk and got a login screen.  There were some icons but I don't have an account to log in under and am not familiar anything MS.  I use gmail.

---

### Post by MarkX on 2008-01-30
I found this thread but haven't had a chance to try what it says:
[http://ubuntuforums.org/showthread.php?t=573867](http://ubuntuforums.org/showthread.php?t=573867)

It's about changing the vendor thing in Firefox from "ubuntu" to "firefox".
Does this mean that Microsoft /Hotmail tries to spy what browser is being used?

Come on folks this is a major problem! It was most embarassing to set up friends computers and Ubuntu not working properly but XP flying along!

---

### Post by erfahren on 2008-01-30
the only other article I've come across about some sites not loading is this:
[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)
there is a link in the article to a bug thread which proposed the easiest fix of just installing Firestarter which would make a change in iptables.

One of those sites the author of the article mentioned - Ohio State University - I couldn't load and I already have Firestarter installed, so I don't know. (I was able to load the other site given.)

> **MarkX said:**
> 
Does this mean that Microsoft /Hotmail tries to spy what browser is being used?

many sites do that (browser detection) they even detect the operating system. They do that so instead of creating one site that is cross-browser compatible (or, backwards comptible) that the web designer and/or the site owner would consider boring, they can tailor the site to work differently in different browsers. Either that or they can just spit out that "your browser not supported - please update your browser to take advantage of the advanced (translated: "stupid and bandwidth intensive") features of this site" message. (I get that alot using Opera - hence the apparent bitterness - lol !)

---

