---
title: "OpenOffice.org 2.4, Java 6 u. 5, and new ntfs-3g released: where in official repos?"
date: 2008-03-27
forum: General Help
---

### Post by newbieforever on 2008-03-27
Hello, I _want_ to _immediately_ upgrade to OOo 2.4, while the ubuntu repos allow only 2.3.0 (even when 2.3.1 was available).

2.3.1 was available from many months, but the repos I can see was not updated. Could someone tell me why? 

2.3.1 made available many important major e minor bug fixes, and some functionality improvement, not available in repos.

In spite of FireFox (for which repos pkg are are almost real time synchronized with new releases on mozilla homepage), OOo is not up to date.

The same can be said about JDK and/or JRE: the actual update is 6.0 update 5, but I cant see them in repos.

Not the least important is ntfs-3g. new releases provide critical fixings and again I cant find them in official repos: I experienced that, because simply accessing in read-only mode to my windows disks with "old" ntfs-3g drivers, destroyed all personal and system grants and ownerships in windows, and I had to "remake" the machine (someone called me unlucky, but I am not the only one with that problem).

OOo and Java & related are among my 24/7 apps, and ntfs-3g is a critical driver for many people, I strongly need to be up to date (this time above all for OOo 2.4 that provide really significant improvements I was waiting for, and obviously fo ntfs-3g drivers).

Could someone help me?

1 - is it my mistake? I have US official repos enabled, have I to make some change to my settings?

2 - if not: could someone kindly tell me how to override the automatic management of synaptic and avoke "local install" management for, OOo and 
Java environment, and ntfs-3g?

Thank you very much, 

I hope this thread could be of general interest

nbfe

---

### Post by colo on 2008-03-27
Ubuntu is not a rolling release distro, but stabilizies given snapshots of software repositories over time. That means that in general, versions of packages do not change for an Ubuntu release. Firefox is an exception for trademark reasons, I believe.

If you prefer to live on the edge of recent software developments, you should consider switching distributions. You might want to try Gentoo, Archlinux, Debian Testing/Unstable or Fedora instead of Ubuntu.

---

### Post by fela on 2008-03-27
i know this aint gonna happen, but i'd love it if there was a single repository that consists of subversions (svn), alongside the other ones, and that there could be an option (say, apt-get -svn install package) to install the svn version instead. Just an idea :KS

---

### Post by colo on 2008-03-27
Check [http://wiki.kaspersandberg.com/doku.php?id=projects:fluidportage](http://wiki.kaspersandberg.com/doku.php?id=projects:fluidportage)

---

### Post by fela on 2008-03-27
> **colo said:**
> Check [http://wiki.kaspersandberg.com/doku.php?id=projects:fluidportage](http://wiki.kaspersandberg.com/doku.php?id=projects:fluidportage)

something like that, but more built in to the whole ubuntu OS, yeah (and with all the packages if poss)

yeah yeah i'm too lazy to build from source...but often things are pretty hard to do that way.

---

### Post by colo on 2008-03-27
What you want is a conceptual impossibility for any binary-packaging distribution (like Ubuntu).

---

### Post by danwood76 on 2008-03-27
Yeah you would need someone to build each package from CVS and as cvs is forever changing its an impossible task.
As already said if you want bleeding edge either DIY or change distros.

Oh and firefox is forever updating due to internet security not trademark.
If firefox was to stay as it was in october there would be quite a few security risks which have been addressed since then.

---

### Post by colo on 2008-03-27
No, it's because you must not patch Mozilla's standard distribution of Firefox if you want to call the resulting binaries "Firefox". Since Ubuntu does want to do so, they are forced to upgrade the application even if the version changed; they may NOT backport security fixes to a prior version of Firefox and still call it that way. That's why Debian and Co. ship Iceweasel instead of it.

---

### Post by intel on 2008-03-27
OpenOffice does not get updated packages very often under ubuntu,

1) OpenOffice is Very Very Very complex software platform

2) OpenOffice packages all its dependencies together rather than using the available ones, (If a utility "example v1.x" is required to compile it, Sun developers package & use exactly that utility, even if "example v1.x+1" a newer version is already installed on the system), and this is very bad practice, beacuse it requires more maintenance & is bad for security.

