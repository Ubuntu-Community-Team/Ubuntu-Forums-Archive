---
title: "Breezy - SUDO Problems-Admin Problems-"
date: 2005-10-27
forum: General Help
---

### Post by winxp2kubuntu on 2005-10-27
Just installed the long awaited Breezy. Everything went smooth during the install except for the wireless PCI not being detected(DlinkDWL-G510). 
Boot for the first time, everything looks great.
I decide to work on the network issues.Then the trouble begins. 
I cannot do any changes whatsoever to my network settings, cannot access administrator mode. I get "Su returned with an error" and back to the greyed out stuff.
So I go to a Terminal window and type sudo dhclient eth0.
I get another friendly message saying "unable to lookup (myhostname) via gethostbyname"
In Hoary, I got around fine as a Linux newbie and was just begining to get comfortable. In Breezy, I am now completely stuck.
I googled this issue and found several fixes, none of which worked.
In my efforts to migrate from XP to Linux, I was hopping Breezy would bring a couple of enhancements to Hoary, I suppose it did for some people, for me, it's the worst scenario ever. I do not possess enough command line knowledge to get around this problem. So I have to boot to Windows XP to look up fixes, then boot back to Breezy to attempt stuff, then go Back to XP again. HUGELY FRUSTRATING. What to do now?
Any help would be appreciated, I really like the KDE environment but it's absolutely useless to me without the most basic thing in the world, access to admin privileges. So I can hope to get another basic thing going, Internet connectivity. This is the second installation already and I am stuck with no idea what to do. I would love to have the old SUDO working again like in Hoary. Why did they ever change that? Security issues I imagine. But there was no warning.
Olivier
Montreal, Canada

---

### Post by Topsiho on 2005-10-27
I suddenly have this same problem in Breezy, which was not there before today (or maybe yesterday): everything was normal then and I could apply the updates, which now I can not (5 updates waiting).....

The command sudo results in:

sudo: unable to lookup Bromo via gethostbyname()

in which Bromo is my computername.

I found I am root when rebooting into recoverymode, so then I can change what needs to be changed.

Only thing is: what is to be changed that sudo works again? Of course after a normal boot.

:)  (which is nicer than :(   :)  )

