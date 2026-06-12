---
title: "You Can Get Viruses on Ubuntu Too? [Resolved]"
date: 2006-12-11
forum: General Help
---

### Post by SuperMike on 2006-12-11
FYI...

After my wife's Windows 98 PC was infected with a virus, I formatted it and switched her to what I had, which was Ubuntu. I then updated her system as prompted and installed clamav to run on a daily scan that dumped output to a logfile. I added a local inbound firewall on her system as well as mine. Next, I added a hardware-based firewall to our network, set it for MAC filtering, and checked to see if it needed any firmware updates. As well, it had outstanding ratings at Secunia.com.

Sure enough, around Sept 14th, and unfortunately too late for me to know, her system was infected with a virus. This virus spread through her PC and into mine. So now I have turned hers off and I will soon be formatting both, reinstalling Ubuntu again, and restoring our stuff again.

I have a funny feeling the virus came either through an infected web page that had a Firefox exploit, or through an infected PDF, and perhaps on a day when I had not updated her workstation to the latest Ubuntu patches.

So yes, Virginia, you can get viruses on Ubuntu too, it seems. Nothing is safe anymore.

Here's the mutation path that I could find in the logs. It seemed to infect /proc/kcore, whatever that is. I don't know if I can delete that file or what, but it's a moot issue because I'm going to have to wipe everything, reinstall, restore data, change all our passwords on every thing and every bank account or financial site we interact with, and the whole nine yards.

So folks, if you haven't installed clamscan, configured it properly to scan your files and log the result somewhere, or you haven't updated your web browser or PDF viewer to the very latest, or you haven't updated your Ubuntu patches in awhile, please consider doing so because this could happen to you too.

Here's the mutation path of this virus upon /proc/kcore:

Trojan.Bat.Killfiles-14 (original)
Worm.Nacona.B
WM.Dark.B
Traceback-3029
Trojan.Qhost.AH
Gergana.2
Exploit.Linux.Gv
Gen.5792
DIR-II
Gergana.3

---

### Post by Patrick-Ruff on 2006-12-11
wow, that's insane. that seems really weird to me, however, make sure you guys have VERY good root passwords. see, the best thing crackers have against people that use ubuntu is what we call social engeneering, if you execute something that is a virus programmed to mess up an ubuntu system, well, that's your own fault.  this just seems too strange to me, you have better security then my bloody school, and you still manage to get hacked. either someone is out to get you or you guys really need to start watching what you open.

also, make sure firefox is the latest, I've never browsed to any infected sites that managed to kill my computer, on my windows computer I only have a firewall and it's been running smoothly for over a year on the same partition.

either way, there shall be better posts then this.

good luck to you

---

### Post by wieman01 on 2006-12-11
Well, are you sure all of these are real Linux viruses? I doubt it... To give you an example:

**"Exploit.Linux.Gv"** is a false positive. It's discussed here: [http://forums.clamwin.com/viewtopic.php?p=2815&sid=d62790c23b45faa119146f059fa94afd]("http://forums.clamwin.com/viewtopic.php?p=2815&sid=d62790c23b45faa119146f059fa94afd")

I am on the cautious side as well, but I don't think there is a need to panick. Reinstalling would not have been necessary. Perhaps try another virus scann e.g. AVG.

And isn't **"GERGANA"** and old DOS virus infecting .COM files? **"DIR-II"** definitely is: [http://antivirus.about.com/library/virusinfo/bldir2.htm]("http://antivirus.about.com/library/virusinfo/bldir2.htm")

---

### Post by _simon_ on 2006-12-11
Aside from the false positive one, aren't they all windows viruses?

We already know that youe linux box can contract windows viruses but there is nothing that they can do once on. The only issue you would have is reinfecting your wife's machine.

---

### Post by nocturn on 2006-12-11
kcore is your entire memory.  I'm guessing these are false positives.  You cannot get DOS virusses on Linux (unless you use wine, and even then only few work).

---

### Post by theslut on 2006-12-11
all of those are windows only. you might have the files on them but i can't see how your machine can actually be infected. are you having stability issues or information going through the internet to another computer?

seems highly unlikely to me.

i don't even bother with an antivirus scanner on my linux station. whats the point? the only one ive' got installed is on my server that people use for email and it scans the emails for them but those are windows users on a linux server.

no need to panic i think.

---

### Post by elcasey on 2006-12-11
It's certainly pleasant to hear this isn't as bad as originally thought. My only further advice would be to use the NoScript plugin for Firefox, which would keep any untrusted websites from executing scripts, period. It blocks a lot of advertising for me as well and when coupled with AdBlock I don't see many ads.

I have Kaspersky AV but I haven't installed it yet. Should I just stick with Clam? I'm not super-paranoid, but I am security-minded.

---

### Post by technodigifreak on 2006-12-11
> **elcasey said:**
> It's certainly pleasant to hear this isn't as bad as originally thought. My only further advice would be to use the NoScript plugin for Firefox, which would keep any untrusted websites from executing scripts, period. It blocks a lot of advertising for me as well and when coupled with AdBlock I don't see many ads.

I have Kaspersky AV but I haven't installed it yet. Should I just stick with Clam? I'm not super-paranoid, but I am security-minded.

"Just because you are paranoid, doesn't mean no-one is after you." (Patrick Stewart - Movie "Safe House" [http://imdb.com/title/tt0120051/](http://imdb.com/title/tt0120051/).)

Security conscious is good.  Nothing is impenetrable, but adding layers helps toward that end goal.  Yes, Linux can be infected by viruses, but thanks to it's architecture there is very little that the virus could do (unless it's run by a superuser).  You are probably A-OK if you and your wife do not constantly login and run things as a super user.  ClamAV should be all you need, however AVG works very well also.  I highly recommend the No-Script extension for Firefox. To be honest, I've used it long enough that I almost forgot what a pop-up box looked like.  :-D

---

### Post by SuperMike on 2006-12-11
Hey you guys! This is major EXCITING news. So Ubuntu is secure and I'm getting a mix of false positives and DOS-type junk that won't run on Linux.

---

### Post by ]Nbx*cmD[ on 2006-12-11
Anyway, if an antivirus detects a virus in a GNU/Linux system, that 
DOESN'T MEAN your system is infected, but just that file. If you transfer this file to a window$ computer then it will turn into a dangerous virus.

GNU/Linux antiviruses are designed to prevent window$ users from being infected from files stored in GNU/Linux systems and containing viruses.

Your system WON'T GET INFECTED, don't worry ;)

