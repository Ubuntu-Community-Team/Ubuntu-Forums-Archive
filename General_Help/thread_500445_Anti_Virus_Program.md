---
title: "Anti Virus Program"
date: 2007-07-13
forum: General Help
---

### Post by crazygun on 2007-07-13
Hey everyone,
     I am helping my sister with her new computer. I am having problems finding a Anti Virus, and Anti Spyware  program for this OS. If anyone knows any program made by AVG or Norton or any other company please replay to this. Thanks!

---

### Post by CautionaryX on 2007-07-13
AVG does have a free anti-virus for linux distributions if you wish to use it. The easiest way I've seen to update is to type "sudo avgupdate -o" into a terminal.

[free.grisoft.com]("http://free.grisoft.com")

---

### Post by rovernaut on 2007-07-13
Avast also have a linux program.

---

### Post by TheRingmaster on 2007-07-13
Linux doesn't really need antivirus unless this ubuntu computer is in on a network with a windows computer. Other than that it is not necessary.

---

### Post by nelamvr6 on 2007-07-13
> **TheRingmaster said:**
> Linux doesn't really need antivirus unless this ubuntu computer is in on a network with a windows computer. Other than that it is not necessary.

One of the big reasons Linux has enjoyed relative security is because it has presented a very small target.

Eventually a bunch of script kiddies are gonna notice a whole bunch of Linux users who believe they don't need a defense.

That's the way it happened in the Window$ world.  Believe it.

I'd rather have too much protection.

---

### Post by Seraed on 2007-07-18
I've been using Avast for the past 2 years, its great! Small footprint, and a great social responsible company. They understand that everyone should be protected if we really want to stop viruses and so they offer their Home version for free for personal and non-commercial use.

Within a week of having it installed it had cleaned up shop on my old Windows box and even alerted me when I ended up browsing a page that had a virus embedded in a jpg. :P

---

### Post by FSHero on 2007-07-18
Has anyone tried ClamAV? I ask this because it is free, GPL-licensed, so it might be in the Ubuntu repositories.

Avast sounds good; if you think they are socially responsible, then I might give it a try!

One question: since an anti-virus scanner can have pretty close access to system critical files, is it trustworthy to use a proprietary program? Or should we let proprietary anti-virus scanners 'off the hook'? :P

---

### Post by weblordpepe on 2007-07-18
> **FSHero said:**
> Or should we let proprietary anti-virus scanners 'off the hook'? :PNope.
Having a bunch of cowboy security tools with proprietary code loaded to use Ubuntu would kinda turn it into another Windows.

The concept of needing extra apps to make the OS safe is pretty hmm...well its a Windows concept that we've been largely free from. Eg software firewalls.

---

### Post by durkhrod chogori on 2007-07-18
> **TheRingmaster said:**
> Linux doesn't really need antivirus unless this ubuntu computer is in on a network with a windows computer. Other than that it is not necessary.

Are you 100% sure what you are saying is true? Because I heard Windows malware does not affect a Linux box. I need a final confirmation on this, please.

Cheers.

---

### Post by Crafty Kisses on 2007-07-18
> **crazygun said:**
> Hey everyone,
     I am helping my sister with her new computer. I am having problems finding a Anti Virus, and Anti Spyware  program for this OS. If anyone knows any program made by AVG or Norton or any other company please replay to this. Thanks!

You don't really need it.

---

### Post by Hallvor on 2007-07-18
> **durkhrod chogori said:**
> Are you 100% sure what you are saying is true? Because I heard Windows malware does not affect a Linux box. I need a final confirmation on this, please.

Cheers.

Windows viruses won`t run on linux; Windows spyware won`t run on linux. You only need a virus scanner if you share files with Windows computers - to protect them.

This does not mean you are invulnerable and that is is a good idea to browse russian cr@ck and p0rn site or installing a "cool" program found on google by Boris Hacker.  Common sense is still the best security.

---

### Post by az on 2007-07-18
> **durkhrod chogori said:**
> Are you 100% sure what you are saying is true? Because I heard Windows malware does not affect a Linux box. I need a final confirmation on this, please.

Cheers.

Windows malware does not affect linux in any way share or form.  Unless you are running a mail server, you do not need a windows anti-virus program.  Unless you are running a (web/email/files) server that is connected to the internet, you do not need a filrewall.

