---
title: "Trying Lubuntu 20.04 LTS..."
date: 2021-08-31
forum: General Help
---

### Post by wyattwhiteeagle on 2021-08-31
I'm trying Lubuntu20.04 LTS

I know about the Lubuntu Manual and Forums at [https://lubuntu.me](https://lubuntu.me)
Seems a bit confusing to me.

How do I disable or delete the other 3 desktops that is default enabled?
I only need one desktop.

Does QTerminal accept the same command lines as Ubuntu's?

How do I "add to favorites"?

How do I get to the "Applications Panel"? You know, the dot square where you can click on whatever app you want to open and use.

Is there a tool like Nautilus for Lubuntu?
(I don't think I spelt that correctly)

Is Synaptic Package Manager good for Lubuntu?

It seems quite different from the regular Ubuntu.

In Ubuntu, it's called Software Center...but in Lubuntu, it's Discover.

Lubuntu doesn't use gedit. Lubuntu replaces it with FeatherPad.

I'm not sure what replaces Thunderbird Mail.

---

### Post by wyattwhiteeagle on 2021-09-01
> There are currently 6572 users online. 19 members and 6553 guests

Oh, c'mon...

You mean this thread has been here about 3 hours and not 1 of the 6571 other users online can at least give some kind of response?

---

### Post by Impavidus on 2021-09-01
I don't use Lubuntu myself, but I'll answer some of your questions.
> **wyattwhiteeagle said:**
> 
Does QTerminal accept the same command lines as Ubuntu's?
Mostly.
There are three "layers" involved in the terminal. The top layer is the terminal program: QTerminal, gnome-terminal, xfce4-terminal, konsole, xterm, many others. Those are just an interface between your screen, keyboard and mouse on one side, and the text based application on the other side. All terminal programs are fairly similar and don't affect what commands you can run.
The next layer is the shell: bash, dash, sh, csh, some others. This layer processes command lines, sets up redirection of input and output, handles filename globbing, shell variables, starts the tools you want to run from command line etc. It's actually capable enough to be used as a complete script interpreter. Ubuntu and Lubuntu typically use the same shell in the terminal, bash.
The third layer are the tools you run in your terminal: mv, cp, rm, wget, gcc, sudo etc. Every tool in the Ubuntu repositories can be installed in every Ubuntu flavour, but the different flavours don't install the same set of tools by default. Some tools don't make sense on some flavours. For example, the command line tool that allows me to set my desktop wallpaper on Xubuntu wouldn't be useful on Lubuntu. But there is a core set of tools that you can expect to be present on every flavour.
> Is there a tool like Nautilus for Lubuntu?
Every flavour has a file manager.

> Is Synaptic Package Manager good for Lubuntu?Synaptic package manager handles .deb packages. All Ubuntu flavours (and all other Linux distros in the Debian family) are based on deb packages and Synaptic works for all of them.

> It seems quite different from the regular Ubuntu.

In Ubuntu, it's called Software Center...but in Lubuntu, it's Discover.Synaptic is quite different from Software Center. Synaptic doesn't hide technical details, making it more powerful but also more intimidating to new users. Synaptic only handles .deb packages, Software Center also handles some others like snaps. I don't know about Discover.

> Lubuntu doesn't use gedit. Lubuntu replaces it with FeatherPad.There are many text editors. All of them are good for editing text.

> **wyattwhiteeagle said:**
> Oh, c'mon...

You mean this thread has been here about 3 hours and not 1 of the 6571 other users online can at least give some kind of response?
It's Wednesday morning in Europe and middle of the night in America. Not the time when you expect the most active users on the forums. Don't expect those 6500 random passers-by to reply.

---

### Post by tea for one on 2021-09-01
> **wyattwhiteeagle said:**
> Oh, c'mon...
You mean this thread has been here about 3 hours and not 1 of the 6571 other users online can at least give some kind of response? 
Apologies for the tardy response, I was having breakfast in bed - cup of tea and lightly buttered toast with whisky marmalade.
> **wyattwhiteeagle said:**
> 
I know about the Lubuntu Manual and Forums at [https://lubuntu.me](https://lubuntu.me)
Seems a bit confusing to me.

[highlight]Is there a tool like Nautilus for Lubuntu?[/highlight] > [https://manual.lubuntu.me/stable/2/2.4/2.4.4/pcmanfm-qt.html](https://manual.lubuntu.me/stable/2/2.4/2.4.4/pcmanfm-qt.html)

[highlight]I'm not sure what replaces Thunderbird Mail.[/highlight] > [https://manual.lubuntu.me/stable/2/2.1/2.1.5/trojita.html](https://manual.lubuntu.me/stable/2/2.1/2.1.5/trojita.html)

The Lubuntu manual looks like a very comprehensive document to me.

---

### Post by guiverc on 2021-09-01
> **wyattwhiteeagle said:**
> 

How do I disable or delete the other 3 desktops that is default enabled?
I only need one desktop.



There is only one desktop; LXQt. 

The **Lubuntu** session includes all the Lubuntu modifications/scripts to it, ie. it's LXQt plus.

The **LXQt Deskto**p session is a purer upstream version of the LXQt, ie. without the Lubuntu modifications that we document in our manual.

Thus the first two are both the LXQt desktop.

LXQt is a WM *agnostic* desktop; and Lubuntu has chosen to use `**openbox**` as it's WM. We've also given the end-user the option to use it without the LXQt desktop if they wish since it's installed; a WM needs to be installed for LXQt to operate.

They are variations of the Lubuntu system giving you more choice; but needing no more packages/space/RAM than if they weren't available.

> **wyattwhiteeagle said:**
> 

Is there a tool like Nautilus for Lubuntu?


LXQt uses `pcmanfm-qt` as it's file-manager, as it's super light & efficient on the LXQt desktop (*it's the program that actually draws & handles your desktop so it's already in memory, using it as a file-manager won't use anything beyond what's really needed to operate your system*).

FYI:  You say you know about the manual; but also note there are two copies of the manual offered; the *stable* which is the the latest *stable* release (ie. 21.04 currently), plus the *lts* version which covers Lubuntu 20.04 LTS currently.

For the Lubuntu 20.04 LTS manual use [https://manual.lubuntu.me/lts/](https://manual.lubuntu.me/lts/)


> **wyattwhiteeagle said:**
> 
Is Synaptic Package Manager good for Lubuntu?
..
In Ubuntu, it's called Software Center...but in Lubuntu, it's Discover.
..
Lubuntu doesn't use gedit. Lubuntu replaces it with FeatherPad


It won't be efficient and will waste resources. It was included with Lubuntu releases up to Lubuntu 18.04 LTS, as it made sense then, but it doesn't with any release from 18.10 onwards.

Synaptic can be used yes, but it'll require your system to load & use multiple libraries that do the same thing, ie. Qt5 *libs* for the desktop & LXQt apps, and GTK3 *libs* just for `synaptic` to run.  That's why Lubuntu comes with [Muon Package Manager]("https://manual.lubuntu.me/lts/4/4.2/muon.html") (*it will use libraries/toolkits that are shared with the desktop itself*).

if you've enough RAM - you can use whichever you prefer.

The same applies with Software Centre vs Discover.  Kubuntu & the latest release(s) of Ubuntu Studio also use Discover & Muon, as it's more efficient sharing Qt5 toolkit/libraries that are used by the desktop itself.  Again if you've loads of RAM, you can use whichever you prefer.  FYI: KDE uses the same Qt5 *libs* as LXQt does.

The same applies with Featherpad; it shares the same Qt5 libs that are needed to operate your desktop, where as using `gedit` would mean you'd need to load additional libraries wasting RAM; not a problem if you've heaps, but leaving less for apps (eg. web browsers) which are better with more.

> **wyattwhiteeagle said:**
> 
It seems quite different from the regular Ubuntu.


Fair enough - to me it's the same system, with just a different GUI (graphic user interface) that I as a user control; but an identical system underneath where it matters.

I consider this system a Ubuntu one; even though I'm using LXQt & Lubuntu currently. On my box I have the option to logout & switch to GNOME (Ubuntu), or Xfce (Xubuntu) when I log back in, but I'm strange I guess (*don't mind bloating my system for the days when I want something different to my usual Lubuntu/LXQt system*).

---

### Post by wyattwhiteeagle on 2021-09-01
> **Impavidus said:**
> I don't use Lubuntu myself, but I'll answer some of your questions.

Mostly.
There are three "layers" involved in the terminal. The top layer is the terminal program: QTerminal, gnome-terminal, xfce4-terminal, konsole, xterm, many others. Those are just an interface between your screen, keyboard and mouse on one side, and the text based application on the other side. All terminal programs are fairly similar and don't affect what commands you can run.
The next layer is the shell: bash, dash, sh, csh, some others. This layer processes command lines, sets up redirection of input and output, handles filename globbing, shell variables, starts the tools you want to run from command line etc. It's actually capable enough to be used as a complete script interpreter. Ubuntu and Lubuntu typically use the same shell in the terminal, bash.
The third layer are the tools you run in your terminal: mv, cp, rm, wget, gcc, sudo etc. Every tool in the Ubuntu repositories can be installed in every Ubuntu flavour, but the different flavours don't install the same set of tools by default. Some tools don't make sense on some flavours. For example, the command line tool that allows me to set my desktop wallpaper on Xubuntu wouldn't be useful on Lubuntu. But there is a core set of tools that you can expect to be present on every flavour.

Every flavour has a file manager.

Synaptic package manager handles .deb packages. All Ubuntu flavours (and all other Linux distros in the Debian family) are based on deb packages and Synaptic works for all of them.

Synaptic is quite different from Software Center. Synaptic doesn't hide technical details, making it more powerful but also more intimidating to new users. Synaptic only handles .deb packages, Software Center also handles some others like snaps. I don't know about Discover.

There are many text editors. All of them are good for editing text.

It's Wednesday morning in Europe and middle of the night in America. Not the time when you expect the most active users on the forums. Don't expect those 6500 random passers-by to reply.

> **tea for one said:**
> Apologies for the tardy response, I was having breakfast in bed - cup of tea and lightly buttered toast with whisky marmalade.

[highlight]Is there a tool like Nautilus for Lubuntu?[/highlight] > [https://manual.lubuntu.me/stable/2/2.4/2.4.4/pcmanfm-qt.html](https://manual.lubuntu.me/stable/2/2.4/2.4.4/pcmanfm-qt.html)

[highlight]I'm not sure what replaces Thunderbird Mail.[/highlight] > [https://manual.lubuntu.me/stable/2/2.1/2.1.5/trojita.html](https://manual.lubuntu.me/stable/2/2.1/2.1.5/trojita.html)

The Lubuntu manual looks like a very comprehensive document to me.

Thanks for the info.

Tea, toast, and whisky marm...sounds like a breakfast of champions.

I was installing Lubuntu while the responses came in.

Apparently, I´m under the impression that Lubuntu doesn´t use Gnome.

How do I limit/prevent the collection of temporary files in Lubuntu?

Can someone help with a Ubuntu/Lubuntu Equivalent List?
(Please ee quote below.)

> Ubuntu.......................Lubuntu

Software Center........Discover Software
Thunderbird Mail.......BlueDevil Mail
Gedit.........................FeatherPad
Favorite´s.................QuickLaunch

Ubuntu tool´s I haven´t found in Lubuntu...

System Settings
System Monitor
Disk´s
Disk Usage Analyzer
Gparted

---

### Post by wyattwhiteeagle on 2021-09-01
> **guiverc said:**
> There is only one desktop; LXQt. 

The **Lubuntu** session includes all the Lubuntu modifications/scripts to it, ie. it's LXQt plus.

The **LXQt Deskto**p session is a purer upstream version of the LXQt, ie. without the Lubuntu modifications that we document in our manual.

Thus the first two are both the LXQt desktop.

LXQt is a WM *agnostic* desktop; and Lubuntu has chosen to use `**openbox**` as it's WM. We've also given the end-user the option to use it without the LXQt desktop if they wish since it's installed; a WM needs to be installed for LXQt to operate.

They are variations of the Lubuntu system giving you more choice; but needing no more packages/space/RAM than if they weren't available.



LXQt uses `pcmanfm-qt` as it's file-manager, as it's super light & efficient on the LXQt desktop (*it's the program that actually draws & handles your desktop so it's already in memory, using it as a file-manager won't use anything beyond what's really needed to operate your system*).

FYI:  You say you know about the manual; but also note there are two copies of the manual offered; the *stable* which is the the latest *stable* release (ie. 21.04 currently), plus the *lts* version which covers Lubuntu 20.04 LTS currently.

For the Lubuntu 20.04 LTS manual use [https://manual.lubuntu.me/lts/](https://manual.lubuntu.me/lts/)




It won't be efficient and will waste resources. It was included with Lubuntu releases up to Lubuntu 18.04 LTS, as it made sense then, but it doesn't with any release from 18.10 onwards.

Synaptic can be used yes, but it'll require your system to load & use multiple libraries that do the same thing, ie. Qt5 *libs* for the desktop & LXQt apps, and GTK3 *libs* just for `synaptic` to run.  That's why Lubuntu comes with [Muon Package Manager]("https://manual.lubuntu.me/lts/4/4.2/muon.html") (*it will use libraries/toolkits that are shared with the desktop itself*).

if you've enough RAM - you can use whichever you prefer.

The same applies with Software Centre vs Discover.  Kubuntu & the latest release(s) of Ubuntu Studio also use Discover & Muon, as it's more efficient sharing Qt5 toolkit/libraries that are used by the desktop itself.  Again if you've loads of RAM, you can use whichever you prefer.  FYI: KDE uses the same Qt5 *libs* as LXQt does.

The same applies with Featherpad; it shares the same Qt5 libs that are needed to operate your desktop, where as using `gedit` would mean you'd need to load additional libraries wasting RAM; not a problem if you've heaps, but leaving less for apps (eg. web browsers) which are better with more.



Fair enough - to me it's the same system, with just a different GUI (graphic user interface) that I as a user control; but an identical system underneath where it matters.

I consider this system a Ubuntu one; even though I'm using LXQt & Lubuntu currently. On my box I have the option to logout & switch to GNOME (Ubuntu), or Xfce (Xubuntu) when I log back in, but I'm strange I guess (*don't mind bloating my system for the days when I want something different to my usual Lubuntu/LXQt system*).

This is a great help.
Thank´s a bunch.

In the install process, for the keyboard layout, I´m accustomed to seeing ¨English (US)¨ in both lists of choices. I didn´t see it in the 2nd list in Lubuntu. I chose the ¨US, Int¨
I think I did something wrong because when I hit the apostrophe/quotation key, I´m actually having to pound on the key to get it to type correctly.

When I dont pound on the key the onscreen output look&#347; like that s with the mark above the letter.

How do I get the keys to work right for my region...Western hemisphere USA region New York time zone.

---

### Post by guiverc on 2021-09-01
> **wyattwhiteeagle said:**
> 
In the install process, for the keyboard layout, I´m accustomed to seeing ¨English (US)¨ in both lists of choices. I didn´t see it in the 2nd list in Lubuntu. I chose the ¨US, Int¨
I think I did something wrong because when I hit the apostrophe/quotation key, I´m actually having to pound on the key to get it to type correctly.

When I dont pound on the key the onscreen output look&#347; like that s with the mark above the letter.

How do I get the keys to work right for my region...Western hemisphere USA region New York time zone.

There is/was a English (US), and as a *dumb* aussie, I'm happy to accept it, or the English (Australian) if so offered (ie. internet is connected) as they are the same.

In fact (*a fact which suits you perfectly*), as Lubuntu uses the `calamares` installer; it's default timezone & keyboard setup is that of New York, New York USA, meaning the default suits you pretty well  (*if you don't have internet connected; it'll pick your defaults anyway!*)

To change your default keyboard layout; have a look at the manual, or

[https://manual.lubuntu.me/lts/3/3.2/3.2.8/keyboard_and_mouse.html](https://manual.lubuntu.me/lts/3/3.2/3.2.8/keyboard_and_mouse.html)

(go down to *Keyboard Layout* on the page)

---

### Post by GhX6GZMB on 2021-09-01
I'm running Lubuntu since 2019 and I like it a lot! 18.10, 19.10 and now 20.04 LTS.
It's lightweight and easy to use, but you'll need to throw a bit of Win and Gnome ballast overboard.

Completely basic (I don't want to insult you here), but the Applications Menu is the blue dot in the lower left corner of the screen (like Win "Start" menu).
You'll find all installed applications/programs here. You can drag them onto the desktop if you like for executing from there.

I've never used "Discover" myself, I find it pretty useless, but that's because I already know what I want to install on my system.

For updates I use Synaptics "sudo apt update, sudo apt upgrade" and PPAs, but also the muon Package manager. They work well together.
Same for installs. I mostly use muon, but there are programs where entering the PPA directly is easier.
I stay far away from snaps, the first thing I do after a fresh install is to purge snapd (using muon, of course).

QTerminal, Featherpad, PCManFM-Qt etc. are all great, no problems.

For customizing your desktop, "Preferences -> LXQt settings" is your friend.

The issue with the 4 desktops is a little tricky and non-intuitive. You set this under:
"Preferences -> LXQt settings -> Openbox Settings" (click "desktop" when you get there).

Feel free to ask further questions. Cheers.

---

### Post by wyattwhiteeagle on 2021-09-01
> **ml9104 said:**
> I'm running Lubuntu since 2019 and I like it a lot! 18.10, 19.10 and now 20.04 LTS.
It's lightweight and easy to use, but you'll need to throw a bit of Win and Gnome ballast overboard.

Completely basic (I don't want to insult you here), but the Applications Menu is the blue dot in the lower left corner of the screen (like Win "Start" menu).
You'll find all installed applications/programs here. You can drag them onto the desktop if you like for executing from there.

I've never used "Discover" myself, I find it pretty useless, but that's because I already know what I want to install on my system.

For updates I use Synaptics "sudo apt update, sudo apt upgrade" and PPAs, but also the muon Package manager. They work well together.
Same for installs. I mostly use muon, but there are programs where entering the PPA directly is easier.
I stay far away from snaps, the first thing I do after a fresh install is to purge snapd (using muon, of course).

QTerminal, Featherpad, PCManFM-Qt etc. are all great, no problems.

For customizing your desktop, "Preferences -> LXQt settings" is your friend.

The issue with the 4 desktops is a little tricky and non-intuitive. You set this under:
"Preferences -> LXQt settings -> Openbox Settings" (click "desktop" when you get there).

Feel free to ask further questions. Cheers.

Thanks for that info,
I was wonderin when you'd stop by.

Ubuntu-Extended-Extra's, There are a few...maybe only 4 at the most...windows apps that are important to me.
Me being completely new to Lubuntu and somewhat "new" to Ubuntu...is Extended Extra's good for Lubuntu?

File History Tracking. In Lubuntu, How do I get to where I can disable it?

Trying to set a wallpaper, the part where you add the file path is grayed out like it's been disabled.
How can I enable it?

Resource Usage. I like to keep the resource usage as low as possible.
In Windows it's fairly easy to tell which settings are needed to maintain a low resources use.
Ubuntu and Lubuntu, not quite so easy for me.
In Ubuntu, I tried Stacer. It seemed to not save my custom settings and when I uninstalled it, System Monitor in Ubuntu seemed to have been "different".
Almost like in Windows when something gets uninstalled.
Sometimes the Uninstalled doesn't revert back to the original settings.
That's where a "Restore Point" comes in.(Restore Points are for another thread, though crucially important for my situation)

What are some good settings to keep the resource Usage at a safe minimum?

---

### Post by grahammechanical on 2021-09-01
> Apparently, I´m under the impression that Lubuntu doesn´t use Gnome.

It doesn't. Utilities that are part of the default Ubuntu install are Gnome applications. Installing them on Lubuntu is possible but doing so would bring in a lot of libraries and running them would use up more memory that the default utilities of Lubuntu.

As I understand it the philosophy of the LXQt developers is to produce a Desktop Environment that minimizes the use of hardware resources. The Lubuntu developers have a similar philosophy. Which is to take Ubuntu and replace the Gnome Desktop Environment with the LXQt Desktop Environment. For many years Lubuntu was the choice for older hardware that could not meet the demands of the latest versions of Ubuntu. A lot of people use Lubuntu because they like the style of the desktop user interface even though they have modern machines.

By the way, I do not think that GParted is included in any default installation of Ubuntu and its favours. GParted is a powerful tool that used incorrectly can break an OS. This is why it cannot be used on the operating system it is running on. GParted is included in the Ubuntu live session. I think the same must be true of the Lubuntu live session. We manage our partitions from a live session. There is no need for a Lubuntu equivalent to GParted.

Regards

---

### Post by wyattwhiteeagle on 2021-09-01
> **grahammechanical said:**
> It doesn't. Utilities that are part of the default Ubuntu install are Gnome applications. Installing them on Lubuntu is possible but doing so would bring in a lot of libraries and running them would use up more memory that the default utilities of Lubuntu.

As I understand it the philosophy of the LXQt developers is to produce a Desktop Environment that minimizes the use of hardware resources. The Lubuntu developers have a similar philosophy. Which is to take Ubuntu and replace the Gnome Desktop Environment with the LXQt Desktop Environment. For many years Lubuntu was the choice for older hardware that could not meet the demands of the latest versions of Ubuntu. A lot of people use Lubuntu because they like the style of the desktop user interface even though they have modern machines.

By the way, I do not think that GParted is included in any default installation of Ubuntu and its favours. GParted is a powerful tool that used incorrectly can break an OS. This is why it cannot be used on the operating system it is running on. GParted is included in the Ubuntu live session. I think the same must be true of the Lubuntu live session. We manage our partitions from a live session. There is no need for a Lubuntu equivalent to GParted.

Regards

Thank you for that.

When using the installed session, I used Gparted only to see the details of volumes and partitions.
I never used it to try editing the volume it was installed on while in an installed session.
I ain't claiming to have much sense here but I would be senseless to even consider doing that.

So, not using the cli "sudo lshw", how can I see these "other" details in a LXQt GUI?

---

### Post by guiverc on 2021-09-01
> **wyattwhiteeagle said:**
> Ubuntu-Extended-Extra's, There are a few...maybe only 4 at the most...windows apps that are important to me.
Me being completely new to Lubuntu and somewhat "new" to Ubuntu...is Extended Extra's good for Lubuntu?

File History Tracking. In Lubuntu, How do I get to where I can disable it?

Trying to set a wallpaper, the part where you add the file path is grayed out like it's been disabled.
How can I enable it?

Resource Usage. I like to keep the resource usage as low as possible.
In Windows it's fairly easy to tell which settings are needed to maintain a low resources use.

..

What are some good settings to keep the resource Usage at a safe minimum?

`ubuntu-restricted-extras` is installed in my system, and I see nothing that would impact any Ubuntu *flavor*, especially Lubuntu.  (ie. [https://packages.ubuntu.com/focal/ubuntu-restricted-extras](https://packages.ubuntu.com/focal/ubuntu-restricted-extras))

File tracking - sorry I don't know what you mean so cannot help there

The wallpaper can be changed (see [https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html?highlight=wallpaper](https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html?highlight=wallpaper)) but sorry the feature isn't as great as it is in later releases (the *focal* version starts in the wrong directory so it's not pointing anywhere that's helpful. Navigate to other directories (wherever you have downloaded wallpapers, or the included ones in /usr/share/lubuntu/wallpapers/ )

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   ls /usr/share/lubuntu/wallpapers/
2004-city-bridge.jpg         2004-lubuntu-solid-humming.jpeg  2104-leaves.png                lubuntu-default-wallpaper.png
2004-city-sky.jpg            2004-lubuntu-wire-fossa.jpg      2110-friends-dark.png
2004-lubuntu-background.png  2004-lubuntu-wire-humming.png    2110-waves-dark.png
2004-lubuntu-logo.png        2104-blue-logo.png               lubuntu-default-wallpaper.jpg
```

Note: I'm on *impish* so have different ones, but the location is the same (ie. /usr/share/lubuntu/wallpapers/)

In other messages I saw mention of `gparted` which Lubuntu included up to 18.04 (as it made sense on releases then), but was replaced with KDE Partition Manager.

If you contrast

- [https://packages.ubuntu.com/focal/gparted](https://packages.ubuntu.com/focal/gparted)
- [https://packages.ubuntu.com/focal/partitionmanager](https://packages.ubuntu.com/focal/partitionmanager)

you'll note the requirements of the programs, ie. for `gparted` you'll see things like

```
[libgtk-3-0]("https://packages.ubuntu.com/focal/libgtk-3-0") 	 (>= 3.0.0)         
GTK graphical user interface library         

```

ie. it assumes a GNOME type system is running, meaning it cannot share and libraries used by the LXQt desktop - this will waste RAM when it is used (and a short time after it until the system has cycles available to clear it away).  If you've plenty of RAM, it's not a problem; esp. on tools like `gparted` that you use rarely, and not for very long really anyway.

In contrast the KDE Partition Manager uses

```
[libqt5core5a]("https://packages.ubuntu.com/focal/libqt5core5a") 	 (>= 5.12.2)          [amd64]
Qt 5 core module         
                          	[libqt5core5a]("https://packages.ubuntu.com/focal/libqt5core5a") 	 (>= 5.5.0)          [not amd64]
                          	[libqt5gui5]("https://packages.ubuntu.com/focal/libqt5gui5") 	 (>= 5.7.0)         
Qt 5 GUI module         

```

ie. Qt5 libs as used by the LXQt desktop; ie. good chance your box will already have those in memory so won't be filling RAM with libraries that do the same thing slightly differently.

If you don't want to use a browser & look up links like I provided (easy to read on sights like this), you can query your system via command, ie. the following shows the dependency requirements of `gparted`

```
apt-cache depends gparted
```

I personally still use boxes with 1GB of RAM, and on those boxes (old x86 thinkpads) I'm careful with what I have running at the same time.  I used those boxes to test Lubuntu releases up to 19.04, but out minimal test environment is 2GB now and that's only a single box (most testing is on 4GB or more) 

I just consider which *libraries* and *toolkits* (ie. GTK3 or the gimp+gnome toolkit ver 3, or Qt5 or Q toolkit ver 5;* fyi: the owner of Qt5 wants it pronounced Cute-5 as that's supposed to be smile worthy*) that will be used, and ensure whatever I use will share the libraries.

I'm very careful on boxes with 4GB and less (ultra-careful in fact on 2GB or less), somewhat careful on 5GB too, but tend to not worry on boxes with >6GB of RAM. 

My box is a 2009 dell desktop (*no i-series cpu on this box; too old*), running Lubuntu *impish* (*our next release*), but I'm still using `hexchat` I've used for *yonks* (a GTK2 program), my mail MUA (*mail user agent or email program*) is still `evolution` being GTK3 or a GNOME program, as is my RSS reader (`liferea`) both being what  I used back in GNOME 2/GTK2 days. With my  8GB of ram I can afford the hit with what I do; but when I need more RAM I just switch to workspace 2 & close both those GTK3 apps.  I'd not use those apps if this box had less RAM though.

For me, I consider the background of the apps (liferea & evolution are GTK3/GNOME3 apps, hexchat is GNOME2/GTK2 & ancient & I gotta kick that one!) and consider it before I load them, mentally calculating what I have running, what it'll use and what will need to be loaded (at least `liferea` & `evolution` use the same libs so the real hit is when the first is loaded)

---

### Post by wyattwhiteeagle on 2021-09-01
> [COLOR=#000000]File tracking - sorry I don't know what you mean so cannot help there[/COLOR]
[I][I]
...

In other messages I saw mention of `gparted` which Lubuntu included up to 18.04 (as it made sense on releases then), but was replaced with KDE Partition Manager.

If you contrast[/I][/I]

I'm not meaning to seem contrasting. I sincerely apologize.
Sometimes my overloading mouth can remove all doubt about my senselessness.

File Tracking. I mean keeping record of recently viewed, etc. Um...I'm probably thinking cache's, logging...

Maybe I'm accepting a bit of a conspiracy theory about Microsoft here.
Microsoft tries to keep some of the folders "hidden" and "secret" from the user, as if it's some kind of "Top Secret and Confidential Black-Op" by Microsoft.

---

### Post by guiverc on 2021-09-01
> **wyattwhiteeagle said:**
> 
Microsoft tries to keep some of the folders "hidden" and "secret" from the user, as if it's some kind of "Top Secret and Confidential Black-Op" by Microsoft.

GNU/Linux is a ***unix* ***like* system, which has become POSIX today.

All files/directories that start with a "." are treated as hidden. No special file-system attribute exists in POSIX file-systems by default; the usage just allow  some *usually non-user friendly* files to remain hidden.  If you've used a OSX mac; being a POSIX compliant OS (*hey apple paid $s so they can call it unix too*) it's the same there too.

If you use `ls` to view your files, then contrast with `ls -a` (ie. the -a tells it to list ALL files) you'll see the *hidden* files.

Cookies and the like (*thinking browsers*) used to be readily found when there were stored in simple text files, but now they're hidden away in databases so the cookies are harder to find.  If you want protection so one browser can not read the cookies (*database entries*) of another browser, consider running your browsers in containers, ie. use *snaps*.

Lubuntu offers firefox in *deb *by default, but if you `snap search firefox` you'll find it available. Chromium is now only available via snaps for Ubuntu, so it runs in it's own container (*and cannot access files from other snaps or your file-system outside of specific areas anyway*).  Note: I'm no expert here, and can think of various questions I'd ask with what I've written (different *confinement* models I've ignored etc) but I get long...

---

### Post by wyattwhiteeagle on 2021-09-01
Thank you a bunch

A main problem I'm having...
Apparently, I don't know how to search for things.

When I google something...I'm thinking in this manner...
> "Lubuntu 20.04 lts permanently disable or uninstall bluetooth"

I include the quotation marks in the search.

It gives all kinds of results about Ubuntu, Linux, etc.
It's taking hours upon hours for me to find just one that is known to work for Lubuntu 20.04 LTS.

It causes me to resort to asking questions here on the forums.

---

### Post by wyattwhiteeagle on 2021-09-01
> **guiverc said:**
> GNU/Linux is a ***unix* ***like* system, which has become POSIX today.

All files/directories that start with a "." are treated as hidden. No special file-system attribute exists in POSIX file-systems by default; the usage just allow  some *usually non-user friendly* files to remain hidden.  If you've used a OSX mac; being a POSIX compliant OS (*hey apple paid $s so they can call it unix too*) it's the same there too.

If you use `ls` to view your files, then contrast with `ls -a` (ie. the -a tells it to list ALL files) you'll see the *hidden* files.

Cookies and the like (*thinking browsers*) used to be readily found when there were stored in simple text files, but now they're hidden away in databases so the cookies are harder to find.  If you want protection so one browser can not read the cookies (*database entries*) of another browser, consider running your browsers in containers, ie. use *snaps*.

Lubuntu offers firefox in *deb *by default, but if you `snap search firefox` you'll find it available. Chromium is now only available via snaps for Ubuntu, so it runs in it's own container (*and cannot access files from other snaps or your file-system outside of specific areas anyway*).  Note: I'm no expert here, and can think of various questions I'd ask with what I've written (different *confinement* models I've ignored etc) but I get long...

In particular, I'm thinking of folders like "Recent" in Windows.

In Lubuntu, is bleachbit able to be used?
(someone may have already mentioned something about this and I just didn't catch it)

---

### Post by guiverc on 2021-09-01
> **wyattwhiteeagle said:**
> 
A main problem I'm having...
Apparently, I don't know how to search for things.


I'll give my 2c worth.

I tend to ignore the Lubuntu for most searches; I've said before I think of my system as a Ubuntu one, so I'd use `ubuntu` in my search unless it was desktop (ie. LXQt) specific, or a LXQt desktop app.


I don't use google (unless I've failed using startpage/duckduckgo etc & am forced to, as I won't use anything google in my firefox browser; so a google search requires me to switch to another browser)

For your example, my first search would likely be with

```
bluetooth ubuntu 20.04 site:*.ubuntu.com
```

ie. keyboards **ubuntu**, the release **20.**04 and **bluetooth**.

I'd also limit the first search to official guides, thus the `**site:*.ubuntu.com**`bit..  I'd expand to others, IF i couldn't find official documentation that was helpful, OR what was there wasn't modern enough thus I was forced to go wider.

As stated, if it was desktop specific, I'd not bother with the Lubuntu or LXQt. If I wanted a Lubuntu search, I'd use instead something like `bluetooth ubuntu 20.04 site:*.lubuntu.me`  (*I didn't even swap out ubuntu to lubuntu you'll note*)

Bluetooth though is most base OS stuff; so the Lubuntu isn't unique, except how it's operated using the GUI/desktop itself. I'm not a bluetooth user sorry, so I've never explored how it operates, nor how unique/common the Lubuntu bluetooth code is.

--

I can't / won't answer the next one sorry.  I last really supported windows in the XP days; so my knowledge is out-dated, with me having no need to keep *up-to-date* there.  I've also not used `bleachbit` so can't offer any assistance in that area either.

---

### Post by wyattwhiteeagle on 2021-09-02
I don't like bluetooth.
To me personally, I feel like Bluetooth or anything like it is a waste.

I'd rather uninstall it and not allow it back on.

I just haven't figured out how to prevent full-upgrade from re-installing it.

I don't like mail clients either. (ie, Thunderbird and the like)
Yahoo.com or something similar is my forte on mail.

---

### Post by guiverc on 2021-09-02
> **wyattwhiteeagle said:**
> I don't like bluetooth.
..
I'd rather uninstall it and not allow it back on.

I just haven't figured out how to prevent full-upgrade from re-installing it.


You can look at the *depends* rules via links or commands I tried to highlight in a prior message, ie.

[https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)

shows a number of *depends* (*recommends* too) requirements that Lubuntu will re-install (or if you force install for some of them, they'll force removal of the lubuntu-desktop package).

I tend to just leave such packages alone.  Yes you can force them to *go away*; but this usually prevents a *release-upgrade* when that time arrives, and it's a royal pain unless you specifically remember what you did to stop those packages from being installed; as you'll need to install/upgrade them to allow *release-upgrade* to occur.. ie. I choose to just ignore them rather than have issues come 22.04 upgrade time


FYI: You can add a `--no-install-recommends` to install commands to stop the *recommends* from installing.

---

### Post by GhX6GZMB on 2021-09-02
I'm with guiverc here: if there's something you don't like, just don't use it. Leave it as is, removing things causes more trouble than it's worth.

The resource manager is called Htop.

---

### Post by wyattwhiteeagle on 2021-09-02
> **ml9104 said:**
> I'm with guiverc here: if there's something you don't like, just don't use it. Leave it as is, removing things causes more trouble than it's worth.

The resource manager is called Htop.

Much appreciated.

Rather than removing bluetooth, is disabling it a better option?

---

### Post by GhX6GZMB on 2021-09-02
> **wyattwhiteeagle said:**
> 
Rather than removing bluetooth, is disabling it a better option?

Yeah. You might even be able to do this in the BIOS.

---

### Post by wyattwhiteeagle on 2021-09-02
> **ml9104 said:**
> Yeah. You might even be able to do this in the BIOS.

My BIOS doesn't give the option.

Bluetooth doesn't appear anywhere in BIOS.

I'm wanting to disable it completely from doing anything and from starting up at boot.

What are alternate ways to accomplish this in Lubuntu?

I'm thinking Muon or maybe Stacer, I'm not exactly sure though.

In Ubuntu, Stacer wasn't saving the settings.

On LiveUSB is understandable, but on a full install...not saving settings made it seem useless to me.

It could be because my install is on a usb.

---

### Post by guiverc on 2021-09-03
> **wyattwhiteeagle said:**
> 
On LiveUSB is understandable, but on a full install...not saving settings made it seem useless to me.

It could be because my install is on a usb.

Is this an installed system to USB?  or a *live* system on USB?

Don't forget, if it's *live* with persistence, it's still a *live and *and not an installed system.

---

### Post by wyattwhiteeagle on 2021-09-03
> **guiverc said:**
> Is this an installed system to USB?  or a *live* system on USB?

Don't forget, if it's *live* with persistence, it's still a *live and *and not an installed system.

> wyatt@wyatt-aspiree1532:~$ sudo parted -l
[sudo] password for wyatt:
Model: SanDisk Cruzer Glide (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:                                                                                                                           
                                                                                                                                      
Number  Start   End     Size    File system     Name  Flags                                                                           
 3      17.4kB  1050MB  1050MB  fat32                 msftdata                                                                        
 1      1050MB  124GB   123GB   ext4                                                                                                  
 2      124GB   128GB   4195MB  linux-swap(v1)        swap
wyatt@wyatt-aspiree1532:~$     

Nope, it's not a live with peristence, it is an actual full install to a usb like to an internal HDD.

It's an installed system to a usb.

I probably need to repartition and reinstall because my FAT32 partition is /dev/sdb3 and the ext4 is the /dev/sdb1

 I believe the sdb1 needs to be the fat32.

I also created a 4gb linuxswap partition on the usb.

My "Alt+PrtSc" isn't working. I don't know what's wrong with it.

I wish I could take screenshots to let people see what I am seeing.

Most times I run into people thinking, "That's not possible, he must be on a live with persistence and just don't know it"
But they never give me the info on how to provide the evidence and so they continue assuming it is a "with persistence" install.

---

### Post by guiverc on 2021-09-03
Print Screen is achieved with PrtScr; no ALT is needed

[https://manual.lubuntu.me/lts/2/2.3/2.3.2/screengrab.html](https://manual.lubuntu.me/lts/2/2.3/2.3.2/screengrab.html)

I have no real experience with bluetooth; but I'll provide the following link

[https://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup](https://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup)

(*I'm not using focal or 20.04 currently, having only impish boxes in front of me; my own and test installs I'm running, so I can't currently confirm the `/etc/bluetooth/main.conf` will be found on your system; but it's where I'd look first.  Later I maybe able to check on a focal system but can't currently sorry*)

---

### Post by GhX6GZMB on 2021-09-03
On Lubuntu PrtScr calls up a screenshot program.
If you want the Win-like PrtScr and Alt-PrtScr functionality where screen or window gets copied to the clipboard, you'll need to set it up yourself. I've done this on my machines, if you want the recipe, say so.

---

### Post by wyattwhiteeagle on 2021-09-03
> **ml9104 said:**
> On Lubuntu PrtScr calls up a screenshot program.
If you want the Win-like PrtScr and Alt-PrtScr functionality where screen or window gets copied to the clipboard, you'll need to set it up yourself. I've done this on my machines, if you want the recipe, say so.

Ok...here goes :)

May I please have the recipe for the Wihdows-like printscreen function?

---

### Post by TheFu on 2021-09-03
I dislike bluetooth.  Got hacked through it on a freshly installed, freshly patched, ubuntu box.  I usually disable it, but in my rush to travel to a conference, I thought the fresh install and patch should handle all my security needs. Clearly I was wrong.
Since then, I blacklist the bluetooth kernel driver and check that it doesn't get loaded at boot every reboot.
Bluetooth was added as a dependency for qemu about a year ago - why I don't know.  Regardless, it kept showing up, so preventing it from loading in the kernel was my final answer after purging all blue* packages didn't work.
There are blacklist files in /etc/modprobe.d/  Follow those examples.

Haven't touched Lubuntu in a long time. All DEs seem too bloated for my needs, plus I don't really use menus.

---

### Post by GhX6GZMB on 2021-09-03
> **wyattwhiteeagle said:**
> Ok...here goes :)

May I please have the recipe for the Wihdows-like printscreen function?

OK, here it is:

Preferences -> LXQt settings -> Shortcut Keys

You'll find that PrtScr is already there (it's called "Print") Edit it and replace the existing command with:
```
[COLOR=#000000]sh -c 'scrot -o /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''
[/COLOR]
```[COLOR=#000000][COLOR=#222222]
Then add the Alt+PrtScr shortcut and add this command:
[/COLOR][/COLOR]
```
[COLOR=#000000]sh -c 'scrot -o -u /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''[/COLOR]

```[COLOR=#000000][COLOR=#222222]
Both work the same way, the only difference is the -u option (select active window).

sh (shell) is invoked to run scrot (screenshot) followed by xclip to place the shot on the clipboard. Only one shot is placed on the clipboard, a second shot overwrites the previous one. In all suitable programs you can now place the shot using Edit -> Paste.
There's no provision to shoot a selection of the screen. I usually just paste into Kolourpaint to crop the shot as desired.

Cheers.

[/COLOR][/COLOR]

---

### Post by wyattwhiteeagle on 2022-02-12
I reverted back to Ubuntu.

Lubuntu was a bit confusing to me.

No offense to anybody.

---

### Post by wyattwhiteeagle on 2022-03-14
I'm back here at Lubuntu, seems my system spec's are quite small for anything more resource hungry

---

### Post by ajgreeny on 2022-03-14
If you are finding Lubuntu too confusing, possibly due to its use of the Qt libraries instead of gtk, you might find that its worth investigating Xubuntu or Ubuntu-Mate, both of which use gtk.

I hope i have not added even more confusion to your mind but this thread has talked mostly about Lubuntu and Ubuntu, thus missing some similarities that the other DE versions I mention have with Ubuntu which you seem to know  best.

As you will see from my signature information, I use Xubuntu and have done so since 2010 or thereabouts; now that Lubuntu has moved from LXDE to LXqt, the resource usage of the two systems is very similar so your hardware ought to manage Xubuntu well.

---

### Post by wyattwhiteeagle on 2022-03-14
> **ajgreeny said:**
> If you are finding Lubuntu too confusing, possibly due to its use of the Qt libraries instead of gtk, you might find that its worth investigating Xubuntu or Ubuntu-Mate, both of which use gtk.

I hope i have not added even more confusion to your mind but this thread has talked mostly about Lubuntu and Ubuntu, thus missing some similarities that the other DE versions I mention have with Ubuntu which you seem to know  best.

As you will see from my signature information, I use Xubuntu and have done so since 2010 or thereabouts; now that Lubuntu has moved from LXDE to LXqt, the resource usage of the two systems is very similar so your hardware ought to manage Xubuntu well.

Adding to my confusion...nah...your fine.

The confusion was when I was paying more attention to the Lubuntu manpage without paying as much attention to what people here was saying.

The main of the confusion was that Lubuntu doesn't use gnome...
I thought, "Ok now what...I can't even install the packages I'm used to because they are gnome...and Lubuntu doesn't use gnome."
At the time, I didn't know the difference between gnome and packages.

Anyway, I have now tried Xubuntu.
It seems like it's a mixture of Ubuntu, Lubuntu, and Linux-lite.
While trying it, I got the feeling that Xubuntu is more for gamer's and high-end entrepenuer's.
I am neither of those.

I'm just a simple southern disabled American vet tryin to make ends meet at home every month.
For me...Xubuntu just seems way too overloaded with bloat on top of way too many configurable settings.
Also...seems like the longer I was trying it...the more over-whelmed I was feeling.

Xubuntu might be best for my system...but it isn't best for me.
So I choose second-best...Lubuntu

---

### Post by guiverc on 2022-03-14
> **wyattwhiteeagle said:**
> 
The main of the confusion was that Lubuntu doesn't use gnome...
I thought, "Ok now what...I can't even install the packages I'm used to because they are gnome...and Lubuntu doesn't use gnome."
At the time, I didn't know the difference between gnome and packages.


Ubuntu Desktop is the Ubuntu base system with the default GNOME desktop installed over it.

The GNOME desktop is GTK3 based; so it includes all of GTK3 toolkit & librariues; GTK3 is rather heavy (unlike the much lighter GTK2 version it replaced *looong* ago), but that extra weight provides additional features such as scaling & capacity to deal with HiDpi monitors & more... ie. the extra weight has advantages.

What's included - you can look at the 
- [https://packages.ubuntu.com/focal-updates/ubuntu-desktop](https://packages.ubuntu.com/focal-updates/ubuntu-desktop)
- [https://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.manifest)

Lubuntu is a *flavor *of Ubuntu, meaning it's built on the same Ubuntu base as all Ubuntu products are, but instead of `ubuntu-desktop` it has the `lubuntu-desktop`.

The means it's got the LXQt desktop instead of GNOME, LXQt uses the *lighter* Qt5 toolkit/libraries so Qt5 has replaced GTK3 used by GNOME etc.  That also means most apps are replaced with Qt5 apps that can share *libs/TK* with the desktop itself, otherwise the *lightness* wouldn't be there - thus why apps differ.

To see what's included with `lubuntu-desktop` you can peruse
- [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)
- [https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest)

The same applies with other *flavors* too, ie. 

Xubuntu uses the XFCE desktop & uses `xubuntu-desktop`.  It's also a GTK3 desktop now, thus isn't as *light* as it used to be, but that also means it can deal with HiDPi monitors better than older Xfce could etc.. but what it can do is release specific.

Kubuntu uses the KDE desktop & uses `kubuntu-desktop`.  It's also Qt5 based, but also requires KF5 to provide features that Qt5 doesn't provide, which is what allow it to deal with HiDPi that LXQt/Lubuntu cannot.. Even with Qt5 + KF5 it's still *lighter* than GTK3, but it's not as light as using Qt5 alone (*but as always adding KF5 provides more capabilities*).

If you want to use GTK3 apps; you're best using a GTK3 desktop; unless your box has enough resources (esp. RAM) to have both libs/toolkits in RAM as required when desktop & apps don't match; otherwise you'll notice a *rather severe* slowdown in performance as the system will be required to swap in/out of cache/RAM.

If you want to use Qt5 apps; you're best using a Qt5 desktop, again unless you've plenty of resources (esp. RAM) to have multiple libs/toolkits (*that do the same thing, just slightly differently*) before the slowdown occurs.


Personally, I still use old thinkpads with 1GB only of RAM. They are x86 or 32-bit only, so they're running older releases, and like all my boxes I have multiple desktops installed, and decide which I'll login to and use each sessions based on what I believe I'll be doing that session, and what will be most efficient.  I don't worry about the extra disk space used by having multiple DE/desktops installed, as I have more disk space than RAM - but I'm careful in what runs at the same time; ie. co-exists in my boxes usually limited RAM.

I'm using my primary desktop now, but it's a 2009 dell box, thus it's resources are rather *limited* by today's standards (they were great in 2009!).

Ubuntu has great choice - ie. you're not limited to the main Ubuntu (GNOME) desktop thanks to *flavor* teams - [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

I'm on the Lubuntu team (*and am using Lubuntu/LXQt right now*), but I've also got Xfce/Xubuntu installed on this box, GNOME/Ubuntu installed too.....  I'm a Ubuntu member & involved with multiple teams actually, and really like multiple desktops too (*this Lubuntu/LXQt desktop is setup to mimic my Xfce/Xubuntu desktop actually*) and whilst i'm not as careful on this box due to it's 8GB of RAM, I'm very careful with how I use my desktops when on boxes with fewer resources (esp. RAM).


FYI:  My links:  The *manifest* tells you what is included on the ISO.  The *packages.ubuntu.com* is probably the easiest place to look, as options you use at install can mean all packages included on the *manifest* won't be included.

---

### Post by wyattwhiteeagle on 2022-03-15
> **guiverc said:**
> Ubuntu Desktop is the Ubuntu base system with the default GNOME desktop installed over it.

The GNOME desktop is GTK3 based; so it includes all of GTK3 toolkit & librariues; GTK3 is rather heavy (unlike the much lighter GTK2 version it replaced *looong* ago), but that extra weight provides additional features such as scaling & capacity to deal with HiDpi monitors & more... ie. the extra weight has advantages.

What's included - you can look at the 
- [https://packages.ubuntu.com/focal-updates/ubuntu-desktop](https://packages.ubuntu.com/focal-updates/ubuntu-desktop)
- [https://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.manifest)

Lubuntu is a *flavor *of Ubuntu, meaning it's built on the same Ubuntu base as all Ubuntu products are, but instead of `ubuntu-desktop` it has the `lubuntu-desktop`.

The means it's got the LXQt desktop instead of GNOME, LXQt uses the *lighter* Qt5 toolkit/libraries so Qt5 has replaced GTK3 used by GNOME etc.  That also means most apps are replaced with Qt5 apps that can share *libs/TK* with the desktop itself, otherwise the *lightness* wouldn't be there - thus why apps differ.

To see what's included with `lubuntu-desktop` you can peruse
- [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)
- [https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest)

The same applies with other *flavors* too, ie. 

Xubuntu uses the XFCE desktop & uses `xubuntu-desktop`.  It's also a GTK3 desktop now, thus isn't as *light* as it used to be, but that also means it can deal with HiDPi monitors better than older Xfce could etc.. but what it can do is release specific.

Kubuntu uses the KDE desktop & uses `kubuntu-desktop`.  It's also Qt5 based, but also requires KF5 to provide features that Qt5 doesn't provide, which is what allow it to deal with HiDPi that LXQt/Lubuntu cannot.. Even with Qt5 + KF5 it's still *lighter* than GTK3, but it's not as light as using Qt5 alone (*but as always adding KF5 provides more capabilities*).

If you want to use GTK3 apps; you're best using a GTK3 desktop; unless your box has enough resources (esp. RAM) to have both libs/toolkits in RAM as required when desktop & apps don't match; otherwise you'll notice a *rather severe* slowdown in performance as the system will be required to swap in/out of cache/RAM.

If you want to use Qt5 apps; you're best using a Qt5 desktop, again unless you've plenty of resources (esp. RAM) to have multiple libs/toolkits (*that do the same thing, just slightly differently*) before the slowdown occurs.


Personally, I still use old thinkpads with 1GB only of RAM. They are x86 or 32-bit only, so they're running older releases, and like all my boxes I have multiple desktops installed, and decide which I'll login to and use each sessions based on what I believe I'll be doing that session, and what will be most efficient.  I don't worry about the extra disk space used by having multiple DE/desktops installed, as I have more disk space than RAM - but I'm careful in what runs at the same time; ie. co-exists in my boxes usually limited RAM.

I'm using my primary desktop now, but it's a 2009 dell box, thus it's resources are rather *limited* by today's standards (they were great in 2009!).

Ubuntu has great choice - ie. you're not limited to the main Ubuntu (GNOME) desktop thanks to *flavor* teams - [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

I'm on the Lubuntu team (*and am using Lubuntu/LXQt right now*), but I've also got Xfce/Xubuntu installed on this box, GNOME/Ubuntu installed too.....  I'm a Ubuntu member & involved with multiple teams actually, and really like multiple desktops too (*this Lubuntu/LXQt desktop is setup to mimic my Xfce/Xubuntu desktop actually*) and whilst i'm not as careful on this box due to it's 8GB of RAM, I'm very careful with how I use my desktops when on boxes with fewer resources (esp. RAM).


FYI:  My links:  The *manifest* tells you what is included on the ISO.  The *packages.ubuntu.com* is probably the easiest place to look, as options you use at install can mean all packages included on the *manifest* won't be included.

OK...
I just looked at the dpkg -l in Lubuntu both in a full install and in a Live session.
If Lubuntu doesn't use gnome, why are there gnome app's in Lubuntu?
Aren't those gnome app's installed when the user installs Lubuntu?

If the app has the word gnome in the title, does it specify that the app is for a system that uses gnome?

How I understand what you said...it isn't good to have gnome apps on Lubuntu.

---

### Post by guiverc on 2022-03-15
From the [20.04 manifest]("https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest") I provided (ie. list of what's found on the 20.04 daily ISO), I see

```
gnome-accessibility-themes    3.28-1ubuntu1
gnome-icon-theme    3.12.0-3
gnome-keyring    3.36.0-1ubuntu1
gnome-keyring-pkcs11:amd64    3.36.0-1ubuntu1
gnome-themes-extra:amd64    3.28-1ubuntu1
gnome-themes-extra-data    3.28-1ubuntu1
libpam-gnome-keyring:amd64    3.36.0-1ubuntu1
libsoup-gnome2.4-1:amd64    2.70.0-1
network-manager-gnome    1.8.24-1ubuntu3
pinentry-gnome3    1.1.0-3build1
```

I don't see any of those as GNOME apps myself.  Some are just theme related so LXQt theme/control related so [https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html](https://manual.lubuntu.me/lts/3/3.2/3.2.2/appearance.html) works correctly in controlling GTK apps.

Yes it'd be wonderful if Lubuntu was all Qt5, but that's not realistic in my opinion, as users will want to use GTK2/GTK3 apps (*I sure do, I'm still using `hexchat` (GTK2) for my IRC, `evolution` (GTK3) as my MUA etc*), and if Lubuntu/LXQt wasn't GTK aware; those apps would look terrible when users installed/used them (*so having the system pre-configured to make them look ~okay to me makes sense*).

What apps are you asking about?

FYI:   I probably should have used a release ISO manifest sorry; so it's **not**a moving target like the *daily* I used.. the *daily* was used as I didn't need to go find it as I'm using them very regularly.

---

### Post by ajgreeny on 2022-03-15
Just to add more meat to the bones of what guiverc says above, don't worry too much about the set of libraries that applications need and use, ie, gtk or Qt, use what you need.

For many years, in spite of using Xubuntu, a gtk DE, I have needed kmymoney, most definitely a Qt application, so I install that and run it with no problems.
OK, it may use a little more ram than some other apps but it still works exactly as it should and with 8G of ram it is worth it for me and my needs.

For me, this flexibility and configurability of the Ubuntu family of OSs is one of its great strengths; you can do with it more or less what you want and are not constrained by developers in the way that users of other OSs are.

---

### Post by wyattwhiteeagle on 2022-03-20
I'm guessing from ajgreeny's post...
htop wouldn't have a problem running on Xubuntu...

Would Xubuntu have a problem using htop instead of "Task Manager"?

Why does it seem like guiverc is trying to suggest that we need to stay "gnome-specific" or "gtk-specific" etc in choosing which app's we use, especially when others confirm other-wise?

I quoted quiverc (see below) ...
Is guiverc talking about general overall performance or is he talking about strictly "resource-usage"?

It is true I need to pay attention to Resource Usage, but ajgreeny seems to suggest a more sensible approach for my issue's.

Here's why...
In Xubuntu, "Task Manager" is installed.
In Lubuntu, "htop" is installed.
htop seems to be more what I need due to Xubuntu's "Task Manager" showing very limited information.
htop shows more of the information that Xubuntu's "Task Manager" doesn't show.

Seems to me I need htop instead of "Task Manager".

> **guiverc said:**
> Ubuntu Desktop is the Ubuntu base system with the default GNOME desktop installed over it.

The GNOME desktop is GTK3 based; so it includes all of GTK3 toolkit & librariues; GTK3 is rather heavy (unlike the much lighter GTK2 version it replaced *looong* ago), but that extra weight provides additional features such as scaling & capacity to deal with HiDpi monitors & more... ie. the extra weight has advantages.

What's included - you can look at the 
- [https://packages.ubuntu.com/focal-updates/ubuntu-desktop](https://packages.ubuntu.com/focal-updates/ubuntu-desktop)
- [https://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/focal/daily-live/current/focal-desktop-amd64.manifest)

Lubuntu is a *flavor *of Ubuntu, meaning it's built on the same Ubuntu base as all Ubuntu products are, but instead of `ubuntu-desktop` it has the `lubuntu-desktop`.

The means it's got the LXQt desktop instead of GNOME, LXQt uses the *lighter* Qt5 toolkit/libraries so Qt5 has replaced GTK3 used by GNOME etc.  That also means most apps are replaced with Qt5 apps that can share *libs/TK* with the desktop itself, otherwise the *lightness* wouldn't be there - thus why apps differ.

To see what's included with `lubuntu-desktop` you can peruse
- [https://packages.ubuntu.com/focal/lubuntu-desktop](https://packages.ubuntu.com/focal/lubuntu-desktop)
- [https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest](https://cdimage.ubuntu.com/lubuntu/focal/daily-live/current/focal-desktop-amd64.manifest)

The same applies with other *flavors* too, ie. 

Xubuntu uses the XFCE desktop & uses `xubuntu-desktop`.  It's also a GTK3 desktop now, thus isn't as *light* as it used to be, but that also means it can deal with HiDPi monitors better than older Xfce could etc.. but what it can do is release specific.

Kubuntu uses the KDE desktop & uses `kubuntu-desktop`.  It's also Qt5 based, but also requires KF5 to provide features that Qt5 doesn't provide, which is what allow it to deal with HiDPi that LXQt/Lubuntu cannot.. Even with Qt5 + KF5 it's still *lighter* than GTK3, but it's not as light as using Qt5 alone (*but as always adding KF5 provides more capabilities*).

If you want to use GTK3 apps; you're best using a GTK3 desktop; unless your box has enough resources (esp. RAM) to have both libs/toolkits in RAM as required when desktop & apps don't match; otherwise you'll notice a *rather severe* slowdown in performance as the system will be required to swap in/out of cache/RAM.

If you want to use Qt5 apps; you're best using a Qt5 desktop, again unless you've plenty of resources (esp. RAM) to have multiple libs/toolkits (*that do the same thing, just slightly differently*) before the slowdown occurs.


Personally, I still use old thinkpads with 1GB only of RAM. They are x86 or 32-bit only, so they're running older releases, and like all my boxes I have multiple desktops installed, and decide which I'll login to and use each sessions based on what I believe I'll be doing that session, and what will be most efficient.  I don't worry about the extra disk space used by having multiple DE/desktops installed, as I have more disk space than RAM - but I'm careful in what runs at the same time; ie. co-exists in my boxes usually limited RAM.

I'm using my primary desktop now, but it's a 2009 dell box, thus it's resources are rather *limited* by today's standards (they were great in 2009!).

Ubuntu has great choice - ie. you're not limited to the main Ubuntu (GNOME) desktop thanks to *flavor* teams - [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

I'm on the Lubuntu team (*and am using Lubuntu/LXQt right now*), but I've also got Xfce/Xubuntu installed on this box, GNOME/Ubuntu installed too.....  I'm a Ubuntu member & involved with multiple teams actually, and really like multiple desktops too (*this Lubuntu/LXQt desktop is setup to mimic my Xfce/Xubuntu desktop actually*) and whilst i'm not as careful on this box due to it's 8GB of RAM, I'm very careful with how I use my desktops when on boxes with fewer resources (esp. RAM).


FYI:  My links:  The *manifest* tells you what is included on the ISO.  The *packages.ubuntu.com* is probably the easiest place to look, as options you use at install can mean all packages included on the *manifest* won't be included.

---

### Post by ajgreeny on 2022-03-21
I'm pretty sure that htop is just an n-curses display sitting on top of **top** so it does not use either the qt or gtk libraries to create a GUI; the terminal you use in which to run htop will, of course use those libraries but that will not make any problems as you'll use whichever terminal came with your OS.

You can even run htop as far as I'm aware in a tty terminal from Ctr+Alt+F1 with no GUI running at all.
I can't help with task-manager as I've seldom used it and when I last did so was many years ago.

---

### Post by GhX6GZMB on 2022-03-21
Why this focus on htop?
I'm running Lubuntu since four years now and have never had to use it. The system just runs. Period.
This is getting autistic.

---

### Post by guiverc on 2022-03-21
> **wyattwhiteeagle said:**
> 
Why does it seem like guiverc is trying to suggest that we need to stay "gnome-specific" or "gtk-specific" etc in choosing which app's we use, especially when others confirm other-wise?

I quoted quiverc (see below) ...
Is guiverc talking about general overall performance or is he talking about strictly "resource-usage"?

It is true I need to pay attention to Resource Usage, but ajgreeny seems to suggest a more sensible approach for my issue's.


Ubuntu-MATE is a GTK3 based desktop, like Xubuntu is - yet includes `htop` as well.           I agree with @ajgreeny in that `htop` is light as doesn't require anything that should already exist if run in a terminal that matches your chosen desktop.

eg. [https://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/jammy-desktop-amd64.manifest](https://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/jammy-desktop-amd64.manifest)  & a quick look will show `htop` is there

`htop` is just a tool... it's more colorful than `top` I learnt to use in the 1980s...

My language is likely unclear, for which I apologize.  I suffered a brain injury years ago in a motorcycle accident, and my thoughts are a little [I]scattered.

[/I]I'm on my primary box now which is running *jammy*, but right now I'm using GNOME instead of my usual LXQt/Lubuntu desktop (I have mulitple DEs installed on it).  My apps though are normal ones, ie.

- featherpad for my usual copy/pastes (a LXQt/Qt5 app!)
- hexchat for IRC (a GTK2 app so it's not native on GTK3 or Qt5 desktops!)
- firefox & chromium, telegram (both are *snap* packages so requirements are packaged inside snap, today is the first day I'm using the *snap* of firefox)
- terminal (I always use the native terminal, so it's `gnome-terminal` today; but it'll be `qterminal` when using LXQt, `xfce4-terminal` if using Xfce...)
- music is currently playing using `audacious` another *old* GTK app; if using Qt5 I use `clementine`
- my mail MUA is `evolution` which is GTK3, my RSS reader is `liferea` so GTK3

ie. I'm using all of GTK2, Qt5 & GTK3 apps. 

If I was in my usual LXQt desktop on this box  (*I'll be logging out & switching soon I suspect; I'm nearing my end of being able to cope with GNOME*) all apps except for music player would be the same.. 

This box however has 8GB of RAM.   If I'm using a box with less RAM, eg 5GB or less, I'm more careful with what apps co-exist in RAM.  When using boxes with 3GB or less I'm more careful again.    I'd not leave `evolution` or `liferea` sit in RAM if using a Qt5 desktop (eg. LXQt/KDE)  except whilst I was using them; and I'd likely close browser(s) to use those GTK3 apps. As I'm currently using GNOME or a GTK3 desktop, I'd have used likely `mousepad` (a Xfce text editor if not `gedit` which is GNOME's) instead of `featherpad`; but I opted to use the Qt5 app just as it has the *restore session* option & suffer the resource hit (*hey I usually can't sit on GNOME that long before it annoys me*).

**ie**. before I start an app; I do a quick mental '*assessment*' of what resources the box has available, what is currently running, and what is required for the app I want to run, and what effect starting it will cause; or should I *unload* an app first.  When using my usual LXQt desktop, the first apps I usually *unload* are `evolution` or `liferea` which are the GTK3 apps.

I plan to *kick* my habit of using hexchat & old GTK2 apps sometime, but I've been thinking/saying that since 2019 probably, it'll happen yes - but it's not a high priority.

As I still uses boxes with only 1GB of RAM, and want them to perform *fast*, I've gotten pretty good at *estimating* the resources used by various apps for various releases.

It's *general performance* which also means *resource usage.  *As most of my boxes are old (*this is a 2009 dell*) effects are rather noticeable as on *higher end* equipment the adverse effects are *shorter* thus easier to dismiss.

---

### Post by QIII on 2022-03-21
> **ml9104 said:**
> Why this focus on htop?
I'm running Lubuntu since four years now and have never had to use it. The system just runs. Period.
This is getting autistic.

Which do you not understand:  htop or autism?

You are welcome to keep that sort of remark to yourself.

---

