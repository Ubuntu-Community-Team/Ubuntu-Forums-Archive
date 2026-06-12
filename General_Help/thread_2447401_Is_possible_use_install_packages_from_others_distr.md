---
title: "Is possible use install packages from others distros ?"
date: 2020-07-18
forum: General Help
---

### Post by aug7744 on 2020-07-18
I am new to Linux.
I see that softwares installs use file extension DEB, RPM, APPImage and others.
Each package type is for each distro or is possible to use all in Ubuntu ?
I see also that is all number of packages for Ubuntu that means that has more softwares for Ubuntu than others distro ?
Thanks for replay.

---

### Post by Paddy Landau on 2020-07-18
**First**

There is a newish system known as [snap]("https://snapcraft.io/"), and a competitor known as [flatpak]("https://flatpak.org/"). Where possible, I'd recommend that you use snaps (preferred by Ubuntu) or flatpak. For example, GIMP, LibreOffice and Zoom are all available as snaps, and DropBox as a flatpak. Snaps and flatpak are generally reliable, as they eliminate the dependency problems that you get from DEB installations, and you don't have to faff about with finding and adding PPAs.

EDIT: It seems that an [appimage]("https://appimage.org/") is a competitor to snaps and flatpaks, but I've never used one.

**Second**

Where an app isn't available through a snap or flatpak, you can use RPM with [alien]("https://wiki.debian.org/Alien"). Alien converts RPM and a few of others to DEB.
[LIST=1]
[*]Install [FONT=lucida console]alien[/FONT] (either through your Software Manager or with this command (unfortunately not available in a snap or flatpak):
```
sudo apt install alien
```
[*]Convert your downloaded RPM package to DEB with the following command (change "package" to the name of the package that you downloaded):
```
alien package.rpm
```
[/LIST]
It's rare indeed that you need to worry about doing this, because when there's an RPM, there's almost always a DEB.

---

### Post by TheFu on 2020-07-18
Yes, but it is not a good idea.  

Additionally, it is a bad idea for someone new to Linux who doesn't fully understand AND have a few years experience working with APT and dependency hell. You shouldn't do this.  Do not install RPMs. There are some tools which will do this, but it is a bad idea.

Now, you can use flatpak, snaps, and AppImages. Those are supposed to be distro agnostic.  Turns out they aren't, but at least they won't screw your APT dependencies up and trash the APT DB for every program on the system.  Those self-contained packages are supposed to include all required dependencies too - turns out they don't always.  I've had terrible luck with snaps where only 20% actually work.  But when they don't work, just use **snap remove**.  [LIST]
[*]Snaps really don't allow any control for local needs due to upstream constraints. Also, snaps update without asking just like Win10 does. How rude!
[*]Flatpaks are better, in that we can locally control the constraints or disable them.
[*]AppImages don't have any constraints. Sadly, they won't work by using a symbolic link to the file, but that's a minor inconvenience really.
[/LIST]
All three of these solutions are extremely bloated in both disk and RAM use, have slow startups or worse, make booting your Ubuntu system slow.
I avoid all of them whenever possible and seek out a trusted PPA.

Of course, it is your system and you should be free to use it as you like.  Please have a backup ready BEFORE you install any RPM or random .DEB files.  Things will probably be fine for a week or a month, but then the dependency issues will start and get drastically worse over time. By 3-6 months in, you won't be able to patch the OS at all, so reinstalling fresh will be the only option.

If you need a newer version of some program than what the Canonical repos provide, use a trusted PPA or snap or appimage or flatpak.  The PPA method extends the OS APT repo to include that PPA.  Which means if the PPA owner isn't trusted, she might do all sorts of nasty things to your setup.  But PPAs for specific projects run by the project are minimal risk.  After all, those projects created the .deb file which Canonical adds to their repos, so what's the difference?  OTOH, anyone - you, me, someone not very nice, can also create a PPA and modify some code in the programs. Sometimes those modifications are exactly what we want and sometimes those modification include extras we don't - perhaps a crypto-miner.

---

### Post by Paddy Landau on 2020-07-18
> **TheFu said:**
> … flatpak, snaps, and AppImages. Those are supposed to be distro agnostic.  Turns out they aren't…
I didn't know that! I've been using snaps and flatpak for only a relatively short while, and so far I've had good results. On the other hand, I've been sticking to reputable apps such as GIMP and LibreOffice. Are you able to give an example of a problematic app (for my never-ending curiosity)?
> **TheFu said:**
> … Please have a backup ready BEFORE you install any RPM or random .DEB files. … PPAs for specific projects run by the project are minimal risk…
Excellent points! I've stuck to PPAs from reputable projects, and for that reason I've hardly had problems. Even so, projects such as LibreOffice have given me the occasional problem while using their PPA, but not (so far) with its snap.

---

### Post by TheFu on 2020-07-18
VidCutter is one.  If I try to run it over X11 from a remote system, it fails, badly.  If I run it on the local system, it works.  The AppImage works both locally and over X11, so it is definitely a snap failure.

Chromium is another.  Same problem.
```
$ ssh -X regulus chromium-browser &
[1] 27705
X11 connection rejected because of wrong authentication.
[74721:74721:0718/095621.819118:ERROR:browser_main_loop.cc(1469)] Unable to open X display.

[1]+  Exit 1                  ssh -X regulus chromium-browser
```
But if I run any non-snap over ssh -X, they work as expected.  It is a failure of snaps.
```
$ ssh -X regulus xterm -sb & 
```
works perfectly.  There have been many more, but when they fail, I remove them and seek out a different solution. 

Snaps have all sorts of well-known problems that have been discussed in these forums to the point of ranting. I really recommend seeking those other threads out before you are burned by a snap refusing to work in a way you need - and you will be burned. Everyone will be, they just haven't hit a limitation yet.

BTW, your post above has lots of great information in it. I only worry that in this situation, your skills will understate what someone new to linux would need to know if/when things go south using an RPM.  I've been able to avoid APT-hell the last 10 yrs.  Around 2000, I did get a home RH server into RPM hell. Eventually, it was part of a reason that machine got hacked.

---

### Post by TheFu on 2020-07-18
Ouch - looks like the snap not working under remote X11 can be solved:
> $SNAP_USER_DATA/.Xauthority, which of course did not exist. I then ran: $ ln -s ~/.Xauthority ~/snap/brave/current/.Xauthority, tried again and it worked.
[https://forum.snapcraft.io/t/x11-forwarding-using-ssh/2381](https://forum.snapcraft.io/t/x11-forwarding-using-ssh/2381)

The fix of 
```
export XAUTHORITY=/home/thefu/.Xauthority
```
didn't work. but on the remote system where I want the program to run from, 
```
cd ~/snap/chromium/current
ln -s ~/.Xauthority
```
did work.  I'll need to add that to my ever-growing, how-to-hack snaps so they work file.  Maybe that will get vidcutter working too?  I often run programs on remote systems and have them display locally.

---

### Post by Paddy Landau on 2020-07-18
Thanks for all of that information, @TheFu.

I'm brand new to Appimages. Looking at them, I see two problems:
[LIST]
[*]I don't find many of my preferred apps (as far as I can tell, there's [a single list]("https://appimage.github.io/apps/") of them).
[*]They don't auto-update. I know that you don't like it, but for "average" users, auto-update is immensely useful.
[/LIST]
> **aug7744 said:**
> I see also that is all number of packages for Ubuntu that means that has more softwares for Ubuntu than others distro ?
I forgot to answer this question.

DEB packages are those that work on any [Debian system]("https://www.debian.org/") (hence the name "deb"). Those DEB files aren't made for Ubuntu; they are made for Debian.

However, any system that runs Debian, which includes Ubuntu and Ubuntu-based packages (there are many others), can therefore use DEB files.

Debian itself, and Debian systems, are highly popular (partly thanks to Ubuntu), which is why it's so well supported.

---

### Post by TheFu on 2020-07-18
Not all .deb files are created equal.  

While they include some dependency lists, then don't include all, so it is really easy to find a .deb file from 10 yrs ago, download it and attempt to install it.  If the user uses **sudo dpkg -i /path/to.file-versions.deb ** it will be installed, but without the dependencies.  Ok, so there's a fix for that - run **sudo apt install -f** and apt will try to resolve the dependencies and install them.  But those dependencies are for an old Debian release from 10 yrs ago. All the core libraries have been updated since then, so either the system has a package installed which doesn't work or, worse, apt "fixes" the dependency problems and replaces the current versions of those packages with 10 yr old ones.  1 program works, but 1000 others do not.  Now the entire OS is in "APT hell", because until the /path/to.file-versions.deb package gets removed, the dependencies will be screwed.  When we install a .deb file, it is very important to keep track of it, so when APT starts complaining in a month or 3 or 6, we can go through the list and remove those packages to fix APT's dependency problem.  Without that list, it is next to impossible to get out of APT-Hell short of doing a fresh install .... or restoring from a backup BEFORE the .deb file was installed.

I put the warning first.  Some .deb files ARE fine.  They were built for the specific release with the same core libraries as Ubuntu and the dependencies don't conflict with that Ubuntu release.  

Anyone who's run any Linux OS knows about these dependency issues or learns about them quickly.  All the distros have this same issue. Arch, Redhat, Fedora, Ubuntu-whatever, Oracle, Debian, Mint, PopOS, and the other 500 distros. We all have the same problem.  But when we choose to run a fully supported LTS version of Ubuntu, pretty much all desktop applications will target our release so it is safer.

Snaps, flatpaks, appimages were created in hope of preventing these dependency issues AND making a universal way to distribute software across the different distros.  Let's be honest, if you run Ubuntu 18.04 or 20.04, snaps have probably all been tested on those systems and should pretty much always work.  OTOH, I still run the supported 16.04.6 release. It meets most of my needs AND gets fewer patches since all the code has been around 4.5 yrs now.  But sometime before next April, I'll have to move all those machines off 16.04 to either 18.04 or 20.04 to keep security updates without hassle or paid support.

If any .deb file can install AND work onto any debian-based distro, then there wouldn't be a need for snaps, flatpaks, appimages.  Alas, there is the theory and then there is reality.  Reality screws up all sorts of things, right - except a freshly changed by someone else baby giggling. ;)  That reality is pretty awesome.  Sometimes Ubuntu is like that giggling baby - all is right in the world.  Then sometimes it is like a 2 yr old who learned "no" or a teen who hates her parents and says so, loudly, often.  But eventually, we get a 30 yr old Ubuntu (16.04) which has moved out and thinks we were brilliant parents.










er.  Perhaps not.  ;)

