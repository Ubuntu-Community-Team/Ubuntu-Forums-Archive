---
title: "New to ubuntu, have an array of installation/use questions."
date: 2008-04-12
forum: General Help
---

### Post by TeleJesus on 2008-04-12
I've been using Windows XP since forever, and recently decided to switch to ubuntu.  I have the ubuntu 7.10 live CD, and plan to install whenever my questions are resolved, so to start:

1.) How hard will it be switching OS's overall?

2.) I game quite frequently, how will this effect older games (think Warcraft III), and newer games, like Call of Duty 4, World of Warcraft, or Battlefield 2?

3.) Would my Zune software also be compatible? This also leads to my next question...

4.) Would any of the other software on my computer be compatible?  I don't want to go into a whole detailed list of what they are, but along the lines of a DVD ripper, music app's, chat app's, etc.

5.) Will I lose any file data (papers, music, videos)?  Or should I just back everything up?

6.) Is there any need for anti virus software?  I currently use the AVG free edition, Ad-aware, and PC Tools Firewall.  If so, what should I use?


This is all I could really think of in the time I spent composing this.
Any help would be greatly appreciated!   =D

---

### Post by chewearn on 2008-04-12
Can't answer all the questions, but I give it a go.

** 1.) How hard will it be switching OS's overall?**

In terms of installing, easy to hard to impossible.  It depends on whether your hardware is fully supported, partially supported, or not supported at all.

In terms of usage, just need a change in way of thinking.  A lot of info here:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)


** 2.) I game quite frequently, how will this effect older games (think Warcraft III), and newer games, like Call of Duty 4, World of Warcraft, or Battlefield 2?**

No idea, but generally Windows game don't work in Linux.  Sometimes, there is a Linux port, or you might be able to make it work thru [Wine]("http://ubuntuforums.org/winehq.org") or another Windows-Linux compatibility layer.


** 3.) Would my Zune software also be compatible? This also leads to my next question...**

No idea.  If Zune is a mass storage USB device, probably yes.


** 4.) Would any of the other software on my computer be compatible?  I don't want to go into a whole detailed list of what they are, but along the lines of a DVD ripper, music app's, chat app's, etc.**

It's generally advisable to find a Linux equivalent to replace what you use in Windows.  Some Windows apps has a Linux version.


** 5.) Will I lose any file data (papers, music, videos)?  Or should I just back everything up?**

It's always a good idea to back-up everything first.


** 6.) Is there any need for anti virus software?  I currently use the AVG free edition, Ad-aware, and PC Tools Firewall.  If so, what should I use?**

No anti-virus required for Linux system, but there are anti-virus program running in Linux with the purpose of scanning for Windows malwares.

Adware is not a problem in Firefox browser, that comes with default Ubuntu install.  You can use the same adblock and noscript plug-ins to secure your web surfing.

Ubuntu uses iptables as firewall; it's build-in and you don't have to do anything to install it.


PS: You don't have to switch completely, try dual boot set-up until you are comfortable.  It took me about a year to fully switch over from XP to Ubuntu, and replace all my Windows apps with Linux equivalent.

---

### Post by Nameless_one on 2008-04-12
Concerning the software you use, you will find that for each task, there is most probably a free open source program, which usually works differently than the one you used in Windows: sometimes better, some times worse. I for one, haven't found a task for which there isn't a program for linux (besides games). 

For the most common tasks, you should consult this:

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

### Post by russo.mic on 2008-04-12
As far as gaming goes, you could always duel boot.  Keeping a 10G partiton for XP isn't that bad in my eyes.

---

### Post by TeleJesus on 2008-04-12
How hard is it to set up a dual boot?

---

### Post by h4mx0r on 2008-04-12
To dualboot:
scan disk then defrag windows and run the alternate install cd if there is no extra space for ubuntu it will resize the ntfs section window uses and install there. Reinstalling windows will screw your system over unless you backup grub (never done it myself, usually I virus scan/replace files for the windows side and hope everything starts working again). 