3) Very few Ubuntu developers are capable of building/compiling openoffice & packaging it.

4) Users of openoffice don't care, they either use it or use MicroSoft Office.


5) Sun developers don't care about Ubuntu, not enough to release *.debs for it anyways


My Suggestions :-
Make 2 versions of OpenOffice always available through repos, installable side-by-side at the same time

Version 1
OpenOffice
(Latest Stable release + bug/security fixes)

Version 2
Openoffice
(Latest experimental build, which is usable, but may have bugs)

then ubuntu users can report issues to be resolved with the latest source code Sun developers are working with

---

### Post by newbieforever on 2008-03-27
Hello to everyone who replied so soon! It's gratifying for me to have raised your interest... 
Hem... I admit I dont understand all you said about CVS and SVN, and building every update from source...
And I admit I have asked my question perhaps not in the right way.

I love Ubuntu, and the only alternative OS I could see could be Debian, but only as an "extrema ratio".

I accept the limitations about packages updating. I've seen other distro, actually, although I didnt use them personally. I also briefly "studied" some debian-based distros on [DistroWatch]("http://www.distrowatch.com/") and I think that I want a distro with a solid future I should stay on Debian itaself or Ubuntu. If I compare these limitations to the exceptional advantages Ubuntu give to me, I have to conclude to remain on Ubuntu.

I also think that everyone has the real need to be up to date "to the limit" only on a narrow set of packages or apps, especially when these come "out of the box" in a .deb file, without dependencies problems and so on... (those ones I have mentioned for my personal needs belong to this category, isnt it?)

That said, if we love Ubuntu, and we only want to tune it under some a little number of points of view, let me set the focus of the discussion on an "how to": 
which could be the best practice to manually manage some packages we need?

1 - For example: I imagine that Java make calls to the system, and other "framework" could make the same (am I wrong if I say Qemu? or Wine?)
In this category could someone suggest a tutorial to keep the system consistent? I come from windows as you can figure... :-) Have I to set "environment variables", and how? Is that enough for this kind of components? Or we have to be very experienced to manage them manually?

2 - And about drivers... ntfs-3g, I think it is the one we all share more, many people have to interact with windows environments... is it safe to remove it from synaptic and follow the directives of [www.ntfs-3g.com]("http://www.ntfs-3g.com")
to integrate it with the system every time there is an update? (I subscribed the newsletter, and I notice that it is updated about monthly or few more in this stage...)

3 - In the end, let me consider "standalone" applications, as OOo, Blender, Gimp, HTML editors, or various languages IDE, and many other apps or utilities which depend on everyone needs: could we remove them and ignore Synaptic notifications about updating, and simply re-install them every time we need? 

4 - Let's consider also the situation in which ordinary repositories dont provide our needed app at all. For example I use TrueCrypt for usb pendrive volumes: every time there is a new release I go to synaptic, I remove it, then I pick the .deb installer and "mount" the brand new version.

In all these situations I dont mean to build those components from the source, simply installing the binary packages. And I think behind the scenes we also have to make a little of maintenance (purging no more needed or orphaned files, libraries and packages), as well explained in some threads I cant find at the moment.

I hope some of the most experienced among us could clarify the various scenarios considering that we, as I said, love and want Ubuntu! :-)

Thanks to everyone, 

nbfe

---

### Post by newbieforever on 2008-03-27
While I was writing some minutes ago you posted about Firefox and OpenOffice.
May be a little superficial or unexperienced, but I found that OpenOffice comes with a Java installer, that resembles very much to windows installer for linux... In this case should be really difficult to maintain it updated?

All apart I dont believe that the most of OOo users dont mind about the version of the suite itself. I am on Ubuntu from some weeks, but I got rid of Office from more than one year: I needed a more stable, efficient, effective and low price solution to my document management, and I also use it for its good capabilities in basic vector graphics (I cant have the same results with Office, while I really dont need much of the "beatification only" features Office provide).

I instead believe that OOo is one of the bridge that in this period could bring many people from the bank of windows to linux one!

My needs are about office automation are strong but frugal... that's why I prefer OOo :-)

nbfe

---

### Post by pelikan555 on 2008-03-27
> **intel said:**
> ...
5) Sun developers don't care about Ubuntu, not enough to release *.debs for it anyways


