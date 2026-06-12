---
title: "The SO is called ubuntu or bugbuntu?"
date: 2007-03-29
forum: General Help
---

### Post by ozp on 2007-03-29
Hello, I wonder if the name of the SO is really ubuntu or should be bugbuntu

I think bugbuntu may be better because there are so many bugs....

I'm sad because of the last problem that happend on a bugbuntu box that I have in my office.

All the problems started when I instaled the x64 version. Too bad that the CD or the webpages do not alert you about the x64 problems: no flash, more bugs and no java

The solution was to install a 32 emulation or some equivalent deal and run firefox and other tools on it.

Firefox was the first to die. Cannot be updated (out of the box) and crash all the time

Now OOo died as well

with this error (google dont find pages related to the error)

```

ipc@sempron:~$ ooffice

/usr/lib/openoffice/program/javaldx: error while loading shared libraries: libst lport_gcc.so.4.6: cannot open shared object file: No such file or directory

/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: l ibstlport_gcc.so.4.6: cannot open shared object file: No such file or directory



** (process:5243): WARNING **: Unknown error forking main binary / abnormal earl y exit ...

ipc@sempron:~$
```


I know that no one will reply and if someone does will take my post as a flame, fudge or equivalent

but the fact is that I support linux, support ubuntu

I even use ubuntu in my own box. I want to use only ubuntu in all my systems

But I'm just a regular user, not a hacker

the box is a 6,06 x64

---

### Post by solar george on 2007-03-29
Have you tried reinstalling, but with the ordinary ubuntu?

---

### Post by orb9220 on 2007-03-29
To keep a stable system I always run the 32bit version. Also alot less headaches for people that don't like to deal with the 64bit issues.

---

### Post by ozp on 2007-03-29
This was the first ubuntu box installed in my office. In that time I was not aware about the x64 flaw.

I'm trying to not reinstall because this will require time that I dont have

Install is fast, but configuration, customizations, instalation of other softwares, network etc takes lots of time

you have to make the box ready for the users, so my users wont understand if they have to install or configure anything

they just say: this is not working

---

### Post by Rui Pais on 2007-03-29
you don't need a 32 emulation, thats an extra work.

you just need linux32 and you can run most 32b versions, even FF with flash and java.

For firefox [read here ]("http://www.ubuntuforums.org/showthread.php?t=202537")an how-to. If it crashs try with Firefox from mozilla.org.   

For a general workaround on 64bits problems, check this [thread here]("http://www.ubuntuforums.org/showthread.php?t=191205"). It's for dapper but the basic principles applies to all versions.

For your openoffice. Seems a know problem, a conflict with your video driver. [Check here]("https://launchpad.net/ubuntu/+source/openoffice.org/+bug/63676"), bug and workaround.

---

### Post by Bachstelze on 2007-03-29
Flash and Java are not part of Ubuntu. It is not Ubuntu's business to tell if they are 64bit-compatible or not.

---

### Post by ozp on 2007-03-29
> **Rui Pais said:**
> you don't need a 32 emulation, thats an extra work.

you just need linux32 and you can run most 32b versions, even FF with flash and java.

For firefox [read here ]("http://www.ubuntuforums.org/showthread.php?t=202537")an how-to. If it crashs try with Firefox from mozilla.org.   

For a general workaround on 64bits problems, check this [thread here]("http://www.ubuntuforums.org/showthread.php?t=191205"). It's for dapper but the basic principles applies to all versions.

For your openoffice. Seems a know problem, a conflict with your video driver. [Check here]("https://launchpad.net/ubuntu/+source/openoffice.org/+bug/63676"), bug and workaround.

I went to the ooo bug page but it is too complicated...
I already loose much of my time to keep my own bugbuntu working.
Right now the chalenges of my own box are:

find a way to burn DVD ISO images (cdrecord bug)
find  a way to use my cell phone with a USB cable. Right now if I connect the cable I can get a complete system freese (some say that this is impossible on linux)
find a easy way to use wi fi and hope that the kernel update did not trashed my wi fi connection (  i did not tested after that)
speculate if a regular bluetooth usb device work out of the box on ubuntu. (I want to buy one)
dream about a way to make IRDA work (and then have a way to connect with my cell phone)




> **HymnToLife said:**
> Flash and Java are not part of Ubuntu. It is not Ubuntu's business to tell if they are 64bit-compatible or not.

Well...  if this is the official ubuntu position than ubuntu is not for human beings
Because the humans that I know use flash and java, and they wont want a system that cannot run those softwares (no matter who falt it is)

If you want to spread the ubuntu use, you must understand that if a box cannot play flash, be box will have no use for a regular human
 (again, no matter who falt is)

---

### Post by Bachstelze on 2007-03-29
Is is not Ubuntu that won't run Java and Flash, it is Flash and Java that won't run on Ubuntu, it's different. Ubuntu would be very happy to run Flash and Java on 64bit but Adobe and Sun do not want to make 64bit versions. Send trolls to them, not to us.

---

### Post by ricardisimo on 2007-03-29
Firstly, you catch more flies with honey than vinegar, a fact you should keep in mind when posting. Secondly, you sound like someone who's made up his mind about Ubuntu, so maybe Windows is for you.

There's nothing wrong with that. There are much easier aspects to it... and they cost money. There's a philosophical and a financial motivation for many of us being here. You need to ask yourself if you share those motivations.

Good luck with the problem.

---

### Post by NicoleM on 2007-03-29
I've only been here for a short time, but I've read a lot of posts, you mention that you think you'll be flamed...I honestly don't understand why are you anticipating that sort of behavior.

I must say there's certainly a very negative tone to your posts, but it's understandable as it's easy to get frustrated with something new.  This forum, however, is probably the last place in the world you will be flamed.

if you're outlining your problems to receive help, there are MANY people here more than willing to help you as I've discovered firsthand in the last couple of weeks.  Out of respect for forum members that are donating their time (read: no pay!) it's best to keep the results of that frustration to a minimum when dealing with other users.  They're a valuable resource, don't burn bridges!

if you're outlining your problems without the intent of seeking help, then there's not much this forum can do for you.  you've already received a few suggestions, but if you're frustrated enough to consistently refer to the OS as "bugbuntu" then it seems as though you've already made up your mind.

when choosing an OS, the main theme i ran into was that linux isn't for everyone.  ubuntu isn't for everyone.  if you find yourself becoming increasingly frustrated and don't have the time, motivation, or patience to seek help, then you may be one of those people for whom this OS (or whatever version of this OS you selected) is not the right choice.

i for one hope you give it a chance if not now maybe at a time when you have a little more time and patience to fool around with it.  In my short time here, I've learned a great deal.  there is a learning curve for sure, but it's not as steep as some make it out to be.  and like I already mentioned, if a guide is too complicated for you to understand copy and paste what parts you've done and what parts you don't understand with specific questions and comments about why yo don't understand it.  this forum is for beginners and the contributors have what seems to be an infinite amount of patience in making things simple for new users, but if you shut  yourself off and say "that looks too hard," well, there's only so much that can be done to assist you.

---

### Post by ozp on 2007-03-29
> **HymnToLife said:**
> Is is not Ubuntu that won't run Java and Flash, it is Flash and Java that won't run on Ubuntu, it's different. Ubuntu would be very happy to run Flash and Java on 64bit but Adobe and Sun do not want to make 64bit versions. Send trolls to them, not to us.

I know that.
But the information about the lack of those apps should be more available.
How many people do you know that installed x64 by mistake?

They think: I have x64 machine, so its better to install x64 software!

When they realyze that they made a mistake its too late.

Ive seen tons of messsages about this issue. 

Its strange how linux developers cannot understand how users work and think

Ubuntu should have a different approach
but as ubuntu grows those linux "warriors" are growing as major group

---

### Post by Warpnow on 2007-03-29
Flamed? heh, the people on ubuntu's forums are so nice it actually scares me sometimes. I want to check and make sure they're not A.I. ;)

---

### Post by NicoleM on 2007-03-29
> **Warpnow said:**
> Flamed? heh, the people on ubuntu's forums are so nice it actually scares me sometimes. I want to check and make sure they're not A.I. ;)

100% agreed.  I consider myself a pretty patient person but the people that donate their time to contribute here are on another level altogether.

---

### Post by solar george on 2007-03-29
> Its strange how linux developers cannot understand how users work and think


Try doing something constructive -like trying to get the website people to put a warning up, not having a go at other users.

