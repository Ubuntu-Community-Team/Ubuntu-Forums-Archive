---
title: "Is Grub bad for Ubuntu?"
date: 2007-03-12
forum: General Help
---

### Post by dannyboy79 on 2007-03-12
I have been in a discussion with another user about grub being poorly implimented into Ubuntu and the fact that Grub is holding Ubuntu back from being a good Linux Desktop. They stated that grub is 1 of the most commonly scene problem in the forums. I have tried to inform him that once Grub is **learned** and **fully understood** it is a very versatile boot loader. What do you think, is grub a good boot loader or do you think grub stinks?

---

### Post by buuntuu! on 2007-03-12
no idea what's so bad about grub!
did several installs and never encountered any serious trouble.
editing the menu.lst isn't THAT difficult, is it??

---

### Post by dannyboy79 on 2007-03-12
well when people start trying to use the "map" option, try to load windows from a non-primary partition, try to have more than 1 windows install on the same disk (have to use the "hide" option) grub starts to get a little more difficult but the thing that people don't do, is actually read and learn about what they are trying to do. They simply come here, post their question with none-sufficient details and say, "I can't get it to work, grub stinks." or they say, "I was told to do this and it didn't work, grub stinks". It all boils down to understanding how boot loaders work and people always want a fast solution, that's the american way, get it done now and get it done right but they lack the patience to learn how to do it and just want someone to tell them how to do it. PS I am an American.

---

### Post by markitect on 2007-03-12
Well my first though is, what do you want, lilo?
I think grub is fantastic, it does everything and while a good portion of the problems are with grub they are usually caused by someone installing something on top of Ubuntu and are usually well documented grub problems you can find on the grub faq. 

That said as a more meaningful discussion, maybe a gnome grubfix program would be useful.  Something for system utilites that would be mainly run off a live disk.  have buttons to fix the MBR, find where grub is, and something that finds kernels and makes entries with ubuntu defaults.

Anyone know if there is a good program out there we might pull in?

---

### Post by mbeierl on 2007-03-12
Another feature that I'd love to see around a boot loader would be an easy method for selecting which os/kernel to use on next boot.  Yes, grub supports it, but telling a newbie how to use it is far from easy.  gfxboot is nice eye-candy, so that would be a nice to have too.

But given the alternatives, I think grub is currently one of the best.

---

### Post by ComputerGuy56 on 2007-03-12
Stick with GRUB. It does what it has to do with no problems. I got five option and Grub handles them great!:)

---

### Post by dannyboy79 on 2007-03-12
> **markitect said:**
> Well my first though is, what do you want, lilo?
I think grub is fantastic, it does everything and while a good portion of the problems are with grub they are usually caused by someone installing something on top of Ubuntu and are usually well documented grub problems you can find on the grub faq. 

That said as a more meaningful discussion, maybe a gnome grubfix program would be useful.  Something for system utilites that would be mainly run off a live disk.  have buttons to fix the MBR, find where grub is, and something that finds kernels and makes entries with ubuntu defaults.

Anyone know if there is a good program out there we might pull in?


the super grub disk can do all that but I don't know how you'd install "it" into ubuntu lve cd.

---

### Post by confused57 on 2007-03-12
In my opinion, grub is a pretty decent bootloader...with all the time & effort Herman has put into his website, going into detail  describing how various bootloaders & utilities(e.g. Super Grub Disk) function, a one-stop resource is there with all the info one should need...detailed & comprehensive, but written in such a way that it's easy to understand, almost like he's explaining it in person...beginners(or anyone) may have to read it several times, if they just want to know how grub works or troubleshoot grub & booting problems.  He also provides a plethora of links, if  one wants to delve further for more info.  I could go on and on, but you get the point.  I realize beginners have to be pointed in the right direction and people go out of their way to assist new users with their booting problems...many just want their system to boot, others want to know how grub actually works & how to configure it.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

Now that I'm beginning to get the hang of how grub works, I've read Feisty is implementing grub2...Herman's probably already on it.

Added:  Herman has written an excellent guide, with screenshots, for how to use("describing how various utilities..Super Grub Disk..function") the Super Grub Disk...as someone mentioned later it was developed by adrian15.  The GAG "howto" is excellent, also.

---

### Post by dannyboy79 on 2007-03-12
I can't believe that there have been 93 views on this thread but only 13 voted!! Why does this happen???? What's the point of reading a Poll but not picking an answer, can 1 of you that read the poll but not picked an answer please answer this simple question? I am not trying to be rude either, I am very curious as maybe we can somehow make picking an answer easier so that more people participate in the poll.

---

