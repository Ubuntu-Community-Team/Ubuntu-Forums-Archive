---
title: "Constant Hacker Attacks On Newbie Need Help!"
date: 2007-07-20
forum: General Help
---

### Post by Blacksasnta on 2007-07-20
):P Hi All:oops:

Im am very new to ubuntu Feisty Dawn 7.04 only been using it for about a week and as all newbie`s I know nothing I have put on version 7.04 AMD_64 vmserver vmplayer and the latest version of wine I have had no help and had to learn many things and do a hell of alot of reading to get this far but first some back ground!

I used windows for over 15 yrs now and no it from version 3.0 to vista fairly well, but about 3 months ago I become constantly attack and hacked with every thing from dll injection Trojans root servers rerouting of my router and my msn journals where being read as well as any other file the perpetrator wish to view or replace or delete.
I tried all sorts of firewalls running 3 at a time and different A class virus scanners and constantly running root spy ware scanners trying to stop the attacks turning off all system resource that could be connected to by anything remote but im afraid there are just to many wholes in windows.

These attacks are constant and I had to basically reformat and start again every 2 days redoing the 2 machines I use and after 3 months of this I got sick of it and switched to Linux Ubuntu and began down loading it setting it up in hope of better protection!
I not an intruder or hacker but I did manage to get the server ip the attacks were coming from and its name but thats all!:(

Then last night I received an email from a person I suspected is behind it telling me to leave it alone im not that good!
I am assuming that he has discovered that im now using Linux and he is assuming im going to attack him which is not feasible as im am a newbie and dont know nothing about that I have switched over merely to get back online and use wine and get back to running my BF2142 Clan that im am the leader of before the attacks I was ranked 21st in Australia for Commanding but alas since I cant get online I have dropped well back.

My problem is I do not know where to go from here software wise as in firewall and setup the best virus scanner to use and how to set it up and any other software I should run!

I NEED SOME SERIOUS HELP PLEASE BEFORE HE TAKES THIS LINUX UBUNTU OS OUT
ANY ADVICE OR HELP WILL BE MOST APPRECIATED OR ANYTHING ANYONE CAN SUGGEST HOW TO GET THE PERPETRATOR OF MY CASE:cry:[-o<

PLEASE DONT HESITATE TO EMAIL ME I NEED HELP YESTERDAY    msn   [email]xj50mm@hotmail.com[/email]
Cheers:)

Blacksanta

Thanks sorry about the essay:redface:

---

### Post by HermanAB on 2007-07-20
First - relax.  Then make sure that you use long passwords.  I use 16 characters, semi-pronounceable. Finally, go to [www.tldp.org](www.tldp.org) and start reading.

Cheers,

Herman

---

### Post by Coelocanth on 2007-07-21
If you have this idiot's server IP and an e-mail from him as well (you did save it, yes?), then I'd say it's time to look into legal recourse about this.

---

### Post by Nythain on 2007-07-21
chances are the "hacker" is probably a bit concerned now that you are running linux, wich he/she more than likely knows little about.

i would relax a bit, follow the advice of using long passwords, and see where it goes from here. linux by default is pretty hard to break into from teh outside world...

you could research iptables, and other gui front ends for it. its ubuntu/linux's default firewall. be carefull how many ports you open up at a tme, and wich ones they are... if you are really being hacked i would halt all torrent connections, webservers you might be running, just about any popular server software that requires certain ports to be opend up.

chances are though, at this point in time, you will probably stop noticing much from this "hacker" for a plethora of reasons, ranging from a lack of linux knowledge, to linux's resilliance to worms, adware, spyware, virii, and trojans.

ps i second the legall action recommendation :)

---

### Post by bodhi.zazen on 2007-07-21
1. Install firestarter and deny his IP

2. Open your /etc/hosts.deny and add these lines :

> ALL:ALL EXCEPT localhost:DENY

ALL: <IP>

where <IP> is his IP

3. strong passwords

4. go to shieldsup and scan for open ports (you should not have any).

5. File a complaint/legal action.

---

### Post by ~~Tito~~ on 2007-07-21
Yea I had the same problem awhile back because a hacker kept on turning off my laptop and it would go on when I was doing something important. The person added 4gb of useless file names and links. USE LEGAL ACTION AND TRY HIM TO THE FULL EXTENT because thats just rude to do that and that person needs to have a life and use a long password for login and router settings page.

---

### Post by sparks0548 on 2007-07-21
I agree with the legal assistance.  I work as a Data Forensics specialist and Litigation Support Engineer, I will tell you first and foremost, whatever logs you have and any other electronic documentation keep it aside, burn it to disc....whatever you can do...SAVE IT.  You've probably already done this, and my think I am repeating what you have already done, but what is just as equally as important to the contents of your data is the META-DATA.  Any data about your data.  Dates, times, last access, modifications.  Anything and everything that can be extracted from the META-DATA will be used in court.  It dictates a timeline and ensures that you didn't just happen to put the information in the logs or emails or what have you.  RFC-822 for email messages requires mail systems to use certain tags when transmitting and rendering email objects.  By extracting those messages you will have enough information and timeline to better your case.

Rock ON.....Good Luck!!!:guitar:

---

### Post by rillip on 2007-07-21
Something nobody's mentioned yet, reset your router password. That will go a looong way.

Also, you're not likely to get BF2142 to run through Wine or anything. You may want to do some serious reading about setting up a Linux box as a proxy server for a new Windows machine, that way you add a layer of Linux between you and him, but still have Windows for your apps that you need it for.

Edit:

I might contact the IP owner (go to dnsstuff.com and do a reverse IP lookup, probably his ISP or a hosting provider) and complain, but I wouldn't bother with "legal" action.  A) no actual damges you can really claim from what's been posted here b) most likely get into international law c) very likely to end up suing some broke punk college kid.

---

### Post by Blacksasnta on 2007-07-21
=D> I wish to thank you all for so quickly coming to my aid I am a bit more relaxed now that I can take some courses of action:grin:
I will get straight onto your suggestions and protect my Linux Ubuntu Box I am deeply appreciative of your kind help and taking the time to respond!
Cheers:)
Thank you So Much All for answering my prayers:)

Blacksanta   [email]xj50mm@hotmail.com[/email]

---

### Post by itruck4fun on 2007-07-28
Rillip has posted the best advice in many regards although much of it other than the "take legal action" is good advice. If you have he his IP assuming it IS his IP file a complaint with his ISP. Close your open ports someone else suggested the site to go to for that and it is a very good site. grc.com and look for the link to check your systems security.

Change your routers password is another good piece of advice. 

If it persists... see if you can't get YOUR ip address changed or have YOUR isp investigate it

Change service providers is another option, although NOT the most convenient, and hide yourself behind a linux proxy as someone else suggested.... 

Someone is mad at you for being at the top of the list and wants to bring you down a few pegs.

keep your friends close... keep your enemies closer!

all good advice

---

### Post by nfox on 2007-08-07
If you are still using Ubuntu by now and you've made sure grc.com's shields up shows stealth, you can always have fun with his IP address. After setting up Peerguardian and such, try taking his IP and find out who it is with Whois. If you see something about wholesale internet lines you can expect the hacker is sitting on a heavy traffic line (you would usually see some person's info or a company's). I would then try to go to his IP ([http://whatever.his.ip.is](http://whatever.his.ip.is)) and see if you can connect. There's no harm since he already knows it. Some one might be tempted to even replace their broadcasted IP to his address and run a script to connect to a whole bunch of sites. That should eat his bandwidth up nicely. 
But getting even shouldn't be the goal, I would even suggest you might want to forward his IP to a nowhereland address. Google it up to check the specs but you can make his connections time out and if he is so apt to get into you os, look into honeypots. Very easy with linux and user-friendly with Ubuntu. He'll think he's found honey but... use your imagination. You can even check his OS/Browser by reading the headers and I bet he's on Winblows. With copious vulnerabilites at your disposal how would he feel if you could open up his hard drive to the world? These are all things you can definately offer as a reward for being such a pain. Remember, you don't have to do any of these but let him know you can and write back if you need any more help!

---

### Post by por100pre1 on 2007-08-07
> **Blacksasnta said:**
> PLEASE DONT HESITATE TO EMAIL ME I NEED HELP YESTERDAY    msn... 

Not a good idea to post your e-mail address just like that. IMHO you should remove it. :)

---

### Post by Immolatus on 2007-08-07
learn to build an ip firewall.

---

### Post by Ergo on 2007-08-07
I am having the same problem, but mine is with Ubuntu.  Someone has tried to access all of my personal accounts (websites, banks, school, etc.).  I noticed this when I tried to access my bank account and the bank informed me that someone from a strange IP address tried to access my accounts, so they froze it.  I got all of that straight, changed my passwords, and 2 weeks later it happened again.  I think someone is getting my information from me when I use my laptop at home.  How do I check for this.  Do they have a script running on my machine, or are they able to access my information through the internet (my house is wi-fi).  I dropped to the command line and found DHCP running when I typed in "ps aux".  I also find that firefox has other background instances that I can not access.  When I try to close my firefox window the other instances close as well.  Anyway, someone is stealing my information, ALL of it.  I have to stop it.  Please give me a clue.

---

### Post by zero244 on 2007-08-07
This nightmare almost sounds like a poster hoax.
If this is a true story I am sorry your having these problems.
I dont think I have heard of a personal case this severe.
If the hacker was using the victims machine wouldn't the the password box come up and alert you that something fishy is trying to happen.
I could see this happening on a Windows box, but it seems unlikely this would happen on a Ubuntu box.
Hope you get it fixed up.

---

### Post by whatrucrazy on 2007-08-07
if this is the case, and i say if, do a fresh install, change your passwords to something strong (upper and lower case, numbers and symbols, at least 10 characters), change your router password, and if you don't know much about wireless encryption just connect via ethernet cable. done. check at shields-up if you're worried, but you should be very unlikely to get into trouble now unless you're doing something out of the ordinary.


> **Ergo said:**
> I am having the same problem, but mine is with Ubuntu.  Someone has tried to access all of my personal accounts (websites, banks, school, etc.).  I noticed this when I tried to access my bank account and the bank informed me that someone from a strange IP address tried to access my accounts, so they froze it.  I got all of that straight, changed my passwords, and 2 weeks later it happened again.  I think someone is getting my information from me when I use my laptop at home.  How do I check for this.  Do they have a script running on my machine, or are they able to access my information through the internet (my house is wi-fi).  I dropped to the command line and found DHCP running when I typed in "ps aux".  I also find that firefox has other background instances that I can not access.  When I try to close my firefox window the other instances close as well.  Anyway, someone is stealing my information, ALL of it.  I have to stop it.  Please give me a clue.

---

### Post by Ergo on 2007-08-08
I can understand your point of view, but I assure you the problems I am having is for real.  This is no hoax (they got into ebay as well).  (I hate MS with a passion.)  But I am confused, I am running linux to prevent this sort of thing.  Can attacks like this happen in linux or have I missed something along the way.  I have always been under the impression linux's security was designed to save me from myself.

---

### Post by kevinlyfellow on 2007-08-08
> **Ergo said:**
> I can understand your point of view, but I assure you the problems I am having is for real.  This is no hoax (they got into ebay as well).  (I hate MS with a passion.)  But I am confused, I am running linux to prevent this sort of thing.  Can attacks like this happen in linux or have I missed something along the way.  I have always been under the impression linux's security was designed to save me from myself.

Have you since changed the passwords on all your internet accounts?  I wouldn't access these sites from your computer at least for a little while.  Again take all of the advice on this thread and if you do believe that someone has installed something on you machine, abandon all of config files (keep your needed data) and make a new user account for yourself.  Change your passwords (for websites and your user account) to something that was randomly generated.  [http://www.pctools.com/guides/password/](http://www.pctools.com/guides/password/)

---

### Post by whatrucrazy on 2007-08-10
as far as i know, given that i am neither a security expert or a coder, it could happen. unlike windoze though you would need to give the program specific permission to install itself on your system (perhaps even give it root access). this may happen when installing closed source code, or any random stuff you just happen to find on the net. a bad idea in any OS.
now if that is the case you don't really have much of an option other than re-installing, changing all of your passwords, your computer, to accounts you may have accessed over the net and even your router.
once this is done you should be fine, just don't install software from anywhere other than the approved repositories and read up a bit on wireless encrytion.

luck.

> **Ergo said:**
> I can understand your point of view, but I assure you the problems I am having is for real.  This is no hoax (they got into ebay as well).  (I hate MS with a passion.)  But I am confused, I am running linux to prevent this sort of thing.  Can attacks like this happen in linux or have I missed something along the way.  I have always been under the impression linux's security was designed to save me from myself.

---