Secondly if you read the 64bit forum you will see this [http://www.ubuntuforums.org/showthread.php?t=368607]("http://www.ubuntuforums.org/showthread.php?t=368607")

---

### Post by Rui Pais on 2007-03-29
> **ozp said:**
> I know that.
But the information about the lack of those apps should be more available.

What apps? everything you mention works here.
> 
How many people do you know that installed x64 by mistake?

None! Anyway if people install blindly stuff they don't understand... 
in your case you should have double care since you are administrate a system for other users.
> 
They think: I have x64 machine, so its better to install x64 software!

When they realyze that they made a mistake its too late.

Never it's too late. 
Sorry to say, but the time you waste writing this kind of threads you could have solved issues by now...
> 
Ive seen tons of messsages about this issue. 

Its strange how linux developers cannot understand how users work and think

Wrong. They are work on it. There is at least 3 different approaches nspluginwrapper, gnash and swfdec... besides the previous mentioned tones of times: use firefox32 or swiftfox. 
> 
Ubuntu should have a different approach
but as ubuntu grows those linux "warriors" are growing as major group
a bit pretentious don't you think?
skipping the name calling... did you expect that a full distro, hundreds of persons, devs and users, will change they behavior because you seems to not have time or patience to try to solve your issues? 
There are thousands Linuxs and a dozen, at least, different OSs, most of them free. 
You are not forced to use Ubuntu (even less 64b) if you don't like it.

---

### Post by STREETURCHINE on 2007-03-29
> I know that.
But the information about the lack of those apps should be more available.
How many people do you know that installed x64 by mistake?

They think: I have x64 machine, so its better to install x64 software!

When they realize that they made a mistake its too late.

Ive seen tons of messsages about this issue.


to find out about these things ,i think they call it research.

before i install anything or for that matter buy or do anything i look into its good points and the bad  points .

i browsed these forums for a week before i installed and learnt a lot about what it will do and what it wont,

then i made an informed choice and installed ubuntu,



to say there is no documentation is just !"well i will leav it there"

type 64bit  into the search panel and you have just about all the information you want.

so if you really need help post a request in a polite fashion,with all the relevent information and someone will freely give there time to try and help.

---

### Post by ozp on 2007-03-29
> **NicoleM said:**
> I've only been here for a short time, but I've read a lot of posts, you mention that you think you'll be flamed...I honestly don't understand why are you anticipating that sort of behavior.(...) this forum is for beginners and the contributors have what seems to be an infinite amount of patience in making things simple for new users, but if you shut  yourself off and say "that looks too hard," well, there's only so much that can be done to assist you.

I agree with you. 
I came here to say something about my frustrations with ubuntu more than I came here to seek for help.

Im not an expert user, but I have being use (and trying to use) linux since 1998
I'm now able to have linux installed in my machine and also in my office.
I help many people in the subjects that I understand.

my first message is to spread an idea that is: linux is not stable as we think it is and as it is advertise by the linux users. Linux is stable if you dont mess up with the box. If you install and then just use it (no customization)

---

### Post by NicoleM on 2007-03-29
> **ozp said:**
> I agree with you. 
I came here to say something about my frustrations with ubuntu more than I came here to seek for help.

Im not an expert user, but I have being use (and trying to use) linux since 1998
I'm now able to have linux installed in my machine and also in my office.
I help many people in the subjects that I understand.

my first message is to spread an idea that is: linux is not stable as we think it is and as it is advertise by the linux users. Linux is stable if you dont mess up with the box. If you install and then just use it (no customization)

ok so we've established you have not come here to seek help, you've come here to i guess "warn" people about linux?

I think that makes this thread off topic.  I'm sure there are plenty of places for you to voice your concerns and plenty of people that would be happy to hear them, but I don't think the beginner forum where people are coming to seek troubleshooting help and other information is necessarily the correct place for it.  

i'm not telling you that your message isn't valid, I just don't think it's helpful in this forum, and don't think you'll get a very receptive audience to your message, unless of course you're attempting to start some sort of flame in which case I'd encourage other users to simply take this as one opinion and resist the urge to respond in a negative manner.

you're entitled to your views though but be advised there are many that will have very valid counterpoints for everything you've presented.

what you mention regarding stability is not exclusive to linux.  Windows is just as susceptible to user error if not more so, but i'm not here to debate OSes.  I'm sure there are many other forums for such a debate.

---

### Post by ceeg on 2007-03-29
> **ozp said:**
> I agree with you. 
I came here to say something about my frustrations with ubuntu more than I came here to seek for help.

Im not an expert user, but I have being use (and trying to use) linux since 1998
I'm now able to have linux installed in my machine and also in my office.
I help many people in the subjects that I understand.

my first message is to spread an idea that is: linux is not stable as we think it is and as it is advertise by the linux users. Linux is stable if you dont mess up with the box. If you install and then just use it (no customization)

This is true for any operating system. If you don't "mess it up" it will work fine. However, to say you cannot customize linux without "messing it up" is ridiculous, sorry.

What is the point of this thread if you obviously have your mind set? I don't see the point in posting. If you want help, we will be more than happy to provide it though!

Good luck.

---

### Post by Spike-X on 2007-03-29
> **ozp said:**
> 
Right now the chalenges of my own box are:

find a way to burn DVD ISO images 

Install GnomeBaker. The Tools menu has options to burn CD and DVD image files.

> **ozp said:**
> find  a way to use my cell phone with a USB cable. Right now if I connect the cable I can get a complete system freese (some say that this is impossible on linux)

I guess that'd be up to your phone manufacturer to make their software compatible with Linux. 



> **ozp said:**
> Well...  if this is the official ubuntu position than ubuntu is not for human beings
Because the humans that I know use flash and java, and they wont want a system that cannot run those softwares (no matter who falt it is)

If you want to spread the ubuntu use, you must understand that if a box cannot play flash, be box will have no use for a regular human
 (again, no matter who falt is)

Yeah, getting Flash to install on 64-bit was tricky for me. I can't remember exactly how I did it (I really need to start writing these things down), but it involved using ndiswrapper in some fashion.

I don't really think it's fair calling these issues 'bugs', though. It's hardly Ubuntu's fault if software vendors refuse to write compatible software. 

I do agree that there should perhaps be some kind of warning or disclaimer about Flash not being able to be installed directly on amd_64. That was a surprise I could have done without on my first day.

Using Ubuntu hasn't been hassle-free for me, but I've sure learned a hell of a lot by finding solutions to the problems I've encountered.

---

### Post by wpshooter on 2007-03-29
Ozp:

It appears to me from what you said in one of your early postings, that you are attempting (at least at some level) to bring Ubuntu into your work/business envirnoment.

Personally, I do **NOT** think Ubuntu is **YET** ready for use by the general computing public in a business envirnoment for multiple reasons (but I believe in time it **MAY** get there eventually).

BUT, for an operating system that is absolutely FREE, I find it to be very good especially when you think about the relative short time period that it has been in use as Ubuntu/Canonical/Linux as compared to the long life span of the M/S O/Ss.

I think Ubuntu is great for home use now and possibly to use in a business environment on a server basis by those who have special **indepth training** in Linux in general and Ubuntu in particular.

Let us know your specific questions one at a time and I am confident someone will be happy to try to help.

Good luck.

---

### Post by 23meg on 2007-03-29
> **ozp]I agree with you.
I came here to say something about my frustrations with ubuntu more than I came here to seek for help.
[/QUOTE]

This is a technical help forum said:**
> Its strange how linux developers cannot understand how users work and think

FYI, people working on Java and Flash aren't "Linux developers".

[QUOTE=ozp]But I'm just a regular user, not a hacker[/QUOTE]

[QUOTE=ozp]you have to make the box ready for the users, so my users wont understand if they have to install or configure anything[/QUOTE]

As a regular user of an operating system you're not comfortable with, you shouldn't be in charge of setting up others' systems in a corporate environment in the first place.

---

### Post by martinw89 on 2007-03-29
Hey ozp,

I own two computers with processors with 64bit extensions, one an Athlon64 and the other a Mobile Core2 Duo.  I love playing around with Linux and have tried 5 or 6 distros, with both 32 bit and 64 bit versions.  From personal experience, I can honestly and strongly tell you that 32 bit Linux is FAARRRR better in terms of usability than 64 bit versions.  Plus, since 32 bit is tried and true and has existed for a far longer amount of time than 64 bit, software developers like Macromedia have new software out for 32 bit.

