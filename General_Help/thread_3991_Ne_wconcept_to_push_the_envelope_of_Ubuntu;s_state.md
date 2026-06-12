---
title: "Ne wconcept to push the envelope of Ubuntu;s stated goals"
date: 2004-11-10
forum: General Help
---

### Post by shookmon on 2004-11-10
I'm looking at Ubuntu and I REALLY like the position taken towards making PC's available towards the "geeknology challenged".
As such, I have noticed that there may be room for additional assistance. to the end user.

My "philanthopic" goal would be to have an environment where the non-programmer could get a PC functioning and doing what they need. The focus I would like to see is form the point of view of a Elementary School teacher in a dis-advantaged situation (3rd world, inner city with no budget...) Since these poeple have their training focused on how to teach kids, not how to run a PC, I would like to propose that the following is created: an adjunct to the Ubuntu project where a complete novice can find "keystroke-by-keystoke" instructions on how to install or use a software tool inside of the known "standard" Ubuntu install.

The point I'm trying to make is that one single end user will only have the time, patience or capacity to go to a single source to get the infomation they need to get their tasks done or available to the kids. An example is installing Java for a web browser.

I know my own frustration when a How to says to just install the "spamassasin" but since I only have the base install of Ubuntu installed, I can't see that as an option there, but I have no idea what to do next.

 I think we need to recognize that these folks don't have the time and shouldn't have to learn the delicacies of the technology in order to use it in the classroom.

So, I guess, this is a call out to folks like me to create a place where an individual can take ownership of a product and provide exact insructions on how install and use a given tool.

To that end, I have space avaialable on my webserver to host such a beast.

I am extremely open to pushing this forward.

Michael D. Shook
Omega Tower Design Partners

---

### Post by FLeiXiuS on 2004-11-11
[QUOTE=shookmon]I'm looking at Ubuntu and I REALLY like the position taken towards making PC's available towards the "geeknology challenged".
As such, I have noticed that there may be room for additional assistance. to the end user.

My "philanthopic" goal would be to have an environment where the non-programmer could get a PC functioning and doing what they need. The focus I would like to see is form the point of view of a Elementary School teacher in a dis-advantaged situation (3rd world, inner city with no budget...) Since these poeple have their training focused on how to teach kids, not how to run a PC, I would like to propose that the following is created: an adjunct to the Ubuntu project where a complete novice can find "keystroke-by-keystoke" instructions on how to install or use a software tool inside of the known "standard" Ubuntu install.

The point I'm trying to make is that one single end user will only have the time, patience or capacity to go to a single source to get the infomation they need to get their tasks done or available to the kids. An example is installing Java for a web browser.

I know my own frustration when a How to says to just install the "spamassasin" but since I only have the base install of Ubuntu installed, I can't see that as an option there, but I have no idea what to do next.

 I think we need to recognize that these folks don't have the time and shouldn't have to learn the delicacies of the technology in order to use it in the classroom.

So, I guess, this is a call out to folks like me to create a place where an individual can take ownership of a product and provide exact insructions on how install and use a given tool.

To that end, I have space avaialable on my webserver to host such a beast.

I am extremely open to pushing this forward.

Michael D. Shook
Omega Tower Design Partners[/QUOTE]

**Spam Assassin is availabing via APT.**
Seeing as the package "spamassasin" resides in the universe you must have the apt universe enabled.   

For reference on how to enable the universe.  Look here: [http://ubuntuforums.org/showthread.php?t=179](http://ubuntuforums.org/showthread.php?t=179)

After this is enabled, open a terminal / command line and type the following:
```
sudo apt-get install spamassasin
```

That should do the trick.

---

### Post by steffen on 2004-11-11
This thread should probably be continued in the general discussion area. I believe the original poster probably knows how to install spamassassin, or enable to universe. The problem is, neither his or my primary school teacher knows - and will probably never know.

I would be more than happy to contribute to such a project - a keystroke by keystroke howto for Ubuntu. When I initially started with Linux, it took me about a month to figure out how to use the configure|make|make install. Everywhere I looked, it said I should just type it, and it never worked :)

A couple of years ago I helped my grandma get a computer with email up and running. The only way she would be able to use this again on her own, was to write down or draw every single keystroke and mousemove on paper. Simply turning the computer off, and starting OpenOffice would need a keystroke guide. But on the other hand, maketools, terminals, text files, etc. should be completely left out!

The only way to make Ubuntu/Linux usable for everyone is to have extremely detailed manuals on how to do general, easy, day to day tasks. It is far better to have this kind of information/help in one place, where help is structured, than having it scattered around on bulletin boards.

