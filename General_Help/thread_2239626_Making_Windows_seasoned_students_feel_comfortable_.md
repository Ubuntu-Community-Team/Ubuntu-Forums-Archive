---
title: "Making Windows seasoned students feel comfortable with Kubuntu"
date: 2014-08-14
forum: General Help
---

### Post by maygamer96 on 2014-08-14
After two years of endless campaigning by me and my schoolmate and comrade, Ask Ubuntu user [Shubham Rao]("http://askubuntu.com/users/154414/cshubhamrao/"), we have finally succeeded in convincing our teachers to switch from Windows XP to Linux. A massive virus attack has infested all of our computer lab PCs and the mid-session hassle of formatting and losing data made them balk at the idea of reformatting the PCs halfway through the session-and we suggested they try **Kubuntu** to be comfortable while enjoying the safety and open nature of Linux.

They were thoroughly impressed by the visuals of the KDE Plasma Desktop, and how the Microsoft programs needed by the syllabi (Office 2007, Visual Studio 6 etc.) were running natively in Wine. So this is what we agreed to-we will occupy one PC, put Kubuntu on it, customize it continuously to make it Windows-friendly and then clone the entire lab's HDDs.

But we are running into some hurdles which are affecting the comfort of the students-we asked few of my classmates to give Kubuntu a shot, and though they found it much better than Windows, they were confused by some minor things. They haven't used Linux-or any computer operating system save Windows, they lack a bit of intuition, and they found it difficult to hunt for their Windows counterpart programs on Kubuntu-Kate/Notepad, Konsole/Command Prompt, Paint/LibreOffice Draw-specially using the search bar.

We wish to eliminate these minor things **completely** before the entire lab makes the switch to Kubuntu:

[LIST]
[*]**Disk labels, disk labels, disk labels:** We want a drive to be seen as Local Disk C:, Local Disk D:, and not 78.9 GiB Volume, as Dolphin shows it. However, it seems there is no way how to change the labels.
[*]**Adding custom tags to applications listed in Kickoff:** Say, if someone searches for notepad in the search bar, Kate should come up. Or Konsole when we type "command prompt". They don't know the names of the KDE/Linux Counterparts at all.
[*]**Custom Sections in Kickoff:** Much needed, since guys don't have the patience to look for all of the Microsoft Office and LibreOffice programs combined into one "Office" section by the OS automatically.
[*]**Change program labels? Why not?** Of course, this is heartburn, but they won't give two hoots to whether I call a program Media Player or Amarok.
[/LIST]

We would like your advice please, on these and **other issues that might come to your mind** when thinking how to make Windows-seasoned folks comfy on Kubuntu-and make them stay on to the magic of open source-and Linux.

[B]
PS:[/B] This does sound pretty stupid but please don't ask us to try Xfce or LXDE. KDE Plasma is way too awesome to be abandoned. ;)

---

### Post by TheFu on 2014-08-15
[http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) - Linux explained for Windows users.

Trying to convince people that an apple is an orange is a failing idea. They will know it isn't.  Best to post a **conversion table** that contains the cross-ref for things they should be doing.

Also - I agree that showing the coolest desktop is smart for students. It is only the old people, like me, who need the comfort of LXDE. ;)

Of course, you could lie and tell them they are beta testers for the next Windows Release 
[http://www.youtube.com/watch?v=T3ID2CbtnKk](http://www.youtube.com/watch?v=T3ID2CbtnKk) - it is from 2009, so ... an update might be nice.
The Dell Ubuntu commercial from 2009 is really slick too.

---

### Post by QIII on 2014-08-15
When I was learning German in High School, my teacher spoke in German.  

When I was working on a degree in German in College, my professors spoke German.

Works better.

(Strangely, for my Math degrees my professors also spoke Math...)

---

### Post by varunendra on 2014-08-15
I hate to make negative comments (I prefer not to post at all), but seeing the time and efforts you have already put in, and are planning to put in, I can't help but say this -

"If you are planning to convert people to Linux, then trying hard to make them feel like they are using Windows" is almost a guaranteed plan of failure!

Not suggesting something entirely opposite, but while trying to keep them comfortable, make it ABSOLUTELY CLEAR that Linux and its ways are much-much-much different. It takes time to learn (generally the learning curve is considered to be 6 months before a windows user can be really comfortable with it), but once learnt, they'll love it, probably addicted to it (okay, that's too much).

