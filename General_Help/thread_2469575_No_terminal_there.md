---
title: "No terminal there"
date: 2021-12-02
forum: General Help
---

### Post by peter-1984 on 2021-12-02
Hi,
Within Ubuntu below, there is no proper terminal to be called. Please help.

[ATTACH=CONFIG]289568[/ATTACH]

---

### Post by TheFu on 2021-12-03
Why not install the terminal program you want using the package manager?  
Is this a trick question?

I install **xterm** on all my systems, just to be consistent. I've been using xterms for 25+ yrs and know the quirks, but also how to control them.

---

### Post by peter-1984 on 2021-12-03
What should be done now, due to the problem? Currently after havinbg started my OS, it does get into lightdm GUI and I cannot go to the terminal to do other setup.

---

### Post by TheFu on 2021-12-03
Boot into a "Try Ubuntu" environment using the install ISO (flash drive) and fix what ever needs fixing.  How is that related to the need to install a terminal? I posted for that situation, not some other issues which are outside my skill.

---

### Post by guiverc on 2021-12-03
> **peter-1984 said:**
> What should be done now, due to the problem? Currently after havinbg started my OS, it does get into lightdm GUI and I cannot go to the terminal to do other setup.

Please give release details.

LightDM is a DM (*display manager*) and not a GUI.

Ubuntu's main desktop ISOs for recent releases (*17.10 & later*) use GNOME as their GUI, use the `gdm3` DM, thus use `gnome-terminal`.