There is no need to a firewall or an anti-malware program on an Ubuntu desktop.  Period.

Installing a closed-source, proprietary application makes your computer more vulnerable - do not install these programs even if they are anti-virus software.

The only thing you need to do is keep up-to-date with security updates.  In windows, holes cannot be closed, so you have to scan for things that can exploit them.  In linux, the holes are closed when discovered.

> **nelamvr6 said:**
> One of the big reasons Linux has enjoyed relative security is because it has presented a very small target.

Eventually a bunch of script kiddies are gonna notice a whole bunch of Linux users who believe they don't need a defense.

That's the way it happened in the Window$ world.  Believe it.

I'd rather have too much protection.


Not so.  Linux is already as big a target as windows, considering its use in the server market.  Plus, the design of the software contributes to how vulnerable it is.

If you want to have more protection, be zealous about what kind of software you use and avoid anything that can make your computer do things behind your back.

---

### Post by weblordpepe on 2007-07-18
Which is why open-source is safer than closed-source. There's no hidden code.
Anyway - with the latest news about Microsoft patenting advertising engines etc - it looks like the spyware will be coming from Microsoft in the future.

EDIT: Yes windows malware can affect a linux machine if you have Wine installed.
Its obvious - Wine is not a sandbox. Windows applications have access to the directory structure and if a windows program has the ability to figure out that its inside wine, then it can attempt an exploit. Wine is an abstraction layer that allows Windows applications to run in Linux. It's not a magic sandbox which blocks all nasty stuff.

---

### Post by darell_m on 2007-07-18
Being an old Xp user with all programs (zonealarm, avg virus and malware, ccleaner, defrag 8.0 or whatever YIKES). After getting  used to Ubuntu and reading all the forums about "DO YOU NEED THIS IN UBUNTU" I was still a bit paronoid. So, with great difficulty(finally getting to "little" noob level,and can do basics on terminal) . got Clam and AVSscan working (not easy as if you insist search forum) and Firestarter.  (gui sucks but works)

My comment is  WAS  GOOD EXERCISE TO GET EXPERIENCE OF DOWNLOADING - **now I will get rid of them** as, in my opinion are not required. Firestarter gives false positives and Avscan only found dll's when I scanned windows directory.(these are windows programs that do not affect anything - I guess - I still have dual boot with all the bells and whistles)

If you are worried about firewalls hack into your own system using grc at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Until the Unbutu (linux folks) tell me to beware ( And reading forums will tell you any crack will be reported immediately - OPEN FORUM - nothing can hide). I am  confident not to have any antivirus or firewall (other than my router hardware) in place.

Anyway  - my opinion,
 from a struggling noob