Btw, I've never used an antivirus, I'm sorry for window$ users if my files are infected, window$ is a huge virus itself, so there's nothing I can do for them but recommend them to format their HD and install GNU/Linux. :D

---

### Post by koenn on 2006-12-11
> Hey you guys! This is major EXCITING news. So Ubuntu is secure 
> Your system WON'T GET INFECTED, don't worry 
I'd like to put that into perspective:
Running Ubuntu (or an other Linux) does not make you immune from viruses. 

It does make you immune from Windows and DOS (as in MS-DOS) viruses, and to my knowledge there aren't too many viruses targetting Linux (yet ?) but that does not mean Ubuntu or Linux are immune to virus infections. 

Viruses are technically just executables : programs, scripts, ...
What is anyone with a bit of programming skills to stop from writing a virus that can run on Linux ?  
What if such a virus was hidden in a package and then published with something allong the lines of "just install this and all your problems with Beryl, Compiz, nvidia, (insert popular problem here) will be solved". 
Wouldn't it get downloaded and installed ? 

Often virus treaths to Linux are dismissed with "they wouldn't be able do do much anyway, cause they'd be running without root privilegues". 
But you'd be root when installing that package, wouldn't you ? So any malicious code code in, say, the post-install script, would be executed as root, wouldn't it ? And to make things work, that installer script could maybe create an additional superuser account for future use ? a cron job owned by root to do some dirty deeds at regular and frequent intervals ? 

Sounds rather feasable to me - so all this 'hooray hooray I use Ubuntu, no more viruses for me, let the poor Windoze lusers and Micro$oft slaves suffer' is kinda scary. It creates an atmosphere where Linux viruses may actually flourish.

---

### Post by igknighted on 2006-12-11
Yeah, but you would have to follow unsafe practices to get it.  I don't install random .deb's.  If a .deb was so impressive that I wanted to try it, most likely someone in the forum would have tried it and been like "Holdup, its no good".  The point is, to get infected you would have to open the door, so while it is possible, the onus is on you, the user, to be smart.  Windows, on the contrary, leaves all the doors open and you've got to run around and slam them all before something gets in.

---

### Post by jonah1980 on 2006-12-11
i don't know about how feasible viruses could be or not on linux, but would they not be even more destructive if they were possible as linux users rely more-so on the internet than windows users. Afterall we get daily updates, download packages to install and linux is used on more servers??

linux is more internet connection orientated in my opinion, where as microsoft stuff started with off the shelf boxed software and more packaged stuff...

or am i wrong? i don't mind if i am! infact i would be glad! i wanna be safe from these horrible viruses dudes!

---

### Post by technodigifreak on 2006-12-11
> **koenn said:**
> Sounds rather feasable to me - so all this 'hooray hooray I use Ubuntu, no more viruses for me, let the poor Windoze lusers and Micro$oft slaves suffer' is kinda scary. It creates an atmosphere where Linux viruses may actually flourish.

True, security is a mindset.  For any virus to florish on any Linux system, it would have to take advantage of the very trusting nature that people have of anything that calls itself *FLOSS*.  However, I and as should any prudent administrator/user, take careful thought and consideration to everything they install and indeed their every action on a production machine.  Installation only from established repositories, locked down websurfing (kind of an oxymoron), and not executing every script that you see on the 'net as root.  If I do introduce a new program, I make damn sure I've tested it (usually on a red virtual machine).  

Now to make the counterpoint. It is possible to achieve a fully locked down system in WindowsXP that is as secure as Ubuntu is by default.  However, this takes a **long** time and you have to purposefully plan every step.  Never step out of the established routine once you've done this.  Ubuntu (and almost all Unix variants) have these already implemented as default, thus providing an extremely robust system out of the box.  All that is needed is a little user education, a few *minor* tweaks, and you have a very secure setup.

---

### Post by markymarknz on 2006-12-11
> **igknighted said:**
> Yeah, but you would have to follow unsafe practices to get it.  I don't install random .deb's.  If a .deb was so impressive that I wanted to try it, most likely someone in the forum would have tried it and been like "Holdup, its no good".  The point is, to get infected you would have to open the door, so while it is possible, the onus is on you, the user, to be smart.  Windows, on the contrary, leaves all the doors open and you've got to run around and slam them all before something gets in.

The master plan then is to hack the ubuntu repositories and upload infected packages --- :evil:

---

### Post by PrinceArithon on 2006-12-11
I agree it's kinda scary so many people think that just because they are using Linux they are virus free.

For now the majority of viruses are being made for windows.  It's shifting a bit and targeting MAC a little bit more.  Recently I'm hearing that there are eyes out for Linux now.  The sad thing is the entire Linux community isn't prepared.  Including the anti-virus makers for Linux.

Just because you don't download an odd .deb file doesn't mean you can't get a virus.  Just because you are watching out like crazy for what you are loading doesn't mean you wont get a virus.  

Security is so important to any OS, no matter how secure.  No matter how few viruses there are out there for the OS.  Just because you guys haven't heard of someone that got a Linux virus doesn't mean there aren't people who have gotten them.  I know someone who got a linux virus and they had an anti-virus scanner and they were careful of what the downloaded.  They just got one.  It sucked too, the thing was so bad that it got into their BIOS.  He had to flash the BIOS and then reload linux.

So all this bluster about being virus free is fine.  For now most people wont get a virus on Linux.  As soon as more people start shooting for Linux it will happen more often.

Sorry, it's just the way of the world.  There are bad people and you have to protect yourself no matter what it is you are using.

---

### Post by hikaricore on 2006-12-11
....  I'm just going to pretend that I didn't read this insane pile of paranoia and go back to what I was doing now.  Good luck to you all in scaring the @$%^ out of yourselves.

---

### Post by koenn on 2006-12-11
@technodigi... & igknighted:
Yes, you know what your doing, you apply good practices, you have security in mind. 
So IF Linux viruses would begin to show up, you'd probably remain secure. But how many of the people on this forum are aware of what they're doing ? They're first concern is to get that latest newest whatever and will add any source to their sources lists to get it. I've seen people exchange page-long sources lists here - I don't think they think twice about the consequences. 
I'm not too optimistic ...

> you would have to follow unsafe practices to get it.Much of that is true for Windows, actually. You do have "drive-by" downloads, but lots af viruses require some user action to get installed : accept a download , execute a program with some malicious code in it, open an email attachment. People just do it, and those who spread viruses find ways to make people do it. That the techniques they use now would not work on Linux is besides the point; to start spreading viruses on Linux they'd develop techniques or tricks that would work on Linux. 