To game:
tremulous, regnum, globulation2, quake wars, enemy territory, urban terror, nwn, ut2004, savage. So much gaming on linux especially online considering its often considered a "Gaming **server** OS" that means it like.. serves noobs big time ;) All retail games pretty much work under wine though with better performance than their windows counterparts but don't expect to not find the bugs you would running them under windows.

Yes backup everything before installing if your not doing a dualboot because then you will be removing your windows stuff.

Firestarter program is very good at setting up a kool firewall that tells you info about attempted connections and even offers to reroute things like if you wanted to turn your system into a wireless access point. Never again will you have to worry about about your firewall going A-wall on you thinking your trying to jack your own system. And yes no random antivirus scanage lagging you.

When you install ubuntu you have access to over 20,000 programs that can be installed and consistenly updated if its too much to handle you could google linux alternatives to easily find programs you need. But I just run synaptic.

---

### Post by forestpixie on 2008-04-12
Quite simple - best thing is not to rush it, you make the wrong choice at the wrong time and ... ;)

Have a look at these, the second is for feisty but gutsy is similar to install.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

The most important thing is to get the partitioning right - make sure that before you do you defrag a few times, it can also help if you have a lot of system restore points to disable it before you defrag - they don't move.

---

### Post by Olav on 2008-04-12
Just to answer this one:
> **TeleJesus said:**
> 1.) How hard will it be switching OS's overall?
There really is no straight forward answer to that. It all depends. And it depends in no small part on your own flexibility of mind.

Technically it is almost an uninteresting question. It is easy to convert your computer to another OS. Yes, backups are mandatory.

But then.

Me, personally, I have always been able to switch without much effort from using Windows and MacOSX to Ubuntu/Linux/Gnome. I am using all those systems on a regular basis. I am used to thinking of a computer as more than it's user interface. After all, any computer is just a CPU with a few bits attached and I don't care what you put in front of me ;)

On my computers at home, I have been using Linux operating systems exclusively since years. Ubuntu in my opinion is certainly the nicest of all Linux distros, and I have tried a few. Fedora is probably the next best thing.

Your "old" Windows programs are almost certainly not going to work on Ubuntu but you will find alternatives for them (as already explained). Most games are never going to work, since the game publishers keep ignoring platforms other than Windows. Mind you: it would not be too difficult for them to make games that could work on different operating systems. They would only have to say FU to DirectX and start embracing OpenGL. But for some reason, they don't.

I don't play games except [Mahjongg]("http://live.gnome.org/Mahjongg"), but I do have a few needs that Ubuntu does not meet. For instance, I own a Garmin GPS unit (for my outdoor playing: hiking and cycling) and there is NO Linux solution for uploading maps to this thing. I don't blame Ubuntu, I blame Garmin for this.

Anyway, for such programs I have found [VMware server]("http://www.vmware.com/products/server/") to be of tremendous help. I am using it for many purposes. For games, it would probably be too slow.

---

### Post by h4mx0r on 2008-04-12
Reply: Olav

"Most games are never going to work, since the game publishers keep ignoring platforms other than Windows." Why are you even saying that if all you mostly play is just one card game? But yeah like I mentioned any online game that doesn't have a linux server setup would pretty much get laughed off the interwebs. Second off Wine is just uber, directx or opengl. But if you ask me directx10 sucks on performance just like vista. And yeah I do what you do with random usb devices that don't work, virtualize window xp then run them. Except I use virtualbox because its free think its like a suped up continuation of qemu, completely open source.

---

### Post by Olav on 2008-04-12
> **h4mx0r said:**
> Reply: Olav

"Most games are never going to work, since the game publishers keep ignoring platforms other than Windows." Why are you even saying that if all you mostly play is just one card game?
Because I have tried a few, then decided it wasn't worth the effort. I am not a game fanatic but I know that most Windows games don't (and won't) work.

> But yeah like I mentioned any online game that doesn't have a linux server setup would pretty much get laughed off the interwebs. Second off Wine is just uber, directx or opengl. But if you ask me directx10 sucks on performance just like vista. And yeah I do what you do with random usb devices that don't work, virtualize window xp then run them. Except I use virtualbox because its free think its like a suped up continuation of qemu, completely open source.
Perhaps true. But the pure open source solutions still can't hold a candle to VMware, sadly.

---

