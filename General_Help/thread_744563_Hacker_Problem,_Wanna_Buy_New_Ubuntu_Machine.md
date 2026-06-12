---
title: "Hacker Problem, Wanna Buy New Ubuntu Machine"
date: 2008-04-03
forum: General Help
---

### Post by OrcaWave on 2008-04-03
I put this in the *Security Section* of the forum too. Thanks.


Help With Hacker, Wanna Buy New Ubuntu 
This is a VERY long story.

I'll try to keep it short though.

I've had a hacker stalk me for a long time here on the net.

Short story.....I got him fired for putting some of my private medical information on the net.

He worked as the main CT (computer tech) for the hospital where I was a patient.

When the hospital looked, they found that he was not only hacking patient records, but was running a pornography spamming ring with THEIR COMPUTERS!

Our ISP (Mediacom High Speed Internet) even admits that we're hacked (he's using THEIR computers) but refuses to act "because we don't get involved in personal vendetta's".

I've been to the FBI, who surprisingly, knew all about this socio-path, but does not got involved in personal cases (only unless one has a BUSINESS and has been hacked for over $10,000.00 in damages),

After being astounded that the FBI already knew all about him here's what else has happened to us.

After going through six Windows computers, and all of them falling like weeds under a lawnmower, we bought a Mac....it took him NINE MONTHS to learn his way around a Mac, and then he found a back door in our I-Mac G-5, through I-Chat, and Dashboard.

We were using OS X Tiger when this happened. I've heard it all about "Macs CAN'T be hacked", so please don't tell me THAT. It's JUST NOT TRUE.

I'm thinking of switching to a System 76 Ubuntu machine.

But I have questions.

After talking with Tom at System 76 this morning, and telling him our story he said (basically) "I don't know if Ubuntu can do anymore for you than a Mac could do, Mac use's a Linux kernal (I THINK that's what he called it)".

We are using an 'Alpha Shield' external firewall ( [www.alphashield.com](www.alphashield.com) ) and I had ALL of our Mac locked down tight, and NO sharing applications were turned on.

But the Mac firewall WAS ON! And this guy is so "good", he still managed to find some 'backdoor' into I-Chat and Dashboard.

HOW do I go about super securing a brand new System 76 Ubuntu computer?

I'm thinking of trying THIS wireless router, it's got a double firewall in it:



