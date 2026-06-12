---
title: "Firefox slow on SOME sites"
date: 2007-08-26
forum: General Help
---

### Post by kc0eks on 2007-08-26
Hello all,

lets get the specs down first:
Firefox 2.0.0.6
Kubuntu Feisty

I noticed since I installed Kubuntu that firefox runs very poorly in general, but specifically when I visit certain sites. 

If it has lots of images SOMETIMES it will scroll jumpy and very slow
Some sites with very little imagery also scroll and react slowly (java or something maybe?)

to make things more confusing some sites with tons of images scroll and work perfectly.

To try and figure this out I have tried the following:
Loading a site in Konqueror that behaves badly in firefox- When I do this the scrolling/laggyness is gone.
Firefox safe mode - Doesnt seem to make a difference at all
Disabling All extensions and themes - Doesnt help either.
Rebooting the entire pc doesnt help
restarting firefox obviously doesnt help either.

How would I go about figuring out what is causing this and how to fix it?

Thanks all!

---

### Post by kerry_s on 2007-08-26
do you have adblock+ & noscript, they block out 90% of the bad? slow sites are usually due to bad scripting or just plain poor design, some use alot of linked images from other sites & some connections just can't fetch them fast enough. if you can provide links to the trouble sites, so we can look at might help see if it's not just you.

---

### Post by kc0eks on 2007-08-26
> **kerry_s said:**
> do you have adblock+ & noscript, they block out 90% of the bad? slow sites are usually due to bad scripting or just plain poor design, some use alot of linked images from other sites & some connections just can't fetch them fast enough. if you can provide links to the trouble sites, so we can look at might help see if it's not just you.

I do use adblock...I dont use noscript...I will give that a shot as it seems to be some sort of scripting or something...

as for the sites that this happens on...well as is typical I dont have a list. I will start one though :)

---

### Post by kc0eks on 2007-08-26
ok here is a site that behaves badly for me:
[http://kcphoto.smugmug.com/gallery/1383687/1/65362118](http://kcphoto.smugmug.com/gallery/1383687/1/65362118)

you may need to change the style (top right corner) to journal.

when i try to scroll this page it is like using a very very old pc with no ram..it just jump/jerks all over and slowly moves...

and this site also: 
[http://moronland.net/moronia/moron/1077/](http://moronland.net/moronia/moron/1077/)

---

### Post by kerry_s on 2007-08-26
nope i had no problems, i even disabled adblock & noscript.

---

### Post by kc0eks on 2007-08-26
> **kerry_s said:**
> nope i had no problems, i even disabled adblock & noscript.

well that tells me its just my system I suppose, though I dont know what exactly.
Thanks for your assistance :)

---

### Post by Warren Watts on 2007-08-26
What kind of graphics card do you have?  If it is an older card without a lot of RAM, pages loaded with graphics may very well slow down things like scrolling.

---

### Post by kc0eks on 2007-08-27
> **Warren Watts said:**
> What kind of graphics card do you have?  If it is an older card without a lot of RAM, pages loaded with graphics may very well slow down things like scrolling.

its a nvidia 8800 so that shouldnt be slowing it down. The first site I listed had lots of graphics, the second barely had any. yet both behave similiar, slow/laggy scrolling.

---

### Post by sorin7486 on 2007-09-17
Hello,

        I have the exact same problem with daper on my computer at work but things work fine on festy (my laptop) .... both have ati cards btw and neither play nice ;) ... I was just about to write a post looking for an answer for this but I just found mine: upgrade :)

---

### Post by Natume on 2007-10-23
Not to beat a dead horse (then again, has anything been solved yet?), but I'm having similar issues.  The first site given above actually works perfectly fine for me, but the second has the characteristic slowdown.  (I usually check by opening a terminal on top of the site when it fills the whole screen and move it around with the mouse at a moderate pace.  If the response lags significantly, the site's got issues by my watch.)

What's interesting is that it seems to be either good (no to very little lag) or rather poor (considerable graphical lag) with nothing in between.  [www.gametap.com](www.gametap.com) and transmission.m0k.org also have similar issues for me, though it seems the majority of sites work fine.  I've got an ATI Radeon X800 Mobility, so I doubt that's the issue for websites (for games would be a different story).  Likewise, I have 2 Gigs of RAM.

A point to note is that the cpu works up considerably on the bad sites as well.  It's a 3.0 GHz processor, and considering my computer's build, I can hear the fans rev up considerably on those sites.  (As annoying as the fan volume may normally be, it's a pretty accurate measure of how much power the computer's putting out with respect to different components at any one time.)

What I'm concerned about is if the problem is fundamentally graphical in nature (and would affect applications that utilize the internet or significant graphics processing capabilities) or if it's mostly relegated to internet browsing.

If anybody has information, it would be most useful.

~Natume

UPDATE :

Okay, so I just now realized that the fglrx driver wasn't in use, because it's a restricted driver.  (As mentioned, I have an ATI card.)  Enabling it in the Restricted Drivers Manager pretty much solved the problems, though there's still a little lag here and there (though greatly, greatly reduced).

So, if anybody else was unobservant in the same manner I was, let this be a lesson to you =p.  Otherwise, I hope that similar problems can be fixed easily enough.

---

### Post by sorin7486 on 2007-10-24
Hey... I have an ATI card too ... I think the problem might be with the driver.... 2D acceleration might be needed for those pages and as ATI drivers mostly suck ... oh well .... 

