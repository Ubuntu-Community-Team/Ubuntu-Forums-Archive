---
title: "What Linux OS is purpose built for security?"
date: 2021-10-28
forum: General Help
---

### Post by skoggo on 2021-10-28
Hi I am fairly new to Linux I was wondering if there is a more security focused version of Ubuntu.

Or which Linux OS is purpose built for security / built to be like the fort knox of operating systems.

I only need the OS to do two things 1 - connect to the internet and watch youtube videos 2 - work on word documents

I have looked into Tails although this does not seem very practical because of the ToR browser, and save issues

I am also look at Alpine which seems more promising, as well as Qubes.

---

### Post by guiverc on 2021-10-28
The highest level of security would be achieved, I suspect, via either

- if using a *deb *based system (ie. *year.month* release) using only 'main' packages or packages that the Ubuntu Security team were involved with

- using a *snap* only product (ie. *year* based release) where everything runs with *confinement* and few programs have access to your real file-system; which provides better privacy by default.

Yes the other archives (eg. 'universe' or community packages) follow similar procedures to the 'main' archive - but they don't get the security team audit(s).

ie. You don't need a separate product; you can use existing products; and just don't limit yourself to specific packages that meet the requirements you prefer.

Many enterprise users of Ubuntu avoid touching 'universe' or community packages I've noted in support.

---

### Post by monkeybrain20122 on 2021-10-29
Well I think you can make it more secure by fine tuning apparmor or selinux settings. My understanding is that Ubuntu's default apparmor settings are a bit more permissive so that the normal desktop users can actually do normal things without feeling being in a prison. The default Selinux setting on Fedora is very strict so many apps won't run and often the first thing a Fedora user does is too change Selinux's setting to permissive or warnings.

So it has less to do with which distro you use, you can fine tune and configure anything on Linux including security settings.

It depends really on what you use the computer for, the typical desktop use case differs a lot from the "enterprise users", the latter operate in a completely locked down environment that only allows certain specific applications, so IMO what "enterprise users" do is quite irrelevant to the usual desktop users' need and expectations. 

But then according to RMS even going on the internet is risky and if he has to he uses a text based browser like Lynx so watching YT videos is a no no. IMHO  that is a bit paranoid but to each his own.

---

### Post by grahammechanical on 2021-10-29
You want security when using a computer? Don't connect to the internet. Do not let anybody know your password. Do not install software from sources that you cannot trust. Do not use a computer operating system that is the main target for criminal hackers. At the moment Linux is not the main target but things might change.

With Ubuntu 20.04 it is impossible to disable security updates. Once we connect to the internet the OS will check for security updates and if there are any they will be downloaded and installed.