:-({|=

---

### Post by weblordpepe on 2007-07-18
Debian / Ubuntu have the repositories system. 
This allows almost all software to be pre-authenticated as safe. I think you'll be safe as long as you keep an eye on which repositories you use.

However, Linux...for all its good points - still runs software created by professionals OR noobs. This means that there can be exploits found in the future for all internet facing programs.
Eg scripting exploits in firefox.

People are half right when they say linux doesnt get a hard time because its not as popular as windows. But these people really need to factor in that Linux is not just an other Windows. There are huge fundamental differences in the computing model.

---

### Post by cookies on 2007-07-18
> **weblordpepe said:**
> Which is why open-source is safer than closed-source. There's no hidden code.
Anyway - with the latest news about Microsoft patenting advertising engines etc - it looks like the spyware will be coming from Microsoft in the future.

EDIT: Yes windows malware can affect a linux machine if you have Wine installed.
Its obvious - Wine is not a sandbox. Windows applications have access to the directory structure and if a windows program has the ability to figure out that its inside wine, then it can attempt an exploit. Wine is an abstraction layer that allows Windows applications to run in Linux. It's not a magic sandbox which blocks all nasty stuff.

But Wine only makes changes to /home/USERNAME/.wine

That really can't break you system....



Now, you don't really NEED an anti-virus program, though it's not really a big deal if you do decide to get one.

---

### Post by ddrichardson on 2007-07-18
I've never used ClamAV under Linux, but under Windows it returns false positives quite frequently. Also keep a copy on a USB disk and have used it at work - where it failed to pick up an older quite common virus.

I agree with nelamvr6 - complacency helped the spread of viruses under Windows, but if the truth be told the vast majority of viruses are installed through a combination of user stupidity and Windows 95/98/XP Home's instistance on a standard user having administrator privileges Fortunately Linux doesn't, limiting the impact of any malicious soft ware.

---

### Post by stchman on 2007-07-18
> **nelamvr6 said:**
> One of the big reasons Linux has enjoyed relative security is because it has presented a very small target.

Eventually a bunch of script kiddies are gonna notice a whole bunch of Linux users who believe they don't need a defense.

That's the way it happened in the Window$ world.  Believe it.

I'd rather have too much protection.

Viruses for Linux are tough as a file needs to have executable permissions to do anything.  Now if the Linux user downloads a strange file from an unknown person, gives it executable permissions and then sudo executes it then YES the virus will be able to do its bidding.

Also the virus would have to attack a certain distro.  Remember there are many distros out there and all have different weaknesses.  All Windows XP installs are the  same and have the same weakness.  Diversity is a big defense for Linux.

It has been my experience that Linux users in general are very knowledgeable and don't have bad online habits.  Not to mention that 99+% of all viruses are written for Windows.

---

### Post by az on 2007-07-18
> **darell_m said:**
> 
If you are worried about firewalls hack into your own system using grc at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)


Shields up is a joke.  It simultaneously breeds a false sense of insecurity and security. "Stealth" is a joke.  If you are "stealthed", how do you think they know who to portscan?

> **weblordpepe said:**
> 
However, Linux...for all its good points - still runs software created by professionals OR noobs. This means that there can be exploits found in the future for all internet facing programs.
Eg scripting exploits in firefox.


All software has bugs.  The open source model is that of many eyeballs looking at the code, finding and fixing bugs.  I don't think you can say that free-libre open source software is less secure because some developers are not professional software engineers.

---

### Post by strabes on 2007-07-18
You don't need to install a firewall frontend (e.g. firestarter) unless you need to configure/open ports because all non-necessary ports are closed on a default ubuntu install anyway.

Because of how linux is built, even if a virus targeted at linux were to infect your computer, the damage that could be done is minimal because in order to make any system changes it needs root access which only comes with a password. I guess the worst a "linux virus" could do is mess with your home directory which is not a problem if you make daily/weekly/random backups.

---

### Post by weblordpepe on 2007-07-19
> **az said:**
> 


All software has bugs.  The open source model is that of many eyeballs looking at the code, finding and fixing bugs.  I don't think you can say that free-libre open source software is less secure because some developers are not professional software engineers. I didn't mean to imply that open source is less secure because the programmers don't wear ties.

I meant that Linux is a platform like anything else in which anyone can write software for it. That means that there are noobs and pros writing software. So there is still a chance for internet facing programs to be exploited.


Anyway as for wine. Yes affecting the home folder is enough to be dangerous. Thats where all the users files are!
Just thinking of something off the top of my head - a windows virus in wine could scan the directory tree for references to files executed on startup. if it has write permissions to any of them, it could change them.

Im sure at least somebody has a .sh in their home folder rigged to their session start-up.

---

### Post by FSHero on 2007-07-19
Thanks all for the responses.

I have assessed your advice, and will take it on board.

Basically, as long as you don't **allow** anything unscrupulous to run, or as long as you don't do anything "stupid", you're safe.

I shall continue to use Ubuntu with peace of mind!

---

### Post by misfitpierce on 2007-07-19
Anti Virus is not really needed unless you want to make sure you do not act as a host for windows viruses and pass them windows pc's (fun? lol) and there is no antispyware or antiadware for linux either b/c it is def not needed.

---

### Post by cssutto on 2007-07-19
AZ posted:
Shields up is a joke. It simultaneously breeds a false sense of insecurity and security. "Stealth" is a joke. If you are "stealthed", how do you think they know who to portscan?

Is it not correct that when a computer connects with another, its address is identified at that time, whether a correct address or a spoofed.

What is wrong with having Firestarter loaded, whether it is doing anything for security or not?  It does not seem to have appreciable overhead.

I use it as a quick reference to see how good my connection is at any given time.

---

### Post by az on 2007-07-19
> **cssutto said:**
> AZ posted:
Shields up is a joke. It simultaneously breeds a false sense of insecurity and security. "Stealth" is a joke. If you are "stealthed", how do you think they know who to portscan?

Is it not correct that when a computer connects with another, its address is identified at that time, whether a correct address or a spoofed.

What is wrong with having Firestarter loaded, whether it is doing anything for security or not?  It does not seem to have appreciable overhead.


What's relevant is that people think that "stealthed" means invisible when that is clearly not the case.  Installing firestarter is mostly harmless.  Sure it does not slow down your copmuter or take up a lot of ram, But it will make complicate your life if you actually want to run things that talk to the network.  As well, it will offer you a false sense of security.

---

### Post by DalekClock on 2007-07-19
> **FSHero said:**
> Has anyone tried ClamAV?

Yup, and it was the only time Ubuntu crashed.

---

### Post by stchman on 2007-07-19
> **az said:**
> Shields up is a joke.  It simultaneously breeds a false sense of insecurity and security. "Stealth" is a joke.  If you are "stealthed", how do you think they know who to portscan?



All software has bugs.  The open source model is that of many eyeballs looking at the code, finding and fixing bugs.  I don't think you can say that free-libre open source software is less secure because some developers are not professional software engineers.

All shields up does is try to probe ports at a certain IP address.

---

### Post by cmat on 2007-07-19
You don't *need* a virus scanner. One of the biggest misconceptions is that the reason Linux doesn't have any true viruses out in the wild is because most viruses are written for Windows. On the most part this is true, however if more people wrote viruses for linux we would still be relatively safer than Windows. Linux is safe by design, unlike Windows. However doing dumb things like giving suspicious programs executable permissions allowing it read and write access is just silly and defeats the purpose of all the security features in place. Also it would be quite an achievement for someone to write a true linux virus and the motivation to do so would be there, so why haven't I really heard of any.

However everyone no matter what OS needs to worry about browser exploits.

You really need a virus scanner if you are sharing a network with Windows computers or running things under WINE. So you don't unintentionally spread a virus without even knowing it to friends using Windows at school or at work.

---

### Post by az on 2007-07-19
> **stchman said:**
> All shields up does is try to probe ports at a certain IP address.

Right.  And if everything is green and written "stealthed", you are given the impression that you are invisible and that no one knows you are there.  But when you think of it, how did GRC know what ip address to portscan?

Whenever you browse a website, it knows your IP address (how else can it send you packets containing the web page you just asked for?).  The only way to be invisible is to pull the network cable out of your computer.

---

### Post by cssutto on 2007-07-19
The biggest mystery about computers to me is how the internet works and how communications between machaines works.  I just can not get it and I have had computers for over 20 years.

But with that caveat to cover my butt for saying something stupid, it has been my understanding that all stealth means is that random pings do not find you.  Certainly anyone who already has your address can ping you but I understood that stealth means that anyone looking for an open machine with random pinging would not see you.

As I said, I do not understand the internet and never will, so perhaps this belief is a result of that ignorance.


If we do not wish to lose our freedom, we must learn to tolerate our
neighbor's right to freedom even though he might express that freedom
in a manner we consider to be eccentric.

---

### Post by weblordpepe on 2007-07-19
I said it before and I'll stay it again:

Desktop firewalls are a Windows thing, and not a generic computer thing.

Think about it. Really. For two seconds. What on earth is a software firewall going to do when it is running on top of the system its trying to protect? Software firewalls are a rediculus concept by design. On any OS.

Vista coming with a 'bundled firewall' is a prime example of exploiting people's perceptions that you need OS + firewall. And that firewall can run on the OS.

In REALITY all you are doing is changing system policies. This is not firewalling. A real firewall is a seperate device (either hardware or software based), which does not depend on the systems it protects in any way.

Take it from me - if you're on Windows and are hiding warez movies showing george w  bush transforming into his true alien form, throw out the software firewalls on Windows and look into upgrading your DSL router.

---

### Post by stchman on 2007-07-20
> **az said:**
> Right.  And if everything is green and written "stealthed", you are given the impression that you are invisible and that no one knows you are there.  But when you think of it, how did GRC know what ip address to portscan?

Whenever you browse a website, it knows your IP address (how else can it send you packets containing the web page you just asked for?).  The only way to be invisible is to pull the network cable out of your computer.

Website traffic is routed through port 80.

I believe the Shields up site is to let you know if someone is doing a methodical IP address scanning then your ports don't respond.

---

### Post by machspeed_ on 2007-07-24
I'm new to Linux, and thought reading this post on antivirus sounded like a good idea, it was just something that i wasn't sure about after running windows since i was a kid.  I just wanted to add my two cents in about firewalls. 

I've got a Linksys WRT54G wireless router, an $80 piece of equipment very common. it's an excellent firewall, in that it won't allow incoming traffic that wasn't initiated from inside its internal network (unless otherwise forwarded, of course), again, it kinda goes back to an earlier post that said common sense is the best form of antivirus. third-party programs i think are worthless, and end up being way more intrusive than it really needs to be. 

what i wish more people understood is that if you are behind a router, software like that simply isn't necessary to protect against outside attacks. virus protection, however, is a different story, but it seems while running Linux, it isn't of much concern.

I gotta say, I'm impressed with how Ubuntu works on my machine. It's prettier than vista, and sits idle using only 250mb RAM, compared to vista bare, no eye candy at over 450mb. I'm finding it pretty easy to make the switch.

-jas.

---

### Post by weblordpepe on 2007-07-26
250mb? Im sure you can get it lower than that :)