So imho it has, as you too indicate, to do with being aware of what you're doing. While Linux was still mostly used by programmers, sysadmins and other IT pro's, this was not an issue. With distributions actively targetting the recreative users (eg Ubuntu), it does become an issue -imho.
That has always been the week point of Windows : you did not need any IT knwoledge to set up a server and connect it to the internet. It worked out of the box - anyone could set it up - and everyone did (and contributed to a universe where viruses and spambots could thrive). You couldn't do that with BSD or some other unix, or Linux. You needed to be trained. And in training, you learned to set things up secure. That advantage is going away now. 

I do agree with your point that Linux, by design and from its unix legacy (to be used by multiple users and be connected to other systems), is more secure, and that - to accomplish the same on a Windows system, you'd need to really think it true, find the configuration that is both secure and does what you need it to do, and stick with it (or apply decent change management). I argued something similar in an other thread ... here : [http://www.ubuntuforums.org/showthread.php?p=1868239#post1868239](http://www.ubuntuforums.org/showthread.php?p=1868239#post1868239)

But I'm still convinced that lots of what made Windows such an easy target for al kinds of malware, is now slowly beginning to occur in the Linux world as well.

---

### Post by koenn on 2006-12-11
> **hikaricore said:**
> ....  I'm just going to pretend that I didn't read this insane pile of paranoia and go back to what I was doing now.  Good luck to you all in scaring the @$%^ out of yourselves.
You've proved my point.

---

### Post by PrinceArithon on 2006-12-11
LOL that is exactly what I was thinking, and to which my point was proved as well.

---

### Post by rioghal on 2006-12-11
Well, a Linux virus on a Linux system wouldn't do much more than trash the normal user account because the system files/folders aren't writable by the normal user. I never install anything unless it is in the repos and even then I always listen to, and rely on, the community for news about new packages before I install them. If there is an app that I want and it isn't in the repos, I will research the app. If the app has been around for a while and/or the community has audited the source, I'll compile it myself.

That is the amazing thing about Ubuntu, it has a huge, amazing and helpful community. I'd be an airhead to not take advantage of that.

Computer security is a journey, not a destination.

---

### Post by bodhi.zazen on 2006-12-11
You can have files on a Linux box that are "infected" with windows viruses. At this time, however, these viruses have not been able to damage your Linux box.

At this time it is possible to run windows viruses with wine. They do not run well yet.
		[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

Linux anti-virus software is as of yet to protect your friends and family from files you may transfer to them.

At this time I let the Windows users protect themselves and do not feel obligated to protect them.

If I ran a server to widows boxes, however, I would watch for windows viruses....

There are other forms of malicious code. See this site for some general information:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

As Linux becomes more popular there will likely be increasing threats. However, do not forget that viruses and root kits are either installed by you the user (by installing 3rd party software or running as root) or take advantage of vulnerabilities in the Linux (Ubuntu) code.

Since Linux is, for the most part, open-source that means there are thousands of eyes on the code. Keep you system up to date ....

This is different for other OS where the code is not open for review and you are dependent on Microsoft to fix their problems.

In the end, Ubuntu is 'secure' however the only totally secure system is powered off, disconnected from the internet, and in a locked room :twisted:

---

### Post by SuperMike on 2006-12-11
When we scan device files including memory, after a lot of thinking, I imagine it's possible to come up with lots of false positives. Here's why, in my opinion. The way I understand a virus scanner works is that the scanner companies work with international government-based and quasi-government computer security organizations to develop a signature, and/or they combine it with their own database of signatures. A [signature]("http://en.wikipedia.org/wiki/Virus_signature") is a section of bytes at two or more points of the file that line up with the actual virus. These signatures are then given names (which are not always synchronized) and are categorized by type, threat, and variant, in addition to other factors. Then, the virus scanner scans bytes in the designated files and looks for a match. It's a very simplistic operation and it is prone to false positives. Now, if you take a file that has wildly random bytes inside, such as a file that represents memory, it is bound to have false positives.

That's the running theory I have.

Or, perhaps I went to an infected site with Firefox, the virus tried to deploy (and more than likely it was designed for Windows and DOS), and it stuck in RAM cache (although it was useless and harmless to me if designed for Windows and DOS). When the virus scanner scanned /proc/fproc or memory, it might have seen the virus signature.

More than likely the case was the prior theory, not the latter.

---

### Post by technodigifreak on 2006-12-11
> **koenn said:**
> @technodigi... & igknighted:
Yes, you know what your doing, you apply good practices, you have security in mind. 

Thanks for the compliment. 

> **koenn said:**
> But how many of the people on this forum are aware of what they're doing?

Very few...which is why I make it my personal responsibilty to help educate the people here, and indeed all users of any operating system that I interact with.  Basic security principles carry across all architectures.

> **koenn said:**
> That the techniques they use now would not work on Linux is besides the point; to start spreading viruses on Linux they'd develop techniques or tricks that would work on Linux. 

I frequently remind people that rootkits were invented on Unix (hence the term **root**kit).  Also, depending on who you ask and what version you go with, Unix was invented sometime between 1967-1971.  So for arguement's sake, lets say it was invented in '69, that's roughly 37 years of development time.  Since the advent of the internet and most specifically the last 6-7 years, development on Unix variants (BSD's and Linux) has risen at an exponential rate. MS-DOS came to market in 1981 and Windows 1.0 in 1985.  So let's say there's been 25 years of development leading up to Windows Vista.  *That's a developmental difference of 12 years* between the latest version of Windows and most recent Unices (Edgy for example).  One could make a serious agrument that because of the exponential growth in the development of Unices in the last few years, the skew of 12 years could be *considerably larger*. 

The truth is, the Windows world is experiencing the same problems (virii, rootkits, and backdoors) that Unices exerienced throughout the early '80's.  Most of these problems were worked out of Unix systems by the early 90's.  One of the significant pieces that helped Unix through these times was it's compartmentalization.  IT people could simply not run the vulnerable parts of the system.  And infact those parts had to be explicitly turned on (as you had to build the system piece by piece).  

Now the Microsoft way is to turn everything on by default and let the user figure out that their systems dangerous.  That's like building a car with a rocket engine and saying, "Oops, we forgot to include a way to stop it. My bad. Well, on the plus side the user interface (accelerator) is really easy to use."

> **koenn said:**
> ......You needed to be trained. And in training, you learned to set things up secure. That advantage is going away now. 