I tried the pages from the live CD when I reinstalled Ubuntu last week ... and everything worked just fine.

---

### Post by Natume on 2007-10-24
> **sorin7486 said:**
> Hey... I have an ATI card too ... I think the problem might be with the driver.... 2D acceleration might be needed for those pages and as ATI drivers mostly suck ... oh well .... 

I tried the pages from the live CD when I reinstalled Ubuntu last week ... and everything worked just fine.

Have you tried looking at the restricted devices manager?  I just edited my post above to say that things got better when I realized I needed to enable it there.  It might not be the problem for you, but considering I didn't think to look there until I happened upon it just now, it's worth a shot.

---

### Post by sinaen on 2007-10-26
Writing in textboxes in linux  ubuntu 7.10 is intollerable slow. i deinstalled beryl and all the graphics briversl to that proogram uhm beryl and emerald.

the system went faster but still writing in textboxes in browsers is so slow that you have to wait for about a half an hour to get this text to show up, do you have the same problem 
its not just firefox its in galeon too...  i havve an ati card maybe its that the drivers isnt loaded correctly to that card. il try. but i think they should have done something about it before releasing gutsy

---

### Post by tersus on 2007-10-28
i don't know if you solved the problem or not yet, or if this is the case you're describing, but i was having the same problem on my PC and worked around it by creating a new firefox profile through firefox's profile manager.  sites loaded at least 3-4x faster. i had to reimport all my new settings, but it's definitely worth it when browsing is such a huge drag (waiting 5-10 seconds for the nytimes front page to load).  probably caused by some bad cache buildup since my last reformat.

---

### Post by jenhsun on 2007-10-28
Speed up browseing in Ubuntu

1. Disable IpV6 in Firefox
About:config , find ipv6 and disable

2. find.http.pipelining.maxrequests and set to 10

3. In /etc/hosts comment out all reference related to ipv6

# xxxxx.ipv6

4. Add the following to /etc/sysctl.conf (524288 could be too large, try 262144 or 131072 in place of 524288 if you don't notice an improvement. 524288 worked best for me though.):

    # Tweaks for faster broadband...
    net.core.rmem_default = 524288
    net.core.rmem_max = 524288
    net.core.wmem_default = 524288
    net.core.wmem_max = 524288
    net.ipv4.tcp_wmem = 4096 87380 524288
    net.ipv4.tcp_rmem = 4096 87380 524288
    net.ipv4.tcp_mem = 524288 524288 524288
    net.ipv4.tcp_rfc1337 = 1
    net.ipv4.ip_no_pmtu_disc = 0
    net.ipv4.tcp_sack = 1
    net.ipv4.tcp_fack = 1
    net.ipv4.tcp_window_scaling = 1
    net.ipv4.tcp_timestamps = 1
    net.ipv4.tcp_ecn = 0
    net.ipv4.route.flush = 1

    Then to have the settings take effect immediately, run:

    sudo sysctl -p

    Source:
    [http://ubuntuforums.org/showthread.php?t=251509](http://ubuntuforums.org/showthread.php?t=251509)

Or for higher broadband connection

#net.core.rmem_default = 4194304
# default values seems to work fine with my system
net.core.rmem_max = 4194304
#net.core.wmem_default = 4194304
# default values seems to work fine with my system
net.core.wmem_max = 4194304
net.ipv4.tcp_wmem = 4096 87380 4194304
net.ipv4.tcp_rmem = 4096 87380 4194304
#net.ipv4.tcp_mem = 256960 256960 4194304
# this should be uncommented only if it's not working well
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

# don't cache ssthresh from previous connection
net.ipv4.tcp_no_metrics_save = 1
net.ipv4.tcp_moderate_rcvbuf = 1
# recommended to increase this for 1000 BT or higher
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_congestion_control=cubic


5. Gksudo gedit /etc/modprobe.d/aliases
6. Find the line: alias net-pf-10 ipv6 and to:  alias net-pf-10 off

7. Try OpenDNS

---

### Post by YetAnotherNoob on 2007-11-07
I also have this problem, (I think).  Let me clarify what I have:
only the scrolling on some sites is slow.  The download speed is fine.  This is not related to bandwidth.

I believe FF is having issues displaying some of the more complicated layouts.  gmail is v. slow.  As are the sites in the post above.  I will try playing around with some of the options in FF configuration page:
about:config

:confused:

---

### Post by DeepNoob on 2007-11-08
"This is not related to bandwidth."

I think you're right.  On my install FF seems to get into a cpu hog mode after a little usage, depending on what site has been visted.  It then continues to use over 10% of the cpu cycles, and sometimes much more, even if it is minimized to the task bar.  It shouldn't be hogging the cpu while minimized and doing nothing.

---

### Post by jrcmuniz on 2007-11-09
> **YetAnotherNoob said:**
> I also have this problem, (I think).  Let me clarify what I have:
only the scrolling on some sites is slow.  The download speed is fine.  This is not related to bandwidth.

I believe FF is having issues displaying some of the more complicated layouts.  gmail is v. slow.  As are the sites in the post above.  I will try playing around with some of the options in FF configuration page:
about:config

:confused:
Hello "YetAnotherNoob"

I think it'll fix you problem with gmail... try to use this link to open you gmail account: [http://mail.google.com/mail/?ui=1](http://mail.google.com/mail/?ui=1)

This is a problem related with the GUI 2 from gmail... just it... 

Hope this helps

Cheers

---