### Post by keithweddell on 2007-03-12
I read the thread to be informed.  But I just don't have any strong feelings on the subject.  Sorry.

Keith

---

### Post by dannyboy79 on 2007-03-12
well i wish I could change it now to at least add an option that was, "no opinion". that way the poll would at least reflect the amount of people that have viewed it.

---

### Post by ghandi69_ on 2007-03-12
I'll be honest.. I do not know how grub works or what it does... I just know that one time grub got installed on one of my hard drives and linux on the other.. and I was confused as *(&#$.  Now... I usually avoid.. back when I still had windows.. I had windows on one hard drive and linux on the other.... and I would usually select my boot menu from my bios and just select either or.  I think the bios is the best way to boot where you want to go.

---

### Post by aysiu on 2007-03-12
> **dannyboy79 said:**
> I can't believe that there have been 93 views on this thread but only 13 voted!! Why does this happen???? Speaking as someone has read the poll and not selected an option, I'd say your options are rather limiting: > **Is grub wrong for Ubuntu?**
Yes, way to hard to learn but still use it
No, once you properly learn it, its great
Yes, I want a different boot loader
 My answer is *No, it's perfectly fine, and you don't need to learn it properly*

I don't understand what this business is about learning Grub. On the Desktop CD, it automatically installs Grub to the MBR and adds Windows to the boot menu if you have a Windows partition. What's there to learn? You can learn more about it if you want to install Grub to somewhere other than the MBR (using the Alternate CD), but you don't have to.

I'd venture to say most polls that have very few answers have to do with limiting poll options skewed in favor of the OP's idea. For example, if you have a poll that says, "What do you think about Kubuntu?" there should be more than just the following options: "It's great. It's the best. There's nothing wrong with it."
"It stinks. It's the worst distribution on the planet."
"I have no opinion about this."

Most people who would answer such a poll probably think Kubuntu is good but not the best, and they would not be able to honestly select one of the given options. Same thing for your poll. A lot of people probably think Grub is just fine but don't agree with the second option.

---

### Post by mixium on 2007-03-12
This is a silly question (no offense) because GRUB is Ubuntu's bootloader. If Ubuntu used LILO by default then your question would be "Is LILO bad for Ubuntu?". The reason so many people have problems is because so many people use it. You could also ask "Why do so many PC users have viruses?" finding the answer in that fact that many run Windows. The answer is in the numbers. What you need to look at is the percentage of Ubuntu users (All users and not just those in the forums) that have had a difficult time with GRUB. I am willing to bet that number is relatively low.

Most users never have to fool around with their bootloader very often. If they do, it's rarely so. If people tinkered with their bootloader everyday they would get good at it.

I have used both GRUB and LILO over the years. I find GRUB to be much better for a number of reasons. One nice feature is not having to remember to run "lilo" after installing a new kernel. I can't tell you how many new Linux users have done complete reinstalls because they forgot to inform LILO about the new kernel and found themselves completely lost on how to fix such a trivial thing.

Stick with GRUB!

:)

Michael

---

### Post by patrickfromspain on 2007-03-12
the only problem grub has is that it's very ugly... Have you ever seen Xandros' lilo menu? That' would be nice!

[IMG]http://fuxard.free.fr/Sans%20titre%2020.jpg[/IMG]

---