Actually, if you look [here]("http://download.openoffice.org/other.html#en-US"), along the 'English (US)' row, you will see they do release .deb files these days. I was pleasantly surprised myself. I haven't used them though, as I am on Hardy Beta.

To the original poster, installing the Beta of Ubuntu Hardy is always an option, for it includes a release candidate version (not the final version yet) of 2.4.

---

### Post by forrestcupp on 2008-03-27
Well, you're not going to get *bleeding edge* packages this way, but you should make sure your Proposed and Backports repos are enabled.  Go to System->Administration->Software Sources, and click the 'Updates' tab.  Check the boxes next to 'Pre-released updates', and 'Unsupported updates.'

That won't get you the very latest releases, but it will keep you updated with a lot newer packages than the official repos have.

---

### Post by newbieforever on 2008-03-27
> **forrestcupp said:**
> (...)'Pre-released updates', and 'Unsupported updates.'(...)
Did it!
Thrilling! And hope Funny! Isaw those options but I never considered seriously! :-)
I'm downloading @ 900KB/s about one hundred files!
Some more minutes and I will decide whether to retire my "thanks" or not! :-D

nbfe

---

### Post by newbieforever on 2008-03-27
> **pelikan555 said:**
> Actually, if you look [here]("http://download.openoffice.org/other.html#en-US"), along the 'English (US)' row, you will see they do release .deb files these days. I was pleasantly surprised myself. I haven't used them though, as I am on Hardy Beta.
To the original poster, installing the Beta of Ubuntu Hardy is always an option, for it includes a release candidate version (not the final version yet) of 2.4.
That's right! I didnt see it too. Thanks, I'm currently running the "thrilling" partial upgrade, then I will try to dl and install it (although the link seems broken at this moment).
I will let you know...
And sooner or later I will put my hands on JDK, Tomcat, MySQL and Eclipse, and I WILL DO it manually, no repos. That will be the real deal, I hope to be able to give you good news from THIS machine! :-)

nbfe
______________

UPDATED PART 1: There's a little problem: I'm really hooked to many FireFox extensions, and many of the most important to me dont support MFF over 2.x version... (see attachment).
I will be on version 2 until the key add-ons will be upgraded! :-( That's a pity, but fortunately rel 3.x install doesnt affect 2.x version, and they obviously share the same settings... this way I can pick the best of both releases...

---

### Post by newbieforever on 2008-03-27
> **pelikan555 said:**
> Actually, if you look [here]("http://download.openoffice.org/other.html#en-US"), along the 'English (US)' row, you will see they do release .deb files these days. I was pleasantly surprised myself. I haven't used them though, as I am on Hardy Beta.

To the original poster, installing the Beta of Ubuntu Hardy is always an option, for it includes a release candidate version (not the final version yet) of 2.4.

I am the original poster! :-)
Thanks for the advice... I already installed the pre-release and unsupported packages, and I'm now downloading the *.deb OOo 2.4.0, but If I want even more, could you please briefly give a boot-kick to install the Hardy beta upgrade without reinstall the whole OS?

Thanks!

nbfe

---

### Post by forrestcupp on 2008-03-27
If you install Hardy, it *will* install the whole thing.  There's no getting around it.  You'll download **a lot** of updates, and since it's still a testing version, you will have *a lot* of updates every day.

It's still in testing, and that's **very risky** for your main computer.  You shouldn't do it until it is released the end of next month.  But if you think you just have to do it, you can upgrade by typing
```
sudo apt-get update
sudo apt-get dist-upgrade
```

But if you're really a newbieforever, **don't do it**

---

### Post by fela on 2008-03-27
> **colo said:**
> No, it's because you must not patch Mozilla's standard distribution of Firefox if you want to call the resulting binaries "Firefox". Since Ubuntu does want to do so, they are forced to upgrade the application even if the version changed; they may NOT backport security fixes to a prior version of Firefox and still call it that way. That's why Debian and Co. ship Iceweasel instead of it.

yeah i don't like firefox in that way

more importantly, i don't like firefox in another way, i.e. i have a slow machine (p4 1.8GHz) that firefox slows down even more. That is why i use epiphany instead. (the native gnome browser)

---