I do agree with your point that Linux, by design and from its unix legacy (to be used by multiple users and be connected to other systems).....But I'm still convinced that lots of what made Windows such an easy target for al kinds of malware, is now slowly beginning to occur in the Linux world as well.

The strength of Unix based on one very import thing.  The system will not stop you from doing something **very stupid**, because that might stop you from doing something **very smart**.  Keeping this in mind will put all users in good stead to keeping their systems secure.

---

### Post by technodigifreak on 2006-12-11
> **SuperMike said:**
> When we scan device files including memory, after a lot of thinking, I imagine it's possible to come up with lots of false positives. Here's why, in my opinion. The way I understand a virus scanner works is that the scanner companies work with international government-based and quasi-government computer security organizations to develop a signature, and/or they combine it with their own database of signatures. A [signature]("http://en.wikipedia.org/wiki/Virus_signature") is a section of bytes at two or more points of the file that line up with the actual virus. These signatures are then given names (which are not always synchronized) and are categorized by type, threat, and variant, in addition to other factors. Then, the virus scanner scans bytes in the designated files and looks for a match. It's a very simplistic operation and it is prone to false positives. Now, if you take a file that has wildly random bytes inside, such as a file that represents memory, it is bound to have false positives.

That's the running theory I have.

Or, perhaps I went to an infected site with Firefox, the virus tried to deploy (and more than likely it was designed for Windows and DOS), and it stuck in RAM cache (although it was useless and harmless to me if designed for Windows and DOS). When the virus scanner scanned /proc/fproc or memory, it might have seen the virus signature.

More than likely the case was the prior theory, not the latter.


Actually Mike, your second theory is a valid one.  It was probably a part of a client side script (most likely javascript), which was deployed within Firefox.  It got dropped into memory, and having no way to execute, just stayed there.  It could have also been dropped to your swap instead.  It was most likely not a false positive, but a virus which had no way to "sink in it's fangs".

---

### Post by scrooge_74 on 2006-12-11
In summary the best thing a user can do is inform himself as much as possible to avoid mistakes and have a secure system.

Usually those that want to have the latest eye candy are the ones who know the least about their system and will be the targets of any attack.

Plus Windows user are doom and the only way to help them is to make them dump MS for good.

---

### Post by pay on 2006-12-11
The world would be a better place if hackers had something more productive to do than write viruses.

---

### Post by brihy1 on 2006-12-11
how do i install an antivirus scanner(avg,clamav)?im very new to linux

---

### Post by pay on 2006-12-11
```
sudo aptitude install clamav
```

---

### Post by wieman01 on 2006-12-11
> **pay said:**
> The world would be a better place if hackers had something more productive to do than write viruses.
Crackers, please, not hackers. Hackers create code & useful programs, crackers develop malicious software such as virii & worms. There is a distinct difference.

---

### Post by brihy1 on 2006-12-11
i did that and this is what i get? am i doing it right?:confused: 




bri@ubuntu:~$ sudo aptitude install clamav
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bri@ubuntu:~$

---

### Post by organica on 2006-12-11
close out all your open applications except the terminal.  try it again.  you have a package manager application open somewhere.

---

### Post by brihy1 on 2006-12-11
sorry for sounding stupid(used to windows)but how do i know whats running in the backround:confused:

---

### Post by drphilngood on 2006-12-11
> **brihy1 said:**
> sorry for sounding stupid(used to windows)but how do i know whats running in the backround:confused:

Enter this in a terminal
```
top
```

edit:
You would probably be better off installing ¨Virus Scanner¨ from the Add/Remove menu.  That would be easier for you and it works well.

---

### Post by SuperMike on 2006-12-11
> **brihy1 said:**
> how do i install an antivirus scanner(avg,clamav)?im very new to linux

Hey, sure, I can help. I hope I break it down enough for your level of "newbieness". :) 

I'll show you how to use something called ClamAV.

1. Do you see your menus? Keep clicking on them until you find one that says something like Terminal.

2. A white or black window will usually open. That's your terminal. If you are old enough to remember the days of MSDOS command prompt, it's sort of like that. The terminal gives you access to the Linux shell, which is a command environment where you type short commands followed by strange characters and phrases like --this and --that so that you control or configure your operating system, or run something. In the following example, I'm sure there's the GUI way to do this, but I think it's faster for me to show you the command-line way to do this.

3. Type this, and when you are prompted for a password, use the one you used to login to your workstation.
```

sudo apt-get update
sudo apt-get install clamav
```

If you get an error, then it's perhaps that I'm mistaken and you might need to enable the Universe option (*only temporarily*, of course) in something called the /etc/apt/sources.list file. These usually exist and are commented out with the # character as the first character of that line. You basically take an editor and edit this file. It's protected so that only a certain user, root, can access it, so you would edit it with something like:

```
sudo nano /etc/apt/sources.list
```

...and then you would save this file -- but only do that if you received an error on the apt-get commands I mentioned above.

Now, if you were in a situation where you had to edit the sources.list file, then go back and repeat this step # 3 all over again with the sudo apt-get statements.

4. Okay, at this point, the apt-get command may tell you it's going to install extra stuff like libclamav1 and freshclam. This is good news because libclamav is a driver to make the clamav package work, and freshclam is the tool that clamav needs so that it can update its virus signatures. So if it prompts you a Y/N, choose Y and press enter.

5. If you had to turn on the Universe option in order to install clamav, then it's probably not a good idea to leave that option turned on. Ubuntu knows this and that's why they turn it off by default. Universe is the option that's community-supported instead of being Ubuntu-tested. More than likely that means it's still going to work, but sometimes the Universe option, if you were to follow it with a risky command like...

```
apt-get upgrade
```

...might bring your whole computer into a kind of unstable nature. That's why I avoid leaving my computer in Universe mode and only use it *temporarily* to install stuff when I can't find it otherwise.

6. Now, when clamav is installed, I noticed that it doesn't run automatically. Sorry about that, but they wanted to make certain when you installed it that you told it exactly what you wanted it to do. Unlike other virus scanners that only have a few configurable options, clamav has a ton of different options you can choose from and it can't assume which one is going to suit you best.

7. Now, if you're like me, you realize that Linux is a sensitive instrument, unlike Windows. You can't just have your virus scanner catch what it thinks are bad files and start quarantining them. And why? Because it's risky to the operating system and could crash the whole thing. On Windows, however, they have a thing called Windows File Protection, and, as well, the virus scan authors work closely with Microsoft (and pay for that in cold hard cash) so that they don't quarantine files such that the computer would freeze up (usually). **Therefore**, I just have Clamav tell me if it finds a virus and I use forums like this one on the web (and some close Linux gurus I email occasionally) help me determine if the stuff is a false positive or a true virus. If it's a true virus, then I'm from the camp that would rather backup, test backup, format, reinstall, restore data files backup than to try to do "virus surgery" to remove the virus. This is because sometimes when a virus scanner finds the virus, if it's not a false positive, then it's often just found a symptom of the virus and not always the real virus itself. In other words, I don't believe in virus surgery being that affective in eradicating the virus.