### Post by dannyboy79 on 2007-03-12
well obviously you have only dealt with 1 situation of using grub and that's all so I can see why you'd say this. There are literaly a dozen or more different situations that I have helped people thru which required them to either reinstall grub and or me tell them exactly what to do or for them to "learn" to use grub properly and figure it out for themselves. I will list a few of the situations for your reference but I am not going to put the solutions as that would take forever BUT it would be a great idea to have all the different possible scenarios and solutions in 1 place. (i just don't have the time right now. im at work he he he.)

1. Someone has windows already installed on a hard drive, they want to dual boot with 2 hard drives but not have to worry about screwing up windows so they remove the windows drive and install ubuntu and put grub in the mbr of the ubuntu drive, then they re-insert the windows drive and wonder why windows keep booting right up without giving them an option to pick ubuntu.
2. Someone has windows already installed and they want to add ubuntu and vista all on the same hard drive. (this would involve using the "hide" option in grub so that 1 windows install wouldn't see the other windows install's partition)
3. Someone has ubuntu installed and want to install winxp onto a second hard drive and have grub boot it (This would involve using the "map" option, this is necessary when you chain-load some operating systems, such as DOS, if such an OS resides at a non-first drive.) I see people doing this all the time just because it worked for someone else yet they don't even know why they added it. 
map (hd0) (hd1) 
map (hd1) (hd0)

4. Someone wants to move their ubuntu install from an eide hard drive onto a sata hard drive. They used hdclone to copy hard drive to hard drive but that's not enough, you have to manually edit fstab, device.map, and menu.lst OR reinstall grub from scratch.

These are just the weirdest situations I have helped in, a lot of times I just have to tell them how to reinstall grub using the live cd because windows overwrote their mbr. So just because you think it's simple is because you probably understand how it works and it appears as though you've dealt with the simplest of the varying grub situations. That's why I posted this thread/poll, to find out what people think.

---

### Post by dannyboy79 on 2007-03-12
> **mixium said:**
> This is a silly question (no offense) because GRUB is Ubuntu's bootloader. If Ubuntu used LILO by default then your question would be "Is LILO bad for Ubuntu?". The reason so many people have problems is because so many people use it. You could also ask "Why do so many PC users have viruses?" finding the answer in that fact that many run Windows. The answer is in the numbers. What you need to look at is the percentage of Ubuntu users (All users and not just those in the forums) that have had a difficult time with GRUB. I am willing to bet that number is relatively low.

Most users never have to fool around with their bootloader very often. If they do, it's rarely so. If people tinkered with their bootloader everyday they would get good at it.

I have used both GRUB and LILO over the years. I find GRUB to be much better for a number of reasons. One nice feature is not having to remember to run "lilo" after installing a new kernel. I can't tell you how many new Linux users have done complete reinstalls because they forgot to inform LILO about the new kernel and found themselves completely lost on how to fix such a trivial thing.

Stick with GRUB!

:)

Michael
Thank you for your input. Your comment, "I am willing to bet that number is relatively low." this is exactly what I am trying to find out! So yes, I do need the poll because it will tell me if people are having a tough time with grub or not. This is what polls are for.

---

### Post by dannyboy79 on 2007-03-12
[QUOTE=patrickfromspain;2287437]the only problem grub has is that it's very ugly... Have you ever seen Xandros' lilo menu? That' would be nice!

