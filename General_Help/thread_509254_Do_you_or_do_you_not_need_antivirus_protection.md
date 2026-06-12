---
title: "Do you or do you not need antivirus protection?"
date: 2007-07-25
forum: General Help
---

### Post by bone2006 on 2007-07-25
I've been a subscriber to maximumpc for a long time and just recently I read this article:
[http://www.maximumpc.com/article/protect_your_linux_box_from_viruses#comment_form](http://www.maximumpc.com/article/protect_your_linux_box_from_viruses#comment_form)

In which he makes it seem like only a fool would think you don't need antivirus.  Then if you go to wikipedia here it lists the virsus and explains that if you have an updated kernel you are ok
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses_and_worms)

What's the deal, is the guy from maximumpc full of it?

---

### Post by aysiu on 2007-07-25
You don't need anti-virus.

For further discussion, read these links:
[http://www.psychocats.net/ubuntu/security#firewallantivirus](http://www.psychocats.net/ubuntu/security#firewallantivirus)
[why Linux has no virus, adware, or spyware?](http://ubuntuforums.org/showthread.php?t=143119&highlight=virus+linux)
[Ubuntu/Linux/Windows and Viruses/Malware](http://ubuntuforums.org/showthread.php?t=323028&highlight=malware)
[why linux doesnt need an antivirus?](http://ubuntuforums.org/showthread.php?t=435734&highlight=malware)
[What antivirs, anti-ad, anti-spyware, etc. software do you use?](http://ubuntuforums.org/showthread.php?t=295676&highlight=malware)

---

### Post by Seisen on 2007-07-25
Yes and no. If you transfer files between a Windows box and a linux box then yes I would recommend one but if you just use linux then don't bother with a anti-virus.

---

### Post by ddrichardson on 2007-07-25
While I understand the theory behind saying Virus protection is unneccesary, I do worry when people say its not possible. Viruses were not widespread on Windows systems until the boom in Internet use - because so many people didn' t realise the OS had a vulnerabilty.

The thing is though that as Linux becomes more and more popular, the number of people without protection will increase and hence an increase in viable targets.

Let's not forget one of the first major virus infections was the Morris worm which spread over BSD UNIX systems.

While I agree protection may not be necessary at present, I think it will be in time.

The biggest cause of Virus and Trojan attack is still users running programs that they shouldn't and regardless of the security measures in place, someone always seems to find a way.

---

### Post by LaRoza on 2007-07-25
Linux flaws will be fixed much faster than commercial OS's like Windows, remember, MS tooks months to respond to a known problem, the animated cursors. Also, any bad thing running on Linux will be unlikely to be run as root, so the damage will be minimal. 

The user is the best antivirus protection.

---

### Post by ddrichardson on 2007-07-25
> **LaRoza said:**
> Linux flaws will be fixed much faster than commercial OS's like Windows, remember, MS tooks months to respond to a known problem, the animated cursors.
 
Playing devil's advocate here but Windows also has a much longer product life cycle between major updates than Linux distros do, hence new bugs allowing exploits are more likel to arise more often than on Windows - but yes Open Source does allow transparency.

> **LaRoza said:**
> Also, any bad thing running on Linux will be unlikely to be run as root, so the damage will be minimal. 

The user is the best antivirus protection.

Completely agree - however never underestimate the sloppy link - nor how resourceful virus writers can be.

---

### Post by Bablefish on 2007-07-25
There are free linux anti virus programs AVG for one and there are others you could get from Ubuntu's database. But I even asked people who know and even they say you don't need one.

---

### Post by LaRoza on 2007-07-25
> **ddrichardson said:**
> 
Completely agree - however never underestimate the sloppy link - nor how resourceful virus writers can be.

The weakest part of a computer system are the users, a strange and true fact.

---

### Post by bone2006 on 2007-07-25
Again really what the heck is it going to scan if there's nothing to scan?  I mean I'm talking standalone, I really dont' want to hear about something on a network or you could email somebody or something of that nature.  I mean simply a standalone linux system.  Is there any virus out there?
Seems it would only take resource and is a waste of  resource.

---

### Post by aysiu on 2007-07-25
> **bone2006 said:**
> Again really what the heck is it going to scan if there's nothing to scan?  I mean I'm talking standalone, I really dont' want to hear about something on a network or you could email somebody or something of that nature.  I mean simply a standalone linux system.  Is there any virus out there?
Seems it would only take resource and is a waste of  resource.
I agree with bone2006.

There's no point in saying, "Oh, what if..." or "Years from now..." or "When desktop Linux has more marketshare..." Anti-virus isn't infallible. It's as good as its definition maintainers. If something new comes out, something unanticipated, it'll take a shorter time to install anti-virus via *apt-get* than it will for the anti-virus maintainers to update their definitions.

---

### Post by strabes on 2007-07-25
Think of it this way: Have you seen even one thread on these forums about a virus infection in ubuntu? Negative. We need to concentrate on things like broadcom wireless support and composite support for ATI cards. (both of which are the OEM's fault, not the linux community's)

---

### Post by kuja on 2007-07-26
> **LaRoza said:**
> Linux flaws will be fixed much faster than commercial OS's like Windows, remember, MS tooks months to respond to a known problem, the animated cursors. Also, any bad thing running on Linux will be unlikely to be run as root, so the damage will be minimal. 
The damage to the OS may be minimal, but other damage could be devastating. I can always reinstall if the OS gets tanked, but files and/or personal information once lost or stolen on the other hand ...

---

### Post by HermanAB on 2007-07-26
Here is a free virus scanner Bash script for you:

#! /bin/bash
echo Copyright Herman the Horrible, 2007, GPL v3 or later.
echo The One and Only Totally Free Linux Virus Scanner.
echo Downloading latest virus signatures...
sleep 10
echo Scanning...
sleep 5
echo Thinking...
sleep 10
echo Scanning some more...
sleep 20
echo Still scanning and thinking...
sleep 5
echo Omni patri hummm...
sleep 30
echo Almost done...
sleep 2
echo Bear with me...
sleep 1
echo Drum roll...
sleep 3
echo Woohoo! No viruses found!

Put that in a script called /usr/local/bin/scanner and make it executable with 'chmod 754 scanner', then run it whenever you think it is needed.  You'll be amazed at the raw speed of the thing - much better than any Windoze virus scanner.  For best results add a link to it from /etc/cron.hourly.

Cheers,

Herman

---

### Post by lisati on 2007-07-26
> **LaRoza said:**
> The weakest part of a computer system are the users, a strange and true fact.

The only time I've had major trouble from a virus was on XP Home and arose because of carelessness (stupidity?) on my part.

---

### Post by pofigster on 2007-07-26
That is so true!  People think of anti-virus software protecting them from everything, but the fact of the matter is, until a virus has been released and until it's been tagged and understood, your antivirus doesn't do jack shiz.  It's like in Magic the Gathering (I know, I'm clearly a huge nerd) if your have protection from every color but one - and your opponent plays a card of that color. Your screwed.

I figure, if something ever does come out, it'll be all over the boards and it'll be all over techy websites, so, I'll be able to deal with it when it comes, but not fret about it until then.

---

### Post by ddrichardson on 2007-07-26
When the Morris worm came out, people had been saying exactly the same thing for years - that viruses were only proof of concept and that there was nothing to worry about. Well there was, and the entire Internet (well not the JANET part) was disabled in a few hours.

To say that security is less important than wireless drivers is crazy - one of the main reasons to make the switch to Linux is for security!

While I agree that Virus checkers are only as good as their definition files, this argument is often touted on Windows and completely ignores any heuristic component in Virus detection.

And the argument about relying on apt-get or forums is mute without someway of knowing there's a problem in the first place. Remember not all trojans/viruses are aimed at destroying data, many are simply using machines to launch denial of service attacks - something that has been proven in the UK to be an offence under the Computer Misuse Act, and although no-one has as yet been prosecuted for being a zombie that doesn't mean it may not happen.

How much FUD has been spread by Microsoft effectively in the past - quite a lot. All it would take is one minor widespread exploit and they would go to town.

And how would such virus detection be distributed via apt-get? Embedded as a kernel module? Set to run by cron?

In any case we are assuming an attack on Linux, that doesn't mean that Linux based systems cannot be re-distributing viruses to connected Windows boxes.

At the moment we are all relying on the permission structure of Linux to prevent infection but there is no reason that executables with the users permission cant be altered and in anycase it isn't just executables that can carry such information.

---

### Post by hessiess on 2007-07-26
just get a good firewall, and an a/v program withch dus not run in the background, only wen you tell it to run

---

### Post by aysiu on 2007-07-26
No one is saying not to care about security.

We're just saying that running an anti-virus program doesn't make you more secure.

---

### Post by marco123 on 2007-07-26
I think this type of paranoia comes from having a windows backround.  Maybe if you trawl the internet and run every single .bin or .deb file you can find with sudo something may happen, I just use the repos though.

---

### Post by Seisen on 2007-07-26
> **marco123 said:**
> I think this type of paranoia comes from having a windows backround.  Maybe if you trawl the internet and run every single .bin or .deb file you can find with sudo something may happen, I just use the repos though.

I agree with you because thing you do when you install Windows is install a firewall, antivirus, and spyware remover at least.

---

### Post by ddrichardson on 2007-07-26
Its not paranoia - what if a virus were to get into a deb in the repository? It certainly isn't to do with a Windows background as (in my case) I've been Linux since 1995!

As I stated earlier I fully agree that VIrus checkers are only as good as their definitions, so keep them up to date!

All I'm saying is that to blindly believe that there are no viruses and that there never will be is tempting fate. To inform new users that Linux viruses are impossible is foolhardy in the extreme.

---

### Post by marco123 on 2007-07-27
How many Linux viruses have you been infected with since 1995? :)

Edit:  I do agree that users should be educated on the proper way to run and secure a Linux system. (Luckily most of the computer illiterate still use Windows though.)

---

### Post by tombott on 2007-07-27
When I first made the switch from Windows to Linux I installed AVG.

It lasted for about a week till I realised that it was not needed.

If you want to install AVG or the like, then go for it.

If a virus does get released am sure everybody would hear about it pretty damn quickly and that it would be plugged very quickly too.

Here's an interesting read for you though:

[Apple II - First Virus]("http://news.bbc.co.uk/1/hi/uk/6906414.stm")

[URL="http://news.zdnet.co.uk/software/0,1000000121,2065135,00.htm"]
McAfee - First Linux Virus[/URL]

And Linux Format (UK) Magazine did an interesting article on Security etc on all the Major distro's in their July 2007 issue.
You'll be glad to hear that Ubuntu came top, I'll see if I can scan the article or find an online version if anybody is interested?

Tom.

---

### Post by ddrichardson on 2007-07-27
I've had no Windows infections in that time either - because of an up to date scanner, not loggin in with administrative rights and because I don't run attachments from unknown emails.

In any case how many more Linux users are there now than there were in '95?

I ran AVG yesterday after transferring some file from work via USB. These files needed to be emailed to a colleague who runs Windows. One of the files was detected as having Ravmon attached to it.

This is the point I've been raising - regardless of whether Ravmon can infect a Linux based system, it can still be distributed via a Linux box. Had this been under Windows the resident scanner would have detected it and deleted it - if I hadn't manually scanned it then I would never have known and off it would have.

Now you can argue that it's not a Linux problem, fair enough. ;-)

Computer security is a huge part of job, and the common misconception is that only viruses attacking system files are a problem. Its simply not the case. A simple key logger in a users home directory needs no special permissions to log passwords being typed does it? Firefox has a default port open and could send that data on if exploited.

Some incredibly sophisticated virus and trojans have been seen recently: some that inhibit and destroy rival redirectors. Some are capable of imitating virus checkers to elude detection.

A virus checker wont solve everything but its still a damn handy tool to have when you recieve suspect attachments and external media.

---

### Post by tombott on 2007-07-27
> **ddrichardson said:**
> I've had no Windows infections in that time either - because of an up to date scanner, not loggin in with administrative rights and because I don't run attachments from unknown emails.

In any case how many more Linux users are there now than there were in '95?

I ran AVG yesterday after transferring some file from work via USB. These files needed to be emailed to a colleague who runs Windows. One of the files was detected as having Ravmon attached to it.

This is the point I've been raising - regardless of whether Ravmon can infect a Linux based system, it can still be distributed via a Linux box. Had this been under Windows the resident scanner would have detected it and deleted it - if I hadn't manually scanned it then I would never have known and off it would have.

Now you can argue that it's not a Linux problem, fair enough. ;-)

Computer security is a huge part of job, and the common misconception is that only viruses attacking system files are a problem. Its simply not the case. A simple key logger in a users home directory needs no special permissions to log passwords being typed does it? Firefox has a default port open and could send that data on if exploited.

Some incredibly sophisticated virus and trojans have been seen recently: some that inhibit and destroy rival redirectors. Some are capable of imitating virus checkers to elude detection.

A virus checker wont solve everything but its still a damn handy tool to have when you recieve suspect attachments and external media.

I agree with what your saying, but would you open an attachment from somebody you don't know or hadn't requested?

This is the major issues with Viruses, so many of them rely on users stupidity!

If you are dual booting Windows / Linux or exchanging files with Windows users then maybe installing AV is a good idea.

---

### Post by bone2006 on 2007-07-27
ddrichardson
where did the file originated from?  Why wasn't it scanned at work before even placed on your USB, why did it have to be scanned once it touched a linux system and not before?   Your email provider wouldn't scan the virus also before allowing the person receiving it to be infected?  Even crappy hotmail scans the files, so it just seems like so many reasons why not to have a virus scanner on a stand alone system.
Why would I want to put extra software that could slow down my computer for the "just incase" or other people.  

As others have posted, as soon as I format a PC to put windows on it, I put in AV, firewall and antispyware software as well as some office suite.  It just seems to be part of the way protecting windows systems.  With ubuntu coming with iptables and being behind a hardware firewall and not needing antivirus seems like ubuntu just runs so much smoother, of course I don't wasted time installing these things that I do with windows.

Why don't we have spyware scanners?  Just the same argument could be that  we don't have it now, doesn't mean we won't in the future if somebody downloads and installs something that's not in the repositories and have spyware.    But in my opinion think both arguments are silly and I'm not installing any antivirus.

---

### Post by ddrichardson on 2007-07-27
> I agree with what your saying, but would you open an attachment from somebody you don't know or hadn't requested?

That's probably why I said:

> because I don't run attachments from unknown emails. :-)

An on demand virus scanner doesn't slow down your system, it's run on demand. Iptables has nothing to do with virus protection.

I've no idea why everyone seems to be jumping on the band wagon as if I have insulted Ubuntu  - because I haven't. I've simply played devils advocate and said its an idea to protect downstream Windows users. Just because "crappy hotmail" has a virus scanner doesn't mean everyone does. Many ISPs don't provide a solution because they don't offer webmail. Some ISPs offer terrible scanners (BT and the god forsaken Norton products for example). I'm not saying now and haven't said at any point users must run anti-virus. 

The point I'm raising is that saying it hasn't happened so it wont is "silly". Twelve years of running Linux without infection isn't a guage in the same way that Windows viruses pre mass internet adoption isn't a guage. As more and more people move to Linux so the number of people worth writing malware for increases.

The other assumption ofcourse is to do with permissions, but there have already been a number of Firefox exploits and frankly, having seen some users web browsers - people will install anything as an extension.

---

### Post by marco123 on 2007-07-27
I think the thread title sums it up - "Do YOU or do YOU not need antivirus protection?

I think we can all agree that it is subjective. :)

Personally I have no Windows systems in my house/network, I'm an extremely careful user and also I don't forward email attachments to anyone.  So I don't need one, but that doesn't mean that YOU don't need one. 

I personally feel safe, but that doesn't mean that you do.  *hides under desk with machete*

---

### Post by bone2006 on 2007-07-30
> The point I'm raising is that saying it hasn't happened so it wont is "silly". Twelve years of running Linux without infection isn't a guage in the same way that Windows viruses pre mass internet adoption isn't a guage. As more and more people move to Linux so the number of people worth writing malware for increases.

I don't think anybody said that it won't happen.  The point is that you could have a virus scanner on a windows or linux machine and still get hit with a virus, since it's based on the definitions.    Again I still don't see a point in a standalone linux machine to have a virus scanner.  It's going to scan for something that's not there in linux and is there in windows, yet I'm running Linux.

---