---

### Post by lisati on 2007-07-26
> **weblordpepe said:**
> Nope.
Having a bunch of cowboy security tools with proprietary code loaded to use Ubuntu would kinda turn it into another Windows.

The concept of needing extra apps to make the OS safe is pretty hmm...well its a Windows concept that we've been largely free from. Eg software firewalls.

Hmmmm.... no need for firewalls? Try a search on these forums for topics like "I've been hacked".  **It happens.

---

### Post by weblordpepe on 2007-07-26
> **lisati said:**
> Hmmmm.... no need for firewalls? Try a search on these forums for topics like "I've been hacked".  **It happens.I never disputed that.
I simply point out that the desktop software firewall model is a windows thing. Consequently its not a very good one.

---

### Post by lisati on 2007-07-26
> **weblordpepe said:**
> I never disputed that.
I simply point out that the desktop software firewall model is a windows thing. Consequently its not a very good one.
OK point conceded......my personal preference, now that I have the gear, is to use the features built into routers & modems as a first line of defense.

---

### Post by cssutto on 2007-07-28
How do you use a router if you are a road warrior lap top user?

CSSJR

---

### Post by stinger30au on 2007-07-28
> **nelamvr6 said:**
> One of the big reasons Linux has enjoyed relative security is because it has presented a very small target.