you can have a splash screen with grub, give it a try: [http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.0](http://ruslug.rutgers.edu/~mcgrof/grub-images/#1.0)

OR

[http://www.sonic-world.com/blog/?p=28](http://www.sonic-world.com/blog/?p=28)

or 

[http://www.ubuntuforums.org/showthread.php?t=200852&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=200852&highlight=grub)

---

### Post by aysiu on 2007-03-12
Yes, I recognize there are situations in which Grub can get complicated (the ones you listed.

However, it's not the problem of Grub if reinstalling Windows overwrites the boot loader.

It won't matter if you use Grub, Lilo, or something else. If Windows wants to take over, it'll take over.

---

### Post by dannyboy79 on 2007-03-12
> **aysiu said:**
> Yes, I recognize there are situations in which Grub can get complicated (the ones you listed.

However, it's not the problem of Grub if reinstalling Windows overwrites the boot loader.

It won't matter if you use Grub, Lilo, or something else. If Windows wants to take over, it'll take over.

ok, so what do you want here. do you want to be crowned the winner? do you want a cookie? what is your point with your negativity and you making statements which don't relate to the Poll? The poll asks a simple question, if you don't want to participate in it than that's your proagative.
I never stated that it's grub's fault that the mbr gets overwritten when you install windows after ubuntu. I stated that this is a common issue and that the user normally still wants to use grub and people don't know how to accomplish this so they should LEARN GRUB, which goes back to my main statement.
Thank you for your comments regarding grub, you made a vague statement that a user doesn't need to learn grub, I pointed out several reasons why they do need to, end of discussion, I am not going to have a p___ing match with you.

---

### Post by dannyboy79 on 2007-03-12
> **aysiu said:**
> Most people who would answer such a poll probably think Kubuntu is good but not the best, and they would not be able to honestly select one of the given options. Same thing for your poll. A lot of people probably think Grub is just fine but don't agree with the second option.

I agree with you, this is the exact reason I wish Poll's could be edited after they are started. When I created the poll I thought I had the applicable options in the poll, now I see that I left some valuable options out. This doesn't prevent you from making a post about your opinions of grub which will also be viewed and not just the poll numbers itself. If you read the first post, this Poll is created to find out if grub creates too many issues for people or does the average person use it with ease. I now see that I should have added some more options for including options about the trouble with grub and dual booting situations.

---

### Post by aysiu on 2007-03-12
You asked a question I tried to answer. Apparently, you didn't like my answer. If you don't want me to participate in the thread, I won't.

---

### Post by Bigbluecat on 2007-03-12
Grub is fine once you get a little understanding about how it works. And I'm not aware of anything better out there. It is very flexible.

Most problems occur in dual boot systems when Windows overwrites the MBR or the disk configurations are changed.

I looked at modifying the windows bootloader for dual boot and it was horrible.

Incidentally just add to an earlier post regarding Herman's illustrated dual boot site - it is an extremely valuable resource.

Super Grub Disk was developed by Adrian15 (not Herman).

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

With these two resources you can solve and boot pretty much anything.

---

### Post by dannyboy79 on 2007-03-12
> **aysiu said:**
> You asked a question I tried to answer. Apparently, you didn't like my answer. If you don't want me to participate in the thread, I won't.

aysiu, I do want you to participate. I apologize for my bluntness. I took offense to your statement "I don't understand what this business is about learning Grub". You were basically minimizing everyones hours upon hours they have spent trying to learn grub and I didn't appreciate that. I have spent may hours helping others with grub and it's not easy.

---

### Post by taurus on 2007-03-12
> **dannyboy79 said:**
> ok, so what do you want here. do you want to be crowned the winner? do you want a cookie? what is your point with your negativity and you making statements which don't relate to the Poll? The poll asks a simple question, if you don't want to participate in it than that's your proagative.
I never stated that it's grub's fault that the mbr gets overwritten when you install windows after ubuntu. I stated that this is a common issue and that the user normally still wants to use grub and people don't know how to accomplish this so they should LEARN GRUB, which goes back to my main statement.
Thank you for your comments regarding grub, you made a vague statement that a user doesn't need to learn grub, I pointed out several reasons why they do need to, end of discussion, I am not going to have a p___ing match with you.

Would you just relax for a minute?  If you can't have a civilize discussions, then I have no choice but to lock it so nobody can argue with anybody else.

---

### Post by dannyboy79 on 2007-03-12
> **Bigbluecat said:**
> Grub is fine once you get a little understanding about how it works. And I'm not aware of anything better out there. It is very flexible.

Most problems occur in dual boot systems when Windows overwrites the MBR or the disk configurations are changed.

I looked at modifying the windows bootloader for dual boot and it was horrible.

Incidentally just add to an earlier post regarding Herman's illustrated dual boot site - it is an extremely valuable resource.

Super Grub Disk was developed by Adrian15 (not Herman).

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

With these two resources you can solve and boot pretty much anything.

Thank you for your comments, I feel the same way.

---

### Post by klytu on 2007-03-12
> **dannyboy79 said:**
> I have been in a discussion with another user about grub being poorly implimented into Ubuntu and the fact that Grub is holding Ubuntu back from being a good Linux Desktop. They stated that grub is 1 of the most commonly scene problem in the forums. I have tried to inform him that once Grub is **learned** and **fully understood** it is a very versatile boot loader. What do you think, is grub a good boot loader or do you think grub stinks?

I think GRUB is a terrific boot loader. I voted for choice B.  I would add that in my experience many of the same people who don't take the time to learn how to use GRUB don't really understand why a boot loader is needed in the first place or what is going on when a computer boots up.

---

### Post by dannyboy79 on 2007-03-12
> **taurus said:**
> Would you just relax for a minute?  If you can't have a civilize discussions, then I have no choice but to lock it so nobody can argue with anybody else.

i don't understand why this has to happen, we're all adults and there is no reason for myself to receive an infraction. I want this thread to go on so I can see what the census is on whether grub is "holding" ubunut back from being a good desktop. so taurus, can you point out anywhere in here that I insulted anyone???? cause I can't! and apparently complexnumber thinks I did because I am sure aysui told him to give me an infraction or he did it out of spite. I was in an altercation with complexnumber were he tried to tell me what I could or couldn't do, then he didn't even own up and apologize, you had to apologize for him.

---

### Post by fsando on 2007-03-12
> **taurus said:**
> Would you just relax for a minute?  If you can't have a civilize discussions, then I have no choice but to lock it so nobody can argue with anybody else.
Thanks ;) It seems a little heated in here.

On topic:
I have read through the thread and I haven't voted because I have no opinion. Grub is the only bootloader I know. I have tried a little to make the splash screen following some guide but it didn't work. 
I'm thankful for this
> **confused57 said:**
> [http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)Though I havn't looked at it I expect it to worth some studying.
If I can't vote at least this thread is an inspiration to learn more about Grub.

---

### Post by confused57 on 2007-03-12
I think we should just let the poll results & comments speak for themselves...I'd be interested in what other's opinions & experiences are using grub.

---

### Post by Mateo on 2007-03-12
Grub is fine once it's all set up.  The problem is that it doesn't always automatically detect your settings.  So you **have to** learn how to use it.  And users shouldn't have to do that.

---

### Post by paparucino on 2007-03-12
> **dannyboy79 said:**
> I can't believe that there have been 93 views on this thread but only 13 voted!! Why does this happen???? 
I read the posts but I didn't noticed the poll till I read your post. 
Well... I use grub with the default parameters since I have no particular requirements for my system: it has to start. Point.
So my opinion is not relevant and I thenk a lot of other users are in my situation and this explain why there are a lot of readers and so few votes.

---

### Post by markitect on 2007-03-12
Wow this got out of control since this morning.  I think most people will agree that when grub is working its a fine bootloader, and i bet there are some people that don't even know what it is, but use it every day. 

That said: What common problems are there and what would improve them.  So far In my opinion the best idea is to integrate supergrub disk into the live/install CD.  To make fixing the most common problems easier, like windows killed grub problems that pop up a lot.

---

### Post by Dylnuge on 2007-03-12
No matter what you do, problems will occur with any bootloader.

You mention mapping to get Windows to work if on a second hard drive. This is outside of grub. This involves Windows (so does formatting the MBR).

No matter what bootloader you use, you need to reinstall it if you install Windows second, and map if you use a second hard drive for Windows.

Other bootloaders are not eaiser-they just have a GUI. Try Start-Up Manager, a great GUI for GRUB. (Truely awesome-Manages your Kernel list so there is only 1 Kernel Option and 1 Recovery Option, helps you set a password for your recovery option (recommended, since it boots as root without a password).

I aggree with aysiu on this.

---

### Post by Mateo on 2007-03-12
> **Dylnuge said:**
> No matter what you do, problems will occur with any bootloader.

Really?  I've never had a single problem with MBR.  Have with grub though.  Those are the only 2 bootloaders i've ever used.

---

### Post by markitect on 2007-03-12
> **Mateo said:**
> Really?  I've never had a single problem with MBR.  Have with grub though.  Those are the only 2 bootloaders i've ever used.

A quick clarification: MBR or master boot record is the spot on the hard drive where the bootloader resides.  

That said I popped open the super grub disk, if you go into its top directory with files you find a menu.lst that has titles that simply load in other menu.lst files depending on what you want to do.  So we could easily add an enty to the live/install CDs that calls this menu.lst or a similar one, and provide a similar directory tree on the live CD at a cost of 8.6M and then anyone who has installed ubuntu has a handy way to fix grub.


We're past the feature freeze for fiesty, but this should have absolutely no impact on anything else and be a quick addition, if people think its a good idea, get it thrown in by the 15th's freeze

---

### Post by dannyboy79 on 2007-03-12
> **Dylnuge said:**
>  No matter what you do, problems will occur with any bootloader. 
Well this is such a gross generalization that it really can't be said wihout some clarification or reasoning. This is just not true. Grub works without any problems for normal installs, heck even if you leave your hard drive that contains windows in your computer when you install ubuntu, grub will add that into your menu.lst automatically. It's only when special situations arise that grub needs to be understood and updated manually but there's no problem with grub, it's only because of what the user did to cause this.

> **Dylnuge said:**
> You mention mapping to get Windows to work if on a second hard drive. This is outside of grub. This involves Windows (so does formatting the MBR). 

myself and others would appreciate it if you didn't provide information that isn't true. when trying to boot various os's from a non-first hard drive (ie your second hard drive that the bios is not booting) you need to use the "map" option within GRUB, this has nothing to do with anything in windows. Also, you don't need windows to "format" your mbr either!! you can use dd if=/dev/zero of=/dev/sda count=1 bs=512 if you want to (/dev/sda can be whatever hard drive you want to create a new mbr for). u only need to use windows if you want to restore the default windows boot loader, you would use fixmbr, which doesn't merely format your mbr, the fixmbr command used from the recovery console resets the Windows bootloader to its Microsoft-default settings.

you can agree with aysui, that is the point of the poll, to find out what others think but it would be wise to know what you are talking about, that way you can make an informed decision not just based on what others say.

---

### Post by vsandz on 2007-04-12
Ok so i'm a complete newbie to linux or for that matter multiple OSses and the first time I tried to install Ubuntu I messed up the CD writing (at 1x somehow ...) ... anyhow ... I ended up with an Ubuntu CD that had installed but not completely and GRUB would not load up and offer me to boot to Windoze so I could write another proper .iso of Ubuntu. 

I was completely clueless and had to use a friend's comp to burn Ubuntu and then just pray that during the reinstall GRUB would somehow autodetect and "fix" itself.

---

