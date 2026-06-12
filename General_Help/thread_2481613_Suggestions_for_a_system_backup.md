---
title: "Suggestions for a system backup"
date: 2022-12-04
forum: General Help
---

### Post by demonenero84 on 2022-12-04
So a few days ago I broke my system :( 
Now all my software and configurations are back, I did everything manually and it took a while, so here comes the question :)
What tools do you suggest me to backup my system, I don't care about documents and other files ( I have a simple rsync script that copies my files to two external hard disks, so I have a double backup ), I want to backup my config files, all software installed and proprietary drivers for my nvidia GPU . What do you suggest me? will a simple copy of my home folder do the trick? 
Thanks a lot in advance

---

### Post by ajgreeny on 2022-12-04
I've never used it but have a look at timeshift which is in the repos of 22.04 (not sure about 20.04 if you're still using that.
See [https://ubuntuforums.org/search.php?searchid=27824030](https://ubuntuforums.org/search.php?searchid=27824030)

It is a default application of Linux-Mint and there are many threads in the Mint forums about timeshift and the good and bad of its use.
Have a look there as well to see if it is what you want.
[https://forums.linuxmint.com/index.php](https://forums.linuxmint.com/index.php)

---

### Post by demonenero84 on 2022-12-04
thanks for the reply :)
I use kubuntu 22.04 LTS

---

### Post by oldfred on 2022-12-04
Your /home has your hidden user configuration files. If you back that up, you can reinstall apps and have all the same settings.
You can export a list of installed apps, either all apps or manually installed. Re-installing from list will only install apps not already installed.
Many suggest backing up /etc for system configuration. I just copy my edits to grub into /home so that is backed up. 
I do have a script for a few more edits, and then do not backup /etc.
If you install server type apps those are in / and also then need backup.

I then can do a new install, restore /home & data, & reinstall all the apps. Longest time even with fast download is all the apps I have installed. But total time is usually about an hour to restore system with just a few manual settings required. I install a copy and/or next version as tests to make sure my procedure still works, but more to test changes. But keep main working install a latest LTS. And often still have last LTS as a working system.

---

### Post by ian-weisser on 2022-12-04
Over 15 years I tried a lot of different backup methods for applications and configs.

The only three hidden and config files that I back up along with data are 1) Browser  bookmarks, 2) Old POP Email from before switching to IMAP, and 3)  Password database

Everything else can be rebuilt from scratch using my notes.  Turns out for me the simply keeping notes takes up almost no disk space, makes troubleshooting much easier, and makes uninstalling applications and makes reverting customizations simple. Notes, a set of documents, get backed up with the rest of my data.

A few years ago, I rebuilt a system from my notes. Very satisfying and surprisingly easy. Once complete, I smacked my forehead -- I had forgotten that I had a complete system backup for it already. That's when I stopped doing complete system backups. Now I backup data only...and the three hiddens...and notes.

---

### Post by ne29914 on 2022-12-04
Used Timeshift for system backuo over the last years, never let me down. Experimenting, installing dumb things, changing configurations I shouldn't have, whatever. Timeshift always brought me back. Even after a complete reinstall.
I recommend it.

---

### Post by DuckHook on 2022-12-04
My advice is more in the nature of meta&#8209;advice, which most people don't care to hear, but in case you do:

The key to a really trouble&#8209;free computing experience is… don't change your install from its defaults. Yes, I know that this deprives us of the eye candy that customizations and tweaks provide, but after years of wrestling with these cussed OSes, I've come to appreciate the advantages of substance over appearance.

If you keep your install as close to its default state as possible, then not only is reinstallation a breeze, but network upgrades happen without hitches, your system will be more stable and you will be significantly more secure than those who add all those bells and whistles.

Every additional app, utility or service increases your attack surface. Every additional line of code is also an additional point of possible failure. Every change to a system default is an invitation for breakage.

That said, even default installs will run into trouble on very rare occasions. I had one upgrade die with a power outage which basically made the OS unbootable. I defend against those rare occurrences with the following strategy:

[LIST=1]
[*]I install into LVM. It's a proven technology that allows snapshots and rollbacks which, BTW, are quick and easy once you get the hang of them. Before any system upgrade, I take a snapshot. If the upgrade goes south, I just rollback.
[*]I set up the same OS as a multi&#8209;boot. If one bites the dust, I can boot into the other, chroot into the first and fix what went wrong.
[*]Almost all my apps are confined within unprivileged containers. Not only does this add extra security through sandboxing, but it allows me to share the same apps (and their customizations) across all multi&#8209;boots. It also makes it child's play to port the container to another machine, which I do for the sake of further redundancy.
[/LIST]
The price for this sort of safety, integrity and redundancy is one I'm happily willing to pay: foregoing a few trappings.

---

### Post by HermanAB on 2022-12-05
In my experience it is very seldom that a system gets totally messed up >20 years, by which time everything is different and I would then want to have the latest system, not a resurrected old and tired one.   So making a system backup is not really worth the hassle to me.

---

