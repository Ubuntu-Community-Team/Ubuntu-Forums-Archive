---
title: "The biggest reasons Why I don't run Ubuntu or Linux on my business PC's, Yet?"
date: 2007-01-02
forum: General Help
---

### Post by Sapphiron on 2007-01-02
I am a small business IT Consultant specializing in the SOHO and Creative professionals.  I think I speak for every person here that the new Windows Vista activation policies are completely Fubar.  it leaves me, and my clients, with 4 choices:

1.  Pay a fortune in software licensing every time i change something or something breaks.
2.  Stick with Windows XP for as long as we can.
3.  Move to pirated software.
4.  Move to Linux

I have already moved most of my clients onto Linux for their servers as MS SBS2003 is totally overpriced.  I still have some issues and features to "migrate" from the windows services.

On the server front I'm pretty sure I will get everything migrated, its simply a case of Googling or Wikipediaing for the solutions and testing them.  Here are a few of them

1. I still lack proper mail collaboration software (like exchange)  I have tried Zimbra, which works brilliantly, when you can get it working.  I am far from a Linux expert, but I do at least want software installations to take less than a weeks.  Eventually I dumped it until they simplify the installation.  I wanted to try using Kerio Mailserver (I have no problem paying for good software, but I run into the typical problem with 3rd party vendors, They all use RPM package managers.

2.  Raid controllers / backup
I know there is now way to get software RAID to work reliably on Linux.  I instead have to rely on backup software to do the job instead.  normal I run the backup software (Syncback) from a windows box and access the data via Samba.  Are there any good Linux backup software out there (user friendly and fool proof)?

3.  Drivers/ Compatibility
Probably my biggest problem is hardware drivers and compatibility.  Every hardware vendor out there uses a different method.  Either a RPM (which again is a problem with Ubuntu) or a god-awful bin executable that complains that some packages are missing (shame on you Nvidia).

My biggest problem however is desktop software.  My biggest concern with moving to Linux is the one-way nature of the migration. 

1. Email. Once I move my email and calendar into Evolution (which isn't that great) , there is no simple way of going back to outlook (that I know of).

2a. OpenOffice under windows is very good (for Linux office software).  although it is free, It's slow and sluggish, even on my AMD 4400 Dual Core with 4GB of RAM and 10000RPM Raptor.  Most clients don't complain as I usually recommend pretty pacey PC's (no Celeron's in sight), but some of them do, and then they blame me for saving them money!

2b. Although it is moderately user friendly there is still some serious incompatibilities when working in MS office format (which you have to since 99% of people use it, or some people have to use it since they require a feature OpenOffice does not have, or does not properly implement).  Also development on it is so slow.  MS have certainly made more progress(improving performance and user friendliness) from office 2000 onwards than OpenOffice has.


Anyway I have lots of problem, I hope some of them have got solutions you guys can help me with. *Sigh*

---

### Post by gmanigault on 2007-01-02
Email, I prefer Postfix.  For a client you could use Thunderbird.  

Raid,  I always preferr hardware raid.   Two controllers, two drives.  I never use Raid as and alternative to doing backups. 

GWShark



> **Sapphiron said:**
> I am a small business IT Consultant specializing in the SOHO and Creative professionals.  I think I speak for every person here that the new Windows Vista activation policies are completely Fubar.  it leaves me, and my clients, with 4 choices:

1.  Pay a fortune in software licensing every time i change something or something breaks.
2.  Stick with Windows XP for as long as we can.
3.  Move to pirated software.
4.  Move to Linux

I have already moved most of my clients onto Linux for their servers as MS SBS2003 is totally overpriced.  I still have some issues and features to "migrate" from the windows services.

On the server front I'm pretty sure I will get everything migrated, its simply a case of Googling or Wikipediaing for the solutions and testing them.  Here are a few of them

1. I still lack proper mail collaboration software (like exchange)  I have tried Zimbra, which works brilliantly, when you can get it working.  I am far from a Linux expert, but I do at least want software installations to take less than a weeks.  Eventually I dumped it until they simplify the installation.  I wanted to try using Kerio Mailserver (I have no problem paying for good software, but I run into the typical problem with 3rd party vendors, They all use RPM package managers.

2.  Raid controllers / backup
I know there is now way to get software RAID to work reliably on Linux.  I instead have to rely on backup software to do the job instead.  normal I run the backup software (Syncback) from a windows box and access the data via Samba.  Are there any good Linux backup software out there (user friendly and fool proof)?

3.  Drivers/ Compatibility
Probably my biggest problem is hardware drivers and compatibility.  Every hardware vendor out there uses a different method.  Either a RPM (which again is a problem with Ubuntu) or a god-awful bin executable that complains that some packages are missing (shame on you Nvidia).

My biggest problem however is desktop software.  My biggest concern with moving to Linux is the one-way nature of the migration. 

1. Email. Once I move my email and calendar into Evolution (which isn't that great) , there is no simple way of going back to outlook (that I know of).

2a. OpenOffice under windows is very good (for Linux office software).  although it is free, It's slow and sluggish, even on my AMD 4400 Dual Core with 4GB of RAM and 10000RPM Raptor.  Most clients don't complain as I usually recommend pretty pacey PC's (no Celeron's in sight), but some of them do, and then they blame me for saving them money!

2b. Although it is moderately user friendly there is still some serious incompatibilities when working in MS office format (which you have to since 99% of people use it, or some people have to use it since they require a feature OpenOffice does not have, or does not properly implement).  Also development on it is so slow.  MS have certainly made more progress(improving performance and user friendliness) from office 2000 onwards than OpenOffice has.


Anyway I have lots of problem, I hope some of them have got solutions you guys can help me with. *Sigh*

---

### Post by Sapphiron on 2007-01-02
can Postfix do Collaboration (eg  shared address books, shared calendar, shared mailboxes) without taking 20 hours to setup.

Sorry I was not clear.  I always did backups (weekly and Daily).  I need an hourly backup that won't decrease performance too much.

---

### Post by lyceum on 2007-01-02
> **Sapphiron said:**
> I am a small business IT Consultant specializing in the SOHO and Creative professionals.  I think I speak for every person here that the new Windows Vista activation policies are completely Fubar.  it leaves me, and my clients, with 4 choices:

1.  Pay a fortune in software licensing every time i change something or something breaks.
2.  Stick with Windows XP for as long as we can.
3.  Move to pirated software.
4.  Move to Linux

I have already moved most of my clients onto Linux for their servers as MS SBS2003 is totally overpriced.  I still have some issues and features to "migrate" from the windows services.

On the server front I'm pretty sure I will get everything migrated, its simply a case of Googling or Wikipediaing for the solutions and testing them.  Here are a few of them

1. I still lack proper mail collaboration software (like exchange)  I have tried Zimbra, which works brilliantly, when you can get it working.  I am far from a Linux expert, but I do at least want software installations to take less than a weeks.  Eventually I dumped it until they simplify the installation.  I wanted to try using Kerio Mailserver (I have no problem paying for good software, but I run into the typical problem with 3rd party vendors, They all use RPM package managers.

I would a agree with gmanigault and say Thunderbird as well. My wife uses it on her Mac and loves it. The Sunbird calender does not run inside Thunderbird yet, but it works for a calender for now until they are one package. 

> **Sapphiron said:**
> 2.  Raid controllers / backup
I know there is now way to get software RAID to work reliably on Linux.  I instead have to rely on backup software to do the job instead.  normal I run the backup software (Syncback) from a windows box and access the data via Samba.  Are there any good Linux backup software out there (user friendly and fool proof)?

I do not know alot about this, as I do manual backup because I care about data more than the setup. However, I remember seeing something on Automatix2 that offered some sort of back up. I could be wrong, but you may want to try checking that out. 

> **Sapphiron said:**
> 3.  Drivers/ Compatibility
Probably my biggest problem is hardware drivers and compatibility.  Every hardware vendor out there uses a different method.  Either a RPM (which again is a problem with Ubuntu) or a god-awful bin executable that complains that some packages are missing (shame on you Nvidia).

The only out of the box problem I have had is WiFi. You just have to do you homework here before buying anything. I would keep an extensive list of what works, and what never will. With the Feisty release the nVidia and other drivers should not be a problem. The only problem then will be that Feisty is not going to be long term support. That does not matter to me, but it might to a business. That may just take time. Sorry.

> **Sapphiron said:**
> My biggest problem however is desktop software.  My biggest concern with moving to Linux is the one-way nature of the migration. 

1. Email. Once I move my email and calendar into Evolution (which isn't that great) , there is no simple way of going back to outlook (that I know of).

2a. OpenOffice under windows is very good (for Linux office software).  although it is free, It's slow and sluggish, even on my AMD 4400 Dual Core with 4GB of RAM and 10000RPM Raptor.  Most clients don't complain as I usually recommend pretty pacey PC's (no Celeron's in sight), but some of them do, and then they blame me for saving them money!

2b. Although it is moderately user friendly there is still some serious incompatibilities when working in MS office format (which you have to since 99% of people use it, or some people have to use it since they require a feature OpenOffice does not have, or does not properly implement).  Also development on it is so slow.  MS have certainly made more progress(improving performance and user friendliness) from office 2000 onwards than OpenOffice has.


Anyway I have lots of problem, I hope some of them have got solutions you guys can help me with. *Sigh*

You may want to look into crossover office. 

[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

It costs about $40 to $70, but allows you to run Windows programs. The only down side is that you renew the subscription every year. But, you can try it for free first. 


The bottom line though is that you are saving them $$'s on their bottom line. They may want to look at which is better, less $$'s or the extra 2 seconds starting up open office. :)

---

### Post by aysiu on 2007-01-02
I don't see those problems as being that big, honestly.

As long as people use IMAP instead of POP3, migrating from one email client to another isn't difficult at all--since all the messages are stored on the server, not the personal computer.

And, as lyceum points out, there are ways to run Microsoft Office in Linux.

---

### Post by koenn on 2007-01-02
> Anyway I have lots of problem, I hope some of them have got solutions you guys can help me with.  I thought professionals would think a migration path through before implementing it  :)
On the other hand, I like the "its simply a case of Googling or Wikipediaing for the solutions and testing them" attitude. Here's my 50 cents:

I'm supprised you even consider software RAID. imo, if you need RAID, stick a raid controller in that server (but check that Linux/Ubuntu support it. If you don't need raid, why bother with software raids. And it's no alternative to backups (or vice versa).

Collaboration software or "group ware" ***is*** a big problem, and AFAIK there are no complete alternatives to Exchange. MS really did wel on that one (at least qua functionality and feutores. There are those who say the implementation sucks, )
I guess your best bet here is to find out exactly what features your customers require, and then either find a package that offers at least those (check the links on this page : [http://www.roseindia.net/opensource/open-source-groupware.shtml)](http://www.roseindia.net/opensource/open-source-groupware.shtml)), or collect seperate applications for each feature (a POP/SMTP mail server, an IMAP server, a shared calendar, manage resources,such as rreservations of meeting rooms and assign them tho events in a calendar, shared takslists, and so on ...)
That approach is probably easier (even Google offers a shared calender these days !) and you'd only have to install what your respective customers require. downside : you'd miss a certain level of integration


> 3. Drivers/ Compatibility
Probably my biggest problem is hardware drivers and compatibility. Every hardware vendor out there uses a different method. Either a RPM (which again is a problem with Ubuntu) or a god-awful bin executable that complains that some packages are missing (shame on you Nvidia).
A known issue, isn't it. And the obvious explanation (uncooperative vendors) is well known as well. 
If you're gonna sell Linux / Ubunto, why not sell machines with it that have compatible hardware ? Or, if you don't sell hardware, at least you do advise your clients on hardware purchases, no ?
> 
1. Email. Once I move my email and calendar into Evolution (which isn't that great) , there is no simple way of going back to outlook (that I know of).
Do you need to go back ?

> 2a. OpenOffice under windows is very good (for Linux office software). although it is free, It's slow and sluggish, even on my AMD 4400 Dual Core with 4GB of RAM and 10000RPM Raptor. Most clients don't complain as I usually recommend pretty pacey PC's (no Celeron's in sight), but some of them do, and then they blame me for saving them money!
What's the problem ? just leave the choice up to them : 
XP untill it's EOL, then Vista with all the activation hassle you(ve mentioned yourself, + the cost of Windows License, MS Office license, etc, etc, or a reasonably good alternative in OpenOffice ? They blame you for saving them money ? It's their money, let them spend it if they think it's worth it. 
Apart from that, OpenOffice seems slow to start, but once it's running I don't really find it slow or sluggish

2b. Although it is moderately user friendly there is still some serious incompatibilities when working in MS office format (which you have to since 99% of people use it, or some people have to use it since they require a feature OpenOffice does not have, or does not properly implement). Also development on it is so slow. MS have certainly made more progress(improving performance and user friendliness) from office 2000 onwards than OpenOffice has.

---

### Post by phossal on 2007-01-02
I much prefer to stick with the practical advice, usually, but I do have an opinion. If you have non-technical clients - clients who would pay you to choose and install an office suite - how can you possibly offer them *linux?*

Assuming the average dope successfully summits the hill of a learning curve that is the transition to OpenOffice, what do you do every time they want to do something ordinarily simple (in Windows), like plug in their wireless dongle? :)

I would not want the responsibility of supporting *that.* lol Ubuntu is fun, and it offers quite a bit, but it's just not for everyone and every*thing*. The simple reality is that most people use computers to accomplish some very basic tasks - work, music, pictures. They don't, in many cases,  want to *learn* anything.

While the tasks you're trying to complete in your conversion to linux may be, in a sense, more technical than transitioning to OpenOffice, consider your own frustration. You actually *like* computers, and you actually think what you're trying to do is *possible*. Take away the motivation, and the faith, and you have a seriously disappointed customer. The last thing you want to be responsible for is selling Ubuntu. The last thing you want to prove to your customer is that they get what they pay for.


[Edit: If you're bringing Windows to Linux, it's because *Linux* has failed, not Windows. I would argue that the average business owner is not strictly motivated by the cost of a purchase, as long as the utility of the object exceeds it. If you have clients who want Outlook messages, convenient plug-and-play hardware, common commercial software, MS Office, then they want Windows, regardless of the cost.]

---

### Post by Sapphiron on 2007-01-02
> **phossal said:**
> I much prefer to stick with the practical advice, usually, but I do have an opinion. If you have non-technical clients - clients who would pay you to choose and install an office suite - how can you possibly offer them *linux?*

Assuming the average dope successfully summits the hill of a learning curve that is the transition to OpenOffice, what do you do every time they want to do something ordinarily simple (in Windows), like plug in their wireless dongle? :)

I would not want the responsibility of supporting *that.* lol Ubuntu is fun, and it offers quite a bit, but it's just not for everyone and every*thing*. The simple reality is that most people use computers to accomplish some very basic tasks - work, music, pictures. They don't, in many cases,  want to *learn* anything.

While the tasks you're trying to complete in your conversion to linux may be, in a sense, more technical than transitioning to OpenOffice, consider your own frustration. You actually *like* computers, and you actually think what you're trying to do is *possible*. Take away the motivation, and the faith, and you have a seriously disappointed customer.

I think you hit the nail right on the head.  users don't like change.  an Example: I've been working with Office 2007 for the past week or so and I love it.  The ribbon interface makes so much more sense!.  I showed it to a few of my clients and the first thing they asked me is: " can you make it work like the old office?". ](*,) 


ATM I am looking at getting users to drop outlook completely and go for some sort of webmail solution.  most of them have got the collaboration features built-in and on a proper browser, they are very quick.

koenn
I do not need to go back, I imported a copy of my outlook into it and played around with it.  That's all.

Also My accounting practice clients find it very slow when working on their 30mb Excel files.  Takes 5-10sec to open in Excel and well over 30sec in OpenOffice.  We even tried saving it in OpenOffice format.  it was only slightly faster.  There is also a performance lag when they sort the columns or switch between sheets.  Also in spreadsheets with a lot of pictures it is slow to scroll.

It is not so much that it is slow per say, just that is is noticeably slower than MS office.

ATM my standard advice to client is, Try it for 2 weeks, we can always buy office later.  About 95% end up buying Office after the 2 weeks.

I think my feelings are best described by this:

"I feel like a car dealer trying to sell a TATA to a BMW owner"  The fact that he can buy 3 of them for the price of 1 BMW and that it does the same things does not occur to them.

---

### Post by koenn on 2007-01-02
going off topic and towards a windows versus linux discussion, but I'll risk it anyway:

I disagree. It's actually a very _good_ scenario : 
The average "point and click" user can get things done in Ubuntu just as easy as in Windows. It will take them 10-20 minutes to find the right icons and menu items again, and that's it. 

The harder parts (post install config, additional hardwxare support, installl software, general sys admining ...) is the job of the consultant - unlike a home user who has to figure those things out by himself. 

Sounds OK to me - if the problems get work out (or worked around) *before* the customers / end-users come in.

---

### Post by aysiu on 2007-01-02
Businesses need to assess their needs honestly.

If they want Windows, they should stop being cheapskates and fork out the money for Windows.

If they're cheapskates and open-minded, they can try Ubuntu (Ubuntu does have [paid support](http://www.ubuntu.com/support/paid), by the way).

I wrote an essay comparing Windows and Linux as business/desktop solutions:
[http://www.psychocats.net/essays/linuxwindowscomparison](http://www.psychocats.net/essays/linuxwindowscomparison)

---

### Post by lyceum on 2007-01-02
> **aysiu said:**
> Businesses need to assess their needs honestly.

If they want Windows, they should stop being cheapskates and fork out the money for Windows.

If they're cheapskates and open-minded, they can try Ubuntu (Ubuntu does have [paid support](http://www.ubuntu.com/support/paid), by the way).

I wrote an essay comparing Windows and Linux as business/desktop solutions:
[http://www.psychocats.net/essays/linuxwindowscomparison](http://www.psychocats.net/essays/linuxwindowscomparison)

This is absolutely correct. If you put a business plan down, with open and honest expectations of Windows vs. Linux the company can choose what will work best for them. But if you make Linux look like a cheep Windows, that is what it will become, a "Windows" that "doesn't work" not because it doesn't work, but because the expectations were not realistic. I see no reason why Linux can't work in an office environment. Just make sure their IT techs know how Linux works and how to make things work the way it is needed. In the business work it is not vs. it is what is needed to get the job done effectively and efficiently. 

By the way Aysiu, nice link.

---

### Post by TmP on 2007-01-04
Hi!

Here's my perspective as a Linux enthusiast and a fan of Ubuntu who is employed by a large multinational corporation. My position requires _extensive_ use of commercial information sources and tools - either written by the corporation itselfes of by 3'rd party vendors. On one ocasion I asked the IT guy about switching to Linux. He told me that the guys that have suggested that we should consider Linux were put down and quickly have understood why that would be impossible. Now afer a few months I also can see it. 

1. the commercial webpages are not ready for linux: every serious information service expects that you would run Internet Explorer ( take the eurostat webpage as an example ). It's not only a question of dhtml, activex and other stuff that MS holds a patent for and does not share willingly. Actually it's enough that a stupid table is off by a few pixels that makes important information so damn difficult to print to pdf. And nobody likes taking screenshots. So until firefox catches up with the interoperability it's not worth considering.

2. internal IT security procedures: it's nearly impossible to convince sb. at the top to use free software. Why? For instance that there is noone to blame when sth. fails. Microsoft is the standard and we won't stray from a standard. Vista? I don't see haw we would switch to that. Vista also isn't in the safe standards. And the decision process to change that will take forever. Why go for Vista if that is not a standard? And why go for linux?


3. software: our requirements are quite simple - stability under strain from multiple programs runnig at once plus 10 different pieces of Internet Explorer run tools. Some how I don't see how Adobe Acrobat would perform better under Ubuntu. Same for anything else. Ubuntu is great but if one company offers a full solution: Server-Client and every one else has to submit to their standard ( stupid and outdated it may be) there is simply no other choice but Windows. Interestingly the Windows that we are using is heavily modified. It does stuff I never expected it to do. Most of the security is performed at the server level. Anything unsafe is locked out. It rarely freezes and is surprisely stable. 

4. lastly - I suppose the IT specialist are simply better at administrating Windows than at Linux. They also have a learning curve and it's much more steep with every piece of networked software.

Sadly, what could make Linux more useful from the point of a company like mine is the decision of Windows to support Suse Linux. What is needed is a "monopolyst" in the Linux world - one distribution that would be so dominant that software makers and other distros would have to submit to it's standards or perish. More so - the monopolist Linux ( Monux? ) would have to be paid for so that the accountacy dept. would have something to write off for the tax return, and the IT sb. to blame when it fales. This Monux distro would have to be a ready solution - full software package. 

Call me an idealist but I think there is still place for one more operating system on the market. Either that or next Windows will soon run on a modified Suse.

---

### Post by lyceum on 2007-01-04
> **TmP said:**
> 
Hi!

Here's my perspective as a Linux enthusiast and a fan of Ubuntu who is employed by a large multinational corporation. My position requires _extensive_ use of commercial information sources and tools - either written by the corporation itselfes of by 3'rd party vendors. On one ocasion I asked the IT guy about switching to Linux. He told me that the guys that have suggested that we should consider Linux were put down and quickly have understood why that would be impossible. Now afer a few months I also can see it. 

1. the commercial webpages are not ready for linux: every serious information service expects that you would run Internet Explorer ( take the eurostat webpage as an example ). It's not only a question of dhtml, activex and other stuff that MS holds a patent for and does not share willingly. Actually it's enough that a stupid table is off by a few pixels that makes important information so damn difficult to print to pdf. And nobody likes taking screenshots. So until firefox catches up with the interoperability it's not worth considering.

I think Firefox 3.0 is fixing these. Also, the problem here with the pixels is that IE 6 did not conform to the rules set to run a browser, in other words, the pixels were off because of problems with IE, not with Firefox. IE 7 should have fixed these. Which means that the web pages that were broken to that IE 6 could read them will need to be fixed so that IE 7 can read them. In my class last quarter on web design we learned how to write hacks so that when you wrote your code correctly the hack would break it so that IE 6 could read it and make it look right.

> **TmP said:**
> 2. internal IT security procedures: it's nearly impossible to convince sb. at the top to use free software. Why? For instance that there is noone to blame when sth. fails. Microsoft is the standard and we won't stray from a standard. Vista? I don't see haw we would switch to that. Vista also isn't in the safe standards. And the decision process to change that will take forever. Why go for Vista if that is not a standard? And why go for linux?

The blame game. <sigh> Pettiness wins again. I guess the IT guys couldn't be at fault, or if the company paid for the Canonical support, could you blame them? Such a trite excuse, but it works in the corporate world. 

> **TmP said:**
> 3. software: our requirements are quite simple - stability under strain from multiple programs running at once plus 10 different pieces of Internet Explorer run tools. Some how I don't see how Adobe Acrobat would perform better under Ubuntu. Same for anything else. Ubuntu is great but if one company offers a full solution: Server-Client and every one else has to submit to their standard ( stupid and outdated it may be) there is simply no other choice but Windows. Interestingly the Windows that we are using is heavily modified. It does stuff I never expected it to do. Most of the security is performed at the server level. Anything unsafe is locked out. It rarely freezes and is surprisely stable. 

I have found that I can run more faster on Ubuntu that Windows. The real benefit here is that if you hire the right IT guys they can modify the software to work exactly how you need it to rather than how MS wants you to. Take out the bloat you don't need and put in what you do. 

> **TmP said:**
> 4. lastly - I suppose the IT specialist are simply better at administrating Windows than at Linux. They also have a learning curve and it's much more steep with every piece of networked software.

This is a hiring problem. If they went to school and know nothing about Unix or Linux, they did not get their money's worth. I am at a business collage studying web design and they make us do everything with Windows, even though they run Red Hat on their servers. We have still learned about Unix and the Unix environment. We talked about KDE and how web pages look on a Windows machine vs a Mac vs Linux. And I am just learning how to make websites. 

> **TmP said:**
> Sadly, what could make Linux more useful from the point of a company like mine is the decision of Windows to support Suse Linux. What is needed is a "monopolyst" in the Linux world - one distribution that would be so dominant that software makers and other distros would have to submit to it's standards or perish. More so - the monopolist Linux ( Monux? ) would have to be paid for so that the accountacy dept. would have something to write off for the tax return, and the IT sb. to blame when it fales. This Monux distro would have to be a ready solution - full software package. 

Call me an idealist but I think there is still place for one more operating system on the market. Either that or next Windows will soon run on a modified Suse.

I would not be surprised to see the next Windows have a Unix or a Linux core. But MS will use SuSE and dump them. MS is already make money off their deal, and the only thing Novell is getting is the millions form MS and the extra hits to their website. Not that the MS millions hurt any... But the One Distro to Rule Them All idea is not a good one. The point of FOSS is to make thing easier to use, not harder. Companies should stop wasting money on MS and spend it on people that can hack code for them. That would make their offices more efficient, as the programs are designed perfectly for their needs. It worked for George Lucus. Look at the difference between Episodes 1, 2 & 3. They switched in the middle of 2. They had more control and thus could do more and that really showed in 3. (Sorry for the Star Wars, it was just easier than thinking of something else. True geek coming out!) Just my 2 cents ans a wanna be CEO. :)

---

### Post by raul_ on 2007-01-04
I think you're choosing the bad way to present Linux. The way you talk it seems like a cheap OS that will just work, and it's worth the sacrifice just because it's free. Actually it's not. Why not go for a professional solution like Suse? A lot of big companies run on Linux (Google runs on Linux servers!)  so i think you're just painting it bad. I think System 76's site did a good job presenting Linux as a desktop/server solution:
> 
How can Linux benefit you?

Where do we start? Stability, security, no more crappy spyware installing itself on your computer and wreaking havoc. There are so many reasons it's hard to decide. Most importantly, Linux provides you with the freedom to use the software you like, the way you like to use it. You are not locked into any formats that are controlled by monopolistic companies. You choose. Linux also has legendary stability. No more blue screens of death or check disk screens when you boot up. Linux is also easy to use. The learning curve is short and worth while. Once you move, you'll never look back.

And then there is cost. Ubuntu Linux is free and all the software we install is free. Your email client, word processing, spreadsheets, drawing, presentations, and just about anything else you can think of is included or easily available for free. Every six months you receive a free upgrade to the latest Ubuntu operating system. In fact, all of the software installed on your computer is updated through one easy to use application. You don't have to update Windows, Office, Adobe, and all of those other applications separately. It's all done for you. You'll never have to invest in upgrades.

more here [http://system76.com/information.php?info_id=18&osCsid=b48a9ad552e097a213f26c39f1edc136]("http://system76.com/information.php?info_id=18&osCsid=b48a9ad552e097a213f26c39f1edc136")

Now if you say that to the guys with the money, then it's up to them if they want to save a lot of money or not, but i don't see what the big deal is in switching from windows..IT'S NOT THE END OF THE WORLD.  It's a matter of spending some time in formation, and informing employees how to use the basic things.

And as aysiu said, Ubuntu (or Suse) has it's own support team, which you can pay for services

---

### Post by raul_ on 2007-01-04
You should also read my thread on how to make Open Office and Firefox faster if you're so concerned about it. I open my Open Office in 2 seconds flat

[http://www.ubuntuforums.org/showthread.php?t=329309&highlight=tips+ubuntu+faster]("http://www.ubuntuforums.org/showthread.php?t=329309&highlight=tips+ubuntu+faster")

---

### Post by sarc on 2007-01-04
My 2 cents is to think of the users.  If they are busienss people they need things to work, like, NOW, not IF we can find a fix for it.

My Canon printer CANNOT print under Linux; my scanner CANNOT work under Linux; my graphic tablet does not have a Linux driver; it took me a day on the forum to figure out I have to run pppoeconfig to connect to ADSL; my webcam stopped working under Edgy; Skype does not work properly on Linux; it will take me a day to set up multiple monitors on Xwindows.

All of the above took 30 seconds each to do in Windows.  Not Linux's fault, but user's don't care.

---

### Post by raul_ on 2007-01-04
> **sarc said:**
> My 2 cents is to think of the users.  If they are busienss people they need things to work, like, NOW, not IF we can find a fix for it.

My Canon printer CANNOT print under Linux; my scanner CANNOT work under Linux; my graphic tablet does not have a Linux driver; it took me a day on the forum to figure out I have to run pppoeconfig to connect to ADSL; my webcam stopped working under Edgy; Skype does not work properly on Linux; it will take me a day to set up multiple monitors on Xwindows.

All of the above took 30 seconds each to do in Windows.  Not Linux's fault, but user's don't care.

Maybe they'll work in Suse.

 Anyway, if a company decides to migrate to Linux, then the guys in charge know what hardware to buy, wouldn't you say?

---

### Post by sarc on 2007-01-04
Unless you already have the hardware sitting there!  Actually most companies I know do not have an approved hardware list and could not enforce it - users buy first, then complain; hard to argue especialy if it works flawlessly in Windows!

---

### Post by raul_ on 2007-01-04
Then migrate to Vista and buy a whole new new stock of 1000$plus systems instead of buying a couple of new printers (because in most companies i know, there is one central printer) :mrgreen:

---

### Post by lyceum on 2007-01-04
> **raul_ said:**
> Maybe they'll work in Suse.

 Anyway, if a company decides to migrate to Linux, then the guys in charge know what hardware to buy, wouldn't you say?

> **sarc said:**
> Unless you already have the hardware sitting there!  Actually most companies I know do not have an approved hardware list and could not enforce it - users buy first, then complain; hard to argue especialy if it works flawlessly in Windows!

These are both very good points. This is why when the package/plan is laid out it would need to show the cost for the change. Right now there is no way my company could switch to Vista. Most of our PC's have too little ram and it just costs too much. However, we could could switch to Linux with minimal cost, as the hardware on the PC's is compatible. That is why it is so important to look at the big picture and not just make a switch.

---

### Post by aysiu on 2007-01-04
At my workplace, the IT department buys printers and other hardware, not the users...

---

### Post by revertex on 2007-01-08
stick with windows until you learn linux.

you can do all the things you do with windows, maybe more, but at cost that you need to know linux.

maybe another distro like gentoo or slackware, that don't hold your hand and do all the magic  like ubuntu does should be helpful.

take a look at gentoo wiki and forums, there is lots of simple recipes that should answer your questions.


there is tons of backup solutions, you can even use cron an tar and write a script.
the latest kernels have suport for almost all hardware, even nvidia drivres have deb packages that you can install using synaptic, or just use the open nv driver.

try prelink, preload and openoffice quickstart to startup openoffice, or try staroffice, or install crossover office then run MS Office.

Postfix+courrier+qmail are a nice alternative, maybe open-xchange is what you are looking for.

---

### Post by lyceum on 2007-01-08
> **revertex said:**
> stick with windows until you learn linux.

you can do all the things you do with windows, maybe more, but at cost that you need to know linux.

maybe another distro like gentoo or slackware, that don't hold your hand and do all the magic  like ubuntu does should be helpful.

take a look at gentoo wiki and forums, there is lots of simple recipes that should answer your questions.


there is tons of backup solutions, you can even use cron an tar and write a script.
the latest kernels have suport for almost all hardware, even nvidia drivres have deb packages that you can install using synaptic, or just use the open nv driver.

try prelink, preload and openoffice quickstart to startup openoffice, or try staroffice, or install crossover office then run MS Office.

Postfix+courrier+qmail are a nice alternative, maybe open-xchange is what you are looking for.


I sell and give away PC's with Ubuntu all the time to people with no PC skills at all. I let them know that Ubuntu is not MS and that there is a learning cerve. I let them ask me questions and give them a copy of the User Guide. I really do not get many compaints. Every now and then someoe buys the "wrong" printer, but they like the system, and they think it is easy and fun to use.  You maybe right for future power users, but as long as the hardware works, the new users really should be okay.

---

### Post by justifier on 2007-01-08
in  the first four thing you said, arnt 1 and 3 illegal? slightly? under microsoft law?

any way, i cant help on a lot of them but RPM problem alien?

---