8. Therefore, we now need to configure your scanner. But first, wouldn't you like your virus scanner to speak to you over your computer speakers and tell you it found a potential virus? I like that, so I use a program called 'festival'. You'll want to install it just like you did in step 3, and you may or may not need the universe option, but the command is:

```
sudo apt-get install festival
```

9. After you install festival, if you had to turn on the Universe option in your /etc/apt/sources.list file, please consider turning that back off again by commenting it out with # as the first character on that line and doing 'sudo apt-get update' once done.

10. Now test festival like so:

```
echo 'Hello, Computer User' | festival --tts
```

...Did you hear it say something to you? If not, then turn up your speakers or look at getting your sound working on your PC.

10. Now, let's configure ClamAV. There are two things you'll need. These are two files in the /usr/bin directory, which are:

```
/usr/bin/clamscan
/usr/bin/freshclam
```

...you can use the 'ls' command, like:

```
ls /usr/bin/*clam*
```

...to see if those files are there.

11. Now, we need to edit a file called /etc/crontab. To edit it, we do:

```
sudo nano /etc/crontab
```

...and then add these lines at the bottom:

```
00 1	* * *	root	/usr/bin/freshclam
#
30 3	* * *	root	/usr/bin/clamscan --quiet -r -i --no-mail --no-ole2 --no-pe --no-html --max-recursion=10 --log=/var/log/clamav/clamav.log --exclude-dir=/proc|/sys|/dev|/mnt|/media /
#
30 7 	* * *	root	tail /var/log/clamav/clamav.log | grep -i infected | grep -iv ': 0' && echo 'Potential Virus Found' | festival --tts

```

First, it updates your virus scanner files at 1:00am.

This then kicks off the virus scanner at 3:30am in the morning (because it's likely going to need to run a long time), will exclude some common folders where false positives are likely, and will dump the results in a logfile called /var/log/clamav/clamav.log.

It then follows at 7:30am by checking this logfile, seeing if it contains the word "infected", and saying the phrase 'Potential Virus Found" to you if it finds it. I assume you're up by then, checking your email, and if not you can change the time to a more reliable time when you're sitting there. It's not that there is a virus that it found, but there might be one and it requires further investigation, communication with forums like this, etc.

So, anyway, save this crontab file and it's almost ready to go.

12. Now it's a good time to manually run these two tools. Start by typing:

```
sudo freshclam --verbose
```

...and when you get errors about needing to use the latest version of ClamAV, I usually ignore those because their not that critical to me (in my opinion). Besides, I uninstall and reinstall clamav every so many months to ensure I'm on the latest version.

13. Now run the next tool and be prepared to walk away for a few hours. It will slow your system down a good bit.

```
sudo clamscan --quiet -r -i --no-mail --no-ole2 --no-pe --no-html --max-recursion=10 --log=/var/log/clamav/clamav.log --exclude-dir=/proc|/sys|/dev|/mnt|/media   /
```

...oh, and yes, there's a slash on the end that is preceded by spaces --> that's the directory where you want to start scanning from, and in this case that's the root directory.

14. Now when the clamscan command finishes, you need to check the output by doing:

```
sudo cat /var/log/clamav/clamav.log
```

Do you see something like "Infected" followed by a number? If so, then you may or may not have a potential virus and it requires further evaluation with technical people on the web like here, and with good technical friends who know Linux. It will likely happen so rarely for you that you won't need to do that very often.

15. Okay, you don't need to leave the Terminal window open anymore, but you can use it to 'cat' out the clamav.log file occasionally to see how things are going in the next few days.


Commentary:

* Sure, it would be nice to have a GUI front end for all this when you're a newbie, but realize that (a) ClamAV is free, and (b) Someone has to build it and they're taking volunteers, and (c) Linux with a stable GUI (like KDE or GNOME) is still a relatively new operating system on the computer operating system timeline when you compare it to the lifespan of Windows. It's going to take awhile before you see programmers having the time to build this. They probably already are.

* Since the community supports ClamAV, it's good and bad as far as being reliable. It's good in that you'll often find it updated most of the time with newer virus signatures more frequently than you would a commercial package. It's bad in that it has less bureaucracy, and less at stake (because it has no paying customers), and therefore you might end up with occasional false positives because it is not reviewed as meticulously as other commercial packages. It's a tossup -- some days it might beat something like a Kapersky Anti-Virus, and other days it may not. However, since most people like it as the de-facto virus scanner on Linux, I stick with it and trust it, and now will cautiously consider the false positive thing more closely. I've also changed my scan script such that it doesn't look in directories where false positives are more prone.

* If any of you want to comment on this tutorial, or point to better ones on the web, please do so. I'm just sharing my current feeling of how to get this done, and how I do it on my own computer.

---

### Post by Mike'sHardLinux on 2006-12-11
> **wieman01 said:**
> Crackers, please, not hackers. Hackers create code & useful programs, crackers develop malicious software such as virii & worms. There is a distinct difference.

I wish more people were aware of this fact. I'm tired of people going around saying "nuculer" and bad-mouthing hackers! :rolleyes: Stupid media isn't helping, either. Ever since I read "The Hacker Ethic," I am proud of being a hacker! Lots of people are hackers and just don't call themselves that......doctors hack the human body, mechanics (gearheads) hack their cars, etc......

---

### Post by drphilngood on 2006-12-11
> **SuperMike said:**
> ...Sure, it would be nice to have a GUI front end for all this...

...and if you would like one, install clamtk.

```
sudo apt-get install clamtk
```

See here:
[ClamTK: A GUI front-end for ClamAV]("http://clamtk.sourceforge.net/")

---

### Post by hadiriazi on 2006-12-11
Ok, I installed clamAV but where did it go?? ](*,)

Never mind clamTK solved it :)

---

### Post by SuperMike on 2006-12-12
> **hadiriazi said:**
> Ok, I installed clamAV but where did it go?? ](*,)


When you install ClamAV, it goes into /usr/bin as:

/usr/bin/clamscan
/usr/bin/freshclam

You then have to add to your /etc/crontab some commands with the proper switches (do man clamscan to see what I mean) in order to make this work.