### Post by newbieforever on 2008-03-27
> **forrestcupp said:**
> (...)Hardy(...)is **very risky** for your main computer
(..)if you're really a newbieforever, **don't do it**

:-) Ok Forrest, I'm glad for your right targeted and effective reply!
Yes, I'm a newbie in the literal sense now, and I think I will prefer consider myself the same even for the rest of my life, even in the hypothesis I will have learned something more than what I got in some weeks of ubuntu... :-)
Lack of doubts about myself could be dangerous to me... :-)

Thanks for your advice... I dont want to reply to you next time, crying as a child, from my wife's windows computer... :-D

I will continue on current stable Ubuntu release, because I believe in the future, non only in the present, of the project, and I will find the way to reserve to myself the manual management of the part of the system that are critical to me... 

If I will achieve my targets, I will share them, may be in a new thread in a more general and less "egoist" point of view...
**This thread has been very important to me, to widen my perspective in this new world. **

[COLOR=SlateGray]Even if this threaten me, I have to admit that our lives will be more and more bound to the information and communication science... If there is one hope that this incredible tool will be "good" to us, to consciousness, to democracy, to freedom, and not a weapon, well, the way is to be an "open mind", an "open person", and part of an "open society" (pardon my wandering)
[/COLOR] 
Linux is a very expensive investment for me (one ex-windows dummy), very heavy, both psychologically and economically, but every day I see it is the right way. Windows will soon be game over, I should have begun much time ago...

I don't make a mystery that I will give a try to *SympleMEPIS*, the only obstacle is that it doesnt ships with Gnome by default, and also the *testing/unstable Debian*, as I have been suggested. 

Gentoo is not affordable in its future maintenance in my personal opinion, and SlackWare is too hard to me at the moment. PCLinuxOS is attractive, but I have to examine deeply its story to understand its reliability under a "debian-based" point of view. Suggests are welcome, obviously.

nbfe

---