If you still have any faith in Linux, try out a 32 bit distro!  You may find out that you'll enjoy Linux a lot, I have a lot more fun on my Linux installation than my Windows installation.

But, if you're not interested feel free to go back to Windows, we don't try to get a stranglehold by unethically bullying members of the forums to continue to use Ubuntu.  Some people are Mac users, some people are Windows users, and some people are Linux/BSD users, and there's nothing wrong with any of them.  I still have Windows on every box, because I like it for reasons like the established gaming market.

Whatever you do, you seem interested in warning others of your experience.  Feel free too!  As long as you're constructive, Ubuntu provides [many places]("http://www.ubuntu.com/community/reportproblem") to report your use, as well as a testimonial section in this forum.  I hope you get an OS working for you, not you working for it.  Good luck! :)

One quick edit:  If you decide to report your experience to others, make sure to distinguish if it's a bug or a missing feature.  Many of your problems are feature problems, not bugs.  Unfortunately, 64 bit is new and Linux does not have a strong market share so many professional developers choose to ignore us.

---

### Post by ricardisimo on 2007-03-30
> **Warpnow said:**
> Flamed? heh, the people on ubuntu's forums are so nice it actually scares me sometimes. I want to check and make sure they're not A.I. ;)

You read my mind. High-5 on that. [slap]

---

### Post by hikaricore on 2007-03-30
> **ozp said:**
> 
When they realyze that they made a mistake its too late.

Incase it hasn't been mentioned, I wanted to politely inform you that
you have incorrectly spelled the following word:

[SIZE="7"]***REALIZE***[/SIZE]

Having said that, I hope you trip and fall on your own ego.

It seems dense enough to break a few bones.

---

### Post by Lucifiel on 2007-03-30
> **ozp said:**
> I agree with you. 
I came here to say something about my frustrations with ubuntu more than I came here to seek for help.

Im not an expert user, but I have being use (and trying to use) linux since 1998
I'm now able to have linux installed in my machine and also in my office.
I help many people in the subjects that I understand.

my first message is to spread an idea that is: linux is not stable as we think it is and as it is advertise by the linux users. Linux is stable if you dont mess up with the box. If you install and then just use it (no customization)

Hmmm... I actually disagree that any operating system will work fine even if you don't mess with it. After all, many operating systems provide support for thousands of softwares, devices, etc., etc. 

So, given the complexity of an o/s, it is common for bugs to arise even when the user uses the system for working with Open office and other simple tasks. After all, there have been many times when a new update for a software is released and a bug is discovered. And device drivers sometimes DO interfere too with a program or with the operating system. 

Even in the good old days of Win 3.1 and Win95, there were also problems that dogged the operating systems. I wouldn't miss those days, though, for the internet wasn't of too much help if you had problems with your computer. :p 

It's been many years since the first operating system was coded but we're still light years away from totally bug-free operating systems. :)

---

### Post by ceeg on 2007-03-30
> **Lucifiel said:**
> 
It's been many years since the first operating system was coded but we're still light years away from totally bug-free operating systems. :)