---

### Post by SeijiSensei on 2020-07-18
I doubt you'll need a package that exists as an RPM but not as a DEB.  Most every open-source application is ported to all the various distributions. If there's something you need that doesn't reside in an Ubuntu repository, let us know, and we'll see if we can help.  

Right now the only programs I know of that exist as RPMs but not as DEBs are those that use [OpenSSL]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=924937"). Ubuntu is based on [Debian]("https://www.debian.org/"), which has especially strict licensing rules, and its developers have a problem with the OpenSSL license.

---

### Post by aug7744 on 2020-07-19
Unhappily I see that the diversification is killing the Linux because has peoples waiting to known that system and has several distros thus being very difficult to choice and also that problem with packages.
I had tried to known Slackware, but is full of commands and not is better to go it.
I am an advanced Windows user and that problem doing the system more slow when installing much softwares also is in Windows. Several duplicates files spread in folders and softwares allways starting with the system making more slow and less RAM available.
I will download Lubuntu to test and see my experience.
Unhappily I need some Windows softwares that not has in Linux, but if is possible WINE or other software run each Windows software without problems I not will return to Windows.
Another detail that I see is has games, emulators and others types that not is in Linux because exactly of diversification of several distros that does more work and the programmer coder not wait it. Is much work to create and update.

REPLY EDITED BY MODERATOR because I say my "good" experience with other OS. Not offense or bad level words. Nothing of create war between users.