It doesn't really have a GUI on its own, but I see you got ClamTK and appear to be functional with that. Good.

---

### Post by Phototrek1 on 2006-12-12
Super mike really know's what he's talking about. Maybe he should make a (How  to) install and setup an anti-virus with a gui in the how to section. I still consider myself a new linux user. I know there are lot of new Ubuntu users out there and i was one of them.  Two months ago i took the plunge and sold my XP computer and now i'm exclusively using Ubuntu on an old computer. I have to say i went through culture shock but all is well. It just too LOTS of reading and 4 Ubuntu reinstalls!!

Thanks super mike.  :)

---

### Post by jonah1980 on 2006-12-12
well out of curiosity rather than the feel of a new danger upon us - installed aegis virus scanner from add/remove, ran a scan through and it found two infected windows files in my wine directory, so i blasted them away. seems a cool and simple virus scanner, version 0.2 looks really impressive but you'd have to get that from the website as it's not in add/remove.

it uses clam too...

---

### Post by pay on 2006-12-12
> **Mike'sHardLinux said:**
> I wish more people were aware of this fact. I'm tired of people going around saying "nuculer" and bad-mouthing hackers! :rolleyes: Stupid media isn't helping, either. Ever since I read "The Hacker Ethic," I am proud of being a hacker! Lots of people are hackers and just don't call themselves that......doctors hack the human body, mechanics (gearheads) hack their cars, etc......Sorry. I will use cracker now but I thought that they were called blackhat hackers, and using it the context that I used it in I would of assumed that you would realise that I was talking about blackhats. I have respect for white hats.

---

### Post by technodigifreak on 2006-12-12
> **SuperMike said:**
> Hey, sure, I can help. I hope I break it down enough for your level of "newbieness". :) 

I'll show you how to use something called ClamAV.

Mike, great tutorial.  You should definately repost that in the HOW-TO's/FAQ's category!

---

### Post by SuperMike on 2006-12-12
All: I feel the love. And it couldn't come at a better time. I was so [depressed]("http://www.nuxified.org/topic/quitting_job_soapbox") tonight!!!

Yeah, perhaps I can see what it takes to repost the ClamAV howto properly into the FAQ area.

---

### Post by SuperMike on 2006-12-12
> **technodigifreak said:**
> Mike, great tutorial.  You should definately repost that in the HOW-TO's/FAQ's category!

What's the best way to do that without being accused of double or cross posting? I don't want to break the forum's rules.

---

### Post by wieman01 on 2006-12-12
> **SuperMike said:**
> What's the best way to do that without being accused of double or cross posting? I don't want to break the forum's rules.
Cut & paste... Then post the link here. Don't be afraid to do that, we'll back you up for sure.

---

### Post by yabbadabbadont on 2006-12-12
Click the red stop sign button on your post and in the report box, ask a mod to move the post for you.

---

### Post by bodhi.zazen on 2006-12-13
Nice How-to SuperMike

**I added your How-to to the UDSF wiki.**

