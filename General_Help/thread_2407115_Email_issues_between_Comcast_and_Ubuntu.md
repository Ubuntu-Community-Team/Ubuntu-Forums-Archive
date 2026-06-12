---
title: "Email issues between Comcast and Ubuntu???"
date: 2018-11-29
forum: General Help
---

### Post by jaxxas on 2018-11-29
Hello all, I'm new here and of course I come with a problem.

Running Ubuntu 18.04 LTS and it has been working perfectly for the most part until today. I'm using the Thunderbird email client and today it just stopped receiving email from Comcast. The exact error is..

"Thunderbird"

"Failed to connect to server imap.comcast.net."

Strangely it will send through Comcast but I get an error. Also I have no problems with sending/receiving through a Gmail account.

So I called Comcast and they know nothing about, said everything is fine on their end. They did tell me that Comcast was changing their imap port to 995 soon!

Next I installed the Evolution email client and it doesn't work nor does it give an error. I can also send through Evolution without error. 

So at this point I'm thinking maybe that the issue is not an email client but rather with Ubuntu.

Any thoughts, ideas or suggestion are certainly appreciated!


Joe

---

### Post by wildmanne39 on 2018-11-29
This may help you.

[https://ubuntuforums.org/showthread.php?t=2406399](https://ubuntuforums.org/showthread.php?t=2406399)

---

### Post by oldfred on 2018-11-29
Same error.
I changed to imap about 6 months ago. But have used same settings otherwise for years.

Iphone & web mail on Comcast home page still work ok.

---

### Post by Butthead on 2018-11-30
After the last upgrade on 11-29, I've been having the cannot connect to imap.comcast.net problem too (claims the "server is not found" under Kmail settings (my personal email client)), along with the KDE Wallet Service box popping up asking for a password every three minutes or so  I think the problem a corrupt ubuntu-keyring upgrade file or libgs9-common upgrade file (one of the error messages I'm getting in the KDE Wallet Service box that pops up refers to a file with a "9" in it), but what do I know?  

I hope they fix this soon though, having to input my password into the KDE Wallet Service box every three minutes is getting to be a real drag.  Not being able to receive email messages in Kmail is a real drag too, but connecting to Comcast through the browser itself is at least a workaround. :icon_frown:

---

### Post by oldfred on 2018-11-30
I did the fix in the link in post #2.
The one I did was change this in settings:
From:
 imap.comcast.net
To:
imap.ge.xfinity.com

Only had to enter password once, but checked the box to save it.

---

### Post by pbmalloy on 2018-12-01
Yes - thanks - this [imap.ge.xfinity.com] name worked for me as well.  Bravo!

Sure wish I hadn't contacted Comcast though and asked about it - they got my modem into a continuous reboot cycle despite me asking them not to.  My chat was just
about whether they had HEARD about any IMAP connection issues.

I literally said "You aren't going to reboot my modem are you."  Answer: "No."  Okay, I say.

Him: "No I'm just sending some settings!" 10 seconds later the modem is recycling - Obviously this kills my connection.

I finally get back on line using phone as WiFi hots spot - I'd left the chat window open and see that the first guys says "I waited - but you weren't there.  <Ending Chat>.  Seriously???!

Boom! Internet gone for 40 minutes - started new chat and finally the second person finally got my modem to settle down but it kept rebooting periodically for the next hour.  

 This seems like a name resolution issue for Comcast that exists for Linux machines. I'm not sure how to communicate that to them without them being stupid.  The modem is older but I never thought it was a problem. They are sending me a new one.  All other services were working and it is only the Linux machine that was having problems.  I have about 20 devices on my home network and the android and windows machines aren't having problems. My android was set up as IMAP.  I tried POP3 on my Linux box and it wasn't accepting that either.  So the problem seems to be limited to Linux - it started only two days ago for me (the 28th of November).  I'd been using POP3 when my email stopped working, but upgraded to IMAP a few days before (26th?), but just on the Linux box and it had been working for several days. The reason I'd changed is  I'd found a note somewhere that they were obsoleting the old less secure port - so that wasn't a red flag.  Two days later I'm having a problem with IMAP too.

Sorry about the Comcast rant but I thought it might save some people some heartache.  The solution proposed seems like a band-aid because the documentation from Comcast STILL says use
 
imap.comcast.net as we all know does NOT work with our 18.04 Linux distro. Based upon my empirical observations,  I'm thinking this may be a Linux problem actually or Comcast is permitting or implementing something that interferes with the name resolution that is not consistent with some RFC.

---

### Post by oldfred on 2018-12-01
Two years ago I sent Comcast's modem back.
Just saw they raised price of modem "rental" to $11/month.

I purchased a good modem & router as separate devices as I was not sure I wanted them in same location in house. A few issues getting it to pass thru for my security modem which still is theirs and an old POS.

---

### Post by Butthead on 2018-12-01
So, are we saying here that it's something Comcast screwed up by renaming the mail server somehow and not K/Ubuntu upgrade related? :confused:

I'm not an Xfinity fan by far, I just find it funny that the Comcast mail server seemed to go all wonky in retrieving email's right after a K/Ubuntu upgrade. :?:

I might not remember any "fixes" I did to get things working again if Canonical issues a upgrade fix for this issue. :-k

---

### Post by freemedia2018 on 2018-12-01
> **Butthead said:**
> I just find it funny that the Comcast mail server seemed to go all wonky in retrieving email's right after a K/Ubuntu upgrade. 

Not sure this isn't post hoc-- perhaps it's related to the upgrade, perhaps it isn't. I was curious if this was just a Linux problem, and searching for more information I found someone having the same trouble with Windows 10 for the first time, two days ago. That was pretty much the first search result as well.

I'm new to the forum, not sure if linking to the xfinity forums is the best thing to do, but don't be 100% sure this is just affecting GNU/Linux users. I don't use their email so my personal experience won't help here.

---

### Post by QIII on 2018-12-01
I am now able to connect to the imap servers without any issues -- and I have not gotten any Ubuntu updates that might be responsible.

Since Comcast seems to have an irrational fear of Linux (odd, since they use a lot of Linux servers -- a point which I have made often when their techs say they don't support Linux), that fear apparently directed in particular at Ubuntu, it would surprise me not in the least that Ubuntu was targeted.

---

### Post by freemedia2018 on 2018-12-01
> **QIII said:**
> their techs say they don't support Linux

I decided a while ago that the best way to talk to tech support is just to pretend you're using Windows when they try to walk you through something, and then translate their instructions to OS of choice.

Basically like you would with tech support scammers while wasting their time, except you're actually trying to get them to help troubleshoot your connection. Half the time they can't reset the modem and it has to be done manually anyway, but at least they can tell you if there is an outage on their side.

---

### Post by kurt18947 on 2018-12-01
> **pbmalloy said:**
> 
........................................................................
Sorry about the Comcast rant but I thought it might save some people some heartache.  The solution proposed seems like a band-aid because the documentation from Comcast STILL says use
 
imap.comcast.net as we all know does NOT work with our 18.04 Linux distro. Based upon my empirical observations,  I'm thinking this may be a Linux problem actually or Comcast is permitting or implementing something that interferes with the name resolution that is not consistent with some RFC.

Documentation being behind is not an Comcast exclusive. We have Verizon FiOS who switched to using AOL's email system not long after buying AOL. Some documentation - and Thunderbird - seem to think verizon.net email servers are still operating.

---

### Post by QIII on 2018-12-01
And now ... not able to connect.

Nothing on my system changed, so I still suspect this is on Comcast's end.

---

### Post by walts48 on 2018-12-02
> **kurt18947 said:**
> Documentation being behind is not an Comcast exclusive. We have Verizon FiOS who switched to using AOL's email system not long after buying AOL. Some documentation - and Thunderbird - seem to think verizon.net email servers are still operating.

I switched to Comcast from Verizon last November, long after I moved my Verizon email to AOL servers.

I test release candidates of Thunderbird and create my still working verizon.net POP account using the account wizard in Thunderbird with no problem. Send a test email from that account to my Gmail IMAP account. As far as I can tell verizon.net email servers are working just fine.

Just finished testing 64.0b4 today and the current release 60.3.2 on the 29th.

[https://www.thunderbird.net/en-US/thunderbird/60.3.2/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/60.3.2/releasenotes/)

Here is the bug report for the issue [Bug #1805027 “systemd-resolved can't resolve Comcast mail server...” : Bugs : systemd package : Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1805027")

---

### Post by Kris_M on 2018-12-02
[SIZE=4]EDIT: ignore all this
go here
[https://ubuntuforums.org/showthread.php?t=2406399&page=4&p=13820955#post13820955](https://ubuntuforums.org/showthread.php?t=2406399&page=4&p=13820955#post13820955)
and read post 35.
[/SIZE]

- - - - -

I believe this started around when I put up a new clean 18.10 (around Nov 27) though someone said it started on Nov 19.
Works fine on my win7

[http://forums.mozillazine.org/viewtopic.php?f=39&t=3044315&p=14817098#p14817098](http://forums.mozillazine.org/viewtopic.php?f=39&t=3044315&p=14817098#p14817098)

any ideas?
(gmail works fine with TBird)

EDIT : same failure with my 18.04.1 build, so not 18.10 related.

---

### Post by QIII on 2018-12-02
Threads merged.

---

### Post by Kris_M on 2018-12-02
sudo ufw status shows inactive.
set active and...
edit: playing with ugfw yields no change. 
traceroute times out after a few times for pop3.comcast.net or mail.comcast.net

Again, on win7 TBird does not show this prob.

google finds this interesting twist for kubuntu.

[https://support.mozilla.org/en-US/questions/1242290](https://support.mozilla.org/en-US/questions/1242290)

-

strace: attach: ptrace(PTRACE_SEIZE, 2589): Operation not permitted

Check out
[https://ubuntuforums.org/showthread.php?t=2406399&page=4&p=13820955#post13820955](https://ubuntuforums.org/showthread.php?t=2406399&page=4&p=13820955#post13820955)
and go to post 35.
Ubuntu prob.

---