I'm sorry to say, but FLeiXiuS' reply would probably be understandable/usable to about 0.5% of primary school teachers.

---

### Post by HiddenWolf on 2004-11-11
Which, ofcourse is fine on these bulletin boards, since flexius is to the piont, and accurate.

But to get the novice to do anything, you would need a very detailed manual in html format, with pictures etc.

---

### Post by shookmon on 2004-11-11
You are correct in assuming that my issue was not actually with spamassasin. 

So, the next question is, how to set up such a beast so that the hypothetical teacher can use the computer?

Is a FAQ kinda thing gonna do it? Or perhaps a more "Problem Solving" oriented approach: "I'm told I need to install some coffee thing in my browser so I can show a NASA website relating to satellite orbits".

The problem I always have, when I try to use FAQ's is not knowing what to even search for because the problem is so foreign to my current knowledge. (see my recent post re: mouse cursors and alignments)

I could set up a Knowledge Base system perhaps with both generic FAQs and also individual pages for each keystroke by keystroke instuctions for tasks. It would be nice thougth for Q&A's spawned from the individual pages to be "hooked" or linked to the parent too. And of course there would have to "owners" of the pages to maintain updates and corrections and have a central point to answer question re: their pages.

---

### Post by TravisNewman on 2004-11-12
I'd love to see this. Maybe as an extension to the wiki, or rather, rewriting the wiki pages into completely dumbed down terminology. 

I don't have the storage for it though, but I'd be more than willing to help you out shookmon. If you need help setting something up or anything, I'll do what I can. Get a team going and we're golden.

Maybe we can get some help from the Ubuntu developers and doc team as well.

---

### Post by steffen on 2004-11-12
It would need screenshots and keystrokes.

First thing might be, 'How to write an email'. Second, 'How to write a document'.

Both would start 'Make sure your computer is turned on. If not, have someone help you find the power button'?

On the bottom of the 'How to write a document', there could be link to 'If you were not able to print your document, click here'.

Is that a good start?

I'd say the FAQ/Wiki should refer to the Wiki/Howtos on the ubuntulinux.org site, for more advanced problems. Having a screenshot/keystroke guide to using maketools for installing the printer driver should either not be necessary in Ubuntu, or is best left to sysadmins anyway. Teachers shouldn't bother.

---

### Post by randy on 2004-11-12
If your thinking about large scale deployment it might be better off to focus on sysadmins and work on something similiar to Redhat's Kickstart.  In almost every school I've been at now matter what operating system that they run they do something similiar to this.

---

### Post by TravisNewman on 2004-11-12
[QUOTE=randy]If your thinking about large scale deployment it might be better off to focus on sysadmins and work on something similiar to Redhat's Kickstart.  In almost every school I've been at now matter what operating system that they run they do something similiar to this.[/QUOTE]
 I don't think the idea is necessarily for teachers, that was just one example. I think what shook was saying is that it needs to be accessible to anyone who wants to use it. For schools, something like the RedHat kickstart would work well, because the sysadmin could explain it in simple terms. For the average user, who doesn't have a sysadmin but doesn't want to pay for Windows anymore, the kind of new-user-oriented documentation we're talking about here could be what makes them choose Ubuntu over SuSE or Mandrake.

---

### Post by shookmon on 2004-11-12
That's exactly my point, if the end user is in an environment with a sysadmin, it's the sysadmin's problem. But, in my experience, the sysadmin's in disadvantaged environments are in over heads keeping the system going, much less able to do what the individual needs. Hell, my wife works at a nationally recognized college, and it's STILL like pulling teeth to get the sysadmins to do something, much less something right. They actually disabled the users ability to download new anti-virus signatures because "Well, nobody uses it anyway, and the server will push out new signatures every month or so." Go figure.

I do think that the point about keeping the content based on the simple stuff is excellent. The way I figure, if the user is a COMPLETE novice, we need to provide assistance in getting their PC going and functional ( maybe not with the absolute latest bleeding edge technology, but able to get the work done). Once the major learning curve is past, say a year, and the user is comfortable with Linux, their going to start fishing on ther own to get the more advanced stuff for which instructions already exist.

Another point, it would be nice if we had enough volunteers to be able to offer live chat help to people as well. Maybe even able to take over the remote desktop for the really sticky problems. Since Ubuntu already installs VNC, this should be easy to implement.

Another point, since the user may have problems EVEN getting the network up, maybe the instuctions should be in book form available for download or provided with the CD, and the online stuff kept to FAQ's, help forums, and live chat assistance. Since new versions only come out every 6 months, changes or updates would be kept to only the bits that get changed in the new version, so it shouldn't be too bad.