[How_to_ClamAV](http://doc.gwos.org/index.php/How_to_ClamAV)

---

### Post by IusedTObeSOMEONEelse on 2006-12-13
I thought the How-to thing was greatbut, I seem to have run into dependency from hell problems. Any one care to look this over and tell me what I'm doing wrong please? Thank you, :)  Sally                                              $ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav1
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav1
0 upgraded, 4 newly installed, 0 to remove and 28 not upgraded.
Need to get 7867kB of archives.
After unpacking 8765kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe libclamav1 0.88.6-1ubuntu1 [272kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe clamav-base 0.88.6-1ubuntu1 [176kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe clamav-freshclam 0.88.6-1ubuntu1 [7257kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe clamav 0.88.6-1ubuntu1 [163kB]                                             
Fetched 7867kB in 1m33s (84.1kB/s)                                                                                         
Preconfiguring packages ...
Selecting previously deselected package libclamav1.
(Reading database ... 147591 files and directories currently installed.)
Unpacking libclamav1 (from .../libclamav1_0.88.6-1ubuntu1_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.88.6-1ubuntu1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.88.6-1ubuntu1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.88.6-1ubuntu1_i386.deb) ...
Setting up libclamav1 (0.88.6-1ubuntu1) ...

Setting up clamav-base (0.88.6-1ubuntu1) ...
Adding system user `clamav' (UID 110) ...
Adding new group `clamav' (GID 118) ...
Adding new user `clamav' (UID 110) with group `clamav' ...
Not creating home directory `/var/lib/clamav'.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.88.6-1ubuntu1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wieman01 on 2006-12-13
Don't even bother to resolve them if you are using Feisty. As a test user you should be prepared for this sort of stuff. If not, rather use Dapper or Edgy...

---

### Post by IusedTObeSOMEONEelse on 2006-12-13
Never mind, got it ;)                        --------------------------------------
Scan started: Wed Dec 13 02:48:55 2006


-- summary --
Known viruses: 80788
Engine version: 0.88.6
Scanned directories: 529
Scanned files: 4409
Infected files: 0
Data scanned: 220.25 MB
Time: 453.959 sec (7 m 33 s)

---

### Post by revertex on 2006-12-17
common people, it doens't make sense at all.
at starti was lauguing, but now i'm concerned about this tread.

Please, pretty please stop spreading F.U.D.

Linux is unix based, not a windows in disguise.
Virus scanners for linux are intended for fileservers(samba/ftp/http) and mailservers that serve files for windows boxes.

It's almost impossible that you get infected by a win32/dos virus, even running wine.
Run some sort of antivirus in your workstation is a waste of time and eletricity.

if you are concerned about security, do the follow:

-install some rootkit scanner like rkhunter or chkrootkit (or both if you are paranoid).

-install a integrit checker like integrit or checksecurity (or both, don't hurt).

-install a intrusion detection system like aide, prelude or snort.

-install a firewall, if you find iptables hard to configure try shorewall or firestarter.

-audit your network for vulnerabilities, open ports and uneeded services, with tools like nessus.

-stop all services that you don't need and use a firewall.

-never use unsafe services like vnc open to the internet.

-if you are really paranoid, install a portknocker to access services like ssh from the internet to your box, and/or change the default ports.

-use strong passwords that expire until the end of this century, remember, weak passwords are the aquiles heel of every system, never use a "master password" for everything.
 
If memory don't serves you well, use a password manager to store different passwords for every account that you have.

-never install packages from untrusted/unknow sources, prefer the official repositories.
you are at risk of install a package with rootkit installing things from unknow sources.

needless to say that run bash scripts that you grab from the internet blindly is a huge security risk.

-install a http proxy filtering like privoxy to surf securely, you can use privoxy alone, or with squid, squidguard and/or tor.
if you feel unsafe keep javascript disabled at cost that lots of sites will not work properly anymore.

-install a mail system that recieve error logs from the above services, install logcheck to recieve all suspect logs.
don't forget to configure and test everything, just install isn't enougth.

-install bastille and/or harden-tools, but bear in mind that a paranoid level of security comes at cost that you can be trapped ouside or render your box useless.

linux users are much more prone to get a rootkit than a virus, then don't waste your time with old habits.

and finally, even do backups.

this cmd will generate a list off all packages that you have installed, it should be helpful in case you need to reinstall.
use a cron job to get  up-to-date list

dpkg --get-selections > all_packages_installed.log

please forgot my mistakes, i'm in need of some sleep.

cheers

---

### Post by Jason_25 on 2006-12-17
I didn't want to read the entire thread but it doesn't sound like you had a virus.  Just a misunderstanding or a bug.  Sorry you had a bad time.

---

### Post by tturrisi on 2006-12-17
FYI, afaik, you cannot get a virus, even on windows from a pdf file.  There are windows viruses that will infect pdf files but only IF the full blown acrobat pgm is installed, they cannot affect adobe reader.  It may be possible to get certain malware/spyware via scripting from a pdf file but only via the newer versions of adober reder & acrobat programs that have the ability to rebder embedded scripts, which can be disabled via the preferences menu.  I've yet to see such an exploit though, and if they exist, they are extremely rare.

I keep an updated av pgm on my windows computers, disabled and set to completely manual.  The only time I use it is to anymore is to scan clients' systems.  I can do w/out the personal need of av because I know what files I can safely open and what files I should delete as necessary.  Plus Norton Ghost will restore my xp systems in 4 minutes if I should ever do something stupid.  Also, I get all email as plain text.  I've been saying it for years, you cannot get a virus on your computer unless you execute the file that contains it.  On has to DO something first that then results in an infection.  What one DOES is the key to safe computing.  Ignorance and stupidity are the door to infected systems.

---

### Post by hikaricore on 2006-12-17
Why is this thread still alive?   Ohhh..... because someone wanted attention and got it, by posting in the GENERAL HELP FORUM where all the new ubuntu users could see it.

---

### Post by BLTicklemonster on 2006-12-18
Yes, it's still alive.

GNU/Linux rootkits: [http://linuxhelp.blogspot.com/2006/12/various-ways-of-detecting-rootkits-in.html](http://linuxhelp.blogspot.com/2006/12/various-ways-of-detecting-rootkits-in.html) 

eeek!!!


So um, yeah, be aware kids.

---

### Post by d3v1ant_0n3 on 2006-12-18
I remember reading [ THIS ](http://www.pcformat.co.uk/tips/default.asp?pagetypeid=2&articleid=38021&subsectionid=683&subsubsectionid=473) reply to a question in PC Format magazine a good long while ago, so I thought I'd dig it up...it actually concerns Windows, but the theory is still the same

> Imagine if there was a billion dollar industry dedicated to selling you hyenas to control the badgers in your garden. Imagine that, even though there are no badgers in your garden and never have been, these companies told you that you needed to have a snarling, vicious hyena patrolling your lawn in case one should ever appear. And not just one hyena either, imagine they told you to add another hyena every month to provide adequate protection. And imagine that the hyenas were bad-tempered, smelly, dug holes in the lawn and chewed on your leg whenever you stepped outside. Finally, imagine that your garden was surrounded by a high wall anyway and the only way for badgers to get in was for someone to post them to you in a conspicuous badger-shaped parcel that you could simply refuse to accept when the postman delivered it.

That would be a pretty weird sort of business model, wouldn't it? You wouldn't think that they would sell many hyenas.

---

### Post by SuperMike on 2006-12-19
As the original starter of this thread, I wish I could revoke it because I certainly don't want to spread FUD. However, in the process, I learned some things about false positives in ClamAV, how to overcome/minimize them, how most of the things detected are likely in virtual memory or browser cache or email and are intended for Windows, and someone asked me to write a howto on how to get ClamAV installed. I did and so the issue is closed, for me.

---

### Post by BLTicklemonster on 2006-12-19
> **SuperMike said:**
> As the original starter of this thread, I wish I could revoke it because I certainly don't want to spread FUD. However, in the process, I learned some things about false positives in ClamAV, how to overcome/minimize them, how most of the things detected are likely in virtual memory or browser cache or email and are intended for Windows, and someone asked me to write a howto on how to get ClamAV installed. I did and so the issue is closed, for me.

Okay, I did want to post on the problem with rootkits, and this seemed like a great place to put it.

I'll close the thread for you now. 
















no wait, I'm not an admin. Sorry. :-D

---

### Post by bodhi.zazen on 2006-12-19
Quality information is not spreading FUD

Discussions on security are not spreading FUD

---

### Post by aysiu on 2006-12-19
> **SuperMike said:**
> As the original starter of this thread, I wish I could revoke it because I certainly don't want to spread FUD. However, in the process, I learned some things about false positives in ClamAV, how to overcome/minimize them, how most of the things detected are likely in virtual memory or browser cache or email and are intended for Windows, and someone asked me to write a howto on how to get ClamAV installed. I did and so the issue is closed, for me.
I've retitled the thread to sound more like a support request, and I've also marked the thread as resolved.

---

### Post by hikaricore on 2006-12-19
> **d3v1ant_0n3 said:**
> I remember reading [ THIS ](http://www.pcformat.co.uk/tips/default.asp?pagetypeid=2&articleid=38021&subsectionid=683&subsubsectionid=473) reply to a question in PC Format magazine a good long while ago, so I thought I'd dig it up...it actually concerns Windows, but the theory is still the same

Hello good sir, I am interested in buying a hyena.  Will your hyena run on linux?  I've been told there are many linux based badgers being released into the wild lately.

ROFL

---

### Post by BLTicklemonster on 2006-12-19
Hey Bodhi! I'm glad you got those links in your sig, dude! Fluxbox and Icewm are cool windows managers!

---

### Post by bodhi.zazen on 2006-12-19
LOL BLTicklemonster :p

I'm glad to share the information.

[color=blue]Don't forget to thank **Lou**[/color]

---

### Post by weth on 2007-06-27
hi all,

I just installed Rkhunter and ran it.
While checking the system It said the following:

Please inspect:  /dev/.tmp-3-64 (block special (3/64))  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory)


What does it mean? How should I inspect it? Is there a threat to m y system?

thanks!

---

### Post by weth on 2007-06-28
I am really concerned about this issue and will be thankful if someone helps me interpret this message. 

Thank you!

---

### Post by BLTicklemonster on 2007-06-28
> crackers develop malicious software such as virii & worms.

Being from Georgia, I must say that I find this offensive.



























nah, just kidding.

---

### Post by iansane on 2007-09-21
The few people I know who use Ubuntu and convinced me to try it, (even one linux instructor) have said simply that linux doesn't and can't get viruses. I don't know enough to make a convincing argument but isn't it true that if someone takes the time to write one and you are connected to the internet you could get a virus just as easy on any OS if you aren't using AV protection and/or a firewall? Does Windows get more viruses because there are more people writing them for windows? What is it that makes linux systems more secure? I know 3 questions, but they are all related. Thanks

---

### Post by yabbadabbadont on 2007-09-21
> **iansane said:**
> The few people I know who use Ubuntu and convinced me to try it, (even one linux instructor) have said simply that linux doesn't and can't get viruses. I don't know enough to make a convincing argument but isn't it true that if someone takes the time to write one and you are connected to the internet you could get a virus just as easy on any OS if you aren't using AV protection and/or a firewall? Does Windows get more viruses because there are more people writing them for windows? What is it that makes linux systems more secure? I know 3 questions, but they are all related. Thanks

One of the moderators has done a nice write-up on this topic that you should read:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by iansane on 2007-09-21
thanks yabbadabbadont

---

### Post by bodhi.zazen on 2007-09-22
> **iansane said:**
> The few people I know who use Ubuntu and convinced me to try it, (even one linux instructor) have said simply that linux doesn't and can't get viruses. I don't know enough to make a convincing argument but isn't it true that if someone takes the time to write one and you are connected to the internet you could get a virus just as easy on any OS if you aren't using AV protection and/or a firewall? Does Windows get more viruses because there are more people writing them for windows? What is it that makes linux systems more secure? I know 3 questions, but they are all related. Thanks

Just a few comments if you will.

First i think you are lumping all crackers and malware into "viruses".

With that in mind, yes there are crackers out there and thus security is a never ending process.

There have been Linux viruses, but they do not propagate as you would find in other OS . Furthermore, the holes or flaws in the code they took advantage of have long been patched. So, at this time, there are no active Linux viruses. There is no need to run antivirus software to protect a Linux box and Linux antivirus packages screen primarily for windows viruses with the intention of protecting windows boxes. Linux antivirus is typically run on a Linux mail server serving windows clients for example.

The problem with closed source OS is that known security holes are not addressed in a timely fashion and known holes go unaddressed for years. This is not to say holes in the code are completely ignored, it is just that the service packs are few and far between and they do not address all know problems at the time of their release. Thus there is a whole industry of third party antivrus/antispyware to fill in those holes and using such software is a part of running closed source OS.

To follow up on "crackers", security on Linux is different then what you may be used to and the vulnerabilities are different. Yes there are crackers for linux, it is just that the open source community fills in holes as they are discovered, or at least more timely then closed source.

Stay up to date with your packages and security upgrades. If you run a server, know/learn how to secure it.

See this link for further information :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by iansane on 2007-09-22
Now that was a thorough answer. Much better than the arrogant ***were better than windows, just because*** attitude I since from some of the people I mentioned previously. When I ask them why Ubuntu doesn't get viruses there answer is "just because dude"

So thankyou for an intelligent answer. I have a lot more questions now but I'll wait and dump them all on the instructor in my network security class next quarter.

---

### Post by iansane on 2007-09-22
> **wieman01 said:**
> Don't even bother to resolve them if you are using Feisty. As a test user you should be prepared for this sort of stuff. If not, rather use Dapper or Edgy...

Nice to know now that I've installed fiesty. No body told me it was a beta. Thought it was the latest stable release. So I'm trying to learn on a test OS?

---

### Post by yabbadabbadont on 2007-09-22
> **iansane said:**
> Nice to know now that I've installed fiesty. No body told me it was a beta. Thought it was the latest stable release. So I'm trying to learn on a test OS?

Hey buddy, look at the date of that post you quoted....  ;)

---

### Post by iansane on 2007-09-22
oops. Can I be forgiven since I'm a newb? Sorry:)

---

### Post by yabbadabbadont on 2007-09-22
> **iansane said:**
> oops. Can I be forgiven since I'm a newb? Sorry:)

I suppose so.  After you've received your thirty lashes with a wet noodle though.  :lol:

---

### Post by SuperMike on 2007-12-16
Ubuntu by default has no open ports. If you install stuff to open the ports, especially without following up with an iptables firewall script, then this is a security hole, potentially, but note that Linux never runs services as root (except in a sandboxed environment) and some of the existing projects using sandboxed root environments are being overhauled to run under a separate account. Windows, on the other hand, runs most or almost all of its services as root-equivalent (LocalSystem).

Ubuntu by default never lets you become complete admin of the system without typing in your password again, ensuring that no script, popup window, or other virus or malware can run as root without first asking you for your password. By then, you can detect it. Windows, on the other hand, requires you to be local admin for many kinds of tasks.

The only way for a virus to get in is through an exploit, buffer overrun, or by submitting virus-laden code (maliciously or not) to the main package repository. These are maintained by keeping your system up to date and by a series of security hoops that a package must go through before it is permitted in the package repository.

So, can Linux catch a virus? No, not really. And the virus scanners for Linux do nothing but look at signature bytes for viruses that are Windows-based -- which is really only useful in preventing Windows viruses to be deployed to Windows workstations when a Linux server is used as a file or mail server.

Based on this, my virus scanner for Linux is now turned off.

---

### Post by Lostincyberspace on 2007-12-16
If you can login as root then you have no restraints at all no having to put in passwords. at least in Ubuntu. I haven't use others enough to know for sure though but what I have it has been the same.

---

### Post by bodhi.zazen on 2007-12-16
[QUOTE=SuperMike;3960551

Based on this, my virus scanner for Linux is now turned off.[/QUOTE]

It has been my experience that the more experienced Linux users come to similar conclusions. The primary use of antivirus on *nix is if you are either running a mail server or are wanting to protect windows computers on your network.

---

### Post by plantman on 2008-02-11
Has anyone used Secunia Security or know anything about it? I have used it on my Windows desktop. The website seems to have some issues with Linux - not sure.

---

