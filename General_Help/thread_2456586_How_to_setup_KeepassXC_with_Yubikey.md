---
title: "How to setup KeepassXC with Yubikey"
date: 2021-01-14
forum: General Help
---

### Post by Ralph L on 2021-01-14
I want to improve the security of my bank accounts and other financial accounts, so I recently bought a YubiKey 5 NC.  In this forum I have seen recommendations to use it with the password manager KeepassXC.  I need some help in setting these up together, since I really don't know how YubiKey works, and how it can be integrated with KeepassXC.  Here are some of my questions:

1.  When I go to the Keepassxc website  I see multiple methods of installation:  appimage, Official Ubuntu PPA, or Ubuntu Package.  I am running Xubuntu 18.04.  I am wondering which would be best to use.  I kind of like appimages, since they are usually the most up to date, but are there any security risks using appimages.  As far as I know appimages are just object code files that are usually made available to any user of my computer (my wife and I).  What if somebody broke into my computer.  Would an appimage be more vulnerable to some malware, that might be in a user account, than something stored under the admin account??

2.  I see a reference to the YubiKey Personalization Tool.  Do I need to download and use this even though I am going to use KeepassXC??

3.  I see some references to YubiKey slot 1, and YubiKey slot 2.  What are these, and which one should I use???

4.  What is "Challenge Response Mode", and what other Modes are there?  Should I use Challenge Response Mode, and how does it work??

5.  Finally, do any institutions such as banks support the Yubikey directly in such a way that my key goes directly from my Yubikey to the bank (maybe still encrypted) without having to stop off in Firefox where The Fu says it is stored unencrypted for some malware, that might be on my computer, to read??

Thanks in advance for any help.......

---

### Post by Paddy Landau on 2021-01-16
I can't answer most of your questions, unfortunately, but I will comment about appimages.

I recommend against an appimage, because it's never updated automatically. You have to manually go and check on a regular basis. Instead, use a PPA or snap. If you set up your system properly, they'll be updated whenever you run the updates (which I recommend you set up to run automatically).

[LIST]
[*]For the PPA, use the one that [KeepassXC recommends]("https://launchpad.net/~phoerious/+archive/ubuntu/keepassxc").
[*]Or, use the [official snap package]("https://snapcraft.io/keepassxc") (that's what I use).
[/LIST]
There's also a flatpak version, but it's not official and is currently out of date.

---

### Post by Ralph L on 2021-01-16
Paddy,
Thanks for responding. Regarding using a PPA vs appimage, does not a ppa program get special privileges due to being installed under the admin account, rather than a non-admin account where an appimage would be installed.  Wouldn't a ppa program have access to all the admin account files, whereas an appimage installed under a non-admin account have access to only the files owned by the non-admin account.  If the ppa program installed under the admin account had a Trojan in it, could it do more untoward things when executing under a non admin account than an appimage installed and running under a non admin account.
As you can see I don't really understand how linux protects itself against malware.  Any help is appreciated...

---

### Post by #&amp;thj^% on 2021-01-16
> **Ralph L said:**
> 
As you can see I don't really understand how linux protects itself against malware.  Any help is appreciated...

Linux Desktop Malware Exists, But It's Rare more here:[https://www.makeuseof.com/tag/linux-virus-malware-truth/](https://www.makeuseof.com/tag/linux-virus-malware-truth/)
Sorry for the drive by.

---

### Post by CelticWarrior on 2021-01-17
That you need admin privileges to install software doesn't mean said software will run under root. And this is exactly how Unix/Linux is protected.
It seems you're operating under a pre-Windows Vista sort of mentality.

---

### Post by Paddy Landau on 2021-01-17
> **Ralph L said:**
> Regarding using a PPA vs appimage, does not a ppa program get special privileges due to being installed under the admin account, rather than a non-admin account where an appimage would be installed.
I understand what you say, but a PPA is dangerous only if you add a dodgy one that you find on the internet without due checks (exactly the same as downloading an app for Windows without due checks). Snaps are likewise secure. KeepassXC is used by enough people and has sufficient "eyeballs" to make it trustworthy.

To put it another way…

If a PPA or snap can be hacked, so can an appimage. Or, if the owners of KeepassXC wanted to install malware, they would do it in the PPA, the snap *and* the appimage.

If you stick only to the official repositories for any app that you trust, I believe that a PPA or snap is more secure than an appimage for two reasons: 1. The background checks while they download updates, and 2. Your system automatically updates, so it doesn't depend on you having to remember to do so.

If you stick with an appimage, you'll have to set a calendar reminder to check for updates every few days (say, twice a week, or less often if you aren't too worried about security). If you have many appimages, it's going to take up some of your time.

