---
title: "Can This Be Done Easily? Creating Stand Alone Offline Machine"
date: 2020-11-18
forum: General Help
---

### Post by Smallwheels on 2020-11-18
With so many stories of manufacturers updates screwing up hardware (mostly Apple), companies spying on user information, and user data being sold, I want to build an off line computer using GNU/Linux. 

I know that all that is needed is to put the OS on the machine and never connect it to the internet. What I don't know how to do is to get programs in the future. I could in time learn of a new program that I would like to add to my off line machine. How would I download it and then use it? I could have another computer running the same OS, go to the software center, download the program and transfer it to the other machine. What if there are dependencies that aren't on the off line machine that the new program requires? How do I get those and install them? I know how to go to the software center and click install. That's about it. 

Is anybody out there doing this? I am interested in music production and basic video production. In the future I could see wanting to work on publishing with graphics. Once I have the programs that work for me functioning, I would not really need to update them. As long as they function as is, I don't think I would ever need to update them.

---

### Post by DuckHook on 2020-11-18
The vast majority of those who do the cost/benefit analysis conclude that there's far more to gain from being connected than from isolating. While only you know the costs/benefits for your case, before you cut yourself off from the outside world, let's address your concerns one at a time.

> **Smallwheels said:**
> With so many stories of manufacturers updates screwing up hardware (mostly Apple),
If you are referring to HW updates, then this is a non-issue. All such upgrades are under your control whether the HW is Apple or anyone else. And they have nothing to do with whether you are connected or not.

If you are referring to software, then the following is the case: 

[list=1]
[*]SW updates in Linux have improved a lot from days of yore when a run&#8209;of&#8209;the&#8209;mill update could screw up your existing install. What we see on these forums is typically that version upgrades cause almost all of the problems. Everyday upgrades do not. And even version upgrades do not cause the same number of problems that they used to.
[*]It is true that an isolated system will not upgrade, but this is a double edged sword. Upgrades are not just for new features that you may not need; they also close off defects and security holes, which leads to the next point:
[*]While a total quarantine will protect you from on&#8209;line threats, it won't protect you from off&#8209;line ones. In my DOS days, a significant threat was posed by boot sector viruses. If you exchange files at all (by sneaker&#8209;net given that you will not have internet), then bad stuff can still get into your system. An updated system will be resistant to such threats whereas the longer a system goes without updates, the more susceptible it is to them.
[/list]
> …companies spying on user information…
This has nothing to do with your OS being connect to the net. It has everything to do with which OS you use and *what apps you choose to install*. The biggest spyware threat these days are actually Android/Apple mobile apps. Installing anything that is closed source/opaque is a leap of faith (usually unearned and undeserved) that the developer won't spy on you.
> …and user data being sold…
See above. User data being sold is almost entirely a function of lack of user discipline, not holes in the OS. If you are addicted to social media, register for tons of sites on your smartphone, etc, then it doesn't matter one iota how hardened or isolated your computer is.
> …I could have another computer running the same OS, go to the software center, download the program and transfer it to the other machine. What if there are dependencies that aren't on the off line machine that the new program requires? How do I get those and install them? I know how to go to the software center and click install. That's about it.
You have yourself already identified the main problem with your plan. Linux apps depend on Linux libraries. Few are standalone. Moreover, without constant updates, those libraries also fall behind. So, even if you have the library already installed, the version may be too old for your new app.
> Is anybody out there doing this?
The closest environment that I can think of to what you are seeking is the kiosk: a Linux machine configured to work for one implementation only—to interact with anonymous users for one simple task. Such machines are not hooked up to the net, cannot be used for general computing purposes and have a highly defined, dedicated use. But this doesn't seem to be what you are after, witness the following:
> I am interested in music production and basic video production. In the future I could see wanting to work on publishing with graphics.
Essentially, this is general computing. It only looks simple due to our anthropocentric bias. To a computer, these are complex general computing tasks.
>  Once I have the programs that work for me functioning, I would not really need to update them. As long as they function as is, I don't think I would ever need to update them.
This is the one statement that I would caution you against accepting as a given. Back in my working days, there were a few machines that we thought could be treated the same way. The passage of time and hard won experience showed us that we had drastically underestimated the value of connectivity. We could not collaborate. We could not easily exchange files with other machines. We would get a file from a consultant that wouldn't open on our box because our app was too old. With Linux, falling behind could get even worse because upgrading is assumed to be almost entirely reliant on being connected. While it is possible to work around this limitation, the process is not for newies and your own self&#8209;assessment was "I know how to go to the software center and click install. That's about it."