---

### Post by conchobar on 2004-11-13
As a recent Linux convert and long-time Windows user, the difference is fresh enough in my mind to say that documentation isn't enough; a lot of work needs to be done at the actual development level, too, to make applications better integrated into GNOME (or KDE or Xfce...). Most people do not want to use command lines. Most people don't even know what's inside their computer; the only thing they can tell you is that it's a "Dell" or a "Windows". If they don't care enough to even know that much, they probably won't even bother with detailed instructions on how to install a program via command line. To them, dealing with Windows crashing and being insecure is easier to deal with than make install, editing config files, etc. Linux needs a lot of work done on making things work Just Like That.

This isn't a flame or anything; it's just my own honest observations based on my reactions to Linux, and more importantly, the reactions of my much less nerdy friends, family, and acquaintances.

---

### Post by TravisNewman on 2004-11-13
Yeah, this is true, but I still think the conversion rate would be much higher if there were documentation. Even if it only converts a few users to Ubuntu, or Linux in general, it's worth it. I'm not about to spring Linux on my mom-- she doesn't realize that she can talk to me on AIM and browse the web at the same time yet. It'd take some time to educate people like my mom... though she has been getting a lot of viruses, so... maybe... hmm... ;)

---

### Post by HiddenWolf on 2004-11-13
I think before we could make sure we got something like kickstart, we'd need to identify the problem pionts, and start writing very simple, keystroke by keystoke and screenshot-laden manual pages...

---

### Post by TravisNewman on 2004-11-13
Yes, one major problem point will be explaining the new filesystem. There is no C: drive or D: drive, just one filesystem. That just came to mind.

How about just plain email and browsing? Its not that much different, but it is to an extent.

We basically need to cover everything we can.

It'll be tricky. But I think it's worth it.

---

### Post by HiddenWolf on 2004-11-13
Holy shit, yeah. Filesystem is way different. I like it, but I sometimes still go to /usr if I want to find some personal files.

usr, in my book is user, but to linux, it is not. :-)

---

### Post by TravisNewman on 2004-11-13
[QUOTE=HiddenWolf]Holy shit, yeah. Filesystem is way different. I like it, but I sometimes still go to /usr if I want to find some personal files.

usr, in my book is user, but to linux, it is not. :-)[/QUOTE]
 Yeah it took me a while to get out of that habit. I've been using some sort of *nix for about 6 years now, about 3 years of really USING it and not just playing with it, and only about a year ago did I completely get out of that habit. The unix filesystem makes more sense to me than Windows, and definitely makes more sense than Mac (though it's now based on BSD it still tries to pretend it's not, and same goes with Gnome now to some extent), but it's tricky when you don't know what it all means.

---

### Post by shookmon on 2004-11-15
Well, I guess then we need to actually create a space and assign things to specific authors. 

1) any ideas for a domain name? (can I use Ubuntu-something?)
2) the point of view I'd like us to take is if we are explaining something to an overworked, underpaid, barely any time to use the computer, much less try and learn how it's guts work, newbie: henceforth called "Norman the Newbie"
3) "Norman the Newbie" has sucessfully installed Ubuntu, and ONLY that far (we need to always start at the beginning)
4) we can't make ANY assumptions about what "Norman the Newbie" already has installed
5) we need to recommend the easiest, most workable solution set to the issue, NO BLEEDING EDGE SOFTWARE, it's better to get there in a manner that is easily understood, than to get there in the coolest newest way.

How's that for a start?

---

### Post by TravisNewman on 2004-11-15
[QUOTE=shookmon]Well, I guess then we need to actually create a space and assign things to specific authors. 

1) any ideas for a domain name? (can I use Ubuntu-something?)
2) the point of view I'd like us to take is if we are explaining something to an overworked, underpaid, barely any time to use the computer, much less try and learn how it's guts work, newbie: henceforth called "Norman the Newbie"
3) "Norman the Newbie" has sucessfully installed Ubuntu, and ONLY that far (we need to always start at the beginning)
4) we can't make ANY assumptions about what "Norman the Newbie" already has installed
5) we need to recommend the easiest, most workable solution set to the issue, NO BLEEDING EDGE SOFTWARE, it's better to get there in a manner that is easily understood, than to get there in the coolest newest way.

How's that for a start?[/QUOTE]
 Yes, the question is, how to pay for the webspace? Paypal donations?