[https://wiki.ubuntu.com/SecurityTeam/Policies](https://wiki.ubuntu.com/SecurityTeam/Policies)

[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/)

Canonical has a very secure version of Ubuntu called Ubuntu core. It lacks a desktop environment and user interface. Redhat is working on something called Silverblue which I know very little about. Except that it aims to be what is called an immutable OS. Which means the user (and others) cannot alter the operating system. This is the situation with Ubuntu Core. 

There are similarities but the main difference as far as I can tell, is that Canonical is not offering even as a test project a desktop edition of Ubuntu Core. There was such a test project several years ago called Ubuntu Personal. It proved proof of concept but development has not publicaly continued.

Regards

---

### Post by HermanAB on 2021-10-29
Any Linux distribution will suffice for that use case.  I suggest that you install Linux, then relax and enjoy the system.  You will gradually learn why you suddenly don’t have issues with viruses and malware anymore.

---

### Post by ActionParsnip on 2021-10-29
If you install a minimal install of Ubuntu using the minimal ISO, then install libreoffice, firefox and lxde then you will get a very small and punchy OS with a minimal footprint (obviously switch to a different desktop session if you prefer).

Fewer services and applications gives less scope for attack.

As stated above, things like SELinux and AppArmor can be used to improve an OSes security but the weakest link will always be the human using the system.

---

### Post by bunny9000 on 2021-10-30
On the ubuntu gui version I always install gufw which allows you to control your firewall easily with a nice graphical app. You can disable all incoming and anything outgoing if you want. You don't need to install a graphical app. iptables is pretty easy to configure via command line and if your distro has se linux that adds another layer.

Linux is a bit like lego, you can build your distro up from its base to be a secure or insecure as you want. You might also want to check if your home router has a firewall built into and fine tune it. You could purchase a physical firewall at your home or office also.

---

### Post by QIII on 2021-10-30
No Linux distribution is bullet proof.  All Linux distributions can be made as secure as any other if you take the time needed.

If you are looking for one that already has the pieces installed, don't let that fool you.  No matter what, security is not a "fire and forget" exercise.  It is a constantly evolving *process* that will bear your constant attention.  Even if you have one machine with all the security bells and whistles, another unprotected machine on your network can compromise it.  Your security should extend out to your router with regard to security settings and further out to the web with regard to security hygiene there.  Personally, I wouldn't call Tor a security measure.  It provides anonymity and obscurity, but security by obscurity and security by anonymity are not security at all.  And even with Tor you have to pay attention to web hygiene so you don't drop bits of information all over the place for people to gather and build a picture of you.  Further, if you are using Tor with a router using a wifi connection that is unencrypted, the guy driving down your street scanning for unprotected wireless networks will walk right in.  If your password is weak, he only has to take a short while to pick the lock.

If you are looking for distros that claim some superiority in the security department, you might try Qubes, Arch, Tails or Kali.  But as you have noted with Tails, there is still a learning curve to proper setup.

As I said, you also need to choose a router that give you security tools.

You could also look outside of Linux to the BSDs.  Expect a bit larger learning curve there.

---

### Post by HermanAB on 2021-10-31
Btw when I need to be paranoid about security, I use OpenBSD.

---

### Post by TheFu on 2021-10-31
I believe the most secure, end-user, OS is ChromeOS running on a chromebook.  There is a F/LOSS distro called "ChromiumOS", but it loses the tight integration between the OS and the hardware that google provides in their supported Chromebooks.  For typical end-user stuff, ChromeOS is fine and prevents many security problems.  It automatically patches and maintains 2 full OS setups - A and B.  When B is being used, A gets updated. At the next reboot, A will be used and B will be updated. In this way, there should always be a bootable OS, assuming no hardware failures.  The in-use OS is mounted read-only and the updated OS is cryptographically signed and validated. Of course, ChromeOS typically runs on lower powered systems, but it has hardware and driver support for the most challenging video playback work, so we don't care so much that the CPU is slow.

ChromeOS encrypts the user's data area. I don't recall looking at the storage from outside - it is hard because the hardware only boots chromeOS and nothing else.  Modifying the firmware to allow booking other OSes prevents ChromeOS from booting. Once I physically modified the hardware to allow a different BIOS to be installed, I was unable to put the original BIOS back and run ChromeOS again. ;(  This was 6+ yrs ago, and I was able to get ChromiumOS installed and running. But I needed just a little bit more control over the OS - for example, it didn't support NFS which was a game stopper for my needs.  NFS is a way of life here.  Without it, may as well cut off both my legs and 1 arm.

Plus, ChromeOS has this idea of "Powerwashing" the OS - which is basically setting it back to the factory setup. At the next login (assuming a gmail account is used), all the files and settings will be pulled down again.  Doing a fresh ChromeOS install isn't hard either.  I've used 4GB SDHC cards to get things "just so."  

Finding a ChromiumOS distro is getting harder, as the companies creating those restrict the installs.  Used to be that we could pull an installer and run it on almost any system, including into virtual machines, which was very nice for showing off or to use for on-line banking.  Last time I went looking, the virtual machine installs have all been removed or made less easy to install.

Don't expect any privacy.

Obviously, security and privacy are completely different things.

The smaller any OS is, the more likely it will actually be secure. Less code == fewer bugs, right?

---

### Post by skoggo on 2021-11-01
Thanks for the tips everyone I will look into all of the OS's mentioned and might try some of the installs.

My main goal is to keep hackers out of my machine. The very computer I am using to type this was owned when it was only running Windows. I thought installing Ubuntu and erasing everything would be the end of the problem, but the intrusion appears to have carried over. The consensus seems to be that this computer is damaged goods, and probably my entire network for that matter. I don't know the first thing about how to hack into computers, or networks, or MIM. So I have no hope in outsmarting somebody that already knows their way around my network better than I do.

I guess the question is if I do a clean install Ubuntu, and the computer is immediately hacked again / the hack was never fixed is there anybody that would want to know about this?

@TheFu I was interested in Alpine because of the small amount of space that it uses. From what I understand Alpine exists in RAM, so I thought that aspect would be more secure by making methods of cracking into the system incompatible. Alpine is a very small OS, from booting the disk to having the operating installed can take two minutes and most of that is waiting for the hard drive to be wiped.

I understand how annoying the puzzles can be. Installing the OS was one thing, and after that the GUI needs to be setup through the terminal. There was nothing user friendly about it at all for a Linux noob like me. I wasn't able to install the mouse, and keyboard, and after that it was all error codes from the notes I was copying from. I am probably in way over my head but I think its a good way to learn.

---

### Post by TheFu on 2021-11-01
Alpine isn't meant for GUI/Desktop installations.  It is meant to be used for linux containers - basically 1 service - like DNS or DHCP or perhaps a DBMS server.  For someone new, getting a GUI onto it will be a very steep learning curve. There are easier, light, distros, that come with the GUI stuff.  But the reason that Ubuntu-based distros are so popular is all the drivers that "just work", which doesn't happen on those tiny distros. So, if you real hardware is 100% standard (none is), then go for it.

---

### Post by QIII on 2021-11-01
By the way, if this is the same machine and network that you said has been hacked by the likes of Musk, Snowden and "the highest office in the entire world", I say again:  I believe your problem is probably far outside of our field of expertise and we are likely unable to help you with it.

---

### Post by TheFu on 2021-11-01
> **QIII said:**
> By the way, if this is the same machine and network that you said has been hacked by the likes of Musk, Snowden and "the highest office in the entire world", I say again:  I believe your problem is probably far outside of our field of expertise and we are likely unable to help you with it.

If that is true.  But neophytes with computers and Linux sometimes see things that aren't really there. We cannot accurately judge, since we aren't on the system, don't know the environment and don't know the "attackers."

Musk and Snowden don't hack desktops, so that is the basis here, my tinfoil hat is highly suspect on the report.  If you were running a server, then things are very different.  Linux servers get hacked all the time - usually it isn't personal - it is just because of poor administration.  HVTs are more likely to have extremely targeted attacks and QIII is correct, you need to PAY for experts to look at your entire situation who will come up with a game plan.  

Just yesterday, I was consulting with someone who had at least 1 of their accounts compromised.  Here's what I learned.
* He'd been using the same password and email everywhere.  That is a complete fail.  Never use the same password more than 1 place. If possible, use different email addresses everywhere (they are called "email aliases").  With aliases, you can appear to have hundreds of accounts, but have them all filter into the same real account. Basically, you only need to watch 1 mailbox, but give out 50-100 addresses to different organizations. I don't know if the "free" email services support this.  My email server allows emails to 3 different domains and any combination of characters for aliases, provided the name@ part is unique.

* they only had 1 email address for personal stuff and 1 for work stuff.  They mixed social, online purchases AND the banking all in the same email. That was failure #1.  Social/Family emails need to be separate from online purchases and all of those need to be separate from where the money it kept.  At a minimum, I think most people need 5 email addresses.

* Any email address that has been hacked or is suppected of being monitored by someone else needs to be replaced by a new, random, email address and all the online logins using the older email address need to be changed. Stop using the old email address for anything. It is compromised, you must assume this.  That means moving any devices tied to it over to new email accounts as well.

* Use a password manager to keep track of the different logins and passwords and email aliases tied to any online accounts.  I honestly cannot tell you the login account names to any of my banks or investment accounts.  I don't know and I've seldom needed to know.

* Don't to any financial transactions on a tablet or smartphone - ever.  It is 1 thing to order stuff, but keep the payment off you phone!  Phones have "no-click" methods to be compromised.  They cannot/should not be trusted for anything important.  "Important" means anything tied to any of you financial or online purchase accounts.  Definitely don't have your credit-cards tied to anything on your phone.  Use a real computer, with a patched OS, with patched applications, behind a currently supported router that is patched at least monthly, to do anything financial. Those 3 new email accounts for your bank and broker and online shopping places that you use a bunch? Your phone should never have access to them.

* Treat your portable devices like spies - because they are.  Don't connect them to your home network on the inside.  Use the ISP's wifi, if you must, but never connect your computers to that same wifi network/subnet.  

* Use a hardware token for 2FA.  If you get a FIDO2 compatible "key" and tie that to as many of your online accounts as possible, that is a huge solution to any account take-over.  OF course, many online accounts don't support those, but they do support google (which does support FIDO2 devices) and normal people can use their google login to authenticate to many other services.  This is bad for privacy, but excellent for security. If your eyes are glossing over - try to use the google account for longs where ever they are allowed.

* If you have any IoT devices - cams, thermostats, refrigerators, media players, only let those connect to the ISP wifi - NEVER on your internal LAN.  The NSA made this recommendation.

* Don't give out email addresses or your cell phone number to just anyone.  You can get a 1-number VOIP service relatively cheap that forwards calls to your cell phone or house or both with time restrictions.  Then you can give out that 1-number as needed. Many have spam-blocking features built in.  I use voip.ms for $5/month, but it replaces my home phone and cell phone numbers (I currently don't have any cell phone plan).

* Patch your computers and devices weekly.  Patch your router monthly.  If the router you use hasn't seen updates in more than 2-3 months, then support was dropped and you should throw that into the trash and buy a replacement.  My router gets updates every other week.  Last Friday I patched it and there were a bunch of php version patches - sufficient to require a reboot.  My router seldom actually needs to be rebooted for any patch, so that was a big deal.

I've don't some fairly broad security strokes above for someone not very security-minded. There are nuanced exceptions which can apply, but for people that are at high risk of being hacked, they need to deal with the inconvenience.

And Apple phones are not immune to all these issues. Everyone needs to be cautious about all their portable devices and each app on them.

---

### Post by skoggo on 2021-11-02
> **QIII said:**
> By the way, if this is the same machine and network that you said has been hacked by the likes of Musk, Snowden and "the highest office in the entire world", I say again:  I believe your problem is probably far outside of our field of expertise and we are likely unable to help you with it.

Yes this is the same computer. I am aware that neither of them go around spying on people anymore.

To add real world context to the variety of hack that might be occurring, it would be to consider stealing artistic intellectual property.
- j.k rowling who is a best selling author. Would there be a hacker interested in root hacking her devices?
- adele is there a tech savy fan that would want to intercept some of her mp3 files?

That is the simplest explanation I can think of.
You don't know who I am? Or do you? If you can guess my name maybe I'll send you a neat prize lol

As for solutions it seems like resistance is going to be futile. I won't be able to use an all in one setup as my workstation, I will have to divide my work between two different computers.
2 monitors
2 mouse
2 keyboard
2 computers

This machine will be able to browse the web and it will be assumed that all traffic is being monitored. (which I can live with)
The second machine will not have a network adapter, or ethernet. Connecting to the internet will be psychically impossible and I will use that machine as an overbuilt typewriter.

cheers

---

### Post by TheFu on 2021-11-02
> **skoggo said:**
>  
As for solutions it seems like resistance is going to be futile. I won't be able to use an all in one setup as my workstation, I will have to divide my work between two different computers.
2 monitors
2 mouse
2 keyboard
2 computers

This machine will be able to browse the web and it will be assumed that all traffic is being monitored. (which I can live with)
The second machine will not have a network adapter, or ethernet. Connecting to the internet will be psychically impossible and I will use that machine as an overbuilt typewriter.

cheers

Or just get a KVM switch ($50-$150) so the same monitor, keyboard and mouse can connect to the different computers.  I've been using a 4-port KVM switch since around 2000.  It has 3 servers and 1 laptop connected.  Switching between the different computers are a button press away.  The KVM switch model I use also has inline <scrollock><scrollock><number> support, which is nice, so I don't have to take my fingers off the keyboard to change computers.  OTOH, all my systems are networked, so I usually just open a terminal onto the other systems and don't use the KVM switch too often.

Using a disconnected computer is smart. It doesn't need to be expensive, especially if just for writing.  Many people love to use an Atari 400 for this, but a $75 used Core2 Duo desktop can easily handle a word processor too.  Spend the money on the keyboard and monitor. That's what will make for a better experience.  I've been using IBM 101m keyboards for the last 25 yrs. Picked up 2 of them for $0.50 ea in the mid-1990s and still use one daily.  When it gets dirty, I swap in the other one. They are very easy to clean since all the parts are removable.  Today, similar "mechanical" keyboards run $150+.  I love the feel and have gotten used to the clicks, though I'd rather have quieter "brown" keys.  I've been tempted to get a "Das Keyboard" with no labels. After all these decades, I don't need to look at the keys - ever - even for the seldom used characters.

---