Put your time and efforts to make the transition easier (create documentation, presentations, take workshops etc.) rather than trying to convert the Linux ways to "Look & Feel like Windows".

That being said, if you are in New Delhi, India, I'd love to help you with the project as much as I can.

Old, but still relevant : [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by grahammechanical on 2014-08-15
Students not willing to learn new things? What is going to happen when they get a job and find that their employer does things differently to what they have learnt? Those who go to school to learn knowledge become obsolete over time. Those who learn how to learn stay up to date and relevant to what employers need.

Regards.

---

### Post by vasa1 on 2014-08-15
+1 to what others have already said. Instead of modifying Kubuntu to suit the students, get the students to modify their mindset.

---

### Post by nerdtron on 2014-08-15
> **Disk labels, disk labels, disk labels:** We want a drive to be seen as Local Disk C:, Local Disk D:, and not 78.9 GiB Volume, as Dolphin shows it. However, it seems there is no way how to change the labels.
I remember you can change the disk labels using GParted. Or you can boot into live mode. The point is to Open GParted and change the Label of the disk/paritition in question.


> **Adding custom tags to applications listed in Kickoff:** Say, if someone searches for notepad in the search bar, Kate should come up. Or Konsole when we type "command prompt". They don't know the names of the KDE/Linux Counterparts at all.


Nah. Notepad is a text editor and so is Kate. Students should know what TYPE of program they are looking for and not the NAME of the text editor. Notepad is not the only text editor in here. Same thing that command prompt is terminal/console emulator.> **Custom Sections in Kickoff:**Much needed, since guys don't have the patience to look for all of the Microsoft Office and LibreOffice programs combined into one "Office" section by the OS automatically.
I'm not sure about the new Kickoff Menu but there is another widget in KDE that can do this. Have you seen Lancelot lanucher? [http://lancelot.fomentgroup.org/main](http://lancelot.fomentgroup.org/main)


> **Change program labels?** Why not? Of course, this is heartburn, but they won't give two hoots to whether I call a program Media Player or Amarok.
I think they can be changed but why?? These are Linux Programs and the Community has exerted much effort in developing them. Renaming Amarok into something like Windows Media Player or any other names is not a good thing to do.


> **PS:** This does sound pretty stupid but please don't ask us to try Xfce or LXDE. KDE Plasma is way too awesome to be abandoned. 
Yes KDE is really good. And what you would like to do is like slapping the KDE team that I don't like these program names.


**Case in point.** This is not windows. This is Linux and it does things differently. And this will continue to happen. You should understand that Linux is not a drop-in replacement to windows. You're giving yourself a hard time if you think it this way.

---

### Post by stalkingwolf on 2014-08-15
linux is not windows (thank the maker).

you might try the windows look desktop from zorin.

---

### Post by maygamer96 on 2014-08-16
Thank you for responding, guys. I know that indeed what I am doing is sacrilege to the Linux Community and KDE, but considering tight-packed schedules, there's no way we can organize orientation schedules for them (I am in my final year of schooling). But still, we're trying to get them comfy because once they settle into KDE, then we'll roll it back to the usual: this is for them to adapt quickly.

Thank you for the advice, everyone-I'll now try to maintain the purity of Kubuntu as far as their intuition allows me. :p

---

### Post by TheFu on 2014-08-16
We all feel your pain.  

I've attempted to migrate a few companies and it never worked out well.  The only migration that DID work well was my mother's. She got hit with a virus in 2010.  Prior to that, I'd had her using F/LOSS under Windows, so the switch to Linux wasn't very traumatic.  She were already familiar with the programs. That was the key - as was being available to install any programs needed or fix issues and I added her machines to my normal weekly patch script and did remote backups - what is 2 more machine when I'm doing 20 already?  Because she had P4 machines, KDE wasn't an options - we used LXDE and they were happy ... er ... mostly.  When the P4 died, swapped in a Core i7 (no other changes) ... and Mom just said - "it feels a little faster" - but it was about 100x faster. The great thing was that for end-user stuff, the experience really wasn't that different.  The printer never worked with Linux, so I replaced it with a $60 laser ... which was working still when Mom died last year.

I've offered free computer support to my extended family (30 people) since 2008 - if they would switch to Linux. NOBODY has taken me up on it even after seeing it and using it at Mom's place. There is just too much FUD out there.  Most of the "computer people" - i.e. in the business - run OSX now.  The blue collar families have a PC full of viruses in the corner than nobody uses and they get along with their smart phones or a tablet.  One person even bought one of those MS-slate things ... which doesn't work with many websites. It was all FUD. She would have been much better off getting a chromebook - but the FUD scared her into getting the $650 slate thingy. Whatever.

Basically - we're trying to get you prepared for when the computers go unused since the OS is not what the students want. If they are unwilling to try it, change a little, it will never work.  Office 2007? Really?  That's 2 releases behind.  Heck, libreoffice would be better, IMHO.  I wouldn't bother telling them that it is different.

Perhaps if the computer department switched to Linux for programming classes, then the business department, then the normal teachers, then the administration ... of course 1 or 2 systems with Windows available over RDP would still be needed to run those few specific programs that only work on Windows ... but a migration over a 2 yr period is the only way to get this to work successfully.  There is a paper for how the City of Munich, Germany did it.  Most places that talk about it are hit with free Microsoft licenses, which stops the migration for another 3-5 yrs.

Back in 2005, my boss begged me to switch over 20K laptops to Linux - I did a few quick calculations and determined that the $5M/yr we were paying for licenses and support was a bargain compared to what migration would cost. These laptops had extremely specialized software that had been built only for WinXP, with special drivers to interface with telecom equipment. Drivers for any other OS simply are not available, so porting to Linux would be ... $20M for each - perhaps more.  Anyway - it wasn't cost effective even over 10 yrs. Sometimes that is the best answer.

I've also heard where local schools switched over to Linux, only to have the HW support organization come in and reload Windows on a key server because they didn't know any better - which brought down all the client workstations. This was all over a 5 minute-fix-issue, but their lack of Linux knowledge toasted the setup. 

Norwegian schools switch:  [http://developer.skolelinux.no/artikler/2006-04-02-debconf6.pdf](http://developer.skolelinux.no/artikler/2006-04-02-debconf6.pdf)

We really do hope for the best with your efforts.  Seriously - good luck.  Perhaps this time it will work, that just is not what we've seen in the USA.

> "Never doubt that a committed group of people, however small they may
be, can change the world. In fact, it is the only thing that ever has."
-- Margaret Mead --

---

### Post by Rob Sayer on 2014-08-16
I wouldn't touch Zorin.  There's a guy on another forum I use who installed it, thinking it's going to work the same as Windows 7.  Which it doesn't, and their tech support is just ridiculously bad.

As mentioned, linux does not work like windows so making it look more like windows isn't going to change that.  Of course, I still want a Start button ...

Actually linux works more like a Mac because OS X is also derived from Unix.  I don't think it's actually Unix ... they have BSD certification but they use a different kernel ... but Steve Jobs himself said OS X was very linux like.

Put it this way.  If you could make it work that much like windows, linux would *be* much like windows, and I wouldn't be using it.

---

### Post by marco-parillo on 2014-08-16
Kubuntu has a "start button" which makes it more familar to WinXP users, but the default Plasma Desktop behavior is single-click, so you may want to go to System Settings > Input Devices > Mouse and change single-click to double-click.

---