---

### Post by CatKiller on 2020-07-19
> **aug7744 said:**
> I am an advanced Windows user 

This is your fundamental problem, and is why you're struggling. And why you're trying to download random files from the Internet, and why you think you need to poke around in the filesystem. 

Many Windows users find it very uncomfortable to discover that they only know about Windows, rather than computing as a whole, and that all their instincts are wrong. All the people that have successfully switched to Linux from Windows have got over that hump, but there are plenty of people that are unable to expand their knowledge, or to understand that Linux isn't Windows. If you still expect Linux to be *Windows, but not from Microsoft* I can tell you right now that it isn't, and won't ever be. If you want to successfully use Linux then you need to stop doing Windows things; if you want to do Windows things you should do them on Windows.

---

### Post by Paddy Landau on 2020-07-19
> **TheFu said:**
> &#8230; it is really easy to find a .deb file from 10 yrs ago, download it and attempt to install it.
That's why we avoid those old ones. Stick to reputable and well-maintained systems. If I find an app that I want, but hasn't been maintained in six months or longer, I find an alternative.
> **TheFu said:**
> Sometimes Ubuntu is like that giggling baby&#8230;
I love your metaphor!
> **aug7744 said:**
> Unhappily I see that the diversification is killing the Linux&#8230;
As @CatKiller says, you're coming from a Windows-think. In fact, the diversification is precisely what stimulates Linux. Without competition, Linux would still be a backwater specialist niche, or might have died out. Instead, it's used throughout the world, on most supercomputers, web servers, smartphones (Android runs on Linux), routers, IOT, handheld devices, Kindle, TV set-top boxes, and more. MacOS and iOS (iPHones and iPads) run on Unix, which is an older sister of Linux. Only desktops and laptops have more Windows than other operating systems.
> **aug7744 said:**
> I had tried to known Slackware&#8230;
For a beginner, Ubuntu (or one of the official Ubuntu flavours) is the best way to start on Linux.
> **aug7744 said:**
> I will download Lubuntu to test and see my experience.
Lubuntu is excellent on older systems. I have been using Lubuntu on my old machine for a long time. Windows is too slow, but Lubuntu copes OK.
> **aug7744 said:**
> Unhappily I need some Windows softwares that not has in Linux, but if is possible WINE or other software&#8230;
Try [PlayOnLinux]("https://www.playonlinux.com/"). It takes away a lot of the difficulty in using Wine. To install PlayOnLinux, either use your software centre or enter the following command.
```
sudo apt install playonlinux
```
PlayOnLinux is also available as a flatpak, if you prefer.

Be aware that while PlayOnLinux works well for a few Windows programs, there are usually a lot of problems. If you need Windows apps on a day-to-day basis, it might be better for you to stay with Windows and forget about Linux.
> **aug7744 said:**
> Another detail that I see is has games, emulators and others types that not is in Linux because exactly of diversification of several distros that does more work and the programmer coder not wait it. Is much work to create and update.
You are still thinking of Windows. To update Windows, you have to go to Windows Update. Then you have to open (say) Chrome and run its updates. And Adobe Acrobat. And&#8230; and&#8230; and&#8230;

But, if you install apps correctly in Linux, **all** updates are automatic. Once you install an app, you never have to worry about updating it.