---

### Post by Ralph L on 2021-01-17
Everybody that replied:  Thank you very much. I am beginning to understand a little more about linux security from reading each response.

1fallen:  Your reference to EvilGnome is just the kind of malware that concerns me. It contains a key logger that could reveal my bank account passwords.  What I didn't understand, from the website you reference, was how the EvilGnome got installed the first place.  The website says, "Gamaredon Group infects victims using malicious attachments, delivered via spear phishing techniques", but this doesn't tell me where the "security hole" is in linux. Do you know if Evilgnome was spread by people logging into a bad website, by opening a bad email, by installing a bad PPA, by installing a bad appimage, or what? The fact that something like EvilGnome can be installed at all seems to me that it shows linux has security holes.  Can you give me any other information????

---

### Post by #&amp;thj^% on 2021-01-17
That EvilGnome was patched a while back, that reference was to show it can happen on Linux but as said Rarely.
I've been using Linux as my only OS for over 15 years now>>>Not once have I had a Virus, or Malware, Ive even tried to get one, by visiting sites that are not reputable in nature. (Groups know to be bad actors) Not Porn sites but where the bad guys hang.
And the fact that you would really have to help the individual/s install it, I'd just relax and sensibly enjoy your Linux system......Don't Worry Be Happy :D

---

### Post by Ralph L on 2021-01-17
1fallen:  Thanks again for the response.  But just for my better understanding of how to avoid "helping the attacker", what do I do?  Not load from ppas, and never modify a file in /home/MyUserName/.something????

---

