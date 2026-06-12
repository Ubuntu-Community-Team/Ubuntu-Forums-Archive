---
title: "Evolution and Knode Authentication Problems"
date: 2008-06-10
forum: General Help
---

### Post by producer on 2008-06-10
I couldn't log on last night.  Don't know why and couldn't fix it.  I re-patitioned the disk and re-installed from the Hardy CD.  The CD was good with the md5 sum, and installation went smoothly.  I Updated and everything seemed OK.  I am using Moizilla Firefox to browse and Evolution for email and Knode for newsgroups.
I can't get onto almopst anything though. Evolution was the first to balk and keeps asking me for my password over and over again.  I'm sure it right.  I talked to the support people that host my web site and they have no trouble at all getting on to my Webmail page.  But even outside of Evolution I have the same problem authenticating to the webmail page with Firefox.  So I'm pretty much cut off from email.  Then the surprising thing was this afternoon when I went to et up Knode and that won't keep my password at all.  I type it in and click OK.  Then I go to download the newsgroups and nothing happens.  no lights blinking on the modem, nothing.  When I go back to the setup, the password box in clear again, like I never typed it in.
There has to be a common problem and I suspect it's PAM, but I'm not sure and I don't know enough to do anything about it anyway.  The problem is not going away and it's very distressing.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by producer on 2008-06-10
It would have been a help if somebody could have pointed me in the right direction, but i might need a litle more than that.  I'll try to get back here tomorrow.

---

### Post by Zill on 2008-06-10
producer:  You have referred to three different applications so I suggest that we break the problem down into discrete problems and tackle them one at a time.

Firstly, does Firefox work correctly **with this installation** for "normal" websites (eg. [www.google.com](www.google.com))?  If so then describe exactly what happens when you go to your webmail website.  If you are having trouble authenticating your webmail account then you may be entering the wrong info.  Please check this.

Advise how you get on and then once we get your webmail working we can move on to Evolution.

---

### Post by producer on 2008-06-10
Yes, Firefox works well with ordinary web sites.  I have re-installed the Hardy Ubuntu from the disk, without updates so far, and I am having intermittent problems with authentication and whenever I have to enter data to a web site, like posting this message.  Sometimes it works and sometimes I have to do it twice or more to get it going.  Earlier it was just not working at all.  I could not get onto my webmail page.  It would just keep asking me again and again for the user ID and password.  I have been entering this data for about 12 hours now and checked it many, many times.  It's as right as I can make it.  Now after my second reinstall in 24 hours, I have gotten the firefox to access my web mail.  I don't know what is different, and it's only done it once and I'm afraid to log out of it now, but I will soon.  I'm dealing with what email I can, while I can get to it, before I do anything heroic.
Then I'll try logging out and see if I can get back in.  I'm open to other suggestions.  Yes, I've tried variations on my password as it was written. like upper case and lower case, and so on.  It makes no difference.  The times when it has worked as been when it's typed as it is written in my little book on the desk here.  I have often used it.

---

### Post by producer on 2008-06-10
Update.  I have logged off my webmail and was able to log back in with no trouble.  My screen earlier did turn light and fuzzy, although I could still see the web page, (two processes seemed to merge their displays, (firefox and gedit), and it froze everything I had to push the reset button to restart.  Nicely enough when I had rebooted, I started up Firefox, recovered the previous session and I was still logged on to my webmail session.  Go Figure!

---

### Post by Zill on 2008-06-11
producer:  It seems that your installation is corrupted in some way.  Re-installation is not generally necessary and your comments about freezing and the merging of firefox and gedit displays worries me. :(

You said that the iso md5 sum was correct so I suggest that you burn a new CD at slow speed (x2 or x4).  With the new CD in the drive, there should be a menu option to check the disk for defects.  Run this and, if OK, run the live version of the CD.

Open Firefox and log into your webmail account - see if this works correctly.

Regarding usernames and passwords, Linux is case-sensitive but MS Windows is not!  It is likely that your webmail is not case-sensitive but it is always a  possibility.  Your ISP should have advised you of *exactly* what to use when you signed-up so please make sure you enter this correctly.

If the live Firefox webmail works reliably then we can consider installing Ubuntu to your hard drive (again!).  Please advise.

---

### Post by producer on 2008-06-11
Yes, it was corrupted and the DSL connection here is very slow even for dialup service which it isn't.  It's taking a long time to get all the upgrades.  It would take several days full time to download a new .iso image and the current one is supposed to be good it passes the md5 sum tast and the self test when it is booted.  I have no reason to mistrust the CD.  Firefox is now running reliably off my new installation and gets me into my webmail now every time.  Evolution still does not get my emails, although I can send alright.
I reinstalled Ubuntu to my hard drive yesterday and it's working to some extent, it's really slow to install the updates because of the physical connection problems and maybe, just maybe, Sympatico is slowing down the throughput to prevent music downloads.  if so this is playing havoc with those of us trying to keep Linux updated.  Sympatico is affiliated, (owned?), with/by M$.  Maybe the music downloads are just the excuse and they want to disrupt Linux users.

---

### Post by Zill on 2008-06-11
producer:  If the md5 sum for your iso image is correct then there should be no need to download it again.  If the CD has been checked for defects as I suggested and has verified OK then it should work.  However, a bad CD can cause various problems so we need to eliminate this.  Have you tried burning a new CD at a slow speed?

If the new CD is good then it should run properly as a live CD.  I suggest leaving work on the installed version until we get a live CD that runs reliably.

I am not sure if you are using DSL or dial-up but your problems may be down to the DSL connection - I doubt if Ubuntu will run well on dial-up.  If this is not reliable then you will get a lot of connectivity problems.  It may be worth contacting your telco and/or ISP to check the connection.  I doubt if music downloads are to blame as the whole internet is full of this stuff :rolleyes:

---

### Post by producer on 2008-06-11
I think I'm slowly getting things into shape.  I'm going to keep working on the installed version.  The connection is a DSL, but the throughput is eratic.  It works at about 30 kbps for a few seconds then shuts down completely for several minutes and then a little more gets through.  Overall the throughput would be poor for a dialup.  Knode tries to download a list of newsgroups and times out waiting for it.  I can't get newsgroups working because of that.  I don't know if that's affecting Evolution or not.  It seems to accept the password now, but never downloads anything.  It's just abysmal.
Thanks for the ideas.  Lets give it a rest and see what happens.  I'm through the worst of it,... til next time.

---

### Post by Zill on 2008-06-11
producer:  OK.  Glad you are making progress.  It sounds like the problem is primarily with the DSL connection.  Hopefully your telco/ISP should be able to fix that.

Anyway, post back if there are any more problems.  Good luck!

---