There should be at least 2 or 3 people in charge of monitoring the paypal account to ensure that any donations are used for the website, and not for any personal profit. 

I'd be glad to contribute some website design, I've got moderate skill in that area, and I'd definitely be willing to contribute documentation.

There also need to be some filters. When new documentation is recieved there needs to be a copy editor team (only one copy editor needs to correct each document) AND a lead editor (basically to check over the revisions the copy editor suggested) (pulling from my journalism classes here ;)) to make sure that content, context, and useability are in place in each document. Here's the system, in a very gbasic oriented model:

10 Writer writes documentation
20 Writer submits to copy editor
30 If revisions needed, suggest revisions and GOTO 10
40 Copy editor submits to Lead editor
50 If revisions needed, suggest revisions and goto 20
60 Publish

I hope I got that all right, I haven't used qbasic in ages
It doesn't take as long as it seems, I promise.

So lets get it going :) So far we're just talking about it! If anyone has the money to sponsor it until it can get on its own feet, and wants to get the webspace and domain for it, that'd be great. I know I don't ;) We may be able to get Canonical sponsorship if only for the webspace... if they're interested and if anyone has any clue about who to contact... We could call it the Ubuntu Guide for Users New to Linux or something shorter that conveys the same thing.

There are a lot of things to think about, and they all need to be thought out and written out in a few "meetings" whether on AIM, IRC, email or whatever. Input from Canonical employees would be great here as well.

*phew*

---

### Post by Rodney on 2004-11-15
Something like this maybe ?

[http://www.libranet-basics.org/](http://www.libranet-basics.org/)

it all started here 

[http://forum.libranet.com/viewtopic.php?t=4249&postdays=0&postorder=asc&start=0&sid=5cec4d3b844e708687caf12e03fd2023](http://forum.libranet.com/viewtopic.php?t=4249&postdays=0&postorder=asc&start=0&sid=5cec4d3b844e708687caf12e03fd2023)

---

### Post by shookmon on 2004-11-15
Well, my Uncle has a barn....
And my Grandmother has some old dresses...

Ah, just like the community theatre I love.

I have web space available and am willing to operate it gratis as long as it doesn't cost me additional money (due to size or MBs of downloads, etc...) so it should be a good place to start. I'll even register a domain name. Only catch is that it is a MS IIS server, since that what I use for work (.asp, FrontPage, etc) (I am new to this Linux thing after all), but from what I can see there shouldn't be much problem with the web if we stray from the MS fold for this project (FTP uploads and such should work ok). Also, I'll have email addresses available, as well as some other goodies like live interactive chat and such.

Since I'm new to Linux, while I won't be the best person to create the instruction sets, I should make a good editor/test newbie. My A+ and Network+ certifications should keep me on the right path  :-P 

So, we still need a domain name. UbuntuFish? UbuntuCrawl? UbuntuCalm? UbuntuMagic? YouSayOObuntu-ISayUbuntu? UbuntuPFM?

---

### Post by TravisNewman on 2004-11-15
YES that's it! It's only 86 pages, not bad! It could use more, but it's very good.

Yeah, lets do it! Its going to be mostly text with a few graphics, and if we use low quality graphics, we can use a free hosting service, and I can provide a subdomain to my domain (it'd be something like ubuntu-basics.moneyburger.com. I know that's not a great sounding name) I can't provide any webspace, because I have VERY limited bandwidth... we could actually use sourceforge. You can make webpages, and since it's related to open source, it wouldn't just be ripping them off for their space. I keep coming up with new ideas!! I like how they have finance lists so that you can see how the money is being used. that's a good idea, making it public record. That's all for now, I know I'll come up with more stuff anytime now

---

### Post by TravisNewman on 2004-11-15
ubuntu-basics is good I think. not to steal from libranet, but... ;) YouSayOObuntu... etc is funny though. 

Here's what I can do: I can design the site (shouldn't be hard). I can write at least some of the documentation. I can ding and dance. I can be one of the Lead Editors since I've had lots of journalism classes (changed my mind about only having one, since we're doing this in our spare time, and we have school or work to worry about). I can be supreme ruler. or not.

Here's what I can't do: contribute anything monitarily. find a job *beats head against wall*

---

### Post by shookmon on 2004-11-15
[QUOTE=Rodney]Something like this maybe ?