Eventually a bunch of script kiddies are gonna notice a whole bunch of Linux users who believe they don't need a defense.

That's the way it happened in the Window$ world.  Believe it.

I'd rather have too much protection.

Yes but your forgetting that Windows gives everything a ADMINISTRATOR right... in linux you need to do a sudo.
Windows has tons of security flaws that often take weeks or months to fix.
Linux is open source. this means anyone can and does read the source code. if there is a security breach that anyone fan find in the code it gets fixed with in days.

Remember, Windows and Linux are worlds appart.

May i suggest you pickup a few linux books in pdf ro chm format off the net and do some reading, theres a lot to be learnt when stepping from windows to Linux

---

### Post by stinger30au on 2007-07-28
> **lisati said:**
> Hmmmm.... no need for firewalls? Try a search on these forums for topics like "I've been hacked".  **It happens.

i have read some of those posts. most of them were people playing tricks on each other.

if you want a firewall, install firestarter. you can do it form the cli

---

### Post by weblordpepe on 2007-07-29
> **stinger30au said:**
> i have read some of those posts. most of them were people playing tricks on each other.

if you want a firewall, install firestarter. you can do it form the cliIf you want a firewall, you gotta take a long hard look at your security model. If you're going to have a firewall of any kind, make it a device other than the device you are protecting.

Desktop firewall = just software running on top of the device you need to protect. 

Linux kernel = good enough to be a firewall itself. Thats why most DSL routers etc are running Linux in the first bloody place.

---