Oh ja: do not go back to WinXP, but do keep it on your computer as an extra boot.
Working in Linux needs some adjusting and probably you have programs in Windows you (still) like to use, and some hardware that does not work with Linux. I have a Canon scanner which only works in Windows, and still have a kind of diary in Lotus Organizer which I would hate to discard (some day I'll have to oh horror :(  )


Topsiho

---

### Post by winxp2kubuntu on 2005-10-27
Well, I am sure this issue will be fixed soon because you and I are not the only ones. This is a MAJOR problem that NEEDS TO BE ADRESSED QUICK because the OS as it is installed now is of absolutely no use. 
I have heard some people mention editing such and such file, great idea, I wouldn't mind trying except I cant even edit anything since I don't have even temporary root privileges. This is awful, it's not an upgrade, it's a downgrade.
Olivier

---

### Post by Topsiho on 2005-10-28
I have solved my problem which I created myself. For me it's no use blaming Ubuntu (Breezy) :), I don't know about your problem :(

This is how I solved my problem, which was due to a faulty line in /et/hosts which I put there myself :confused: 

1. boot into recovery mode ===> makes you root, which is what is needed
2. fix this faulty line with a correct one, in my case:

<home network ip> Bromo.Brantas Brantas replaced with
<home network ip> Bromo.Brantas Bromo

(the computername is Bromo, not Brantas, which is the domain name)

3. restarted the computer in the normal mode (Linux of course :) )

and sudo worked again.

I want to stress the fact that I myself put the erroneous line into /etc/hosts
which I could only do assuming the rights of the administrator by using sudo: if one does that one should know one can destroy the system which a normal user usually can not....

I wish you good luck with correcting your problem.

Topsiho

---

### Post by winxp2kubuntu on 2005-10-28
And the nightmare continues:
Tried to start in recovery mode, when it asks for the root password, I type it and it refuses me.
I am then forced to hit CTRL-D to continue into a regular log on.
It takes me right back to Kubuntu without admin privileges
I cannot edit anything, any file whatsoever. How can this be, what is a newbie supposed to do when facing such a problem?
At the command, I have tried the folowing :
su  , I type my password and I get authentication failure
sudo kwrite /etc/sudoers to go modify the last line and I get "unable to look up ubuntu (my host name) via gethostbyname.
I also tried:
sudo passwd root, no luck there either. 
Damn it, I just want to be able to edit a stupid file, why is it such a problem?
I cannot remember when is the last time I was this frustrated with a new OS.
Not even windows.
COMPLETELY STUCK, NO IDEA WHERE TO GO FROM HERE. HELP !!!
I miss the old sudo in HOARY! Why take it away without warning?

---

### Post by winxp2kubuntu on 2005-10-28
Topsiho, Thanks for your suggestions. Nothing worked for me though. 
No admin = No network controls = no internet 
The result : A very pretty looking OS with absolutely no use. Oh, yes, I forgot, USB hard disks don't work either. Some upgrade. What a mess.
Olivier

---

### Post by Topsiho on 2005-10-28
I wish I could help you out in this.

However, my experience with the recovery mode is that I am root there straight away. No root password being asked to supply .....

Only thing that I can think of is that somewhere during the installation you made a mistake. You are mentioning a root password, but if you installed (K)Ubuntu as you were supposed to do then there is NO root password.

When sudo-ing a password is asked and the pasword you then give is your user password which you entered during the install.

I hate to say it, but It is in fact inot such an unusual procedure to do, in order to get things quite right: you'd better install all over again. In that process you can also correct other mistakes and misguesses. You LEARN by making mistakes, which should make you happy :)

Succes, and greetz from

Topsiho

---

### Post by winxp2kubuntu on 2005-10-28
Topsiho,
Thanks again for the encouragements, I am already at my 3rd install.
I think this distro is flaky. Or I am doing something wrong.
USB hard disks don't work, admin is a problem, and a ton of other things too. According to the forums, a lot of things seem to not work right in Breezy. 
My MD5 checksums are OK, verifyed a few times over. 
During the install, I was asked to create a username, and a password. In Hoary, that password gave me SUDO access to anything. IN Breezy, it's useless,any password prompt refuses it, so why did it ask me to creat one in the first place is a FRIGGIN mistery at this point.
I am not happy at all with this, I had high expectations for Breezy but so far, it's been a huge waste of my time. I wish there was more help available, some clear explanation that doesn't require massive knowledge of the Terminal command lines. I went from XP to Kubuntu because I was sick of Windows crashing for the most stupid tasks. Hoary was fine (Allthough it couldn't play Windows media, couldn't browse JAVA sites and a whole whack of other things which needed extensice tweaking) but Breezy doesn't do it for me. I am not looking for an OS that requires entire days of researching bug reports to accomplish stupid tasks like tweeking a network card setting. In Hoary, I could at least access those basic settings. Breezy is just not up to it. I am really upset because I thought this was finally a nice distro for newbies to migrate to coming out of XP. Forget it, at this point it's HELL. I don't have time to putz around with this stuff. I was just hoping for a non-microshaft OS that would let me surf the net and collect my email, and write Office documents, I don't ask for much. The only thing I can do is write Office documents. Everything else is out of reach. I have to be a unix guru to understand it seems. Well, I am not. I was getting comfy with Horay, and everything I learned in Hoary is useless in Breezy. 
Enough ranting. Maybe I'll wait a few months for a cleaner distro without all this hellish lack of basic functionality.
Olivier

---

### Post by leo898@gmail.com on 2005-10-28
Hey guys, 
I have been using kubuntu and have had many issues, so i decided to go back to kubuntu and install the KDE desktop. This probably dosnet help, but the following will, lol. 

Allright for those of you who need access to the root account, you will need to change the password of the root account. To do this go to the run command and type in sudo kcontrol - in there look for the user section, you will then need to select the show all users feature and find root, then change password. If you want to give yourself more temp privs just play around with it, sometimes it works and sometimes it dosnet. 

On other forums some of you might have had problems with USB drives not working. The problem with this, is that kubuntu detects the SDA device but every time u insert it into the system, a new id is assigned to to, e.g. sda1 , sda2. To fix this you will have to go into etc/fstab and edit the sda line, i will make a tutorial on this later.

Just rem that you should set the root password to edit anything, kubuntu is really messed up, and it takes a lot of editing, go kubuntu and install KDE.

---

### Post by Topsiho on 2005-10-29
Hello, it's me again :)

I am really sorry that winxp2kubuntu feels that Breezy is bad, especially after  he had better experiences with Hoary. I do not (yet) understand this, as I had the same experiences with Hoary as with Breezy.

In Hoary I created a root account with

sudo passwd root

and then entering a root-password. I have experience with some other distro' s and know how to use the root account. In (K)Ubuntu this was not the same however, so I now just work with sudo, which so far is the ONLY drawback I have with Ubuntu, which I find just great.

If Ubuntu is not what you expected you could try other rather user friendly distro' s such as Fedora (which is great, only be prepared to download tons of upgrades on a daily basis as it is experimental for  RedHat ) or Open Suse or so, or Knoppix which also can be installed on the hard disk, with some effort.

And if you really want to use Linux than you should know some about the command line, which is far easier than you seem to realize. With man <command> one always can get (it'strue, too much) information about a particular command. Using a graphical interface you have to dig and find the location of a particular task. which differs from one distro to another. Plus: the command line gives one far more flexibility.

:cool: If this is not fun to you then better stay with Windows, I am really sorry to say.:cool: 

If Hoary suited you better, then please go back to Hoary. Why go to Breezy if that just frustrates you back to a system that is frustrating you too?

An excellent guide to Linux (not only Ubuntu) is to be found at 

[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)


:)

Topsiho

---

### Post by kasl33 on 2005-12-03
I know it has been a few weeks since you all went through this, but the answer is simple.  Topsiho had it right in the first place, but there is an additional step you can take. 

While in recovery mode (which you get to by rebooting and pressing escape as soon as the GRUB menu comes up), you are the root user.  Enter this command and create a password for root:

passwd root

Enter a password and then verify it as it asks.  From this point on, if you have the problem, you can just su - and fix it from there.  It worked great for me.

---

### Post by Topsiho on 2005-12-04
Thanks for this addition, which tells us how to create a real root.

As far as I know this can also be done by:

sudo passwd root
and entering a password for root,

without rebooting into recovery mode.

For a reason I forgot I regretted doing this in a previous install, I am sorry I cannot really recall why. As I am used to having a root user, in other distro's, it must have been that I had the experience that not all this did work really as it should have.

Secondly, but you need not be hindered by this at all, the Ubuntu developers have a philosophy behind not creating a root user by default. They think (I think :) ) it safer for ordinary users to get root privileges only by sudo-ing, so they cannot forget exiting as root when they have finished doing what they did as root. Or worse: that they habitually work as root, so they can do things without the trouble of first becoming root. Which would Windo(un)wise ( <-- my creation, what do you ihink of it?) Ubuntu :mad: )

Topsiho

---