[http://www.libranet-basics.org/](http://www.libranet-basics.org/)

it all started here 

[http://forum.libranet.com/viewtopic.php?t=4249&postdays=0&postorder=asc&start=0&sid=5cec4d3b844e708687caf12e03fd2023](http://forum.libranet.com/viewtopic.php?t=4249&postdays=0&postorder=asc&start=0&sid=5cec4d3b844e708687caf12e03fd2023)[/QUOTE]

Wow, but that is still WAY over the head of "Norman the Newbie". I don't think he'll care much about "forking processes" and such.  :wink: 

And I'm not convinced that a linear book form is the way to approach this. Remember, this form assumes a basic understanding of the material beforehand (a reference manual) OR the desire to start at the beginning and read until you find the answers to your questions (a teaching book - the classic text book of high school fame). I think a more free flowing, cross linked, Problem-Solution or Task-Solution approach is more appropriate.

---

### Post by TravisNewman on 2004-11-16
The HTML version isn't really linear. It'd be nice, I think to have different formats of reading it. Some people may want different ways to read it, and it probably wouldn't be that hard to do.

---

### Post by Ozitraveller on 2004-11-16
I'm probably totally off the mark here.  But have you look at :

Skolelinux

[http://www.skolelinux.org/portal/about/what](http://www.skolelinux.org/portal/about/what)


What is Skolelinux?
Skolelinux is made as free (as in speech) software, and is an overall computer solution based on school's resources and needs.
Skolelinux is a network architecture tailored for use in schools.
Skolelinux is developed and supported by a large and growing international community.

Skolelinux is designed to be easy and cheap to maintain. 
Skolelinux gives the students their own usernames, home directories and services. 

It's Debian based, same as Ubuntu, and a number of other distros.

I've tried it, just from a standalone point of view.

Anyway I thought it might be worth a look, can't hurt.

---

### Post by Ozitraveller on 2004-11-16
Sorry should have added this:

[http://www.skolelinux.org/portal/product/](http://www.skolelinux.org/portal/product/)



How Skolelinux works  

A short introduction to how Skolelinux works
"Skolelinux" – a GNU/Linux distributionSkolelinux is a GNU/Linux distribution. It is put together by various Linux software components, based on Debian. Debian is a state-of-the-art, user- friendly operating system. Our goal is to make Debian easy to install and maintain for schools – with applications available on the student's mother tongue.
InstallationInsert the CD, answer three simple questions and watch how Skolelinux unfolds on your server. Behind the scenes of that simple installation, are the results of years of careful configuration and tweaking. Lots of services are installed, configured and ready to run when the installation is completed.
An advanced network solutionDespite how easy Skolelinux is to install, with only three questions asked, it is an advanced network solution, with many pre-configured services. With ordinary, closed, proprietary software, these services have to be configured manually for every single school – and that needs careful planning and expertise!
Amongst several pre-configured services are the following:
Central user catalogue: One username and one password for several machines and services. 
Central storage: Regardless of which machine you use in a Skolelinux network, you have access to your files and meet an interface with your settings – an interface you are familiar with. 
Thin client solution: The applications are run on a thin client server, which is a powerful machine. The image from those applications is drawn on a "thin client", which usually is an old, cheap machine. This enables you to use old hardware. Moreover, it eases administration, as you have one server to maintain. 
Printers may be shared and made available in the network. 
A proxy server caches files downloaded from the Internet, resulting in a faster surfing experience. 
See the overview of a Skolelinux network.
Administration and maintenanceDay-to-day administration and maintenance is done with a web browser – through the Webmin administration interface.
Installation and maintenance of software packages is done through Debian's rock-solid "apt-get" system. At a glance, it enables you to upgrade your entire system with only two commands.
SoftwareSkolelinux comes with lots of software for school use, and additional software can be easily installed.

---

### Post by TravisNewman on 2004-11-16
Hey guys, I've been talking to Mako, Daniel, and the doc team, and they all suggest going through the wiki. It's free, it's robust, and it will keep the documentation together in one central place.

There's an Ubuntu Book on the Wiki as it is, and through discussion with the authors of the book, they like the idea, and want to help us out in any way they can. I've brought up the idea of kicking ideas back and forth between Ubuntu Basics (or whatever we decide to call it) and the Ubuntu Book -- basically whenever we get something they might benefit from, we kick it their way, and vice versa -- and they like this idea as well.

So as far as the domain name goes, we don't REALLY need one, but if we wanted to get one we could use the wiki and redirect the domain name to the wikipage. We could also mirror this on another server if need be... there's a lot of flexibility available to us, but we have to worry about overkill as well.

---

### Post by shookmon on 2004-11-16
Now THAT sounds like the way to go. We can concentrate on the key-stroke-by-keystroke stuff, and they can do the book stuff, and then it should all come together for Norman the Newbie.

So, how do we setup the wiki bits?

---