### Post by demonenero84 on 2022-12-05
> **ian-weisser said:**
> Over 15 years I tried a lot of different backup methods for applications and configs.

The only three hidden and config files that I back up along with data are 1) Browser bookmarks, 2) Old POP Email from before switching to IMAP, and 3) Password database

Indeed, I use Firefox that lets you set up an account to save those bookmarks and passwords, it also lets you export bookmarks as json files and passwords as csv files
> **oldfred said:**
> Your /home has your hidden user configuration files. If you back that up, you can reinstall apps and have all the same settings.
.
Do I have to copy those files after installing or before installation and then run the apps?
> **DuckHook said:**
> My advice is more in the nature of meta&#8209;advice, which most people don't care to hear, but in case you do:

The key to a really trouble&#8209;free computing experience is&#8230; don't change your install from its defaults. Yes, I know that this deprives us of the eye candy that customizations and tweaks provide, but after years of wrestling with these cussed OSes, I've come to appreciate the advantages of substance over appearance.

So basically every change increase the chance of something going wrong, I must say that I did't have any stability issues since now, I have been using kubuntu for a year and a half (first 21.04 and the 22.04 LTS)
> **DuckHook said:**
> 
That said, even default installs will run into trouble on very rare occasions. I had one upgrade die with a power outage which basically made the OS unbootable. I defend against those rare occurrences with the following strategy:

    I install into LVM. It's a proven technology that allows snapshots and rollbacks which, BTW, are quick and easy once you get the hang of them. Before any system upgrade, I take a snapshot. If the upgrade goes south, I just rollback.
    I set up the same OS as a multi&#8209;boot. If one bites the dust, I can boot into the other, chroot into the first and fix what went wrong.
    Almost all my apps are confined within unprivileged containers. Not only does this add extra security through sandboxing, but it allows me to share the same apps (and their customizations) across all multi&#8209;boots. It also makes it child's play to port the container to another machine, which I do for the sake of further redundancy.

The price for this sort of safety, integrity and redundancy is one I'm happily willing to pay: foregoing a few trappings.
That is quite interesting, I will try LVM, I really like the idea of containers, I see that you have a link to a guide :)
Thanks to everyone for the information, I will mark this topic as solved :)

---

### Post by DuckHook on 2022-12-06
> **demonenero84 said:**
> Indeed, I use Firefox that lets you set up an account to save those bookmarks and passwords, it also lets you export bookmarks as json files and passwords as csv files
Please be careful about leaving your passwords floating out there in the cloud. I know that many people do this, but do you really want your bank account password "out there" in who&#8209;knows&#8209;where land?
> So basically every change increase the chance of something going wrong, I must say that I did't have any stability issues since now, I have been using kubuntu for a year and a half (first 21.04 and the 22.04 LTS)
Yes, Linux is remarkably stable. We old&#8209;timers sometimes go overboard seeking that extra smidgen of stability when users may already be happy with what they have.

That said, the times when you will appreciate default stability will be when you do a version upgrade. Years ago, when I added all sorts of apps, utilities, services and fluff to my base system, version upgrades would usually choke and die. This is not surprising. Upgrading an entire version involves thousands of files, all of which must go perfectly. The more complexity that you throw into an install, the less chance there is that someone will have tested that specific combination of apps to make sure that it upgrades properly.

Even without upgrades, adding apps/utilities/services galore will geometrically increase your chances of library version conflicts and broken dependencies. We used to get many pleas for help on these forums because of exactly this practice.

My own experience is that, ever since I resolved to keep my base system as clean and close to default as possible, version upgrades proceed effortlessly. The reason for this is obvious: upgrading from the default state will be the most thoroughly tested process by far.
> I really like the idea of containers, I see that you have a link to a guide :)
I've found this to be one of the best advantages of containers: almost all of my apps are now hived off into unprivileged containers. Therefore, the upgrade process sees my base system as simple and bare bones. There are no dependency conflicts or unexpected complexities, so version upgrades are a cakewalk.

If I want to upgrade the apps themselves, then I upgrade the containers (after making a snapshot first!). This process is also usually trouble&#8209;free. With those snapshots, it is certainly risk&#8209;free: if the upgrade goes sideways, I just roll back to the last good snapshot and I'm still up and running. In fact, the security that I'm getting from containers has given me the confidence to start reintroducing the odd PPA back into use. Prior to the sandboxing that I'm getting from containers, I had avoided PPAs for years due to security concerns.

A word of warning though: containers are not easy to implement. Once implemented, they give great advantages, but learning about them and getting familiar enough to work with them is difficult. It has been a multi&#8209;year process of learning for me, so please don't approach them as if they are a magic bullet.

---

### Post by demonenero84 on 2022-12-06
> **DuckHook said:**
> Please be careful about leaving your passwords floating out there in the cloud. I know that many people do this, but do you really want your bank account password "out there" in who&#8209;knows&#8209;where land?
You are absolutely right, sometimes I take an easy solution and underestimate the consequences :(
> **DuckHook said:**
> 
A word of warning though: containers are not easy to implement. Once  implemented, they give great advantages, but learning about them and  getting familiar enough to work with them is difficult. It has been a  multi&#8209;year process of learning for me, so please don't approach them as  if they are a magic bullet.
Ok I will do a few tests in a virtual machine ( I will simply copy my home folder to see if I can use my config files inside a vm ), take a look at timeshift and LVM. I prefer to avoid complex things like containers for now
Thanks a lot :)

