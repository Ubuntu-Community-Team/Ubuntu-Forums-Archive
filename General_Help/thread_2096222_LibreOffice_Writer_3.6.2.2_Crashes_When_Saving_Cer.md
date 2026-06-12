---
title: "LibreOffice Writer 3.6.2.2 Crashes When Saving Certain .DOC Files"
date: 2012-12-19
forum: General Help
---

### Post by Kirk Schnable on 2012-12-19
I am also making this post on the LibreOffice forums...
[http://en.libreofficeforum.org/node/4971](http://en.libreofficeforum.org/node/4971)

We are using LibreOffice in a test deployment right now, (most of our staff are still using an older version of OpenOffice), and I have encountered an unusual issue with one of my test subjects.

They have a legacy Word file from when they had a Windows laptop, and they are trying to make and save changes to the file.  It seems to me, when the DOC converter is running during the save process, something goes wrong, and LibreOffice Writer crashes.

I have tried to reproduce the problem on my desktop with LibreOffice 3.5.4.2 and the problem does not occur.

When saving from the problem version 3.6.2.2, if the file is re-saved as an ODT instead of a DOC, nothing goes wrong, and the software behaves as expected. (I have asked the staff member to do this as a workaround while I talk with the community about the problem.)

I am trying to narrow down this issue, and if someone can inform me of where I can look for additional crash information, I'd be happy to supply it.  When I launch LibreOffice from the terminal, there is no output, just falls back to a terminal prompt when it crashes.

Every time it crashes, I see an entry like this logged into Kern.log and Syslog.
```
Dec 18 15:13:26 computername kernel: soffice.bin[12843: segfault at 68 ip b17caedd sp bfd067a0 error 4 in libswlo.so[b1328000+b20000]
```

If anyone would be willing to try to reproduce this problem on other versions, etc... here is the original file which is encountering this problem.

[http://www.epecweb.com/pub/libreoffice-troubleshooting-dec2012.doc](http://www.epecweb.com/pub/libreoffice-troubleshooting-dec2012.doc)

I would appreciate any input the community might have. 

Thanks,
Kirk

---

### Post by Rexilion on 2012-12-19
Might be [this one]("https://bugs.freedesktop.org/show_bug.cgi?id=55422"). Can you confirm it's the same behaviour described?

---

### Post by Kirk Schnable on 2012-12-19
> **Rexilion said:**
> Might be [this one]("https://bugs.freedesktop.org/show_bug.cgi?id=55422"). Can you confirm it's the same behaviour described?


The behavior sounds similar, but I have not seen the kind of crash output described in the bug report.

What do I need to do to get crash output from LibreOffice?

---

### Post by Rexilion on 2012-12-20
I think it's safe to assume you are talking about the same bug. A specific commit is cherry-picked so I guess that will be an easy fix.

I'm assuming you are using Ubuntu 12.10 (since you mentioned libreoffice 3.6.2.2, but your sig says 12.04).

The Ubuntu Libreoffice PPA: [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)
Contains 3.6.4, I suggest you try that version. Very big chance it contains the bugfix.

---

### Post by IanGrayland on 2012-12-20
your .doc file saves ok here on 3.6.4 on ubuntu 12.04

3.6.2 was still too squiffy for prodution use here. we are still on openoffice 3.3 for production as we use base with MySQL and LO was totally borked in that area until very recently. we have test installs of 3.6.4 on 12.04 and 10.04.4 going well so far, just maybe some minor formatting details on doc files still to be sorted.

no 3.6.4 in the ppa yet for 12.04 or 10.04 so you have to do manual install of .debs - after you've done it a couple of times it's very easy (i can do it in my sleep now)

Regards, Ian

---

### Post by Kirk Schnable on 2012-12-20
Thanks for your responses, both of you.

> **Rexilion said:**
> I'm assuming you are using Ubuntu 12.10 (since you mentioned libreoffice 3.6.2.2, but your sig says 12.04).

I am a 12.04 user, but my end users here are still mostly running 10.04 LTS.  They will probably be receiving a system wide upgrade here pretty soon... we are planning on reimaging most of our computers this winter break with an Xubuntu 12.04 image.

On my test subject's computer, I either used a PPA or I ended up downloading the latest debs from the website... I can't really remember which, it all runs together up here.  I think I did deb packages because the PPA didn't have a recent enough version for my liking.

> **IanGrayland said:**
> your .doc file saves ok here on 3.6.4 on ubuntu 12.04

3.6.2 was still too squiffy for prodution use here. we are still on openoffice 3.3 for production as we use base with MySQL and LO was totally borked in that area until very recently. we have test installs of 3.6.4 on 12.04 and 10.04.4 going well so far, just maybe some minor formatting details on doc files still to be sorted.
Good to know.

> **IanGrayland said:**
> no 3.6.4 in the ppa yet for 12.04 or 10.04 so you have to do manual install of .debs - after you've done it a couple of times it's very easy (i can do it in my sleep now)
I know how to do it from debs... I will probably end up giving that a shot.

Kirk

---

### Post by vanadium on 2012-12-20
I confirm the crash with your document on stock LibreOffice on Ubuntu 12.12 (Version 3.6.2.2 (Build ID: 360m1(Build:2))
LibreOffice "grays" out, then disappears. A "Sorry, Ubuntu 12.10 has experiences an internal error" appears.

Resaving as .odt works, however, after closing the doc, then reopening the odt, Save As doc triggers the error again.

---

### Post by Kirk Schnable on 2012-12-20
> **vanadium said:**
> I confirm the crash with your document on stock LibreOffice on Ubuntu 12.12 (Version 3.6.2.2 (Build ID: 360m1(Build:2))
LibreOffice "grays" out, then disappears. A "Sorry, Ubuntu 12.10 has experiences an internal error" appears.

Resaving as .odt works, however, after closing the doc, then reopening the odt, Save As doc triggers the error again.

Thanks for the information, vanadium.  Looks like this might really be a LibreOffice 3.6.2.2 issue then.  I have asked my staff member when would be a convenient time to try an upgrade. I should be able to get to it today and we'll see if that resolves the problem. (I have a hunch that it will.)

---

### Post by Rexilion on 2012-12-20
Upgrading to 12.10 and using the LibreOffice ppa will get you 3.6.4. I overlooked the fact that it's version stalled for 12.04. Sorry about that. Good luck upgrading!

---

### Post by Kirk Schnable on 2012-12-20
> **Rexilion said:**
> Upgrading to 12.10 and using the LibreOffice ppa will get you 3.6.4. I overlooked the fact that it's version stalled for 12.04. Sorry about that. Good luck upgrading!

Due to the size of our deployment, and our reliability requirements, we prefer to stick with the LTS releases here.

I did install the deb packages for 3.6.4 this morning, and my staff member reports that he no longer has the issue with the document.  It looks like the update resolved the issue.

---

### Post by IanGrayland on 2012-12-20
> **Kirk Schnable said:**
> 

we are planning on reimaging most of our computers this winter break with an Xubuntu 12.04 image.




Hi Kirk, 
Just in case it helps, I find unity works a treat once you shut off the global menu system. All your users have to grasp is opening programs from icons in the (hidden) dock on the left side with a single click instead of double clicking desktop icons. It is real handy for say a quick look at your file system whilst you are browsing the net with a big window. you don't have to move windows out of the way to get to your launchers. that kind of thing. Xfce is great, but it is quite a bit different to good old gnome 2 especially from the admin point of view.
Hope I'm not making false assumptions here about your choices/experience

Ian

---

### Post by Kirk Schnable on 2012-12-20
> **IanGrayland said:**
> Hi Kirk, 
Just in case it helps, I find unity works a treat once you shut off the global menu system. All your users have to grasp is opening programs from icons in the (hidden) dock on the left side with a single click instead of double clicking desktop icons. It is real handy for say a quick look at your file system whilst you are browsing the net with a big window. you don't have to move windows out of the way to get to your launchers. that kind of thing. Xfce is great, but it is quite a bit different to good old gnome 2 especially from the admin point of view.
Hope I'm not making false assumptions here about your choices/experience

Ian

I am using Unity here, even on my work computer which is running Ubuntu 12.04.  I also use Unity on my personal laptop.

However, my user base just made a transition from Windows to Linux in the past two years.  The change to Xubuntu will be welcome because it will bring a lot of bugfixes we've had in the mix for awhile (we're not going to go out of our way to publicize that the change happened, we spent some time theming XFCE to look like Gnome 2 did, and the average user might not even realize we did the upgrade)...  I also created a custom boot splash (Plymouth theme) which contains our school name and logo, we will not have any obvious Xubuntu branding present on the deployment.  My point is, I have expended significant effort in ensuring this transition is a completely smooth, seamless one, so it does not cause any undue pressure on our Linux deployment.

With many of my users, I don't feel that a change to Unity would be embraced, as some of our users still have mixed feelings about the changes we've made so far, even though the changes have brought them significant performance increases.

In short, we spent the last 2 years getting our users used to Gnome 2 Linux, and shortly after our decision to launch with the desktop environment, we found out it was no longer going to be developed.  It was very disappointing, and we looked for the closest alternative we could find.  We currently have an Xubuntu 12.04 lab image running on a set of 250 netbooks in our students' hands, and the reception has been mostly positive.

Additionally, we have to live with the unfortunate reality that some of my labs are 8 year old computers with 512MB of RAM and many still have their original, slow 40GB IDE hard drives.  Even in fallback mode, Unity would be pushing our limits on those computers.  My netbook sets would have no problems, but the old desktops certainly would struggle.

---

### Post by IanGrayland on 2012-12-21
> **Kirk Schnable said:**
> 
In short, we spent the last 2 years getting our users used to Gnome 2 Linux, and shortly after our decision to launch with the desktop environment, we found out it was no longer going to be developed.  It was very disappointing, and we looked for the closest alternative we could find.  We currently have an Xubuntu 12.04 lab image running on a set of 250 netbooks in our students' hands, and the reception has been mostly positive.


Wow! 250 users. I can't muster even a tenth of that.

To describe the loss of Gnome 2 as disappointing is something of an understatement. I felt the same kind of 'disappointment' here after many years of happy Gnoming. The main thing I've noticed is that I never get any requests for help with the system itself. None. Nada. Lots of users need minor help with the nuts and bolts of openoffice - like mailmerging, labels, or fancy formatting. Most don't know what a stylesheet is. But they can all of them use Gnome 2 right away as soon as you show them the power on button.

The Gnome guys didn't just shoot themselves in the foot; they shot both feet right off every Gnome based Linux distro - with impeccable timing. Imagine how popular Ubuntu 12.04 LTS with Gnome 2 with five years support would have been... 

Apologies for the OT rant. Back on topic and on the positive side, LibreOffice as of 3.6.4 is almost there as a fully functional Office suite. As a MySQL front end it has no peer. Just a few more bugs to go.

---

### Post by Kirk Schnable on 2012-12-21
> **IanGrayland said:**
> Wow! 250 users. I can't muster even a tenth of that.
We have about 70 staff and 800 students. We are on year 1 of a "1 to 1 computing" rollout. All teachers have their own laptops, as well as our ~250 freshmen.  The rest of our computers (there are about 450 more) are labs, mobile laptop carts, and classroom sets of netbooks. Our deployment is pretty large. 

> **IanGrayland said:**
> To describe the loss of Gnome 2 as disappointing is something of an understatement. I felt the same kind of 'disappointment' here after many years of happy Gnoming. The main thing I've noticed is that I never get any requests for help with the system itself. None. Nada. Lots of users need minor help with the nuts and bolts of openoffice - like mailmerging, labels, or fancy formatting. Most don't know what a stylesheet is. But they can all of them use Gnome 2 right away as soon as you show them the power on button.

The Gnome guys didn't just shoot themselves in the foot; they shot both feet right off every Gnome based Linux distro - with impeccable timing. Imagine how popular Ubuntu 12.04 LTS with Gnome 2 with five years support would have been... 
Yeah, with Microsoft shooting themselves in the foot with Windows 8 and the Metro UI, if Ubuntu hadn't launched Unity they could have exploded as a more 'traditional' desktop interface. 

To be honest, lately I feel like operating systems are taking the "user" out of "user interface". They're building the interface they feel like building, whether it's particularly useful or not. Unity isn't that difficult to adapt to, but Windows 8 Metro UI is downright confusing to most computer users.

---