Do you really want to arm wrestle with .deb files and scripts on a USB stick?

Here's what I would recommend. Keep your computer connected to the net. If you are really worried about net exposure, then turn off networking as a rule, and turn it on only when you check for updates, say, once weekly. At all other times, networking is off. You still have access to it when needed, but you are protected from unknown threats when net access is not needed.

---

### Post by Smallwheels on 2020-11-18
DuckHook thank you for your wisdom. You have stated many good reasons to not disconnect a computer from the internet. You have given me more to consider. 

I have worked with companies that still use Windows XP Professional. Those machines in one office have a network. None of them connect to the outside world. They all function perfectly doing the necessary office work and other things for which they have programs. Those old machines are safe. To compromise them somebody would need to be in the room with them. If somebody wanted to compromise my off line computer they would need to break into my home. That is a lot more work and danger to someone than hacking a WiFi signal from the street or attacking the router from a remote location. 

Pitivi is the last video program I used. I would like to have a better one, but really that is low level video production. I used audacity to modify the audio that I put into the last video made. I think any Core i3 chip could be powerful enough to handle what I do. Word processing and GIMP level graphics are the other things used. If I do decide to get a publishing program that makes creating pamphlets or magazines easier, then that is what I would do. Computers from the 1970s could do such work. So the tasks that I want to do shouldn't need updates if they work fine as is. 

Apple's new OS, Big Sur, for Macs, has bricked many computers. The update alters the BIOS and crashes a chip that communicates with the power supply telling it what charge to take. To fix it, the entire BIOS must be reflashed onto the chip. Which must be removed from the motherboard for that to happen. IOS updates regularly kill older IOS devices. Apple forces updates at times. They throttled older phones a few years back. Only when they were sued was it revealed. Apple and Windoz machines are spyware. 

I'm not one who uses social media. I suspect that Youtube knows me better than any human on the planet if they store my entire viewing history. I turned that off years ago when offered the chance; but can they really be trusted? No, because they still feed me videos about the topics that I like. How could they do that if they weren't keeping track of my likes? 

I considered the potential problems of transferring files from an internet connected computer to mine. That will be rare. Most of the time it will be the other way. I'll create documents that need printing or videos for posting on Odysee and Rumble, using the sequestered machine, and let a different computer deal with printing or posting the videos tasks. 

I considered occasionally connecting the computer to the internet and only using it to get updates. Since I don't really know how to identify malware or spyware, how would I know if it were loaded nefariously? Only when the stuff activates and does something would I know, and that is assuming that it was designed to cause problems. What if it weren't designed to cause problems but to just spy? Every time I got an update, while connected to the internet, it could secretly send information somewhere. 

I've also considered updating the OS every couple of years by downloading a fresh version, along with the programs I use. That would work a couple of times. Then the hardware might be too old for more OS upgrades. At least with that plan, software bugs from the programs I use could be fixed. Of course that would mean hoping that there weren't new bugs. I would go for the LTS versions. 

Is there a way to know which libraries would be needed by specific programs? If so, is there a way to get them and transfer them to the off line machine?

---

### Post by HermanAB on 2020-11-18
We use several computers for engineering purposes.  On these, once everything we need is working, we simply disable automatic updates.  Then after a few years, we install a fresh version of Linux if needed.  Linux is very robust and a machine can keep running for several years without any issues, usually until the PSU fails - then we junk it and get a new one.

So, if you use Linux, then you can relax a bit.  You need not be totally paranoid anymore, since the OS is designed to handle most of the paranoia on your behalf.

As for Apple Macs, when one gets beyond its support period after seven or eight years, I install Linux or OpenBSD on it and then it is good for a few more years.

---

### Post by DuckHook on 2020-11-19
> **Smallwheels said:**
> &#8230;Since I don't really know how to identify malware or spyware, how would I know if it were loaded nefariously? Only when the stuff activates and does something would I know, and that is assuming that it was designed to cause problems. What if it weren't designed to cause problems but to just spy? Every time I got an update, while connected to the internet, it could secretly send information somewhere&#8230;
As HermanAB so aptly states:
> **HermanAB said:**
> &#8230;if you use Linux, then you can relax a bit.  You need not be totally paranoid anymore, since the OS is designed to handle most of the paranoia on your behalf&#8230;
This does not mean that you can *completely* relax&#8212;Linux is not a silver bullet either. Stupid actions will still yield stupid results. But the sort of concerns that you used to have with Windows XP are greatly lessened with Ubuntu (with the standard caveats of course).

