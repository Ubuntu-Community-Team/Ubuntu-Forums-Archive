---
title: "antivirus fix win xp dual boot using ubuntu?"
date: 2007-10-12
forum: General Help
---

### Post by StooJ on 2007-10-12
I'm posting this here, because as far as anti-virus software goes I'm an absolute beginner.

Having used & maintained Windows installations for years, I know the importance of anti-virus software, especially when you have uneducated users who will always want to know what the latest Powerpoint joke they've been emailed is about.

When I'm presented with a heavily infected Windows PC I usually install AVG from my write-protected USB key and let it pick up as much as it can. Then I try some others.

However, I still have to boot into Windows for that.

I believe the holy grail of anti-virus would be a linux liveCD with an anti-virus programme for Windows machines. You'd boot up in a nice linux-flavoured GUI and set off the anti-virus programme to scan the local hard drives. I'm pretty sure viruses would be far easier to get rid of this way, since they wouldn't be running as services, or at all so they wouldn't be able to propogate themselves while you're using a non-writeable CD for the OS and nothing Windows-ish in the RAM.

Does something like this exist? Would an anti-virus programme be able to detect a virus when it is not  resident (ie, the information is sitting on the HDD but not actually doing anything, since as far as it's concerned there is no OS running)?

I'm not sure if this is possible, but if there is a linux distro with this functionality out there, I'd love to hear about it.

Many thanks

---

### Post by slira on 2007-10-12
Hi
when i have a problem with virus in a W machine i usually boot it in secure mode and run the antivirus, etc. Normally it works better than having the OS booted in normal mode...
In linux I never had an antivirus installed, and so far, so good!
Best
slira

---

### Post by xmouse on 2007-10-12
Hi,

I hope I can help. Here is 3 links for distros you described:
[URL="http://www.bitdefender.com/bd/site/presscenter.php?menu_id=25&n_id=58"]
http://www.bitdefender.com/bd/site/presscenter.php?menu_id=25&n_id=58[/URL]
[http://www.avast.com/eng/avast_bart_cd.html]("http://www.avast.com/eng/avast_bart_cd.html")
[http://www.antesis.org/index.php?lang=en]("http://www.antesis.org/index.php?lang=en")

Have a nice day :popcorn:

xmouse

---

### Post by StooJ on 2007-10-12
Thanks for the links xmouse.

It's good to see that there are possibilities out there.

Unfortunately the bitdefender LiveCD and the antesis viruslive CD don't seem to have been touched since 2004.

The english version of the antesis website seems to be fairly dead as well, and my French isn't what it used to be.

I might have a look at Avast's offering, but it seems to be very commercially based rather than being aimed at a single user who cleans people's PCs as a favour, rather than as a job.

I could always point them to a more secure, easy-to-use operating system of course... ;)

---

### Post by oilchangeguy on 2007-10-12
read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
and this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

i've got two computers running 6.06lts, over a year and no anti-virus software, and no anti-spyware software. and no problems. you don't need to waste system resources by using such software.

---

### Post by philinux on 2007-10-12
I think if you use the live cd then install avg you'll have what you need. Or make your own custom live cd.
Or from synaptic an AV from the repo

---

### Post by bodhi.zazen on 2007-10-12
Well, the biggest problems you might have testing a windows install from a Linux live CD are :

[list=number][*]False positives. Linux scanners tend to make a fairly large number of false positives.
[*]Quarantining. Usually the only option on Linux scanners is to delete the questionable file.[*]As far as I know there are no Linux scanners for windows spy ware[/list]

See if these links help :

[http://www.oreillynet.com/sysadmin/blog/2004/06/scanning_for_viruses_with_knop.html](http://www.oreillynet.com/sysadmin/blog/2004/06/scanning_for_viruses_with_knop.html)

[http://s-t-d.org/](http://s-t-d.org/)

[http://s-t-d.org/tools.html](http://s-t-d.org/tools.html)

---

### Post by MinstrelBoy on 2007-10-12
I use a Bart PE boot CD and Trend Micro damage cleanup engine on a memory stick.
Search Google for more info.
Works great.

---

### Post by StooJ on 2007-10-12
Not really what I was looking for, oilchangeguy, but awesome reads nonetheless.

Expecially bodhi.zazen's guide. Very very informative, bodhi. Many thanks

---

### Post by n3tfury on 2007-10-12
> **oilchangeguy said:**
> read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
and this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

i've got two computers running 6.06lts, over a year and no anti-virus software, and no anti-spyware software. and no problems. you don't need to waste system resources by using such software.

right over your head.  read the OP's post again.

---

### Post by euler_fan on 2007-10-12
I don't know if something like Backtrack or Knoppix are what you are looking for necessarily . . . 

ClamAV is also pretty well regarded and could be installed from source and updated (relatively small all in all) in the LiveCD environment and used to scan disks.

---

### Post by dpar on 2007-10-12
Doesn't anyone think that it's kind of an oxymoron to be setting up a Linux cd to clean up the trash left over from Window's faults.:-k

---

### Post by bodhi.zazen on 2007-10-12
> **dpar said:**
> Doesn't anyone think that it's kind of an oxymoron to be setting up a Linux cd to clean up the trash left over from Window's faults.:-k

No. Windows users need a safe and secure environment in which to work so it makes perfect sense the look to Linux.

---

### Post by dak-AD on 2007-10-12
I've never used the security tools, but the [ultamate boot disc](http://ubcd.sourceforge.net/) comes with F-prot antivirus for DOS, McAfee AV, and bughunter; [ubcd4win](http://www.ubcd4win.com/contents.htm) also has A^2, adAware, CWShredder, EzPCFix, Hijack This, Rootkitty, Spy Bot 	1.4, WinSock Fix, XBlock, AVG 7.5.472, AVPersonal, Avast! Tool, McAfee Stinger, Dr.Web CureIT (phew!)

It's not a live linux cd, it runs off of freeDOS iirc, but it's close to what you're after. also, the ubcd is just all-round cool imo :)

---

### Post by dpar on 2007-10-12
So Linux can be just a big antivirus/antispyware program for windows??Naa, I don't buy that.

---

### Post by bodhi.zazen on 2007-10-12
> **dpar said:**
> So Linux can be just a big antivirus/antispyware program for windows??Naa, I don't buy that.

I did not mean it that way, but unfortunately there are those who are dependent on Windows (there are many many programs without Linux equivalents , especially software used by professionals) and for those Linux may be the tool that keeps their sanity.

---

### Post by dpar on 2007-10-12
Your probably right there, bodhi:)

---

### Post by NotTheMessiah on 2007-10-12
A question: How do you update the Avirus Dbase on the Live disk? You'll need an internet connection which might take a lot of time to set up. 

Trying to get rid of Polymorphic nasties for Windows with the help of the mighty penguin??? Let them suffer i say :lol:

---

### Post by HermanAB on 2007-10-12
Your best bet is to make a BartPE disc with ClamAV and Spybot S&D:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

H.

---

### Post by StooJ on 2007-10-15
Ultimate boot disk may be the way to go after all. I have used it in the past, but I guess I'd forgotten about it :oops:

As for the more philosophical side to my thread (I love it when my threads get involved in bigger issues)

There are just some users that have to use Windows, or flat refuse to move from Windows.

When things go wrong on Windows computers, I get called in and often look to Linux to help me solve immediate problems. When a windows installation is so messed it won't boot up any more, I invariably reach for a liveCD, boot up Ubuntu and back up their files somewhere else before I go messing about with the MBR, repairing windows or wiping the whole shebang and starting again.

Although these users would never dream of leaving Windows for dozens of different reasons (professional software being first on the list) I would never dream of leaving my liveCDs at home when I go to fix stuff.

> So Linux can be just a big antivirus/antispyware program for windows??Naa, I don't buy that.

That's one of the mind-bogglingly awesome things about linux in general. It is so scalable and adaptable for so many different tasks. Linux could be used as a big antivirus/antispyware programme for windows, and could be used for countless other things. I don't think that depreciates Linux's value.

---

### Post by juicymixx on 2007-10-16
Hello,

   My computer is a dual boot system, on one partition I have Windows XP, on the other is Ubuntu.   Recently my XP partition got a nasty Vundo virus infection.   Before I wipe it and reinstall windows, I was wondering if there is some tool I can run in Ubuntu that can scan the windows partition and:
1) identify and remove infected files
2) check out the windows registry

   I know this is asking alot, but with som many people using dual-boot systems I thought that someone may have an answer to this...

Thanks.

---

### Post by milton1 on 2007-10-16
don't know about fixing registry issues, but clamscan or avg might be able to scan and remove infected files.

---

### Post by strabes on 2007-10-16
I doubt any antivirus available for linux is going to have a windows registry cleaner. Once you get the virus removed, there are many registry cleaners available for windows. My favorite is "ccleaner." It's simple and easy.

---

### Post by bodhi.zazen on 2007-10-16
Threads merged ....

---

### Post by dak-AD on 2007-10-19
yes, if you set your windows partition to read/write-able, a linux-run AVG will be able to spot and remove viruses on the windows partition. BUT, I'm not sure how clever it is -- sometimes they rely on encripted viruses decripting themselves into running memory to spot for example (iow, if windows isn't up and running, it might not be able to spot it), and theres allways the registry etc...

iirc from my volunteer anti-malware days, vundo's a hard one to shift and automatic anti-viruses might not be able to deal with it well in any case. you might want to check out some of the a-sap sites online, who'll give you assistance removing it. if you tell them you have a dual boot, then maybe they'll be able to use that (i think HijackThis can run from a linux install and examine a windows one, but i'm not sure... but vundofix was a bat file last i checked anyway).

my memory could be a bit shoddy here and i've no doubt it's changed alot since i was active in that scene, but the bottom line is: if you're prepared and capable of re-installing windows, maybe that'd be the best option rather than trying to fix vundo?

---