### Post by fragos on 2008-03-27
Enabling backports in the software sources helps some.  I monitor [http://getdeb.net](http://getdeb.net) -- it's debs have always worked for me.  A swell as keeping some aps like Gimp more up todate it offers other useful aps like Lives which I prefer for video editing.  Other than that I update Ubuntu every 6 months.

---

### Post by newbieforever on 2008-03-28
> **fragos said:**
> Enabling backports in the software sources helps some.  I monitor [http://getdeb.net](http://getdeb.net) -- it's debs have always worked for me.

Hello, I clicked the link but it gave 500 internal error to me... any idea?
Thanks for the indication!

nbfe

---

### Post by imperius69 on 2008-03-28
having the same problem right now but ive been there, the server must be down, try later.

---

### Post by fragos on 2008-03-28
> **newbieforever said:**
> Hello, I clicked the link but it gave 500 internal error to me... any idea?
Thanks for the indication!

nbfe

Just checked out OK for me using link in the message.  Ocassionaly, I've seen site that required the "www." in front of the domain name.

---

### Post by newbieforever on 2008-04-01
> **fragos said:**
> Just checked out OK for me using link in the message.  Ocassionaly, I've seen site that required the "www." in front of the domain name.
thanks, i registered to the site, and i find very useful... 
great idea by getdeb, not a great idea by ubuntu maintainers...
pardon if i tell something you already now... another great resource is the undervalued [www.linuxappfinder.com](www.linuxappfinder.com), mainly focused on debian and ubuntu, with high availability of 64bit packages..
bye and thanks again
nbfe

---

### Post by ImpressMe on 2008-04-01
Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant elitist "community". But have it your way.

---

### Post by newbieforever on 2008-04-01
> **ImpressMe said:**
> Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant elitist "community". But have it your way.
Let me understand, forgive me, my english is poor and i sometimes miss the core...
So do you agree that claiming that all ex-windows users will be able to turn to linux, or they are encouraged to do it, is very difficult until there are powerful but "hidden" functionalities, until linux is so sensitive to the minimum error touching system configuration files or to installing wrong packages, until hardware vendors really limit the release of driver (restricted or not), until every distribution is strictly bound to the repository maintainers policy, and so on?
I'm experiencing that free software is not so free... linux born from developer to developer... and I think that it suffers again from that...
I often see that someone of whom that help me assumes that I'm familiar with the complex linux OS architecture and management...
so these efforts to help often turn in a complete block of the machine, and I have to format and re-install all the system... 
just an opinion: it's good to be experts about linux, but I don't believe that anyone, these days, have realistically time to start as an expert... may be she/he will become with time, but she/he needs to be able to concentrate on her/his work, and not only on the operating system...

nbfe

---

### Post by fragos on 2008-04-01
It's human nature to preach the merits of the tools we use. It also appears to be human nature to avoid change and to measure something new by how how it's exactly like that which we already use. Change always envolved a learning curve of some kind. The question to ask yourself is will there be benifit once I've learned. Many of the benifits for migrating to Linux from Windows aren't readily apparent to some users. If I for example were to change from Ubuntu to Linux my costs would be in the many thousands of dollars for the software I use alone. Having to purchase a new computer is of course another major cost. With a minimum skill set I can get the latest version of every application when they come out. If I'm willing to wait a month or perhaps more the Linux community will do the work for me. True the latest version of MS applications are readily available but at a price. Thinking of Vista, there are numerious applications that still don't work with it properly, including itself. When a new release of a Linux distribution comes out vertually all the applications work on day one for free. Ubuntu has a new release every 6 months. I believe Vista took perhaps 5 years to be released and after a year it still has problems. Let me summarize. If I'm willing to learn something new I get a totally new system every 6 months for free or I can wait years between releases and pay for them. Just my opinion without getting into the numerious points of technical superiority of Linux.

---

### Post by calc on 2008-04-02
> **ImpressMe said:**
> Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant elitist "community". But have it your way.

So the fact they need to wait an extra month after release of 2.4 to get the easy upgrade (Ubuntu 8.04) makes a huge difference? Take a look at what OOo needs to build and to have installed and then realize how many things would have to be backported with it, and then think how many versions of Ubuntu should it be backported to? The 4 officially supported (for security) releases? Just the last release? Or just the release you happen in particular happen to run?

BTW - openoffice.org_2.4.0-3ubuntu1_source.changes is in Hardy now

---

### Post by newbieforever on 2008-04-02
> **calc said:**
> So the fact they need to wait an extra month after release of 2.4 to get the easy upgrade (Ubuntu 8.04) makes a huge difference? Take a look at what OOo needs to build and to have installed and then realize how many things would have to be backported with it, and then think how many versions of Ubuntu should it be backported to? The 4 officially supported (for security) releases? Just the last release? Or just the release you happen in particular happen to run?

BTW - openoffice.org_2.4.0-3ubuntu1_source.changes is in Hardy now

i agree with you: im completely ignorant about the complexity to compile a huge project like openoffice, please let me say 2 words about my personal experience:
openoffice.org does not provide 64 bit binaries: i cant see a 32 bit notebook from about two year, and we are in italy, 10 years back, comparing usa, but the problem is not only 32-64 bit installable packages

- i use "staroffice" since the firsts releases by STARDIVISION, so i think i could say to know quite well the subject matter FROM THE USER'S POINT OF VIEW; we are talking about over 10 years of experience in USING the program
- i always used it much more than ms office
- i followed every single update, even the tiniest, along these years
- i could i can say that in TEN years the changes of the single modules are quite invisible, trust me
- the binaries are still name "soffice.(ext)": does that say nothing to you?
- the performances are always impressively depressive for the middle/high-need user
- things went worse with the ODF: the user has NO CHOICE: ODF IS COMPRESSED EVERY SINGLE TIME ANY DOCUMENT IS SAVED (EXACTLY AS A ZIP ARCHIVE): IN HUGE DOCUMENTS THIS LOCKED MY MACHINE FOR 30 SECONDS EVERY TIME (I AUTO-SAVE EVERY 5 MINUTES, YOU CAN IMAGINE): THAT'S INCREDIBLE, SAVE SOME DAMNED BYTES IN CHANGE OF WASTING HOURS ALONG THE WORK SESSION (I WORK 14 HOURS A DAY), WHILE THEY DONT UNDERSTAND THAT IF COPY AND PASTE THE SAME IMAGINE IN THE SAME DOCUMENT IT IS ALWAYS THE SAME OBJECT: BUT IF I PASTE 100 TIMES, THE DOCUMENT BECOME 100 TIMES BIGGER, FUNNY ISNT IT?
- spreadsheet performance in particular are dozens of time slower than excel in huge documents, making ooo virtually not usable in certain condition: for me its faster to build every time a specific tiny java command line app to make the specific same task almost instantly (inputing and outputting huge amount of database-retrieved data using mysql)

so i always hope that things could be better, that's why i follow ooo growing as a cactus on the balcony: 1 millimeter a year... may be in the future some little thorn to be able to compete with the user needs...

nbfe

---

### Post by ImpressMe on 2008-04-02
> **calc said:**
> So the fact they need to wait an extra month after release of 2.4 to get the easy upgrade (Ubuntu 8.04) makes a huge difference? Take a look at what OOo needs to build and to have installed and then realize how many things would have to be backported with it, and then think how many versions of Ubuntu should it be backported to? The 4 officially supported (for security) releases? Just the last release? Or just the release you happen in particular happen to run?

BTW - openoffice.org_2.4.0-3ubuntu1_source.changes is in Hardy now

I know all this, but how would you explain that to the costumers? This is developer talk, they don't care at all. Bottom line, only single digit market share for desktop Linux. Always. And the voluntary costumers will always be OS enthusiasts.

The model works for servers, absolutely not for a modern desktop OS.

---

### Post by newbieforever on 2008-04-02
> **ImpressMe said:**
> I know all this, but how would you explain that to the costumers? This is developer talk, they don't care at all. Bottom line, only single digit market share for desktop Linux. Always. And the voluntary costumers will always be OS enthusiasts.

The model works for servers, absolutely not for a modern desktop OS.

hem, beg your pardon, im from italy... i have some difficulties in getting the meaning of some passages in the english natural spoken language...
could you explain your post for me? it seems really interesting but im missing something...

Bottom line?
only single digit market share for desktop Linux?
voluntary costumers?
will always be OS enthusiasts?
The model?
works for servers, absolutely not for a modern desktop OS?

i thank you in advance for your patience...

nbfe

---

### Post by newbieforever on 2008-04-02
> **ImpressMe said:**
> Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant elitist "community". But have it your way.

just a note:
**im really tired with ubuntu**. im spending months to set it according to my needs, and i cant print one single paper page yet

i confess it: im going to try PCLinuxOS, it is very high rated, and very well reviewed, and there are thousands of extremely enthusiast users... and i ask whether is there a reason...

nbfe

---

### Post by Zannax on 2008-04-02
> **newbieforever said:**
> 
openoffice.org does not provide 64 bit binaries: 
nbfe

They do provide 64bit binaries: just check it in the download options under architecture...
There's 64bit too.

---

### Post by Vorian Grey on 2008-04-02
> **ImpressMe said:**
> Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant elitist "community". But have it your way.

I agree. Linux has just as backward of a model as Windows does at times. On any modern OS, it should be as easy as download it, and run it, regardless of the version number.

---

### Post by calc on 2008-04-02
> **ImpressMe said:**
> I know all this, but how would you explain that to the costumers? This is developer talk, they don't care at all. Bottom line, only single digit market share for desktop Linux. Always. And the voluntary costumers will always be OS enthusiasts.

The model works for servers, absolutely not for a modern desktop OS.

So where do you draw the line on what to backport to old releases. If you ask enough people what they want backported they will overall want to backport everything that is in the new version, at which point there is no reason to backport any of it since it would be the same as the new version of the distribution. For example, I'm sure that there are people out there that would love it if all of Gnome 2.22 was backported to Dapper, etc. And anything that links to each other that is to be backported would have to be installed together, so you wouldn't really be able to pick and choose in any case, eg if an application linked against the new Gnome libs that were also backported since someone wanted those you would have to install the new Gnome libs along with the backported application you actually wanted. As someone previously stated in this thread it sounds like you actually want a rolling source based distribution similar to Gentoo, since none of the binary based dists work in that way (to my knowledge).

And with Ubuntu unless the 'customer' is paying for a support contract through some company, eg Dell, Canonical, etc. then they aren't really customers in the traditional sense '1: one that purchases a commodity or service' according to the dictionary. Ubuntu 'customers' get all their updates and new OS versions for free, all they have to do to update is run the update-manager, versus if they were Microsoft customers they would have to pay $300 (USD) to upgrade to the newest Windows version, which would then not come with any useful applications, those cost extra, eg Microsoft Office $500 (USD) and upgrades aren't free for those applications either. So there isn't a large financial disincentive (many thousand USD) to not upgrade as there would be if running a commercial OS. Pretty much the only disincentive to upgrading Ubuntu releases is that things will have changed, which in this case the user actually wants some if not all of the changes.

---

### Post by dasunst3r on 2008-04-02
The only gripe I have about the software versions on my Hardy installation is that OpenOffice.org is at 2.4 RC2, and not the final version.  Does anybody have any idea as to when the packages for the final version will come out?

Also, the last time I checked, I do have Java 6 u5, so that's not much of an issue for me.  Honestly, I'd like to bask in some stability before diving into bug hunting all over again. :P

---

### Post by calc on 2008-04-02
> **Vorian Grey said:**
> I agree. Linux has just as backward of a model as Windows does at times. On any modern OS, it should be as easy as download it, and run it, regardless of the version number.

The reason this doesn't work in the general case and probably never will is due to the fact that the binary would have to be statically linked or the OS would have to have every conceivable revision of every library ever released on it, both of which would result in the same problem. Which is applications would take a HUGE amount of ram to run, since their libraries would no longer likely be shareable by any other application. Microsoft to some extent gets away with this without a major problem due to how slowly they release new versions, there has only been one new OS release from them in this decade. But even still many people have heard of the ['DLL Hell']("http://en.wikipedia.org/wiki/Dll_hell") problem, which is caused by needing different versions of the same library due to what an application actually linked to. BTW reading that Wikipedia article might help you to understand why Linux is not nearly as resource intensive as Windows.

---

### Post by calc on 2008-04-02
> **dasunst3r said:**
> The only gripe I have about the software versions on my Hardy installation is that OpenOffice.org is at 2.4 RC2, and not the final version.  Does anybody have any idea as to when the packages for the final version will come out?

Also, the last time I checked, I do have Java 6 u5, so that's not much of an issue for me.  Honestly, I'd like to bask in some stability before diving into bug hunting all over again. :P

OpenOffice.org 2.4.0-3ubuntu1 is already in Hardy as of last night.

---

### Post by newbieforever on 2008-04-04
> **ImpressMe said:**
> Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant [COLOR=Red]***elitist***[/COLOR] "community". But have it your way.
if you please, you could see this post of mine... thank you...
[http://ubuntuforums.org/showthread.php?p=4645479#post4645479](http://ubuntuforums.org/showthread.php?p=4645479#post4645479)
if only mepis or dreamlinux had a better hardware support, i would turn to them...
even if i really love ubuntu... but ubuntu (i read an entire italian book on it, and his story) is not as "community (only) based" as we are used to think...
---edit---
[http://ubuntuforums.org/showthread.php?p=4651413#post4651413](http://ubuntuforums.org/showthread.php?p=4651413#post4651413)
[http://ubuntuforums.org/showthread.php?p=4649681#post4649681](http://ubuntuforums.org/showthread.php?p=4649681#post4649681)

---

### Post by mikewhatever on 2008-04-04
> **ImpressMe said:**
> Without easy updating of programs like OOo 2.3 to 2.4 then widespread adaption of desktop Linux is an illusion. Not because of ignorant users, but because of an ignorant elitist "community". But have it your way.

Complaining is always the way to go for some. Nobody forces you to use Ubuntu, so you can stop right now. Furthermore, if you didn't like the model, why haven't you picked a rolling release distro in the first place? I am not quite sure what you call the community, nor what it has to do with Ubuntu's model of updating software. There is a Back Yard to spill some negativity, you're most welcome to visit.

---

### Post by newbieforever on 2008-04-04
---edit---
As fragos rightly said, I was wrong with this post... I put it in a personal message...
My apologies to everyone...

nbfe

---

### Post by fragos on 2008-04-04
Newbieforever There's no need to excuse your English. I commend you for doing your best with a language you weren't born into. Most people use forums as a place to learn and help others. When something doesn't work it's fair game to discuss it. Personal attacks however don't help the process. People who use forums for complaining only add no value for the rest of us. Those are the people that many would like to see leave and go elesewhere.

---