That day will never come :(
As the complexity of hardware and software increases, so must the complexity of the operating system. This parallel will always lead to bugs :(

---

### Post by wpshooter on 2007-03-30
> **ceeg said:**
> That day will never come :(
As the complexity of hardware and software increases, so must the complexity of the operating system. This parallel will always lead to bugs :(

Perhaps if they came up with a basic software that could then develop and write the lower level software itself, i.e. the software would be written by the machines and not us (take out the human error factor).

But having said that, I am sure some form of that probably already exists.

---

### Post by ozp on 2007-03-30
Ok guys! thanks a lot for the help and support!!

I know what I am going to do:

I will download the new ubuntu beta (x32) and then ask my student trainee to install it.
To backup the /home dir and after the install to replace the files
Then Ill see if its easyer to install flash and java at the news ubuntu and hope that when the new ubuntu is released my box gets updated


And yes, neither ubuntu or any linux is ready for bussinness use or advanced home user

Is ready for corporate use (when you have a tech support team and very restricted user rights)

I am fighting to use ubuntu, and I dont boot on other system for quite some time

but I am having a lot of problems

someone told that gnomebaker should burn ISO. but it does not (in my box)
neither k3b or any other that use cdrecord 

I get a known bug error

xfburn works, but it can only burn CD images

---

### Post by Adramelech on 2007-03-30
have you tried: right click on your .iso file -> write to disc

---

### Post by daynah on 2007-03-30
> **ozp said:**
> Ok guys! thanks a lot for the help and support!!

I know what I am going to do:

I will download the new ubuntu beta (x32) and then ask my student trainee to install it.
To backup the /home dir and after the install to replace the files
Then Ill see if its easyer to install flash and java at the news ubuntu and hope that when the new ubuntu is released my box gets updated


And yes, neither ubuntu or any linux is ready for bussinness use or advanced home user

Is ready for corporate use (when you have a tech support team and very restricted user rights)

I am fighting to use ubuntu, and I dont boot on other system for quite some time

but I am having a lot of problems

someone told that gnomebaker should burn ISO. but it does not (in my box)
neither k3b or any other that use cdrecord 

I get a known bug error

xfburn works, but it can only burn CD images

Hello! Welcome to the community! I'm going to give you a little introduction to the Ubuntu Community and how to get around here. By the way, in the time it took you to post all of these, you could have reinstalled 32x Ubuntu! :)

When you use linux, I hope you remember something very, very important... the vast majority of linuxes (is that even a word) are made by people like you. That's not just a corny PBS line, it's the truth. And people like you and me, well, the majority use 32x, not 64. So what are the majority going to write for? 32. It's the majority rules, mob mentality. It's great for the average, not great for outskirts.

I'm going to take a guess that you're not a developer. Developers do not get paid. Yes, Canonical is out big corporate sponsor, but they're mostly paying for the servers we're clogging right now, and when you downloaded 64 and 32. Mark S (for the life I can't remember how to spell his username) is mostly working for marketing, making deals with the other big corporate people, not down here doing the grunt work. The developers do the grunt work, and there's a lot of it. You and me, us peeps that don't have a clue of the inner workings? It's our job to tell the devs what's wrong.

Now when you have a lot of work piled on your desk, do you want someone very angrily telling you that you're not doing a good job and you have tons more to do? No way, Jose! Of course you want to know what to do next and to improve on, but you wanna be told nicely. "Hey, by the way, when you're done fixing the things that are REALLY breaking ubuntu, can you make my bluetooth dongle work?" etc. The developers prioritize all of the bugs that come in. You know, that mob rules mentality. What's important for the most people is going to get fixed first.

When you get into 32, you will be able to burn isos by just dragging the iso file onto the cd. I don't know if that didn't work in 64, never tried it. Being a teacher's assistant, I don't know how smart yours is, but I wouldn't trust myself to install, say gentoo, so maybe you should do it yourself.

Good luck, and I hope that next time you find a bug, you report it to bug finder, and if you have a fixable problem, that's when you come here. :) Welcome to the community!

---

### Post by ozp on 2007-03-30
> **Adramelech said:**
> have you tried: right click on your .iso file -> write to disc

LOL! if this works that will be a greak joke!!
I dont have a ISO here
I&#314;l download the new ubuntu and then test it

what about bin/cue images? (generated from devede)

---

### Post by floke on 2007-03-30
> **ozp said:**
> 

And yes, neither ubuntu or any linux is ready for bussinness use or advanced home user 

It seems good enough for the French Parliament, Munich City Council, Amsterdam, NASA, Disney, Industrial Light and Magic, Google, Ebay, Amazon and the US Military....

(shall I go on?)

---

### Post by wpshooter on 2007-03-30
> **Steve.K said:**
> It seems good enough for the French Parliament, Munich City Council, Amsterdam, NASA, Disney, Industrial Light and Magic, Google, Ebay, Amazon and the US Military....

(shall I go on?)

Don't get me wrong I am a real fan of Ubuntu BUT those you mention very likely have highly paid highly trained Linux experts running their show.  I don't think they can be listed as representative !!!

---

### Post by wpshooter on 2007-03-30
> **ozp said:**
> Ok guys! thanks a lot for the help and support!!

I know what I am going to do:

I will download the new ubuntu beta (x32) and then ask my student trainee to install it.
To backup the /home dir and after the install to replace the files
Then Ill see if its easyer to install flash and java at the news ubuntu and hope that when the new ubuntu is released my box gets updated


And yes, neither ubuntu or any linux is ready for bussinness use or advanced home user

Is ready for corporate use (when you have a tech support team and very restricted user rights)

I am fighting to use ubuntu, and I dont boot on other system for quite some time

but I am having a lot of problems

someone told that gnomebaker should burn ISO. but it does not (in my box)
neither k3b or any other that use cdrecord 

I get a known bug error

xfburn works, but it can only burn CD images

Ozp:

I am using k3b on Ubuntu Dapper Gnome 32bit version and it works flawlessly in burning ISO images.

Have you tried multiple brands of CD-RWs ?  I suggest using CD-RW as opposed to CD-R.

Are you doing a complete erase on the media before attempting to burn ?

Do you have the latest firmware installed on your CD-drive ?

---

### Post by floke on 2007-03-30
> **wpshooter said:**
> Don't get me wrong I am a real fan of Ubuntu BUT those you mention very likely have highly paid highly trained Linux experts running their show.  I don't think they can be listed as representative !!!

OK, how about, from the UK, Birmingham City Council, the NHS (Novell servers), the BBC (interactive digital menus), Cheshire Council, Powys County Council, Kent Police, and Stockport schools.

Any more?

Plus, the corporate sector would be dumb to use Linux without trained staff in any case.

Seems ready enough to me :)

---

### Post by fdrake on 2007-03-30
> **ozp said:**
> LOL! if this works that will be a greak joke!!
I dont have a ISO here
I&#314;l download the new ubuntu and then test it

what about bin/cue images? (generated from devede)

open the terminal and type :
man dd
and read this manual it will axplain you how to create and copy many different images and copy them on cd dvd and removable devices like usb.
if you find a message saying no manual found then type:
sudo aptitude install sdd
Password:

---

### Post by martinw89 on 2007-03-30
Hey again ozp,
I noticed that you would get the latest 32 bit **beta**.  I wouldn't do that if you are already having problems with bugs.  Get Edgy 32 bit, it is more stable.  And when mid-late April rolls around you can press a button and your system will update itself to Feisty (April is the expected release of Feisty).  You can even wait longer, the developers around here are very generous and keep supporting old versions for quite a while.

---

### Post by ozp on 2007-03-31
> **wpshooter said:**
> Ozp:

I am using k3b on Ubuntu Dapper Gnome 32bit version and it works flawlessly in burning ISO images.

Have you tried multiple brands of CD-RWs ?  I suggest using CD-RW as opposed to CD-R.

Are you doing a complete erase on the media before attempting to burn ?

Do you have the latest firmware installed on your CD-drive ?

I forgot to mention that I always use RW media.
And the problem may be related to that.
Ive tried diferents types of media and got anoying results

right now I right click ubuntu.iso and the process halted (15 lasting to finish the burn)

clicking on cancel did not do any good

killing the process (xkill) made me try up to 5 times before kill the burn window

now I cannot eject the CD (neither mount or unmount)

Last time this happends unbuntu was not able to recognize the CD media anymore (after a reboot)

I had to go back to windows and then erase the media there

The only way that erase media works is when I use the nautilus burn tool (cd/dvd creator)
before burn it ask to erase


I have the DD here, but I prefer not read manuals on console. 
Apps should be ready to use with no prior reading, research or study


I dont know what firmware I have. I have a dell m70 notebook

The only thing that I know is that the error from gnome baker and k3b is listed in this forum and its related to a CDRECORD bug more than 1 year old

---

### Post by martinw89 on 2007-04-01
Hey again ozp,
I in no way at all mean this as anything personal or as an attack.  But if you don't like reading how to do stuff, Linux really isn't the way to go.  Seriously, you will get more done with Windows because you already know how to use it.  With Windows, you probably had to read how to do stuff at first too but at least you already have and it won't be a problem anymore.

---

### Post by spankymasterc on 2007-04-01
> **NicoleM said:**
> I've only been here for a short time, but I've read a lot of posts, you mention that you think you'll be flamed...I honestly don't understand why are you anticipating that sort of behavior.

I must say there's certainly a very negative tone to your posts, but it's understandable as it's easy to get frustrated with something new.  This forum, however, is probably the last place in the world you will be flamed.

if you're outlining your problems to receive help, there are MANY people here more than willing to help you as I've discovered firsthand in the last couple of weeks.  Out of respect for forum members that are donating their time (read: no pay!) it's best to keep the results of that frustration to a minimum when dealing with other users.  They're a valuable resource, don't burn bridges!

if you're outlining your problems without the intent of seeking help, then there's not much this forum can do for you.  you've already received a few suggestions, but if you're frustrated enough to consistently refer to the OS as "bugbuntu" then it seems as though you've already made up your mind.

when choosing an OS, the main theme i ran into was that linux isn't for everyone.  ubuntu isn't for everyone.  if you find yourself becoming increasingly frustrated and don't have the time, motivation, or patience to seek help, then you may be one of those people for whom this OS (or whatever version of this OS you selected) is not the right choice.

i for one hope you give it a chance if not now maybe at a time when you have a little more time and patience to fool around with it.  In my short time here, I've learned a great deal.  there is a learning curve for sure, but it's not as steep as some make it out to be.  and like I already mentioned, if a guide is too complicated for you to understand copy and paste what parts you've done and what parts you don't understand with specific questions and comments about why yo don't understand it.  this forum is for beginners and the contributors have what seems to be an infinite amount of patience in making things simple for new users, but if you shut  yourself off and say "that looks too hard," well, there's only so much that can be done to assist you.

Hail to that i for once have never since i started using ubuntu have ever been Flamed? maybe in other forums where the community isnt to friendly? because this community is very friendly and i myself have learn from many of the users on these forums... 

As for your problems well i cant help u there unless i was there and it sounds to me that u already gave up on the OS so i think what would be best for you is ask your office to buy you a nice copy of the most selling OS *cough* Vista or Windows and install that without a hassle 

im not one to be flamming and im not trying but u have certainly showed no respect or asked for help in a nice tone.... Good luck to you :) :popcorn:

Edit: Don't reply with a message saying how we flamed you because we didn't and dont use vulgar language as we haven't.. forgot to mention im only 17 and i have Quad booted Linux.Mac,Windows Xp, and Vista.... all it takes is patience....

---

### Post by Trepex on 2007-04-01
> **ozp said:**
> I have the DD here, but I prefer not read manuals on console. 
Apps should be ready to use with no prior reading, research or study

Seriously? Come on now...

---

### Post by slayerboy on 2007-04-01
> **ozp said:**
> my first message is to spread an idea that is: linux is not stable as we think it is and as it is advertise by the linux users. Linux is stable if you dont mess up with the box. If you install and then just use it (no customization)

wait...what :confused::confused::confused:

Let me pose a question.....Is ANY version of Windows bug-free?  c'mon dude!  I'm not one to flame, or try not to, but this is the stupidest thing I have ever heard!

You're using [SIZE=5]_***FREE ***_[/SIZE]software (as in beer in most cases) and complaining about bugs and things that you can't do because you don't want to take the time to research and read up on what you're getting yourself into?  I'm sorry, did you have fun the first time you installed XP and had to find all those driver cd's or download them?  What about helping that person reinstall XP who installed a new NIC and doesn't have the driver disk and XP doesn't recognize it?

Quite honestly, I think Linux is MORE than ready for any environment!  It all depends on how you go about setting it up.  If you just fly by the seat of your pants and expect everything to work, then...uh...yeah...you're going to be severely disappointed.  If, however, you do your research, and realize that there are issues and take steps to try to avoid those issues, then your experience will be much better.

Also, (and I agree maybe this needs to be something that needs to be worked on to get implemented better), /home should be on a separate partition.  It makes life 100% easier if you have to do a reinstall.  Yes, you'll have to reinstall software, but all your settings and documents will still be saved.  If you're running in a corporate environment, you probably already know about the importance of backups on multiple backup sources.  Also, you can get a listing of all the software you have installed on your system and easily reinstall it by following the directions [here]("http://www.arsgeek.com/?p=564") ( [http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564) ).  

Wait...I'll make it easier on you (I've even updated it to use aptitude instead of apt-get!!!):
> 
First, let’s make the list. You’ll be doing all of this in a Terminal Session:
```
dpkg –-get-selections | grep -v deinstall > ubuntu-files
```
Now you’ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a seperate partition or on a disk somewhere. Heck, it’s not that big, email it to your gmail account.

So now you’ve got this list and all is well, until you’re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.

Once you’ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
```
    sudo aptitude update

    sudo aptitude dist-upgrade

    dpkg –-set-selections < ubuntu-files
```

Now you’ve told your system what it needs to install, so let’s install it all.
    ```
sudo dselect
```
This will open up a dselect session. Type ‘I‘ and allow dselect to install of the the packages listed in your ubuntu-files document. When it’s finished, type ‘Q‘ and hit the ENTER key to exit dselect.


Granted, it will take a while to install the missing software, but it's better than trying to remember what was installed!

As far as customizing a system, sometimes, yes, you will run into issues.  That's with ANY OS and ANY software program.  I have yet to run into anything on a computer that doesn't have bugs.  Comptuers and programs are only as smart as the person(s) doing the programming.

Also, just as an FYI, linux developers are generally kernel developers.  That is the kernel is what boots your system and controls the system, the operating system.  The graphical stuff and command line, well, those are just software packages to give Linux added functionality.  Granted, some kernel developers might also help to develop Linux packages or distros, but a Gimp developer is a GIMP developer.  A Ubuntu is a Ubuntu developer.  A Java developer is a Java developer.  Just a little clarification, because problems with individual programs or distros need to be informed to the respective developers with bug reports.  Bug reports are the bread and butter of Linux and it's packages and distros.  Without bug reports, Linux wouldn't be where it is today.

Lastly, like it's been said before, sometimes Linux isn't for everyone, and we recognize this.  If you can't wrap your head around trying to a little research to get things working or not being able to use some windows programs, then you might want to go back to Windows.  No pressure, some people are made for Windows, some are made for Mac, some are made for Linux, some are made for BSD, and yes, even some are made for BeOS.:)

Have fun with whatever you chose, and take it as a learning experience while your doing this.  After all if you're deciding about technical stuff in your company, you're probably in the IT department, right?

:popcorn:

---

### Post by eentonig on 2007-04-01
If you're not familiar with linux, you don't have the time/interest in looking for solutions and trying to 'understand' them AND YOU CAN'T RISK THE SYSTEM NOT WORKING IN A COMMERCIAL ENVIRONMENT, then don't use it.

Hell, I would be fired at my job if I brought a piece of machinery in production, only to say afterwards "Well, I actually don't really now how it works. And it might break regularly"

That said. I do get to install linux machines on the floor. That is. Smaller, unimportant parts of the job, I get the liberty to set up a machine in the lab, get to know the working of it and prove that it can do the job. If that works well and bug-free, I have to write operating manuals for my colleagues so they will know what to do when they have to come into contact with those boxes. And when that's done, I can bring the machine in production. All of this, besides my normal workload offcourse.

For anything you can't afford not being available, don't just put a box and assume it will do what you want. If you want that, and you want to have leverage when it doesn't, pay someone to install it and buy for the support. In that case, when things go wrong, you can take it out on the one who should have known what he was doing. If he's smart, he will make sure he only install software/OS/HW that he knows about and can support.

---

### Post by PlancksCnst on 2007-04-01
All 64 Linux systems have these problems, not just "Bugbuntu".  Actually, Windows X64 has similar problems, too.  It's just a new technology, and it takes time to get everything going smoothly.

By the way, I can sympathize with your frustrations.  I ,too, have been trying to use Linux for many years.  (My first was RedHat
 5.1)  I am only just now beginning to use it as the primary (and only) os on my secondary computer.

---

### Post by ozp on 2007-04-01
> **martinw89 said:**
> Hey again ozp,
I in no way at all mean this as anything personal or as an attack.  But if you don't like reading how to do stuff, Linux really isn't the way to go.  Seriously, you will get more done with Windows because you already know how to use it.  With Windows, you probably had to read how to do stuff at first too but at least you already have and it won't be a problem anymore.


Thats sad... 
I dont mean personal or attack either. 
Your rationale (like many others) does not help the spread of  linux and ubuntu use.
It maintains the linux and ubuntu inside the "geek-hacker" community.

The problems:

It stimulate other OS use instead of linux/ubuntu
It stick with the idea that to use a OS you have to read stuff (you have to study)

If this rationale doesnt change, linux/ubuntu will never make to the masses.
We need linux/ubuntu in the masses because we all love free software (in all the means)

I never had a MAC but I'm 100% sure that I wont have to read anything to complete simple tasks. 
Of course you have to know what are you doing. This knowledge is aside OS knowlegde.
eg: you know that your drive burns DVD, and you know what a .iso image is, and you know what a DVD-RW is, and you know that there are many issues regarding the MEDIA (some are junk).

Why MAC is so good? (its BSD inside)
Because the MAC GUI is so good, its easy!
Its not bugged

The time is running short. Soon OS will be nothing. 
We will be using Google OS over the Web

And I'm not saying that the geek-hacker should be left aside. All the geek-hacker tools still there for your pleasure: vi bash make build grep ...


4 things about 7.04

1- after all the bugs I could burn the ISO image and tested with a desktop box in my house. It started with 1280x1024. I want 1024x768. I changed and it freesed to death. (nothing works)

2- another try and I went to youtube. Firefox installed the flash only by clicking and no reading about how to install flash!!! Thats something! thats what users need, that is what users want. 
Thats what ubuntu should do.

3- happiness does not last long. went to some video sites and the "new codec finder deal" was not able to do the job. The toten plugin opens but does not play or ask to install codec


4- I wonder if 7.04 will able to detect a 5 bottom mouse and configure the buttons like they should work



Just because the flash deal this new ubuntu is far best than the old one.

---

### Post by martinw89 on 2007-04-01
I agree, it does slightly enforce that Linux in general is harder to use than Windows.  Unfortunately, at the moment it can be for certain users depending on their needs.  You seem to be having a hard time doing some simple tasks based on problems with compatibility with your hardware and your software needs.  I sincerely think that your productivity can be much higher with Windows, especially because of where you use your hardware (it sounds like this is a work computer from what I've read).

Also, I know that when I first got Windows I had to read how to do certain things, like home networking, getting drivers, getting on the internet (I had no idea that ethernet drivers wouldn't be there right away when I got my own computer. It's a good thing I had a nice little disc that made it work for me).

I personally think that if the Linux user-base in general does want a change towards usability it will happen.  At the same time, pursuing users to keep using Linux when Linux does not fill their needs does not solve anything.

Ultimately it's your choice, this is just my opinion.  But if you choose to keep using Ubuntu you need to understand that if you want these changes you need to be active in supporting them.  You also need to understand where the line crosses between Ubuntu and other software so you can see how to address your issues.

By the way, to get Flash, just go to it's website and get the installer from there.  I think there's a way through the repositories too but that way is actually simpler.  And because of licensing issues not all codecs are included right away.  Check out [the guide]("https://help.ubuntu.com/community/RestrictedFormats") on installing them.

Again, good feelings all around, I don't mean to make anything personal.  I hope that you find a way to get the productivity and ease of use you want, whether it be through Ubuntu or another OS :)

---

### Post by julian67 on 2007-04-02
Anyone who expects software to be fully useable with no reading or training has a long time to wait. Anyone find Photoshop intuitive the first time they used it? I think not, yet that is one of the highest quality and most used applications in the Windows and Mac environments. If you never used a word processor before i can promise you even using Word requires plenty of struggling. 

I would also take issue with all the people who say if you don't like Ubuntu go back to Windows. There seems to be some conception that Ubuntu is Linux and Linux is Ubuntu. Not true, there are a lot of variations on the GNU/Linux theme and Ubuntu is only one of them (ok maybe 2, 3 , 4 or 5 of them). There are other distros that are being installed in corporate environments tens of thousands of desktops at a time in huge corporations, governments, schools etc. I'd say that's seriously ready for the desktop. If Ubuntu isn't what you're looking for then keep looking because the choice shouldn't be Windows or Mac or Ubuntu, it should be Ubuntu or openSuse or Fedora or Slackware or Mandriva or PCLinuxOS or DSL or RHEL or SLED or Puppy or Mepis or Xandros or Freespire and so on. There's everything in that list from Corporate enterprise OS with paid support to a top quality one man project. If you're looking to use Linux in a business environment than go for a distro that's designed for that environment.

---

### Post by martinw89 on 2007-04-02
The only thing is that third party support for hardware and applications, like flash, does not vary much between distros.  That's the main reason why I think Windows is better than any Linux flavor for this particular situation.

---

### Post by ozp on 2007-04-04
> **julian67 said:**
> Anyone who expects software to be fully useable with no reading or training has a long time to wait. Anyone find Photoshop intuitive the first time they used it? I think not, yet that is one of the highest quality and most used applications in the Windows and Mac environments. If you never used a word processor before i can promise you even using Word requires plenty of struggling. 

Using software like photoshop word ooo gimp requires learning (reading, courses and so on)
But to use a OS, and if you already know what you want you should not need to learn a lot

The only time I had to use a MAC, I had to configure a internet connection.
It as very easy
This is easy with linux now (some flavors) but not for every internet (wi fi is not easy)

The topic is about bugs.

Do you think ubuntu or other linux have many bugs?

I think there are too many bugs, most of them are related to applications 

Right now there is a xorg update to do

If I do the xorg update my X will be broken (because I have nvidia driver)

I have to reinstall nvidia to fix the X

this is a bug 
this happens with no warning
many users think their system is broke, but is an easy fix

stuff like that...

---

### Post by ozp on 2007-04-04
> **julian67 said:**
> Anyone who expects software to be fully useable with no reading or training has a long time to wait. Anyone find Photoshop intuitive the first time they used it? I think not, yet that is one of the highest quality and most used applications in the Windows and Mac environments. If you never used a word processor before i can promise you even using Word requires plenty of struggling. 

Using software like photoshop word ooo gimp requires learning (reading, courses and so on)
But to use a OS, and if you already know what you want you should not need to learn a lot

The only time I had to use a MAC, I had to configure a internet connection.
It as very easy
This is easy with linux now (some flavors) but not for every internet (wi fi is not easy)

The topic is about bugs.

Do you think ubuntu or other linux have many bugs?

I think there are too many bugs, most of them are related to applications 

Right now there is a xorg update to do

If I do the xorg update my X will be broken (because I have nvidia driver)

I have to reinstall nvidia to fix the X

this is a bug 
this happens with no warning
many users think their system is broke, but is an easy fix

stuff like that...

---

### Post by julian67 on 2007-04-04
> **ozp said:**
> 

The topic is about bugs.

Do you think ubuntu or other linux have many bugs?

I think there are too many bugs, most of them are related to applications 



Yes I think you'r right,  there are bugs in every OS and I'm finding far more than I like in Ubuntu. Mostly it's lousy default configuration or bad decisions when the distro was made. 2 examples that have really surprised me:

1: Network-manager. I have principally used openSuse where network-manager and its applet function brilliantly. I was amazed to find that in Ubuntu it is basically non-functional unless you only connect using dhcp, there is no facility to respect static addresses or to connect with dhcp while retaining your own choice of dns with nm. This must have been a conscious decision by Ubuntu as it is done properly in Fedora, openSuse and Slackware, that is it understands your network backend and your own config preferences. For a long time I didn't understand the huge number of posts in Ubuntu forums complaining that nm is terrible, now I do. It isn't terrible, it's actually brilliant but the Ubuntu implementation couldn't be worse.

2. Xorg configuration. I have a laptop with intel graphics and widescreen so i was pleased to find that I didn't need 915resolution, the resolution was correct on first boot. But then I noticed some apps couldn't display fullscreen in Ubuntu even though the same apps worked fine in other distros. I found that the installer's X setup completely ignores the actual monitor dimensions and only sets resolution and depth. Another bad decision. I further found that while a specific (Free Open Source) driver for my graphics set is in the main repos the setup defaults to a generic one designed for older chipsets and there is no prompt to upgrade/update, i only found out by chance.

So I have spent a day investigating and feeling frustrated before settling for using Wireless Assistant for my wi fi and manually editing the config files to fix the dns how I need it, and then reinstalling and reconfiguring X. This should all be unneccessary and in these respects Ubuntu is a very long way behind the 2 big Enterprise led distros and even slackware is easier because you actually expect to do this sort of thing and hence the documentation is better.  A distribution that focuses so strongly on new users had better not keep getting networking so badly wrong, particularly when other Linux distros get it so right and so slick.  I've had a try with Kubuntu feisty and the network manager is still effectively useless, and looking at the bug reports I'm not expecting a lot of progress very soon. 

Another issue I'm dealing with right now is that I'm not stealthed online. Despite setting icmp echo (ping) requests to be ignored my OS keeps responding to them. Not necessarily a major issue but this is unexpected. Even Windows built in firewall  gets this right by default. 

I've found many of the Ubuntu packages to be very old. Afaik Ubuntu is based on Debian unstable but many Ubuntu packages are now older than the ones in Debian *stable*. That is very old indeed! I was looking for some apps in the Ubuntu repos this week and even found one that has not been maintained for 2 years. It's a security product :lolflag: I've spent a huge amount of time compiling from source just to use applications that are either shipped by default in other distros or easily available from a repo. In Ubuntu the choice has been to use very old versions or compile. Mostly I don't mind compiling though sometimes it can be a bitch, but frankly if Slackware shipped with Gnome I might as well use that, it wouldn't take any longer to get it working right. It looks like Debian 4 is going to appear around the same time as the final version of Feisty and maybe openSuse 10.3 will be appearing very soon afterwards. Speaking from experience I am certain that both the Debian and openSuse releases will ship with far fewer bugs,  omissions and ugly hacks than Feisty. 

I was far more impressed with Ubuntu when it was a secondary distro I used to try things out, now I've been trying to use it full time I'm amazed at the power of the marketing that has made it so popular and convinced so many people that it is superior when there are distros out there that show it to be nothing of the sort.

I'm sorry to be so down on Ubuntu but you touched a nerve! I shouldn't be so negative perhaps as Ubuntu Edgy does have some strengths such as a quick install and a good desktop, a good set of default applications,  and it seems fairly stable (though not rock solid) and reasonably economical with memory use but these days that isn't enough. But i'm using it temporarily and it will do for a few months, maybe it will grow on me. I'm using Ubuntu because I bought a new laptop (old one burned out cpu, board) and the soundcard is one of these 7.1 high definition ones with lousy support. I can at least get some kind of functionality in Ubuntu, better than the other distros I use so Ubuntu it is until I've done more testing of beta Alsa drivers etc and can get the thing working OK on other distros.   Anyway now I know why the Ubuntu support forums are the biggest out there. 
Bugbuntu/Hackbuntu/Wedidn'tthinkthatthroughuntu/heywerethegreatestuntu/fanboyuntu/3wisemonkeysuntu take your pick

---

### Post by ozp on 2007-04-04
Yep... Ubuntu foruns are big also because there are too many bugs and problems

Its sad.
Lots of people having the same problems, lots of people helping (but the problems still not solved in ubuntu distro)

For me its come down to the bottom line: 
do we really need that many linux distros? 

Ubuntu linspire deal was the best news Ive reard in many years regargind linux

many distros are migrating to ubuntu

and I ´ d  like to pay for a linux distro (like I did many times with conectiva)

because work require money
and this is nothing to do with free software

---

### Post by Punker on 2007-04-04
I don't think it should be called bugbuntu I just took my time and read a lot and worked out my problems with very little help I used the forum as a big book what ever problem I had I just did a search on the problem and their was post that people had a few years ago with the same problem now I'm chill'n and working on another problem I'm having but its not with Ubuntu  you just need some time to look and dig
I know its a pain in the azz but it will work

---

### Post by julian67 on 2007-04-04
I don't think it's money that makes all the difference, it's having a direction and a focus and getting the priorities right. This is not impossible in a community distro, but harder, whereas a successful company already has a lot of experience in managing collaborative projects and setting targets etc. and has a hierarchy that at certain points has people empowered to override the people below them and just insist on things. I think the general boring "housekeeping" work can suffer in community distros because it's hard to attract volunteers to do unattractive tasks, or to retain those that do start on them. And it's harder in community distros to make good decisions that some people won't like. if you look at Debian and Gentoo they would be non functional as money earning enterprises simply due to the in fighting. It  means that difficult and important decisions get postponed while people get on with the interesting stuff. I don't know enough about the structure of Canonical or the Ubuntu development community so these are general comments.

---

### Post by 23meg on 2007-04-04
> Yep... Ubuntu foruns are big also because there are too many bugs and problems

No, they're big because there are too many users. I can't help but point you to an epic aysiu quote: [read this]("http://ubuntuforums.org/showpost.php?p=2055798&postcount=5"). Better read a few posts back, or the whole thread, to put it in context.

> Its sad.
Lots of people having the same problems, lots of people helping (but the problems still not solved in ubuntu distro)

Lots of people have the same problems, they report them to get them fixed, help each other to find workarounds, and they get solved; some earlier, some later. But as they get solved, new ones emerge, since new features, new hardware, new user needs never stop from emerging, and they inevitably bring bugs with them.

There's nothing you can do about bugs other than reporting and fixing them. They'll always exist, in every release, every platform. 

If you can't bear with bugs, don't use software. If you can't bear with the cold, don't eat ice cream.

> For me its come down to the bottom line:
do we really need that many linux distros? 

Your complaints have nothing to do with the number of Linux distros. We have a [unified Linux thread]("http://ubuntuforums.org/showthread.php?t=328824") where you can find 894738479384 people who asked the same question and got the same answer; feel free to continue your rant there.

> Ubuntu linspire deal was the best news Ive reard in many years regargind linux

When you hear of a much hyped on a deal between two distros, if you think that's one of the rare occurences where distros have ever collaborated, you couldn't be more wrong. 

To a large extent, distros don't develop software; they package and ship it. When distros collaborate or merge, it's not a 1+1=2 situation. Again, read the unified Linux thread where this has been put to rest 4839847 times.

> many distros are migrating to ubuntu

How wrong of them, when there are lots of bugs in Ubuntu.

> and I ´ d like to pay for a linux distro (like I did many times with conectiva)

because work require money
and this is nothing to do with free software

Go ahead. Nobody is stopping you, begging you to use Ubuntu. Use what works for you. Just spare us the FUD that your horribly misinformed comments will cause.

---

### Post by russo.mic on 2007-04-04
wow,

I do all the things you seem to want to do...

IRDA works, as well as my cell as a modem over bluetooth or USB
I can burn CD's
I have flash working, although in 32 bit FF
Java is slow and dumb anyway, but I do have it installed in case I need it.

I have no problems like what your talking about.  All in 64 bit glory.  All it takes is a bit good roll of the sleeves, the wonderful great and fantastic forums here, and google.

Good luck!

---

### Post by julian67 on 2007-04-05
> **russo.mic said:**
> wow,

I do all the things you seem to want to do...

IRDA works, as well as my cell as a modem over bluetooth or USB
I can burn CD's
I have flash working, although in 32 bit FF
Java is slow and dumb anyway, but I do have it installed in case I need it.

I have no problems like what your talking about.  All in 64 bit glory.  All it takes is a bit good roll of the sleeves, the wonderful great and fantastic forums here, and google.

Good luck!

For some people that's true, everything they need works out of the box and no complaints, it's a nice situation to be in, but it isn't the whole story it's only your particular experience (and lots of other people's I hope). Some of the problems go way past bugfixing, they are the result of decisions about how to implement features. Network manager has to be the big one.

And the fact that so many packages are so old is not really anything to do with bugfixing, it says more about strange priorities which i guess are fixed on meeting a rapid release schedule  above all else. When a cutting edge distro ships with packages which are older than Debian stable this is evidence of some serious problems.  Debian's "we'll release it when it's ready" approach is  starting to look good. Even with all their arguments, delays and postponements they're still likely to put out a new stable version that's more up to date *and* more stable than the supposedly cutting edge Ubuntu. I guess it won't look as nice or be as cool though.....

---

### Post by ozp on 2007-04-05
Everything can work on any system. Is just a matter of knowledge and time
You can even write your own aplication or take the source and fix or add stuff.

I dont want to make FUD here. I want to say that I use ubuntu and there are bugs on ubuntu that prevent many people from using it.
I still use because I want to use linux, because linux is free software

If there were a better/easyer distro than ubuntu I'd move
I started trying using conectiva, than mandrake, than fedora, than ubuntu

I dont have an account on lauchpad, the bugs I find are very known ones.


Today I told my trainee to install the beta on the box that had 6.06 x64.
To backup the /home on a DVD and then install 

Bugs:

1 - there was a file with "wrong" encoding, DVD could not be burned. Gnome did not told where was this file. the Find app did not found it. Locate did not found it. (it was on the .trash)

2- I had a hard time deleting trash files. When I copy a file from a CD rom or DVD, the file maintained the permition from the CD (you cannot erase it).  I had to open nautilus as root to be able to empty the trash can


There is another 6.06 box there. I went to that box to play around and my trainee told that the screen resolution was different from his home (it was 1280x1024).
I tried to change the resolution but X broke down, and started again at 1280.

the xorg.conf has VESA as driver. the chipset is VIA.

If I want to change I´d had to look out for tutorials.  I leaved 1280 


I wish so much to use another driver than VESA on those boxes..... VESA is just a trash driver.
but how to do that? 
those VIA chipsets are widely used here. Ubuntu had to recognize them and use the proper driver. 
The video speed is very slow. Its like an old computer



I use ubuntu at my notebook. Yesterday in the middle of the boot process I opened the CD drive and placed a DVD there.

I found out that I could not use the burn app in gnome anymore.

I had to reboot to enable it.


See? this are just some bugs from today and yesterday. All of them have fixes, workarounds, tutorials.
I wont be able to fix them, because I wont look for those fixes

Also I wont fix many bugs in my notebook box, beucase I have a fear: 

A fear that when the 7.04 comes out, that the upgrade from 6.10 will not work good, that because the codecs, plugins, additional softwares, drivers , beryl, nvidia etc that I installed will trash the upgrade.

---

### Post by accludetuner on 2007-04-09
For what it's worth, I have both 32 and 64 versions running on the same box.  The 64 bit works just as well as the 32 and any errors I run across apply to both.  I do not have any firefox issues you described and Java works great.  Sure there are some settings to adjust and conf files to edit but this is all part of Linux and you would experience similar things regardless of flavor.  Maybe there's another Linux version that would meet your needs better being an office environment.  I think that would be worth looking in to since you do not seem willing to put in the necessary time to configure Ubuntu for your needs.  The choice is yours.  I've used Solara Unix servers joined to openSuse desktops for a work environment before with great success.  Of course it required setting changes and conf file edits to get it to work and that seems to be what you're avoiding.  I've never installed any OS (including Windows) and had it function 100% and already set up for what I want and maybe I've just learned to expect to have to set some things up manually.  You would not be disappointed if you expected (and planned for) the same.  I wish you the best whatever you end up doing.

---

### Post by julian67 on 2007-04-09
> **ozp said:**
> Everything can work on any system. Is just a matter of knowledge and time
You can even write your own aplication or take the source and fix or add stuff.

I dont want to make FUD here. I want to say that I use ubuntu and there are bugs on ubuntu that prevent many people from using it.
I still use because I want to use linux, because linux is free software

If there were a better/easyer distro than ubuntu I'd move
I started trying using conectiva, than mandrake, than fedora, than ubuntu

I dont have an account on lauchpad, the bugs I find are very known ones.


Today I told my trainee to install the beta on the box that had 6.06 x64.
To backup the /home on a DVD and then install 

Bugs:

1 - there was a file with "wrong" encoding, DVD could not be burned. Gnome did not told where was this file. the Find app did not found it. Locate did not found it. (it was on the .trash)

2- I had a hard time deleting trash files. When I copy a file from a CD rom or DVD, the file maintained the permition from the CD (you cannot erase it).  I had to open nautilus as root to be able to empty the trash can


There is another 6.06 box there. I went to that box to play around and my trainee told that the screen resolution was different from his home (it was 1280x1024).
I tried to change the resolution but X broke down, and started again at 1280.

the xorg.conf has VESA as driver. the chipset is VIA.

If I want to change I´d had to look out for tutorials.  I leaved 1280 


I wish so much to use another driver than VESA on those boxes..... VESA is just a trash driver.
but how to do that? 
those VIA chipsets are widely used here. Ubuntu had to recognize them and use the proper driver. 
The video speed is very slow. Its like an old computer



I use ubuntu at my notebook. Yesterday in the middle of the boot process I opened the CD drive and placed a DVD there.

I found out that I could not use the burn app in gnome anymore.

I had to reboot to enable it.


See? this are just some bugs from today and yesterday. All of them have fixes, workarounds, tutorials.
I wont be able to fix them, because I wont look for those fixes

Also I wont fix many bugs in my notebook box, beucase I have a fear: 

A fear that when the 7.04 comes out, that the upgrade from 6.10 will not work good, that because the codecs, plugins, additional softwares, drivers , beryl, nvidia etc that I installed will trash the upgrade.

You know if you're having so much trouble it would be better to switch to a different distro. You have a choice, there is way more to GNU/Linux than Ubuntu. I spent a lot of hours yesterday working out how to get the Alsa beta drivers installed and set up right in openSuse for my ICH7 hda sound controller and I switched back to it last night and no regrets. The 3D graphics acceleration is way better in openSuse, I have all the options in beryl working whereas in Ubuntu I could only run the basic set, this is with the same modules loaded and the xorg.conf set up the same. I got quite a few memory allocation erros in Ubuntu which  related to its inability to exploit the (limited) capability of my 64MB Intel Integrated Graphics. I now have up to date libraries and applications, the latest stable versions of Rhythmbox, Liferea, K3b, Epiphany, Krusader, Audacious, F-Spot etc  and the rock solid stability I missed in Ubuntu. I have network manager effortlessly switching between dhcp wireless encrypted and wired static IP networks, all the while with my chosen DNS config.  I have a preconfigured IP tables firewall by default and AppArmor locking down paths and permissions. All this and it uses less RAM that Ubuntu (i managed the runlevels on both the same as far as possible). You know if you don't like Ubuntu you have choices, there are several other distros that aim to please the technical and non technical user alike and you should try some of them. Debian 4.0 was released today, if you feel happier in the Debian type environment  you could have a look at that, but I think maybe a change of flavour might be better for you. But some things you're having trouble with are common to all distros. You just *have* to learn something about file permissions, it isn't complex at all but if you ignore it it will bite you. And setting up your distro to use the correct graphics drivers and display the right resolution shouldn't take you long to figure out if you spend maybe half an hour or an hour reading online HOWTOs or buy one of the Ubuntu books. I think it's also a mistake to think that because you can install Ubuntu in 30 minutes that that's as long as it takes. Realistically you need to take several hours to set up each machine, minimum. If you have any identical machines you can clone the drive from one install.

---

### Post by ozp on 2007-04-09
ok, thanks again!

I may not look at other distros anymore. The problem is that I dont have time or it anymore.
My work is not about computers. I know computers because I like (more than I need). This opened many doors for me, but I cannot spend more time on computers.

I'm with ubuntu more because of the filosofy 

I hope that the system gets more stable as the time goes by and more features may be added to make life easyer.

Examples from this weekend:

I went to a buddy farm to spend the weekend.
I took my notebook so we could watch some movies that I downloaded


I had a hard time  making the S-video to work. Nvidia settins said that some changes requires X restart ( who told that linux does not need restarts??)
Restarts did not work

Went back to windows and S-video was ok (very easy to configure using the nvidia app)

I could not watch the video on windows because It cannot read linux partition (windows sux)

I could not transfer the file to windows partition because ubuntu does not write on NTFS (it can be done, but not just "clicking") I had no connection there

I tried many options on nvidia settings and were able to make s-video work as a twin view

As I was trying to make this work my friends said:

Why do you use linux? its worse, it has problems, it does not work!

And for the worse, the "check forced after 30 boots" went up and I have to wait very long to boot (my friends: linux is slow!)

After finally make s-video work I had to choose what app to play the video

Video lan were choosed because It can resize the video window to fit the TV screen (crop video)
But video lan has problems with subtitles. I dont know why it does not play all the subtitles. It play some, halt, play another, halt, and so on

I had to use mplayer or gxine.

This is another tale of the linux bugs and problens that I face.
Maybe this subtitle problem does not happend on another box. maybe because of the version, maybe because of the sub file (srt), maybe because of the codec.. who knows?

why I did now used the default ubuntu video app?
Because it is the worse of all. Subtitles does not even play on it. they play with wrong char set

çãé - those chars play wrong

---

### Post by julian67 on 2007-04-09
> **ozp said:**
> 
I'm with ubuntu more because of the filosofy 


The philosophy isn't really different from the other Free distros, Aside from the Live installer the Ubuntu distro isn't really that different from Debian. It's the marketing that is more powerful :lolflag:

---

### Post by ozp on 2007-04-11
Its very different!!!

It has a comercial and marketing policies and it does not have a comercial version!

Debian does not have anything comercial and debian does not care much about the end user

Other linux distros are striped down versions of the comercial distro

---

### Post by julian67 on 2007-04-13
> **ozp said:**
> Its very different!!!

It has a comercial and marketing policies and it does not have a comercial version!

Debian does not have anything comercial and debian does not care much about the end user

Other linux distros are striped down versions of the comercial distro

I can't really see the difference between Ubuntu/Impi and Fedora/Red Hat or openSuse/SLED. All the distros have a no cost Free version and a paid for commercial version with support.

---

### Post by ozp on 2007-04-13
Red Hat is different from Fedora
As open suse is different from Novel linux
Like mandriva free and paid

Enterprise versions and free versions

Ubuntu is just ubuntu, we dont have the comercial version of ubuntu

---

### Post by Josey on 2007-04-13
Something I got for free isn't working like I want!  I'll go bitch at some people.... be back in a bit.

---

### Post by julian67 on 2007-04-14
> **ozp said:**
> Red Hat is different from Fedora
As open suse is different from Novel linux
Like mandriva free and paid

Enterprise versions and free versions

Ubuntu is just ubuntu, we dont have the comercial version of ubuntu

[http://www.impilinux.co.za/]("http://www.impilinux.co.za/")


> Impi Linux' primary business centres around the development of desktop operating systems to exact customer requirement. This involves doing an audit of existing systems, documenting existing infrastructure, evaluating an organisation's readiness to migrate to a Linux desktop operating system, developing a strategy for the migration, documenting migration paths and then building a distribution, incorporating both open source and proprietary software to meet the customer's exact requirements. Training (including certification), facilitation and change management services are also offered. ...................


...................Impi Linux is today owned by Shuttleworth's HBD Business Holdings (65%), Khuselo Investments (Pty) Ltd (10%) and several minor shareholders (5%).....

---

### Post by vigyani on 2007-05-11
Ubuntu works wonderfully for me. If there are some problems, I spend my time on solving them, not acting a victim. There is a wonderful Ubuntu community. Most of the problems have work around and solutions. The more I use it, more I love it. Just enjoy working on it.

---

### Post by louieb on 2007-05-11
> **ozp said:**
> ...Other linux distros are **striped down** versions of the comercial distro
I guess your referring to Fedora / Red Hat and Open Suse / Suse. Glad you pointed that out. I had alway thought that the **non commercial version** of those distributions are on the **bleeding edge** get the new stuff out, let whoever want use them and test them. Then when a new feature works reliably it is added to the commercial version of those products.      

Ubuntu  seems to have a stable version in Dapper 6.06.1. It doesn't have all the bell and whistles of Edgy,  Feisty, or what was it you said you were downloading the latest 32 bit beta?

---

### Post by ozp on 2007-05-13
I installed de beta and now it is the stable (updated) version

I have another box with 6.06 but the via driver does not install out of the box, and the video is too slow.

beside the stable / bleging edge side of the free and commercial version, there are also some features that are not included with the free version of those linux distros.

---

### Post by moogle on 2008-06-09
ozp I've skimmed the majority of this thread and am going to try my hardest not to incite some flamage. Basically what you are going through is what I've seen a majority of new linux users go through when switching from windows. They complain and flail about blaming this and blaming that, comparing this feature of windows that doesn't work the same way in linux. These tends of rants tend to get very annoying for the community over time, especially when heard over and over again 100's of times. Often the person doesn't realize that the community has heard some of the same complaints many many many times before. The answer boils down to this, Linux is not nor will ever be Windows, Mac what have you. It has no *INTENTION* of being this, therefore all efforts to compare it to another OS is meaningless. 

Secondly most problems new users experience are *SOLVABLE* , they're either known problems that are being addressed or problems that are fixable with a little reading or intelligent questions. 

Thirdly, people are busy and especially people on this forum, if you have a specific question or a genuine problem ask away, there is a respectful way to do this while providing information about the problem in the most efficient manner to solve it. Then there is spoonfeeding, going " X doesn't work" which is followed up by "What does "X.log say?" and back and forth and so on. No one likes dealing with someone who acts like a baby, refused to provide specific information in order to solve THEIR problem, and all the while bitches about how linux isn't mainstream enough or no adequate for their needs. This people are usually urged to go back to whatever OS makes them feel happy and safe, ie usually windows. Don't bitch about linux and then show an overaching concern about where the community is heading or that its only ready for "hackers and geeks" or "advancing the cause" it only dilutes what help you asking for and tangents discussions away from the actual help people were trying to provide. Please remember this lecture if you (or your trainee) decide to continue to participate in this support forum.

---

### Post by Spike-X on 2008-06-11
That's one hell of a grave dig there. This thread is a year old! How bored were you?

---