LightDM is used by *flavors* of Ubuntu; eg. Kylin uses it ([https://packages.ubuntu.com/impish/ubuntukylin-desktop](https://packages.ubuntu.com/impish/ubuntukylin-desktop)) but it uses `mate-terminal` so providing your specific OS & release details may help.

---

### Post by KBar on 2021-12-03
Can you be more specific and explain what you're trying to achieve?

What's the version of Ubuntu? What's the default language of the system?

Do you not want GUI? You can always invoke a virtual terminal with the _Ctrl_-_Alt_-_F1_ key combination.

Did you uninstall your terminal? Check if these files exist:
```
/usr/bin/gnome-terminal
/usr/bin/gnome-terminal.real
/usr/bin/gnome-terminal.wrapper
/usr/lib/systemd/user/gnome-terminal-server.service
/usr/libexec/gnome-terminal-server
/usr/share/applications/org.gnome.Terminal.desktop
/usr/share/dbus-1/services/org.gnome.Terminal.service
```

---

### Post by peter-1984 on 2021-12-03
Thanks to all.


Guiverc,
Should the command be like the following?


sudo apt-get install gdm3


Kbar,
I cannot get into Virtual terminal by Ctrl-Alt-F1.

---

### Post by deadflowr on 2021-12-03
> Should the command be like the following?


sudo apt-get install gdm3

Did you uninstall gdm3 at some point?

Also does a login screen appear when you try ctrl+alt+F1?
If so, then you are already running gdm3.

gdm3 is the default display manager for Ubuntu so unless you removed it or
reset the display manager it should probably already be running.

Also what does ctrl+alt+T do?
That's the shortcut for opening a terminal.

---

### Post by KBar on 2021-12-03
> **peter-1984 said:**
> I cannot get into Virtual terminal by Ctrl-Alt-F1.

Well, try other function keys. _F1_ through _F6_ by default makes */dev/tty1* through */dev/tty6* the foreground terminal. _F7_ returns you back to the GUI.

---

### Post by peter-1984 on 2021-12-03
Thanks a lot to all. Yes, I can get into Terminal using Ctrl-Alt-F3 but not fine to return to GUI by Ctrl-Alt-F7 and I get the following

[ATTACH=CONFIG]289573[/ATTACH]

how to ensure that I can switch between Terminal and browser within the GUI?

---

### Post by KBar on 2021-12-03
As deadflowr said, try the default _Ctrl_+_Alt_+_T_ key combination. It should invoke the terminal emulator.

There are many reasons that make it seem that you don't have a terminal emulator. Off the top of my head:

[LIST]
[*]You simply uninstalled them 
[*]You somehow removed their desktop entries 
[*]Your installation might be broken 
[/LIST]
As far as I can tell, you like to fiddle with your system. At least, the fact that you cannot, for whatever reason, switch back to tty7 suggests that. I'd advise you to read and educate yourself before you pass some commands to the shell.

Also, you did not tell us whether you have GNOME Terminal installed. Please check out my previous reply and see if you can find the appropriate files.

---

### Post by TheFu on 2021-12-03
Didn't Ubuntu move the GUI tty to tty1?  That means <c><a>-F1 will return to the GUI.  It was F7 for a very long time. I don't know why.

gdm3 is required for Gnome3 to be used as the DE.  For other DEs (LXQt, Mate, KDE), other display managers (which is an odd term to me, since they feel more like login managers) are used. Gnome3+ is tightly coupled to gdm3, so other DMs cannot be used.

All this is confusing. So many choices and some are mandatory while others can be selected by the sys admin for the install.

---

### Post by KBar on 2021-12-03
Honestly, I have no idea either. It's F7 on my Focal.

---

### Post by TheFu on 2021-12-03
> **kbar said:**
> Honestly, I have no idea either. It's F7 on my Focal.

New install or upgrade?  Sometimes our upgrades retain old settings.  I've noticed that netplan can be avoided on systems upgraded with ifupdown there. Not relevant to this thread, just an example. IDK.

---

### Post by KBar on 2021-12-03
> **TheFu said:**
> New install or upgrade?

It was a fresh installation back in May. I don't usually do upgrades.

---

### Post by TheFu on 2021-12-03
[https://askubuntu.com/questions/105955/end-the-gui-on-tty7-and-start-a-new-one-elsewhere](https://askubuntu.com/questions/105955/end-the-gui-on-tty7-and-start-a-new-one-elsewhere) might help the OP understand to switch to a different tty, restart the gdm and get a GUI there.  Again, gdm is for Gnome3. Other DMs (display managers) can usually be used with all the other DEs (desktop environments).

Don't know if anyone cares, but running with a GUI and a DE is completely optional.  Below the DE is something called a WM - Window Manager. This is the thing that controls the windows and controls (those resize and buttons in the corners).  Again, Gnome3 is tightly coupled to a specific WM, I don't know the name, but most of the other WMs and DEs can use any compliant ICCCM-compliant WM.  

Openbox, fluxbox, fvwm, mwm, i3 are all WMs. I use fvwm without any DE to get the proper mix of usability and lightness.  fvwm has some quirks, but the ability to customize it for any needs via a little perl is freakishly AWESOME!  Openbox is fairly simple and has an XML-based config file which can be customized, somewhat. Most new users probably want a DE, so there is a menu in the expected place.  Distros built around a DE will also include some setting application to make a GUI-way to tweak the interface settings.  That's probably a good thing for the non-hard-core users of the world.

---

### Post by peter-1984 on 2021-12-03
Thanks to all.

> [COLOR=#000000]gdm3 is required for Gnome3 to be used as the DE.
 Any help to the following?

[ATTACH=CONFIG]289575[/ATTACH]

---

### Post by KBar on 2021-12-03
It doesn't answer your question directly, but I highly recommend reading these books and tutorials:
[LIST]
[*][https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview) 
[*][https://webwerks.dl.sourceforge.net/project/linuxcommand/TLCL/19.01/TLCL-19.01.pdf](https://webwerks.dl.sourceforge.net/project/linuxcommand/TLCL/19.01/TLCL-19.01.pdf) 
[*][https://wiki.debian.org/AptCLI](https://wiki.debian.org/AptCLI) 
[*][https://www.debian.org/doc/manuals/debian-faq/pkg-basics.en.html](https://www.debian.org/doc/manuals/debian-faq/pkg-basics.en.html) 
[/LIST]
The acquired knowledge will help you greatly.

---

### Post by slickymaster on 2021-12-03
@peter-1984:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by deadflowr on 2021-12-03
Ubuntu uses gdm3 but it's not strict. It can use any other display manager.
Other desktops like Xubuntu use lightdm, but that too is not strict.
Kubuntu and Lubuntu use sddm. And again, same as above.


As the Op has gdm3 installed then they can set it as the login display manager by running
```
sudo dpkg-reconfigure gdm3
```
select the option for gdm3 and toggle to the Okay.
(basically up down to selection the option wanted and left right will move to the Okay button)
After that reboot as it's easier than reloading since sometimes reloading fails when switching the display manager.

---

### Post by grahammechanical on 2021-12-03
Personally, I think the best solution for this situation is a fresh install. Either that or the OP providing more complete information as has been requested.

Based on the first screenshot image it seems that the desktop environment is Gnome 3 shell. The Ubuntu dock is missing. Even with the dock set to auto-hide it still remains on the screen when Activities is clicked. Byobu is a terminal (but much more than a simple terminal). It used to be a default part of  a Ubuntu installation years ago. As was Xterm. But Xterm is for the X-Server. And the X-server has not been the default for Ubuntu since 21.04. So, I am not surprised it is not installed on my Ubuntu 20.04.

If Gnome terminal is installed it should be possible to load it by right  clicking the wallpaper and selecting Open in Terminal. I suspect that  Gnome terminal is not installed. I also doubt that the system has wallpaper.

Based on the two other screenshots I think that this is a server install and the OP has added stuff to it. But not added the full Gnome 3 shell desktop environment.

Regards

---

### Post by peter-1984 on 2021-12-03
Thanks to all.
Graham,
Yes, this is server version and it is fresh setup as well. How to ensure Gnome terminal is there to use?

---

### Post by TheFu on 2021-12-03
> **peter-1984 said:**
>  Yes, this is server version and it is fresh setup as well. How to ensure Gnome terminal is there to use?

Server installs don't have GUI programs installed by default.  If you add GUI stuff to the server, then it is your responsibility to add whatever you need.
If you want a GUI, best to just install a normal desktop with a DE to start.

Most DEs have a meta package that adds the full desktop for that DE with all the dependencies ... look for {DE}-desktop in the package manager.  From a non-GUI setup, you can search for packages like that using
```
apt-cache search '\-desktop$'
```
That returns many options. This works too:
```
apt search '\-desktop$'
```
The search term is really "-desktop", but it needs to be regex safe. I added the end-of-line requirement, $, so lots of other packages with desktop in the middle of the name don't get shown in the list.

---

### Post by peter-1984 on 2021-12-04
Command below does not do proper setup for terminal, right?


apt search '\-desktop$'


what should be done to have proper terminal available?

---

### Post by deadflowr on 2021-12-04
Did you change something since you posted any of your screenshots?
As those clearly show you have the desktop installed and the default display manager as well.
It really doesn't matter how the initial install was done, as you added the desktop at some point.
How did you install the desktop?

---

### Post by KBar on 2021-12-04
GNOME Terminal can be installed with this command:

```
sudo apt install gnome-terminal
```

> **peter-1984 said:**
> Command below does not do proper setup for terminal, right?


apt search '\-desktop$'


what should be done to have proper terminal available?

Again, I suggest you read the books and tutorials the links to which I provided earlier.

The command above doesn't install a terminal. It just searches the official Ubuntu repositories for names and descriptions of packages that cointain that particular regular expression.

If you want help, you better be open for suggestions and actually read what people say to you. 

To have a proper terminal emulator, first, determine what exactly you want to achieve on your server (you failed to mention that throughout your thread). There are tons of terminal emulators out there. After that, you'd want to have a shell, such as *bash*, *csh*, *ksh* or *dash*.

Hopefully, people that have experience of working with servers will help you further and you can sort this out (once you actually do what they ask and tell).

---

### Post by dragonfly41 on 2021-12-04
In post#22, OP clarified that this is a server installation.
That being so, to add to the above advice I suggest installing webmin which runs on port 10000 and offers a terminal *in the browser.* Look for Custom Commands.

Typically in local desktop mode I can run .. [https://localhost:10000](https://localhost:10000) .. to bring up webmin menu in browser. For a remote server give webmin the server IP address.

---

### Post by KBar on 2021-12-04
> **dragonfly41 said:**
> In post#22, OP clarified that this is a server installation.

It took 20+ replies and even then, someone else had to guess and ask if their guess was correct.

---

### Post by ActionParsnip on 2021-12-04
CTRL + ALT + T will fire up a terminal for you

---

### Post by ActionParsnip on 2021-12-04
Personally I like guake. The terminal shows and hides with a shortcut key

---

### Post by TheFu on 2021-12-04
> **peter-1984 said:**
> Command below does not do proper setup for terminal, right?


apt search '\-desktop$'


what should be done to have proper terminal available?

That command just shows package names with the full desktop suite of programs. It was just a "search" command. You should pick one, then install it using whatever tool you prefer, probably **apt install** since a GUI may not be working?  This system is off the normal setup which is usually done by people with more expertise. 

For someone really new to Linux, it is best to use a full install ISO that has the GUI you want.  Then it will come with the expected suite of programs and those programs will be mostly integrated together.  Starting from a server, non-gui, install, then trying to add the correct 150 other packages to make a systems useful is best left to very experienced folks with a solid understanding of the package management tools.

If you'd like to learn more about package management, there are lots of resources. Best to begin with the manpages on the system.  **man apt** is the command. That will have references for other package management tools. Review each of those ... like **man apt-get** to see how they are related.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good place to fill in knowledge gaps too.  I learn new stuff reading that book all the time.

Causing problems is a great way to learn, BTW. If everything goes smooth, we'd never learn some of the important details about these tools.

---

