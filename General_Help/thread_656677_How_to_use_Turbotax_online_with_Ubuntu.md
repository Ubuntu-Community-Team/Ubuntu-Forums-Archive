---
title: "How to use Turbotax online with Ubuntu"
date: 2008-01-02
forum: General Help
---

### Post by Sean Foster on 2008-01-02
I tried Turbotax online today and could not get past the first page.  This is because Turbotax does not Like Linux.  After reading a few posts on how to work around this, I came up with my own idea:  why not install Firefox for Windows and run it with Wine.  Then, Turbotax will think it is seeing a Windows box.  It worked!  I am now doing my taxes as we speak.

At first, this may be seen as a limitation of Linux, but it is in fact the other way around . . . it is a limitation of Turbotax and as always, Linux is able to overcome the problem.

This kind of makes me think . . . maybe some day Windows will be able to overcome the problem of running a program not built for it like Linux does . . . NAH!  Windows has problems running even it's own programs!

---

### Post by hardyn on 2008-01-02
wow... i would not think that a web deployed application would need to be os specific. interesting.

I have had no trouble using quicktax online for my canadian taxes.  that might be worth an email to the company, i cant seem them alienating there potential apple clients, so perhaps there is somthing silly happening?

---

### Post by halw on 2008-01-02
Last year I ran online turbotax using Ubuntu with no issues that I recall. Haven't tried this year yet.

---

### Post by PeterJS on 2008-01-02
Hmm, I wonder if there's any actual need there or just claiming that there is. Because if it works with Firefox under wine, then it can't possibly be an activeX issue. As an interesting experiment, I wonder what would happen if you used native linux Firefox with the windows Useragent string. If it's just arbitrarily turrning you away because of the useragent string that's rather silly.

---

### Post by Sean Foster on 2008-01-02
I don't know.  Maybe it would work with the Windows useragent string.  I'll have to try it.

---

### Post by scholzilla on 2008-01-08
sean,

thanks for your post--i'll give it a try, but turbotax doesn't even list linux as an OS it is compatible with (see attached screenshot). I've had the same problem as you. I have the latest mozilla version and i can't get past the screen i've screenshot.

m

---

### Post by PeterJS on 2008-01-08
The question posed in the last two post which hasn't answer yet is, are they bluffing or is there a legitimate technical reason behind their denial.

---

### Post by scholzilla on 2008-01-10
Actually, I'm thinking now that this is a firefox issue. I tried using turbotax from a windows machine running firefox and had the same problem as before. I then used internet explorer and had no issue. I haven't tried running ie on my linux box yet (the very idea makes me cringe).

---

### Post by Feenix217 on 2008-01-10
Uhm...

I logged in yesterday to Turbotax.com after reading the OP's comments.

AFAIK, I won't have any problems using Turbotax on my Ubuntu box this year via Firefox.

Feenix

---

### Post by najames on 2008-01-11
It could be like my old Hells Fargo mortgage website.  It refused to let me see my account or do anyting with Firefox.  I installed the user agent switcher plugin and chose Explorer to fool the stupid website and all was well for years until they rebuilt their webiste.  The new website no longer checks for Explorer, so it doesn't need the switcher.

Never, ever open asset management accounts with Hells Fargo.  You will be doomed with their gross incompetance.  Excuse me while I go look for another mortgage company.

---

### Post by kwunderlich on 2008-01-16
This problem does occur but I found a link that bypasses the browser check and allows you to log in anyway.