### Post by Hagar Delest on 2021-01-18
As said by Paddy Landau, the ppas are not dangerous as long as they are managed by trusted teams. These repositories are just to provide more updates to the users (who don't have to wait for the distro upgrade, that may come, or not). If many people use the ppa without any problem, then you can do it. Open source project experience enough scrutiny to offer a good level of protection. And I doubt that bad guys would set up a ppa to deliver junk code.

The /.something are configuration files and folders for your applications (from desktop management to standard applications). You can modify them but seldom the need (custom .desktop menu entries for example).

Helping the attacker would be going in known places for phishing or that offer to win the lottery by downloading a great application. It is just common sense!

But in fact, you have bought a Yubikey without checking first if it is supported by your bank(s)?

I skimmed quickly the Wikipedia article about Yubikey and you may have noticed that the code has been closed, that means that nobody can check it anymore.

---

### Post by Paddy Landau on 2021-01-18
To clarify further what @1fallen and @Hagar Delest have (correctly) said:

Whilst there have been, very rarely indeed, dangerous zero-day exploits for Linux, they have, to the best of my knowledge, only managed to infect systems that have had poor security or outdated software. The last point is why it's a better idea to use a PPA, snap or flatpak, because if you've set them up correctly, they'll automatically update.

As for other types of malware, common sense is all that you need.

[LIST]
[*]**Beware emails!** When you receive an email, always be on guard for a links within the email. For example, when I receive an email from PayPal (as I regularly do), I know that the email needs to be from paypal.com (not, say, paypal-account.com, which would be a scammer), it has my name, and a link goes to paypal.com (again, not, say, paypal.com.secureyou.com). Then, on top of that, for sensitive sites (banks, Gmail, shopping sites, etc.), I won't click the link, but instead go directly to the site myself.
[/LIST]

[LIST]
[*]**Beware text scams!** Much the same advice applies to SMS as to emails.
[/LIST]

[LIST]
[*]**Beware scams via letters!** Again, the same advice. For example, just today I received a letter from my solicitor asking for payment. I telephoned the solicitor to confirm that the letter was genuine and that the bank account details were correct (they were).
[/LIST]

[LIST]
[*]**Don't download software directly.** For example, it used to be that some people would download [GIMP]("https://www.gimp.org/") (instead of using the official snap, flatpak or PPA) and find malware infecting their machine. That's because a bad actor had gone up the search rankings for GIMP, but had inserted malware into their copy of the GIMP software. The lesson is this:
[LIST]
[*]If you want to install software, do it via the official software centre for your system.
[*]If the software is unavailable there, or it's too out of date for you to use, research the correct source. Google it by all means, but once you've found it, search reliable forums (e.g. this forum or [AskUbuntu]("https://askubuntu.com/")) or reliable articles (e.g. on [OMG Ubuntu]("https://www.omgubuntu.co.uk/")) to check that it's a bona fide source (i.e. do they point to the same website?). Only once you're sure of the source, get the software using the official method on that website (I always double-check that it's https and not http). If I find an article about great software on a website that I'm unfamiliar with, I double-check the software elsewhere before deciding whether to go ahead or not. I have, on occasion, decided against it.
[*]Generally, for modern hardware, a snap or flatpak is an excellent choice, but a PPA is also good especially for older hardware.
[/LIST]
[/LIST]

[LIST]
[*]**When your system asks for your password,** ask yourself why. Did you ask to install software? Were you expecting the prompt? Is it from your automatic updates? If you're unsure, cancel and seek further advice. (The automatic updates don't ask for your password except when they update critical software such as your Linux kernel.)
[/LIST]

[LIST]
[*]**Make regular backups** both online and offline. I back up my machine daily, both online (I use [SpiderOakONE]("https://spideroak.com/")) and offline (I have three different external hard drives, which I rotate, so that if one goes bang or gets ransomware, I still have safe backups, albeit a bit out of date).
[/LIST]
Be safe!

---

### Post by #&amp;thj^% on 2021-01-18
> **Paddy Landau said:**
> To clarify further what @1fallen and @Hagar Delest have (correctly) said:

Whilst there have been, very rarely indeed, dangerous zero-day exploits for Linux, they have, to the best of my knowledge, only managed to infect systems that have had poor security or outdated software. The last point is why it's a better idea to use a PPA, snap or flatpak, because if you've set them up correctly, they'll automatically update.

As for other types of malware, common sense is all that you need.

[LIST]
[*]**Beware emails!** When you receive an email, always be on guard for a links within the email. For example, when I receive an email from PayPal (as I regularly do), I know that the email needs to be from paypal.com (not, say, paypal-account.com, which would be a scammer), it has my name, and a link goes to paypal.com (again, not, say, paypal.com.secureyou.com). Then, on top of that, for sensitive sites (banks, Gmail, shopping sites, etc.), I won't click the link, but instead go directly to the site myself.
[/LIST]

[LIST]
[*]**Beware text scams!** Much the same advice applies to SMS as to emails.
[/LIST]

[LIST]
[*]**Beware scams via letters!** Again, the same advice. For example, just today I received a letter from my solicitor asking for payment. I telephoned the solicitor to confirm that the letter was genuine and that the bank account details were correct (they were).
[/LIST]

[LIST]
[*]**Don't download software directly.** For example, it used to be that some people would download [GIMP]("https://www.gimp.org/") (instead of using the official snap, flatpak or PPA) and find malware infecting their machine. That's because a bad actor had gone up the search rankings for GIMP, but had inserted malware into their copy of the GIMP software. The lesson is this:
[LIST]
[*]If you want to install software, do it via the official software centre for your system.
[*]If the software is unavailable there, or it's too out of date for you to use, research the correct source. Google it by all means, but once you've found it, search reliable forums (e.g. this forum or [AskUbuntu]("https://askubuntu.com/")) or reliable articles (e.g. on [OMG Ubuntu]("https://www.omgubuntu.co.uk/")) to check that it's a bona fide source (i.e. do they point to the same website?). Only once you're sure of the source, get the software using the official method on that website (I always double-check that it's https and not http). If I find an article about great software on a website that I'm unfamiliar with, I double-check the software elsewhere before deciding whether to go ahead or not. I have, on occasion, decided against it.
[*]Generally, for modern hardware, a snap or flatpak is an excellent choice, but a PPA is also good especially for older hardware.
[/LIST]
[/LIST]

[LIST]
[*]**When your system asks for your password,** ask yourself why. Did you ask to install software? Were you expecting the prompt? Is it from your automatic updates? If you're unsure, cancel and seek further advice. (The automatic updates don't ask for your password except when they update critical software such as your Linux kernel.)
[/LIST]

[LIST]
[*]**Make regular backups** both online and offline. I back up my machine daily, both online (I use [SpiderOakONE]("https://spideroak.com/")) and offline (I have three different external hard drives, which I rotate, so that if one goes bang or gets ransomware, I still have safe backups, albeit a bit out of date).
[/LIST]
Be safe!

=d> Well Put Sir!

---