---

### Post by DuckHook on 2022-12-06
Given that you are comfortable with VMs, implementing a LXD container may not be that difficult for you. I like your idea of trying first in a VM. LXD will work in a VM. So will Docker. Very safe and allows you to unscramble any eggs you make by accident.

---

### Post by demonenero84 on 2022-12-09
So I made a quick test:
I installed kubuntu 22.04 LTS in a virtual machine (I made the minimal install)
I made a script to remove unwanted apps and install all the apps that I use (including flatpak apps), It works fine but keeps asking "press Yes or no to continue" or "press enter to continue"
I copied the contents of my home dir to the vm home dir
It took about 30 minutes but at the and I had all my apps, my configuration files, bookmarks and saved passwords for firefox, thunderbird with my accounts (including my filters) and basically everything else (wallpaper, application launcher settings ...)
Is there a way to avoid pressing enter multiple times when my script runs?
Thanks a lot in advance

---

### Post by oldfred on 2022-12-09
Add -y to command.
see  this, not sure if also in apt or not.
I believe apt-get recommended for scripts & apt for command line use by user.
I also put multiple apps on one line so y only requested once. I like to see what dependenies are also installed.
I did to to prevent any apps from installing python2 when some apps still used it.

man apt-get
[FONT=monospace][COLOR=#000000]**-y**[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000]**--yes**[/COLOR][COLOR=#000000], [/COLOR][COLOR=#000000][B]--assume-yes


[/B][/COLOR]


[/FONT]

---

### Post by demonenero84 on 2022-12-09
Thanks a lot :)

---

### Post by TheFu on 2022-12-09
Please don't use browsers to share or retain passwords.  Get a proper password manager and use that.  Keep it decoupled from all the browsers.  

Browsers are some of the most complex software on our computers and they are full of bugs and security issues.  I suppose having your UbuntuForums login stored in the browser isn't THAT bad, but if you connect that account to systems management like Landscape offers or load Ubuntu Core (which forces using SSO keys), you've just lost control and opened the system to external hacks.

Never have your email passwords saved in a browser. Email is often a substitute for real credentials at many different online businesses.  If your email can be hacked (and it can), assume they will try to use that information to take over every other account they can find.  Banks, online shopping, Apple, MSFT, Google, department stores, everywhere.   This is why people need more than a single email account.  

Social network email needs to be very different from the email you use with banks and brokers and retirement accounts.  Probably needs to be separate from the email addresses you provide to family too and definitely separate from work and the email you interact with health care and separate again for the email you give to govt agencies.  Keep them all separate.  Don't use "Sign in with Googbook" options either.  All you need is for those companies to have more ways of tracking you around the web.  Until they pay me what they make from stealing my data, which is about $500/yr, they can't have it easily as far as I'm concerned.  Make it worth my while, and we can discuss access to specific data for short periods, but never forever.  That isn't what Bookoogle wants, so we have to agree to disagree.  I've gone nuclear with my blocking of tracking and 1st party sites. Blocked at the network layer.  They forced this by stealing data without asking.

I use a completely different email alias for every business I deal with.   Most people can't do this, but they can have 5 tiers of sensitivity for 5 email accounts and protect them as the correct sensitivity level.  Some are about the same, but just need to be kept separate.

It is very clear when spam comes in, which business was hacked, since they aren't supposed to be sharing any of my information with anyone else.  When I found that a credit card and airline had shared an email address, when I'd given each of them separate addresses, I called and complained.  They manually switched it back, but I had to make a big stink about it. Initially, they were certain they were helping me, when all they were doing was making connecting 2 completely separate businesses easier for them and the "bad guys".  

At this point, I have hundreds of email aliases, but really only about 5 email accounts.  I go out of my way to keep them separate and a few are changed annually, just to keep them guessing.  I have a few email accounts setup just for training my anti-spam tools.  I've placed those accounts on hidden parts of websites that no human would see, but data gathering tools do see them. By definition, any email they get is spam. Makes for excellent training.

Oh ... backup tools.  There are lots and lots.  I use rdiff-backup and have posted some simple scripts and how to restore a few times in these forums. I don't backup the entire system. If you search, you can find how I do restores, which will explain what I backup and why.  If my current desktop crashed right now, I'm confident that I could restore from a backup made around midnight in less than 30 minutes.  Desktop restores are pretty easy. Servers have more complex needs - takes me about 45 minutes to restore a server.  I need to say that 95% of the time, I don't need to restore the entire OS, just selected parts, so most issues are handled in just a few minutes with some data or config file restores.

---

### Post by demonenero84 on 2022-12-10
Thanks for the reply, I deleted my firefox account, I will remove my credentials from my browser

---