How do you do this?
[LIST]
[*]As far as possible, stick with Linux apps. That Windows app that you want&#8230; is there a Linux replacement? For example, if you want Photoshop, try [GIMP]("https://www.gimp.org/") instead. Do you want Word, Excel, PowerPoint? Try LibreOffice (Writer, Calc and Impress) instead. (GIMP and LibreOffice both work on Linux, Windows and MacOS.) And so on. Most Windows apps have a free equivalent for Linux.
[*]Always install apps the Linux way. Use your package manager (that's Synaptic Package Manager on Lubuntu). Or, find the correct PPA, add it, and install from there (again, use your package manager for this). Or, use a snap or flatpak.
[*]Don't use Appimage, because they don't automatically update.
[*]Don't download a DEB file and install it, because it won't automatically update.
[/LIST]
Let's use an example: GIMP. Here are six different ways to install GIMP.
[LIST=1]
[*]Download the DEB and install it. *Updates won't be automatic. Also, there are DEBs with adware or malware that you might accidentally find.*
[*]Download the Appimage and run it. *Updates won't be automatic.*
[*]Install from your package manager. *Updates are automatic. This is the easiest  and most reliable way, but updates might be significantly delayed.*
[*]Find the official PPA. Add the PPA and install GIMP using your package manager. *It can be difficult to find the correct PPA, and you run a risk of finding a PPA with malware. But, updates are automatic.*
[*]Install GIMP using snap. *Updates are automatic.*
[*]Install GIMP using flatpak. *Updates are automatic.*
[/LIST]
Can you start to see how Linux is very different from Windows?

---

### Post by TheFu on 2020-07-19
Everyone new to Linux goes through the same struggle to shift "how things work" from whatever they used previously. We all did.

Centralized package management has been part of Debian for 22+ yrs. These packages from repos are cryptographically signed by the project team who created them.  That is verified automatically for us when we use the package manager. All the bits are correct.

Some '.deb' files will also add their PPA to the system as part of the install.  I which I knew a way to tell when/if that will happen or not BEFORE doing the install.  Best to just say using the official version of a package from the main Canonical repos.  
While these may not be the newest version from the project team, Canonical does backport any security fixes to all supported Ubuntu Releases, usually within 1-2 days.  
From a security standpoint, this is what we want.  
From a business standpoint, we don't want while new updates getting installed on our systems, so having the same productivity software, just patched for security or major bugs that impact millions of users is all we want.  We don't want the newest version released 2 days ago by the developers, which include new bugs.

It isn't hard to control when Ubuntu patches for APT stuff, if you don't want new software versions magically installed daily.  Unfortunately, snaps don't provide a way to block their updates short of using a DNS black-hole solution.  I only want new software during maintenance periods, not in the middle of my work day.

If you want to better understand what files go where on any Linux system, there is a standard that all major Linux distros follow: [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)  IMHO, it is worth a 30 second look at the table and reading the top-level directories.  It will make things so much clearer than the Windows method.

Lubuntu is more like WinXP from a GUI standpoint.  But the GUI is just another program. The differences between each Ubuntu "flavor" is just that GUI, the login control screen and the default installed applications and tools.  We are free to install other GUIs, other software, from anywhere in the Ubuntu family for the same release.  
It is possible to have multiple GUIs on the same system at the same time. Some of those GUIs use the same underlying GUI libraries, so the configuration DB + files might have some conflicts. The way to ensure that doesn't happen is to use different userids for each GUI while you look around at each.  Linux is multi-user from the beginning. It doesn't care whether 1 person or 20,000 people use the same system. Settings are almost always stored per-userid ---- well, unless you go out of your way to have them shared, which is necessary for some process control systems in control centers around the world.

There are lots of GUIs.  People seem to love or hate the default Gnome3 system.  There are other Win7-like GUIs - Mate, XFCE, KDE, Cinnamon. It really comes down to personal preference.  If you want an extremely lite GUI, which provides control over everything, those are available too, but those settings are all controlled using text config files.  I use one of those ... which I found in the mid-1990s and used for years.  Just a few years, I decided to run it again and it has gotten the GUI out of my way to get work done.

Whenever we use "apt" or "apt-get" in these forums, don't think that is the only way to manage software on Debian/Ubuntu systems. There are pretty GUIs and you should feel free to use whichever of these tools you like. It is fine to use one, then another, then another.

[https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) is from 2014, but still relevant for Windows user initial acclimation to Linux.

We all started somewhere.  Slackware was my 2nd Linux disto.  At the time, it was considered extremely user friendly compared to others - AND it was.  Things are so much better today.  We have GUIs.

We have many, many, choices that have never been available previously.  **Linux is all about choice**, but that makes it hard for someone new without a friend to provide initial guidance and help the first few months.  We all need someone to answer those thousands of questions in the beginning.  Many people really new to Linux like Linux-Mint, which is separate from Canonical, but based on Ubuntu.  Mint has decided against including snap support by default. Besides that, it feels like any other Ubuntu Flavor just with a slightly different GUI.  In my LUG (Linux User Group), we have a few die-hard Mint fans. Mint releases are usually based on an LTS Ubuntu release.  Just something to consider.

You might find yourself asking "why" something is the way it is.  Trust me, there is a reason. **There is always a reason.**  Lots of really smart people came before us.  Almost anything you can imaging needing a solution for has already been solved.  It may not have been solved the way you expect or want (coming from Windows), but it was most likely solved in a highly efficient way that lends to being automated.  Come at each problem seeking a solution, not the method or steps and you'll be very surprised.  Logical people want solution steps to follow what they believed was the best way.  When someone is new to Unix systems, that seldom turns out well. We all had to learn to think the Unix way.  My short attempt at explaining the difference with a common pattern for solutions: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

Every time I have to use Windows, I've learned to just click "next, next, next" because whenever I over think the correct answer, it doesn't work out so well.  Fortunately for me now, there are only a few Windows applications that I still need to use. BTW, I was a Windows software developer for about a decade, so a little more than a power user, but not an admin.  Administration on Windows is just too hard compared to Unix-like OSes.  Today, I only admin about 15 systems but there was a time when I was the admin for hundreds of Unix systems, in addition to my role as a commercial software developer for Windows and about 12 Unix platforms.  By far, we spent more time on a single Windows platform to get things working than on all the Unix versions. By far - perhaps 3x more effort on Windows.

Wow, we've bounced all over the place with this thread.  Good questions. Hopefully, the different answers are helpful.

---

### Post by Paddy Landau on 2020-07-19
> **TheFu said:**
> The differences between each Ubuntu "flavor" is just that GUI…
… and the amount of memory. After loading apps like Chrome, Ubuntu doesn't fit within my system's RAM, whereas Lubuntu does.
> **TheFu said:**
> It is possible to have multiple GUIs on the same system at the same time. … The way to ensure that doesn't happen is to use different userids for each GUI while you look around at each.
Man, I wish that I knew that years ago! My attempts at having multiple GUIs have never worked well.
> **TheFu said:**
> [https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](https://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) is from 2014, but still relevant for Windows user initial acclimation to Linux.
I've not seen that page. It's pretty good, though it could do with a few updates.
> **TheFu said:**
> Administration on Windows is just too hard compared to Unix-like OSes.
This reminds of the pre-PC days (I'm that old). We had mainframes. The big name was IBM. It ruled the computer world, and was ridiculously complicated. A single IBM mainframe needed a team of people to keep it running. A single Burrows mainframe (one of the big competitors) needed just one person, part time. From everything that I saw, I concluded that IBM's almost-monopoly held back the computer world. When Microsoft took over from IBM, again, I concluded that Microsoft's virtual monopoly was holding back the computer world.
> **TheFu said:**
> Wow, we've bounced all over the place with this thread.  Good questions. Hopefully, the different answers are helpful.
It's been fun! Thank you, @Agoaug7744, for your thread! I hope that you've realised that things are a lot simpler than you thought. You just need the right way of looking at things.

---

### Post by monkeybrain20122 on 2020-07-19
> **aug7744 said:**
> Unhappily I see that the diversification is killing the Linux because has peoples waiting to known that system and has several distros thus being very difficult to choice and also that problem with packages.
.

It is very easy for beginners, just stick to one distro (Ubunu and derivatives are easy) and don't try to install packages from other distros.

---

### Post by monkeybrain20122 on 2020-07-19
> **Paddy Landau said:**
> I didn't know that! I've been using snaps and flatpak for only a relatively short while, and so far I've had good results. On the other hand, I've been sticking to reputable apps such as GIMP and LibreOffice. Are you able to give an example of a problematic app (for my never-ending curiosity)?

Excellent points! I've stuck to PPAs from reputable projects, and for that reason I've hardly had problems. Even so, projects such as LibreOffice have given me the occasional problem while using their PPA, but not (so far) with its snap.

Gimp from both snap and flatpak cannot access external plugins. Try to open a raw file. If you install a .deb you only need to install darktable (from deb) and gimp will find it, but gimp snap or flatpak throws an error. I never tried installing gimp from .deb and darktable from snap or flatpak to see if it works but doubt it (gimp doesn't work with darktable called from a wrapper script, for example)

I have not run into dependencies problems for flatpak on an older OS (16.04), never tried snap there. But some appimages don't work because they do use external dependencies (you can extract an appimage and run the bin or the startup script in the terminal and see which libraries it tries to load and fails) Strawberry provides an appimage but can't make it work in Ubuntu 16.04, I ended up compiling, it is much easier than tinkering with the appimage, supposedly if you know the exact versions of the runtime libraries you can add those by hand and then just run the bin or the startup script, whether repackage it as an appimage or not.

---

### Post by sudodus on 2020-07-19
Thanks for a very interesting thread :-)

I will link to it in order to let more people share it.

---

### Post by Mark Phelps on 2020-07-19
@aug7744

Do NOT depend on Wine to run ANYTHING of Windows.  Most of the stuff in the WineHQ database is listed as running poorly or not at all.

IF you're moving to Linux, then: MOVE TO LINUX!  Stay away from Wine.

IF you're going to rely on Wine for running Windows stuff, then stay with Windows.

---

### Post by grahammechanical on 2020-07-19
I do not agree that diversification is killing Linux. Install a distribution and then install software through the distribution's software store and very little can go wrong.

Diversification has created the Linux many of us know and love. If we wanted to be locked in to one corporation's computer operating system we would all be using Microsoft's Windows and using only the applications provided by that corporation and we would be paying for the privilege without actually owning the operating system or applications we paid for. And I have not forgotten Apple Corporation either.

You complain about the incompatibility between rpm and deb packaged applications but really you would like to run Windows applications in Linux without paying the Microsoft "tax." I do not fault you for that. It is the reason why I use Wine to run a Windows application that is distributed without charge and does not have a Linux equivalant.  

The idea behind Free and Open Source Software (FOSS) is to do things differently from Microsoft and not to imitate Microsoft. The Wine developers are limited in what they can achieve and it is not because they are not good at what they do but because Microsoft is not open about the way its software works.

Regards

---

### Post by aug7744 on 2020-07-20
Thanks very much for all replies.
My previous reply was edited because I had posted that is "bad an system" that freeze for more of 1 minute even having more 2 GB RAM free only using internet browse. Nothing of bad words or etc against users.

@CatKiller
"Many Windows users find it very uncomfortable to discover that they only know about Windows, rather than computing as a whole, and that all their instincts are wrong. All the people that have successfully switched to Linux from Windows have got over that hump, but there are plenty of people that are unable to expand their knowledge, or to understand that Linux isn't Windows. If you still expect Linux to be Windows, but not from Microsoft I can tell you right now that it isn't, and won't ever be. If you want to successfully use Linux then you need to stop doing Windows things; if you want to do Windows things you should do them on Windows."

Yes I understand that Linux not is Windows.
Simply I want to has all and any software packages downloaded saved in my local disk because I use an internet metered access and if not is possible to do it totally in Linux is bad detail that need to be fixed.
I had posted in previous reply about how I never have an good experience using Windows and was removed. Never was exactly good for me.
Peoples that say Windows is good are almost allways hardcore users that wait to buy powerful cpu and gpu to say that has an powerful machine that run high requirement software and latest games in high resolution with high details plus high frame rate being the detailt that I more see in all users that say anything "good" about Windows.
Linux in other hand I say see users saying the is more fast and has "all" when is saying about if has or not video editing software or others software in Linux.
The other detail is users saying about details about distro and trying help to "help" to spread Linux and new users trying to known Linux has difficulties to choice the correct distro and version doing thus much time downlading and testing distro that is the "detail" I say more ahead.
Nothing bad or against Linux.

@Paddy Landau
"As @CatKiller says, you're coming from a Windows-think. In fact, the diversification is precisely what stimulates Linux. Without competition, Linux would still be a backwater specialist niche, or might have died out. Instead, it's used throughout the world, on most supercomputers, web servers, smartphones (Android runs on Linux), routers, IOT, handheld devices, Kindle, TV set-top boxes, and more. MacOS and iOS (iPHones and iPads) run on Unix, which is an older sister of Linux. Only desktops and laptops have more Windows than other operating systems."

Yes stimulate to use Linux, but all diversification if in extreme number create problems.

"Lubuntu is excellent on older systems. I have been using Lubuntu on my old machine for a long time. Windows is too slow, but Lubuntu copes OK."
My fisrt experience is that is really fast how you is saying.

"Try PlayOnLinux. It takes away a lot of the difficulty in using Wine. To install PlayOnLinux, either use your software centre or enter the following command."
I not wait to play games. Only some current softwares that I not see in Linux.

"Be aware that while PlayOnLinux works well for a few Windows programs, there are usually a lot of problems. If you need Windows apps on a day-to-day basis, it might be better for you to stay with Windows and forget about Linux."
In moment I not wait to not use Linux and perhaps in future versions WINE and playonlinux will run almost perfect Windows software.

"But, if you install apps correctly in Linux, all updates are automatic. Once you install an app, you never have to worry about updating it. Can you start to see how Linux is very different from Windows?"
When is installed programs in Linux all is installed in own folder not spreading files over the disk or how is in Windows in several folders ?
Look to be similar how is cell phones.

"and the amount of memory. After loading apps like Chrome, Ubuntu doesn't fit within my system's RAM, whereas Lubuntu does."
Lubuntu here is using 384 MB from an fresh install without anyting installed.

@Thefu
"There are lots of GUIs. People seem to love or hate the default Gnome3 system. There are other Win7-like GUIs - Mate, XFCE, KDE, Cinnamon. It really comes down to personal preference. If you want an extremely lite GUI, which provides control over everything, those are available too, but those settings are all controlled using text config files. I use one of those ... which I found in the mid-1990s and used for years. Just a few years, I decided to run it again and it has gotten the GUI out of my way to get work done."

In the link [https://www.openoffice.org/dev_docs/source/sys_reqs_aoo41.html](https://www.openoffice.org/dev_docs/source/sys_reqs_aoo41.html) the requirements to use OpenOffice is X-Server and has others software that say requirements GNOME3.
That means if is installed one software in Lubuntu that need GNOME3 the default XFCE not will start the software ?
I not see problems if fot some task to be configured using text files instead of Windows registry.

"Every time I have to use Windows, I've learned to just click "next, next, next" because whenever I over think the correct answer, it doesn't work out so well. Fortunately for me now, there are only a few Windows applications that I still need to use. BTW, I was a Windows software developer for about a decade, so a little more than a power user, but not an admin. Administration on Windows is just too hard compared to Unix-like OSes. Today, I only admin about 15 systems but there was a time when I was the admin for hundreds of Unix systems, in addition to my role as a commercial software developer for Windows and about 12 Unix platforms. By far, we spent more time on a single Windows platform to get things working than on all the Unix versions. By far - perhaps 3x more effort on Windows."

EXACTLY is one of my main becuse to swtich to Linux.
Microsoft try to show that Windows is easy to use (for an user that not wait to be an programmer) and has good support to users and developers being that not is exactly true. See the high number of users in official Windows forums not having replies and some times having non sense replies from Microsoft that the same default reply "use restore tool, use chkdsk and etc" and the user has an clue or an solution from others users that reply to the topic. Good reply even you will have in non official forums.
You say that is an programmer. Microsoft had done an good support to previous Xbox 360 console, but is all about competition against Sony.
I can say Windows is more complex than Linux in almost all even from user configuration to programmer that need to learn several APIs to do the even that Linux does using less code and in other hand LInux is more work to configure.
That is my experience with Windows in all years and few experience with Linux.
In moment my difficulties are about configure settings, understand how softwares are downloaded to be installed and device drivers. Others details are more simple to figure.

@monkeybrain20122
"It is very easy for beginners, just stick to one distro (Ubunu and derivatives are easy) and don't try to install packages from other distros."
In moment is one of my difficulties in use Linux.
Windows you install an program and if need dependences (VC redistributable) is easy to install.
One package not work exactly in all distro and need to convert and see that has chance of create problems.
Softwares packages are files where is the software install and each package is one type of install method where for an distro ?
Software packages not has compatibility that all distros because inside files (similar to DLLs in Windows ?) are an not are required for all distros and have distros that the software not run because the software package not have inside the need files to run thus need to the user to figure which files need to be installed in system ?

@Mark Phelps
"IF you're going to rely on Wine for running Windows stuff, then stay with Windows."
Is possible that Windows will run correctly in WINE future versions.

@grahammechanical
"I do not agree that diversification is killing Linux. Install a distribution and then install software through the distribution's software store and very little can go wrong."
I not see possible to user install software from repositories and save to local disk avoiding download again from internet.

"The idea behind Free and Open Source Software (FOSS) is to do things differently from Microsoft and not to imitate Microsoft. The Wine developers are limited in what they can achieve and it is not because they are not good at what they do but because Microsoft is not open about the way its software works."
WINE has problems because coders not have enough information about the Windows and thus need to figure trying information in software developer tools ?
If yes will have much time to run correctly Windows in Linux.
The main because that I wait to use WINE is because government and banks software are more for Windows than Linux. Is problem for me say to any friend that need both software types to try Linux.

Look how the Linux system partition is much better than Windows where is more simple to figure where is the system files.
Linux distro had to be more simple to configure to begginer and users that only wait to use computer to access internet.
I have downloaded current geforce drivers to install in Lubuntu. The driver file has an run extension and perhaps see that not is will be simple to install.
Others strange details is that I not see how to change color in taskbar and window title and if is possible to change with an own choice not using themes not is simple to figure where is the configuration GUI and file manager not is simple to browse how is Windows File Manager.
Yes Linux not is Windows, but some softwares had to be more easy and simple to use to any Linux users.
An file manager where you browse using only one window and need to do much more command to see files than simple browse how if Windows File Manager ?
Look how some softwares are a few done to be challenger to users.
Lubuntu file manager file browsing not is simple. I want to browse using left panel and see each folder in right panel thus is simple and fast to see where is files than an more complex browse that does to be more difficult to understand how folder directories and removable disk drives are displayed and the real path values of the each one.

Today I not fell good to use Windows ... have alternatives ....
Anyone with good sense who understands problems that are occurring in "places" and where is the root not feeling well using a product derived from that origin.
I not wait to create war. I not see bad to say it.

Linux creator say that avoid Ubuntu and the choice Fedora where say "Debian is hard to install". Even him saying about the best distro need to figure what exactly him is saying. He not will say exactly all.
I not see hard to install Ubuntu how him is saying.
Nothing against Ubuntu mainly because I had watched youtube videos about Debian creator. Look to be an good man, He "not had" an sad look , but unhappily ...

Have distro "fighting" against Debian distros ? Ubuntu is the more used distro. If yes is the because of "bad reviews" about Ubuntu ? More of half of false wrong reviews are from Ubuntu users that were Windows users that not understand how Linux work ? Is high the number of wrong posts about Ubuntu distros and more worst are web sites trying to help new Linux users to choice distros and youtubers that not understand how hardware and system work where is an mess creating problems to choice one distro having some users give up to try Linux.
I had tried known Ubuntu Debian and see several post spread in internet randomly about good and bad about Ubuntu and even before of install Lubuntu more of 70 % of post about "bad details" about Ubuntu are not sense even for me in my begginner Linux experience.
I need to say again, but only difficulties are about how softwares are downloaded and installed, software package types and few others details.

I need to say UBUNTU FORUM IS MUCH MORE FRIENDLY THAN official Microsoft forums.
Thanks very much for read my reply and have an nice week.

---

### Post by CatKiller on 2020-07-20
> **aug7744 said:**
> I have downloaded current geforce drivers to install in Lubuntu. The driver file has an run extension and perhaps see that not is will be simple to install.

This is the kind of Windowsism that will cause you problems. You install software by using the package manager, not by downloading files from some random website. There's a tool to identify, download and install the proprietary driver required by Nvidia hardware, already included with your install. 

To answer some of your other questions, packages downloaded through the package manager are cached so that you don't need to download them again if you need to reinstall them for some reason. Files are sorted by function rather than origin: configuration files are in one place, documentation is in one place, binaries are in one place, libraries are in one place. You don't need to poke around in them.

---

### Post by TheFu on 2020-07-20
Gnome3 is both the name of a DE, but it generically refers to a set of cross-platform libraries used to build software. Before Gnome3 libraries, we had Gnome2 libraries. Before that, we had just "Gnome" libraries.  I have a prediction - "Gnome4" will be the next major release of the libraries in 2-7 yrs. Those are the layman terms.  In reality, GTK and GTK+ are the "gnome libraries" use to build not just the DE, but all the Gnome-based programs on our systems.

On my 20.04 desktop:
```
$ dpkg -l|grep gtk|grep common
ii  libgtk-3-common                       **3.24**.20-0ubuntu1                    all          common files for the GTK graphical user interface library
ii  libgtk2.0-common                      **2.24**.32-4ubuntu4                    all          common files for the GTK graphical user interface library 
```
So both GTK3 and GTK2 libraries are installed.  That was automatic, either by the installer or when I asked for a program built using those to be installed.

On a 16.04 desktop:
```
$ dpkg -l|grep gtk|grep common
ii  libgtk-3-common                             **3.18**.9-1ubuntu3.3                               all         common files for the GTK+ graphical user interface library
ii  libgtk2.0-common                            **2.24**.30-1ubuntu1.16.04.2                        all         common files for the GTK+ graphical user interface library

```

These are sometimes called "toolkits" as well.  The KDE toolkit is Qt. There are multiple versions of it, but it seems only Qt5 is installed on my systems.  Programs that begin with "K" - like "Kate" or Konqueror tend to be built using Qt libraries.  Programs that begin with a 'g' 0r 'gnome-' use the GTK toolkit.  **gedit** is a gnome-based editor. **Kate** is a Qt-based editor.  Why does this matter?  If you don't have much RAM, making a choice to avoid one or the other toolkit will mean those libraries don't get loaded into RAM. These toolkits are large, multiple hundreds of MB of RAM is needed.  But programs built using the same toolkit and version will share that code in RAM, so there's only 1 copy for all 20 programs using it. This assuming a "shared library" is used at compile time, which is common.  Shared libraries on Linux are .so files.  Look in /usr/lib/ to see those. On Windows, they are .dll files.

**Can we run programs that use a different toolkit?** Yes. If you have plenty of RAM, I doubt you'd even notice any performance difference running both sorts of programs.

---

### Post by monkeybrain20122 on 2020-07-20
> **aug7744 said:**
> i
@monkeybrain20122
"It is very easy for beginners, just stick to one distro (Ubunu and derivatives are easy) and don't try to install packages from other distros."
In moment is one of my difficulties in use Linux.
Windows you install an program and if need dependences (VC redistributable) is easy to install.
One package not work exactly in all distro and need to convert and see that has chance of create problems.
Softwares packages are files where is the software install and each package is one type of install method where for an distro ?
Software packages not has compatibility that all distros because inside files (similar to DLLs in Windows ?) are an not are required for all distros and have distros that the software not run because the software package not have inside the need files to run thus need to the user to figure which files need to be installed in system ?


The rpm, deb etc are just packaging formats for easy distribution. The packages are tailored for the distro and the version of the OS so even a deb from a different distro (say Debian) or a different Ubuntu release may not be installable or if it does may work differently (mostly for things like tool bars and buttons which depend on the DE) 

But in Linux if you want fine grain control you don't go around downloading bits and pieces randomly from the web, you should compile from source. This is not something Windows users usually do since a lot of their software doesn't offer source code. The same software can be compiled on different linux platforms and made to behave somewhat differently depending on how you configure your build.

---

### Post by monkeybrain20122 on 2020-07-20
> I have downloaded current geforce drivers to install in Lubuntu. The  driver file has an run extension and perhaps see that not is will be  simple to install.

If you are not experienced you should use the prepackaged driver from the repo rather than installing the .run file. If the official repo doesn't have the new version you can always use the graphic driver [ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"). Add the source to your repository and you can just install it like other software. You may have to install the .run file for other distros but Ubuntu is easy. Linux caters to users with different levels of experience and want different levels of control, if you have the time and the expertise you can even build a whole OS and the software from ground up (see Linux from Scratch aka LFS)

It seems you are making your experience more difficult because of your Windows habit.

The supposed ease to install Windows software has nothing to do with MS or Windows being a "better" platform, but because software developers package their stuffs for Windows so they can reach most users. McDonald's probably has more customers than other restaurants, doesn't mean it offers the best food.

---

### Post by aug7744 on 2020-08-09
Thanks very much :)

---

### Post by Paulgirardin on 2020-08-18
> **aug7744 said:**
> Thanks very much :)

I'll make a couple of suggestions:

Use Libre Office instead of Open Office. Libre Office was forked from Open Office and has had far more development.
Most Linux distros have Libre Office already installed.

Depending how much Windows software you need to run, consider using a Virtual Machine running in Linux with a Windows version running on it.

I have a friend who won't switch from Photoshop so I installed Win7 in Gnome Boxes VM for him to run PS on from inside Ubuntu.

This worked well on a 2 core 1600 MHz system.

Gnome boxes seems to run better than Virtual box.

---

### Post by Paddy Landau on 2020-08-19
> **Paulgirardin said:**
> This worked well on a 2 core 1600 MHz system.
That's impressive. How much RAM on his system?

Thanks for the notes about Gnome boxes; I hadn't heard of it. I've always used VirtualBox.

I see that Gnome Boxes is available on Flathub. Do you have a recommendation for a tutorial for Gnome Boxes?

---

### Post by Dennis N on 2020-08-19
> Gnome boxes; I hadn't heard of it. I've always used VirtualBox. I see that Gnome Boxes is available on Flathub. Do you have a recommendation for a tutorial for Gnome Boxes? 
You also can find Boxes in Ubuntu (Gnome). It's in the Ubuntu repository.
_Compared to Virt-Manager:_
[https://arstechnica.com/gadgets/2020/04/virtualization-on-the-linux-desktop-gnome-boxes-vs-virt-manager/](https://arstechnica.com/gadgets/2020/04/virtualization-on-the-linux-desktop-gnome-boxes-vs-virt-manager/)
Lots of how-tos on the Internet.

---

### Post by Paddy Landau on 2020-08-19
> **Dennis N said:**
> You also can find Boxes in Ubuntu (Gnome)…
Thank you!

---