Just a few further thoughts:

On the app front, you are still thinking in Windows/Apple terms, in which software is closed source, opaque, and therefore impossible to review or audit. In those proprietary ecosystems, it is a given that developers can and therefore will program their apps to skim metadata (often outright data) with no regard for your privacy because such ecosystems have monetized this behaviour to such an extent that the rewards to the offending developer are irresistible.

In contrast, the FOSS ecosystem is, by definition, open to review and audit. Anyone knowledgeable enough can parse through the source code. It is almost impossible to hide anything nasty from such a multitude of prying eyes. This creates an ecosystem which is sociologically the opposite of the proprietary one because apps built to skim your data would be obvious and shunned by all. This completely disincentivizes the creation of such apps in the first place.

The upshot is that your approach to Linux apps needs to be the opposite of your approach to proprietary apps. With FOSS apps, you don't need to be worried about *intentional* invasions of your data/privacy. Instead, you should redirect your worry to *un*intentional bugs and third&#8209;party exploits that might compromise your data/privacy. This is the reason that Linux users update like mad (of course, if you choose to install proprietary apps into Linux, then all bets are off).

Your habits and worries are currently geared towards the dangers of the proprietary world. The FOSS world is so opposite that you need to change your perspective almost 180°. The primary danger in Linux is to fall behind on your updates. Therefore, if an unconnected computer is likely to retard updating, then, counterintuitively, that becomes a weakness and not a strength. This feels perverse only because you have been conditioned by years of Windows/Apple thinking. Not your fault, but you need to understand where your habits of thought are coming from and where they can mislead you.

---

### Post by Smallwheels on 2020-12-20
> **DuckHook said:**
> Your habits and worries are currently geared towards the dangers of the proprietary world. The FOSS world is so opposite that you need to change your perspective almost 180°. The primary danger in Linux is to fall behind on your updates. Therefore, if an unconnected computer is likely to retard updating, then, counterintuitively, that becomes a weakness and not a strength. This feels perverse only because you have been conditioned by years of Windows/Apple thinking. Not your fault, but you need to understand where your habits of thought are coming from and where they can mislead you.
I see your points but disagree. Just because something is open source doesn't mean somebody won't create a virus and use it. I honestly don't know what percentage of users actually review code or even have the skills to identify something malicious. That probably takes a lot of time. 

How many updates and tweaks and changes does it take to make one's hardware too slow to run a program that at one time ran just fine? Ubuntu is getting really fancy. Every year their recommended hardware requirements are going up. I want to use the Ubuntu Studio OS. I tried it last week and I really don't like the way the software makes my trackpad work. I might just download the latest Ubuntu and add the Ubuntu Studio programs. Regular Ubuntu doesn't mess up my trackpad. 

Here is an example of losing control and companies screwing up a computer. Google Chrome is now broken for me. It won't synchronize my GNU/Linux computer and my Chromebook. Every time I go to use the other computer it wants me to change my password due to suspicious activity. If I change the password on one machine it isn't accepted on the other via sync. So there is this infinite loop of changing passwords if I continue using both machines. EVEN USING A FRESH LIVE USB with no apps or extensions, Google says suspicious activity is happening on my account. It wants me to change passwords again. I have posted this on their forum and there has been no reply in over a month. I know that I'm on a list of trusted reporters of problems because for years, everything I report gets fixed on the next update. With one exception. That is the numbered list tool in Docs when using size 16 or larger text. That's a Libreoffice problem Google adopted. 

I have considered putting a new OS on a machine and just not using browsers ever. I could turn on the WiFi only for updating the existing software. Once updated the WiFi would be switched off. That only works if the router software hasn't been compromised. A different solution would be to just get a new OS every year or two and to check that updates are installed when it is installed. Then disconnect the machine. Still, that doesn't help with the problem of ever increasing program sizes that require better hardware. 

Nobody has really answered my original questions about updating dependencies or adding software without using the software center.

---

### Post by HermanAB on 2020-12-20
Note that you can make your own mirror server to completely control the install process.  This is not difficult.  A Raspberry Pi with a large disk is all you need.

How much control you want, depends on your level of paranoia.

---

### Post by C.S.Cameron on 2020-12-20
Tails is said to be very secure: [https://tails.boum.org/install/](https://tails.boum.org/install/)
It even comes with Tor Browser.
Might be worth checking out.

---