[https://turbotaxweb.turbotaxonline.intuit.com/open/registration/Start.htm](https://turbotaxweb.turbotaxonline.intuit.com/open/registration/Start.htm)

It simply asks you if you have ever used the site before and once the user and password are entered, it takes you to where you expected.

---

### Post by scholzilla on 2008-01-17
yep, that works. Thanks a lot!

---

### Post by rosswmcgee on 2008-01-21
I can not get past the start page which lists the os they support.I did turbotax online last year. How did you do it?

---

### Post by rosswmcgee on 2008-01-21
How did you do it? where are op's comments?

---

### Post by PeterJS on 2008-01-21
> **kwunderlich said:**
> This problem does occur but I found a link that bypasses the browser check and allows you to log in anyway.

[https://turbotaxweb.turbotaxonline.intuit.com/open/registration/Start.htm](https://turbotaxweb.turbotaxonline.intuit.com/open/registration/Start.htm)

It simply asks you if you have ever used the site before and once the user and password are entered, it takes you to where you expected.

This post at the top of the page seems to have the best solution.

---

### Post by rosswmcgee on 2008-01-21
Thank you so much. I did not want to go to my wife's windows machine! I did download the wine deal, but have not tried it. This is so much simpler. Made my day!

---

### Post by dustinkirkland on 2008-01-22
> **Sean Foster said:**
> I tried Turbotax online today and could not get past the first page.  This is because Turbotax does not Like Linux.  After reading a few posts on how to work around this, I came up with my own idea:  why not install Firefox for Windows and run it with Wine.

I started doing my taxes last night and I ran into the same problem--Turbo Tax Online simply refusing my standard Ubuntu/Firefox browser.

Rather than dealing with wine, however, I simply changed the user agent string reported by Firefox for the operating system.  That's all it took for me.  I documented the procedure in the Ubuntu Community Documentation wiki here:

[https://help.ubuntu.com/community/TurboTaxOnline]("https://help.ubuntu.com/community/TurboTaxOnline")

Cheers,
:- Dustin

---

### Post by rosswmcgee on 2008-01-22
Bravo! I did it and it works. After the taxes are done is it best to return to the original strings?

---

### Post by Rex72 on 2008-02-01
After changing the lines 

general.useragent.vendor to Windows and
general.useragent.vendorComment to Windows NT 5.1

I still have the same issue.

---

### Post by ewanchic on 2008-02-04
I had called them sometime in the middle of January. They informed me that it was "only compatible" with Windows and Mac OS X, using either Firefox or Interenet Explorer. It was not compatible with the linux system.

I politely argued the point that I did do my taxes last year on "Suse" I believe, and that Mac OS X is a derivative of the BSD Linux system. After politely getting passed the tech to the supervisor, she made a call to their corporate. Supposedly they're still claiming the same statement. One technician suggested installing windows into a vmware session.

It is really unfortunately that TurboTax as made such a negative decision.

---

### Post by Palmyra on 2008-04-15
> **kwunderlich said:**
> This problem does occur but I found a link that bypasses the browser check and allows you to log in anyway.

[https://turbotaxweb.turbotaxonline.intuit.com/open/registration/Start.htm](https://turbotaxweb.turbotaxonline.intuit.com/open/registration/Start.htm)

It simply asks you if you have ever used the site before and once the user and password are entered, it takes you to where you expected.

WARNING/IMPORTANT: Do not use the above link if you are trying to file your federal taxes for free.  I learned this the hard way when I got to the end and was told I would have to pay about $30 to file the return.

If you want to file the return for free, go to the IRS website first.  Go here:

[http://www.irs.gov/efile/article/0,,id=118986,00.html](http://www.irs.gov/efile/article/0,,id=118986,00.html)

Click on "Start Now" and select Turbotax Freedom edition.  This is the proper way to get to the free version.  Yes, this is indirect, but these companies *want* you to do this and Turbotax is not alone; I checked with another one too.

Once you access Turbotax indirectly using the above link, you will need to do the useragent thing (scroll up for another forum member's instructions - or just use the UserAgent Switcher Firefox extension...I am using Firefox 3, and the forum member's instructions don't apply so I used this extension).  This will trick Turbotax into thinking you're using a Windows computer.  Here's where it gets complicated: change the useragent when accessing Turbotax, but as soon as you get to the log in page, change the string back.  This is because you only need the string to be Windows up until the point of log in (once you get to the log in part, you will already have passed their system check).  I guess you can leave the string, but that may cause a problem.

By the way, instead of going through all this hassle, support another company (especially a competitor).  I used FreeTaxUSA, and it looks like I'll get back a dollar more than what Turbotax promised ...yay!  Why support a company that suggests it doesn't want your business unless you make a significant change (i.e. change your operating system).

---