[http://www.tigerdirect.com/applicati...0079&CatId=373](http://www.tigerdirect.com/applicati...0079&CatId=373)




But there MUST be MORE that I can do yet.

I've heard from reliable sources that Ubuntu is coming out with a firewall in their next update on April 24th, 2008.

Will this be a GOOD and strong firewall, do you think?

A Mac comes with reformat disc, what if you need to wipe the hard drive clean on a Ubuntu machine, can you burn a Ubuntu disc, and use it in the same way that you can in a MacIntosh?

That is, to wipe the hard drive, and to reformat the computer?

Can you please tell me that there is some way to really LOCK DOWN a Ubuntu machine, to where NO ONE can get through it, or is Tom right, and eventually this guy will be able to get through no matter WHAT I DO for security?

If you decide to write back could you please not use 'computerese' and please just say it in plain English (if that's possible, I mean)? Thanks.

I REALLY want to try Ubuntu, and one more thing.

This hacker cuts through Mozilla Firefox like hot butter, so is there another browser to use with Ubuntu that's SAFE do you think?

I'm VERY discouraged from what I heard from System 76 this AM, can you guys help me PLEASE?

Here's the computer that we plan on buying:


Graphics: Intel 950 Graphics Media Accelerator

Sound: Realtek ALC 662 4 Channel Audio

Processor: Core 2 Duo E6420 2.13 GHz FSB 1066 MHz L2 4 MB

Memory: 2 GB - 2 x 1 GB DDR2 667 MHz

Hard Drive: 250 GB SATA 300 Mbps - 7200 RPM 8 MB Buffer

Ottical Drive: First CD - RW / DVD 

Second Optical Drive: CD - RW / DVD

Wireless: 802. 11 bg

Thank you so very much! Orca Wave

---

### Post by pseudo-random on 2008-04-03
Before we even get into the technical stuff...
I take it you know this guy since you know where he works?!?
If the feds aren't interested then don't be surprised. They've proved themselves to be crap usually.
Take a baseball bat to his legs, or get a friend to do it. Make sure there's no witnesses and just deny it when he squeals to the police. It's your word against his, they'll throw it out.
Then install ubuntu. :)

---

### Post by heartburnkid on 2008-04-03
OK, first thing you should do is change ISPs.

Second, set up a **wired** router that has Network Address Translation (practically every one on the market does).  Don't do wireless; wireless security is a joke.

If this guy's such a super-hacker with a super-grudge as you claim, I doubt any OS is going to keep him off of you for long.  No OS is hack-proof to the determined hacker, and anybody who'd say otherwise is either arrogant or ignorant (and most Mac fanboys are both).  A Linux OS such as Ubuntu is more secure than Vista or OSX (which uses a BSD kernel, not a Linux kernel), but it's not a panacea.  It does help that Ubuntu exposes no ports to the outside world by default.  As well, the two apps you mentioned him exploiting (iChat and Dashboard) simply don't exist on Linux.  But don't be fooled into thinking that this will keep him out forever.

Also, keep in mind that most hacks are accomplished through social engineering.  Think very carefully before accepting email attachments, etc. and never give anybody any password for any reason, no matter who they say they are.

---

### Post by Cappy on 2008-04-03
iChat has remote login built-in which was a huge problem for you. You should not be running VNC, SSH, Telnet, Apache, or any other services that will allow connections from outside your network. You should be running a software firewall such as Firestarter.

Use Firefox with noscript if this actually is a problem. More importantly, practice safe browsing habits such as not following suspicious links.

This is not a "genius" hacker, it's just a normal person who is exploiting the doors that are left open.

---

### Post by OrcaWave on 2008-04-03
Cappy,

    You said:  "You should not be running VNC, SSH, Telnet, Apache, or any other services that will allow connections from outside your network."

I KNOW what Telnet IS, could you please explain the other things that you mentioned here.....what they are exactly?

And HOW do you block them OFF on Ubuntu?

Thanks, Orca Wave

---

### Post by Cappy on 2008-04-03
They are services you can run so that you can access your computer from other computers. They do not come enabled by default and you should not enable them. VNC comes installed but not enabled. It is **VERY** easy to "hack" so in your case NEVER install VNC (unless you restricted it to only be able to connect to your localcomputer and would tunnel it over SSH. This is more advanced and you would need to search for a tutorial). It is at System-->Preferences-->Remote Desktop in Gutsy.

Apache is a webserver. It would be okay if you kept it and all sotware on it up to date. E.g. Outdated forum or Content Management software is a common problem.

SSH is similar to telnet but secure. If you ever want to run SSH you would run it with a shared key: [http://ammonlauritzen.com/blog/index.php/2006/04/16/shared_key_ssh_authentication](http://ammonlauritzen.com/blog/index.php/2006/04/16/shared_key_ssh_authentication)
Just don't use SSH with just a password authentication.

There is no substitute for Googling still. Googling "Secure ubuntu" comes up with some useful links such as [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/) which could be a good starter checklist.

---

### Post by Crafty Kisses on 2008-04-03
Get a new ISP, but if this Hacker is stalking you and putting your personal information on the internet, I'd think about reporting him.

---

### Post by Cappy on 2008-04-03
> **Codename said:**
> Get a new ISP, but if this Hacker is stalking you and putting your personal information on the internet, I'd think about reporting him.

The ISP has nothing to do with it. The only thing changing the ISP would do would be to change the IP which you can do _anyway_. If it is a home router it can be done very easily by going in to the router web config, releasing the IP, turning it off, waiting overnight, reconnecting it. This only works if your ISP uses DHCP to request an IP (most do).
Otherwise, you can call the ISP and they would be able to help.

---

### Post by Crafty Kisses on 2008-04-03
> **Cappy said:**
> The ISP has nothing to do with it. The only thing changing the ISP would do would be to change the IP which you can do _anyway_. If it is a home router it can be done very easily by going in to the router web config, releasing the IP, turning it off, waiting overnight, reconnecting it. This only works if your ISP uses DHCP to request an IP (most do).
Otherwise, you can call the ISP and they would be able to help.

Yeah, I guess, but it sounds like a shady situation.

---

### Post by jflaker on 2008-04-03
If this person is accessing medical information without authorization and/or your approval and then also PUBLISHING your medical information without your WRITTEN PERMISSION, this "Hacker" is in violation if HIPAA rules and you may sue and the person may serve jail time for his actions.

[http://www.hhs.gov/ocr/privacysummary.pdf]("http://www.hhs.gov/ocr/privacysummary.pdf")

Of course, this is a US law and if you are outside of the US, your local laws may or may not have a similar counterpart.

Anyway.  You can stop this person by calling yourstate's  attorney general (again,USA).

---

### Post by Crafty Kisses on 2008-04-03
> **jflaker said:**
> If this person is accessing medical information without authorization and/or your approval and then also PUBLISHING your medical information without your WRITTEN PERMISSION, this "Hacker" is in violation if HIPAA rules and you may sue and the person may serve jail time for his actions.

[http://www.hhs.gov/ocr/privacysummary.pdf]("http://www.hhs.gov/ocr/privacysummary.pdf")

Of course, this is a US law and if you are outside of the US, your local laws may or may not have a similar counterpart.

Anyway.  You can stop this person by calling yourstate's  attorney general (again,USA).

Yeah, I was thinking he could possibly sue, but I wasn't sure.

---

### Post by jflaker on 2008-04-03
No, You can definitely sue should all the evidence show it was in fact your hacker......

Contact an attorney and be prepared to follow through.........

---

### Post by Crafty Kisses on 2008-04-03
> **jflaker said:**
> No, You can definitely sue should all the evidence show it was in fact your hacker......

Contact an attorney and be prepared to follow through.........

I would imagine you'd get something out of it. I mean if he is posting your information online.

---

### Post by OrcaWave on 2008-04-03
OK, knowing all of this, if it was YOU, would you STILL purchase a Ubuntu machine?

And if I could NOT use Mozilla, what OTHER browsers work on Ubuntu?

AND, how hard is it to refomat a Ubuntu machine?

Thanks,  Orca Wave

---

### Post by heartburnkid on 2008-04-04
You... haven't been listening at all, have you?

Changing OS's isn't the end-all and be-all here.  You need to take more severe countermeasures, as well as take more proactive measures as many other people in this thread have discussed.  Just using a different OS and a different browser isn't going to do jack ****.

You can throw up as many roadblocks at this guy as you want, but determination wins out in the end unless you get his *** put in jail and/or something more drastic.  And until then, you need to get yourself educated about computer security, rather than just sitting here thinking, "Hmmm... maybe if I switched to Ubuntu and used nothing but Pidgin and Ephiphany..." because those have holes too.  Every program does.  And the biggest hole is the one sitting in front of the keyboard, staring at the monitor.

That said, I'd definitely choose an Ubuntu machine; it's a more secure OS.  But be aware that it's not going to keep you super-ultra-safe just because it's Linux.  YOU need to play the larger part.

---

### Post by c1rcu17 on 2008-04-04
It hasn't been said yet, so I'm just gonna put it out there. It is definitely a good idea to be changing your passwords up every month or so. Find a good random (preferably offline) password generator, and use that (check firefox addons). Try to include characters of multiple cases (iIeEaA) symbols (!@#$%) and numbers. Use different passwords for everything. Critical accounts (banks etc.) need a completely different password of their own. ***Don't store any passwords online*** anywhere. Also, if you can, dump the account names that you are using now. If you can afford to, create a totally new online personality (if your really that paranoid). Do your absolute best to not have any information linking those accounts back to you (use fake names, addresses etc.) Like every has said, your best defense is to practice safe browsing. The latest firefox with the noscript addon is a great tool. Use this pdf as a great guide to hardening your Ubuntu OS. [http://www.infosec.org.uk/media/archive1/papers/Securing_&_Hardening_Linux_v1.0.pdf](http://www.infosec.org.uk/media/archive1/papers/Securing_&_Hardening_Linux_v1.0.pdf)
Also, sue his a**.

Cheers

---

### Post by OrcaWave on 2008-04-04
> **heartburnkid said:**
> You... haven't been listening at all, have you?

Changing OS's isn't the end-all and be-all here.  You need to take more severe countermeasures, as well as take more proactive measures as many other people in this thread have discussed.  Just using a different OS and a different browser isn't going to do jack ****.

You can throw up as many roadblocks at this guy as you want, but determination wins out in the end unless you get his *** put in jail and/or something more drastic.  And until then, you need to get yourself educated about computer security, rather than just sitting here thinking, "Hmmm... maybe if I switched to Ubuntu and used nothing but Pidgin and Ephiphany..." because those have holes too.  Every program does.  And the biggest hole is the one sitting in front of the keyboard, staring at the monitor.

That said, I'd definitely choose an Ubuntu machine; it's a more secure OS.  But be aware that it's not going to keep you super-ultra-safe just because it's Linux.  YOU need to play the larger part.


Dear Heartburn Kid,

    YES, I've heard (and READ) everything here.

But you know what, it comes down to we've lost around $4,000.00 so far, do I wanna invest another THOUSAND or so dollars, OR NOT.

I understand MOST of this security depends on ME.

I'm not real computer saavy, but I figured out a Mac in about 2 or 3 months, and it seems like Ubuntu works a lot like a Mac (no offense intended).

They don't call it "social engineering" for NOTHING. I understand this TOO.

I'm just trying to make the RIGHT DECISION about money, BEFORE I spend a lot more of it.

Do you understand this?  Thanks a lot for your help!   Orca Wave

---

### Post by s3a on 2008-04-04
_A Question to Others:_Wouldn't sudo and firestarter protect him/her from all his/her being hacked problems?

_Information to the one experiencing the problem (OrcaWave):_
Sudo=application that is installed by default that forces you to put password on everything you do.

Firestarter=Firewall

---

### Post by OrcaWave on 2008-04-04
> **s3a said:**
> _A Question to Others:_Wouldn't sudo and firestarter protect him/her from all his/her being hacked problems?

_Information to the one experiencing the problem (OrcaWave):_
Sudo=application that is installed by default that forces you to put password on everything you do.

Firestarter=Firewall


According to another Tech at 'System 76' (where we plan on buying our computer probably) on April 24th, 2008, a firewall will come on ALL the computers that they sell, and these are ALL Ubuntu Computers.

I'm assuming that it will be 'Firestarter', but I'm NOT sure.

Can you please tell me MORE about 'Sudo'?

Thank you,  Orca Wave (I'm a guy by the way)

---

### Post by ensou on 2008-04-04
Sudo is not a program. It's essentially a built-in mechanism that forces you to input a password before making changes/doing certain things.

For example, you want to run a command in terminal (like command prompt). If it's installing something, writing something, moving something, etc. you have to type 
>sudo [password] apt-get install....
or the command without at pwd and it will ask you for one.

Easy stuff, really. But useful too.

I've had to privatise myself once before too. What I did was - changed ISP, thus getting new IP, host name, etc. Then I added a router in there, and a firewall. That SHOULD be enough, unless this person is REALLY stalking you, in which case that is a criminal offense and could go to jail for it. Why not go see your local police? See an attorney. I live in Canada, which means that for us, this stuff is really easy to do (charging someone, that is) I don't know where you live, but I'd give it a try. Given everything you've said so far, it would be really easy for you to win. Don't go see the FBI - they couldn't care less. If the guy's not a terrorist, then too bad.

---

### Post by ed-koala on 2008-04-04
One thing no one thought to ask, but can help a lot ... what are you doing most of the time with your computer???  If you are not online much, just turn off the modem.  Nothing is more secure from outside hacks than no service at all.

Another thing to do is encrypt the data on your PC.  Even if someone gets the file, if you use secure encryption, it's useless to them.

And, here's a final thought ... you are NOT spending money for an Ubuntu machine.  If you think your PC is fine and the OS isn't, Ubuntu is free, just download (or in your case, I'd order a CD).  You pay nothing to try this on your current equipment, no reason to buy a new machine unless you wanted to upgrade anyway.  (I'd do away with wireless tho if at all possible, it's a big weakness).

Try running Ubuntu from a Live CD to make sure all your equipment works before installing it, and with the security tips everyone gave you, you should be as safe as it's possible to be online.

---

### Post by alexforcefive on 2008-04-04
This story is pretty crazy, man. How does this guy keep finding you in the ether of the internet? If what you're saying is true, this guy either has physical access to your computer, or you're on an unsecured wireless network and he's camping outside your house. Either of those cases are very serious crimes, and the police should be involved.

If he's not literally on your property, and he's still gaining access to your computer, then you are making some grave mistakes in regards to your personal security and no OS is going to help that. Your ISP should have some information about keeping yourself safe online (i.e. don't open email attachments, don't click random links, etc) and if not, there is information available online, or you could even take a night class in computing.

PS whatever you do, don't spend more money on a new computer if you have seven computers lying around your house

---

### Post by MountainX on 2008-04-04
It sounds to me like you are going to have to invest in yourself -- to educate yourself more about computer security.

While you are educating yourself, consider these (possibly short term) solutions:
1. disconnect from the Internet when you don't need it. If you have just one computer, simply unplug the cable that connects it to your broadband modem. Severely limit your time online. Do not leave your computer connected to the Internet when you are not using it. (And as was already mentioned, don't use a wireless network.)

2. use a product like TrueCrypt. Put all your important personal stuff in an encrypted partition and mount it (ie, make it visible and accessible) only when you need to access that info. When finished, unmount it. If someone gets access into your computer, they will not be able to see your personal info if the TrueCrypt partition is unmounted. Use a very strong password.

3. spend some money for a consultant. Hire someone to help secure your system. Don't rely totally on the reseller. When I first started using Ubuntu I paid someone for 3 hours of their time to help secure my system (a web server). It was money well spent. I'll give you the guy's name if you want it.

If you are running Ubuntu and you don't install the extra apps people already mentioned, and you do the steps above and are religious about it, I can't see anyone getting your data.

After you have been doing this for a while, your stalking will probably get frustrated and move on. Let's hope so anyway :)

---

### Post by skydiver|goose on 2008-04-04
have you talked to an attorney about this guy?

I know from experience you can have restraining orders put on him from stalking, then once he violates it by calling you once, you can have him federally prosecuted. any attorney with half a brain will push it, even if he IS witness-protection.

---

### Post by badfish591 on 2008-04-04
Ubuntu is definately a more secure alternative than both windows or mac. Here is a link to the final day report of a  hacking compitition with a macbook, a vista, and an ubuntu system and the ubuntu system was the only one that wasn't hacked.   [http://dvlabs.tippingpoint.com/blog/2008/03/28/pwn-to-own-final-day-and-wrap-up]("http://dvlabs.tippingpoint.com/blog/2008/03/28/pwn-to-own-final-day-and-wrap-up")
of cousre that doesn't mean it isn't possible, just more secure than the others.
that being said, i totally agree with the first post.Iif this guy is causing you upwards of 4,000 dollars in loss, AND putting you through all the mental ******** too, he deserves a good o' fashioned *** whuppin. I feel the baseball bat approch would work nicely, but dont let this guy terrorise you and force you to spend more and more money. Even if you get an ubuntu system and end up being safe, he has still won. He may be a tough guy behind a computer screen but i assure you things will change when you shatter a kneecap on this douche.

 just remember.

new computers and other hardware = $4000

700 mile plane ticket = couple hundred bucks

seeing this guy regret every second of this crap as you knock his teeth down his throat = priceless

---

### Post by Cannaregio on 2008-04-05
(CrossPosted on both the threads this guy started)

Back to your original questions.
Maybe you should just stop posting kilometers about "your" hacker. 
Your questions are relevant on these forums only insomuch as they apply to [COLOR="Blue"]every[/COLOR] hacking attempt, not just one private case.
And, frankly, you shouldn't use all those uppercase crap either: no need to shout.

> **OrcaWave said:**
> But there MUST be MORE that I can do yet.

There's: read, study and in a couple of months you'll hopefully begin to understand some basic security.

> **OrcaWave said:**
> I've heard from reliable sources that Ubuntu is coming out with a firewall in their next update on April 24th, 2008.

Will this be a GOOD and strong firewall, do you think?

Not particularly "GOOD" nor particularly "strong" (nor your sources seem particularly "reliable"). A firewall is no automatic guarantee anyway. 
Much more important is, for instance, your knowledge in how to manipulate the host file or the [iptables]("https://help.ubuntu.com/community/IptablesHowTo"), duh.

> **OrcaWave said:**
> A Mac comes with reformat disc, what if you need to wipe the hard drive clean on a Ubuntu machine, can you burn a Ubuntu disc, and use it in the same way that you can in a MacIntosh?
That is, to wipe the hard drive, and to reformat the computer?

Macs and GNU/Linux are different beasts, and reformatting isn't necessary, unless you are using toy systems like windows and are at the same time a complete newbee (which you wont do/be either, if you read and study long enough, see above most of the answers to your extremely long postings). "Can you buy an Ubuntu disk?". Your need to study is immense.

> **OrcaWave said:**
> Can you please tell me that there is some way to really LOCK DOWN a Ubuntu machine, to where NO ONE can get through it, or is Tom right, and eventually this guy will be able to get through no matter WHAT I DO for security?

It depends. Short answer is no. In fact I would say he will surely be able to get through, no matter behin which OS you'll hyde, since, as stated,  knowledge and hence defence capacities are inversely proportional to paranoia, yet you do seem to enjoy the latter most.

> **OrcaWave said:**
> I REALLY want to try Ubuntu

Be REALLY our guest, and go ahead if this is true. But my impression is that you just want to speak loudly about your hacker.

---

### Post by steveneddy on 2008-04-05
You have thought about a lawyer, right?

If you know he is doing it, get a good lawyer and take everything but his underwear.

And why don't you try shutting down the router, PC's and DSL/Cable modem at night, and maybe only using a Live CD to use the PC for a couple of months.

Change your e-mail address.

Move.

Change all of your passwords on your online bill pay sites and start over.

Don't forget, sue the pants off of this guy.

---

### Post by yssida on 2008-04-05
I have found Ubuntu to be very secure myself...

Still, if this guy manages to break in, I'd bet 100% the developers would be very happy to know about it. They are always trying to make improvements, and security is one area of concern, though Linux users can get a bit complacent about security, yours doesn't seem to  be the case. File a report of the loophole in launchpad or to the relevant developers of the program concerned, in case he does.

Second, Ubuntu is free. Free as in Speech, but also like free beer! You can easily download it off the net, or if you don't want the cracker to know you're moving to Ubuntu, you can ask someone else to download it for you. Better yet, create a temporary email, create a launchpad account and order/request free Ubuntu CD's and do it at a public access area, or ask someone whom that hacker doesn't know to kindly do it for you.The CD is given for free and you only have to pay for postage, I'm in faraway Philippines and paid **nothing** even postage. In two to four weeks, you'll have an Ubuntu CD..Install it into one of your computers, come back here so the community can help you, and practice caution. No need to buy another expensive computer with all the hardware.....

Just my two cents...

---

### Post by stalkingwolf on 2008-04-05
If a teenager can hack into Government computers any system can be hacked given enough time
and the desire to do so.

A musket ball or load of 00 buck should do the trick.

---

### Post by MountainX on 2008-04-05
> **Cannaregio said:**
> 
Be REALLY our guest, and go ahead if this is true. But my impression is that you just want to speak loudly about your hacker.

Cannaregio - wise points. Both of them. Of course we would like to help the OP with Ubuntu, but the OP should take a good hard look at your other point too, for his own good.

---

### Post by OrcaWave on 2008-04-05
> **yssida said:**
> I have found Ubuntu to be very secure myself...

Still, if this guy manages to break in, I'd bet 100% the developers would be very happy to know about it. They are always trying to make improvements, and security is one area of concern, though Linux users can get a bit complacent about security, yours doesn't seem to  be the case. File a report of the loophole in launchpad or to the relevant developers of the program concerned, in case he does.

Second, Ubuntu is free. Free as in Speech, but also like free beer! You can easily download it off the net, or if you don't want the cracker to know you're moving to Ubuntu, you can ask someone else to download it for you. Better yet, create a temporary email, create a launchpad account and order/request free Ubuntu CD's and do it at a public access area, or ask someone whom that hacker doesn't know to kindly do it for you.The CD is given for free and you only have to pay for postage, I'm in faraway Philippines and paid **nothing** even postage. In two to four weeks, you'll have an Ubuntu CD..Install it into one of your computers, come back here so the community can help you, and practice caution. No need to buy another expensive computer with all the hardware.....

Just my two cents...

Can you please tell me just where to get the free Ubuntu disc?

Thanks, OW

---

### Post by OrcaWave on 2008-04-05
Ok, let me tell you what I have learned.

I'm responsible for the security of whatever OS that I use.

Ubuntu, Mac...whatever.

After all of these posts, I've finally figured that out.

Yes, all that I've had as "a weapon" is free speech.

Or 'free press', as the case may be. The Russian's understoood this in the days of Communism, why don't *you*?

David can't stop me from posting about his nefarious activities.

Do I "enjoy" this? Not really. But I *can see* how it might look that way.

Do I think that there is "a spiritual side" to this......"Why do I need this in my life" I think the quote was.

Yes, I'm a firm believer that there's way more than we see with just our physical eyes.

Did I "draw" this to me somehow.........Richard Bach, in his great book 'Illusions', might have 'Donald Shimoda' ask me.

Yes, maybe I did.

I've not totally finished processing just *why* yet.

Have I gone to a good counselor about this?

Yes. Several times. And yes, I was believed as to this being true.

Look, here's the bottom line. 

I know a sure proof way to put this man into prison, but it involves my wife's work computer which she has at home.

Until she will allow me to go to the hospital who she works for, all I can change is *my own computer*.

She's *my wife* and unless she says "Yes, go and talk to them", I can't act on my own.

So, you've all helped me alot, and now it's time for me to help *myself*.

I always thought:

"Well, this piece of hardware will fix it." Or, "If I have this kind of computer it will fix the problem".

But that's not the solution at all, the solution is get up off my butt, and really learn computer security, from the ground up.

Is that scary? Yeah, kind of.

Might it be worth it in the end?

Absolutely!

To those who have not believed. Someday it could happen to *you*.

To the rest of you, thank you so much for being strong with me. I *really* appreciate it!

I needed it, and I didn't even know that I needed it!

That's kind of sad isn't it?

I've been so involved in this for so long, that I actually never really understood what I really needed to do. The main thing (learning computer security from the ground, up), I mean.

Thanks for showing me that.

And I will rent "The Secret', movie tonight. thanks.

Bless you all, Orca Wave

---

### Post by russo.mic on 2008-04-05
Just throwing this out there, but you could pretty easily install Ubuntu on your Mac,

Also, it's not accurate to say that a mac uses a Linux kernel, there both unix like operating systems, but there are enough differences to make them pretty different.

no computer system is fullproof, just as with anything in life, but I can tell you that it's fairly accepted that linux is very secure when used the correct way.

[http://www.allheadlinenews.com/articles/7010483023](http://www.allheadlinenews.com/articles/7010483023)

here is an article about this very thing.

---

### Post by Lolicon on 2008-04-05
I would change the ISP to one with a dynamic address.

---

### Post by MountainX on 2008-04-05
> **OrcaWave said:**
> Ok, let me tell you what I have learned.

I'm responsible for the security of whatever OS that I use.


I read your whole post. I think you are on the right track.

---

### Post by Crafty Kisses on 2008-04-09
No offense, this story just doesn't sound right. I mean I know determination and all this could be the cause of this Hacker finding you over and over again, but there's something you must be doing, because if this guy is finding backdoors through iChat that's insane. If I were you, try the Ubuntu machine, start over.

I just don't see how this Hacker is finding you over and over again. Remember Social Engineering could be the cause in this one, because I think after everything you've done, and he's still found you, I mean again it could be determination and all that, but I'm pretty sure it's the user.

You've also mention he Hacked a couple of e-mail accounts you had. That probably means you either got phished, or you had a really bad password and he cracked it with a Bruteforce attack not that hard to do, remember make a strong password with symbols and numbers in it and don't tell your password to anyone, also if you see a suspicious link and you click on it and it looks like your email client's website, don't login from it. Make sure any website you login at, says the real website name. For example:
```
www.ubuntuforums.org
```
If you see this:
```
ubuntu.geocities.50webs.freewebsites.net
```
Don't login from there, it's common sense. OK I'm done, but remember be safe.

---

### Post by yssida on 2008-04-22
shipit.ubuntu.com is where you get the free CD.

be safe

---

### Post by Sef on 2008-05-21
Locking this thread.  Advice has been given on what to do.  And thread seems to be getting personal.

Check out [OpenBSD]("http://openbsd.org/"), if you want a highly secure OS.  Everything is turned off and you must turn everything on that you want.

---

