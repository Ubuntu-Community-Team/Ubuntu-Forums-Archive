---
title: "SO Far......"
date: 2004-11-08
forum: General Help
---

### Post by Slapdash on 2004-11-08
Ok some of you might know that I was going to install Ubuntu this past weekend.
I am a complete noob to linux so this was / is my experience.

I installed it without a hitch. I love grub I think it solves more problems than LILO ( more problem prone )

I noticed after I installed Warty that the file system says its a ext2f.  But I know it was formated ext3. So what is wrong here?

Totem movie player does not work with ANY of my avi movies or even mpg's I have.
I was REAL dissapointed with this as I had Mandrake 10.0 on my PC ( deleted it for UBUNTU ) and it's Totem played EVERYTHING I threw at it. :(   real sad here? Any ideas ( CODECS? )

Wich brings me to this question.

I bought a Linux Format Magazine the other day that has a lot of Apps on it.
Some Source, some RPM's some Debian (.deb ) files etc.
Now, ne of the Games ( a WORMS clone ) had a DEB RPM and SOURCE in there.
I right clicked on the .DEB package and sellected "Open with Synaptic" wich returned the error - "You have to open this under root" - Something along those lines anyway

Now how do I log on as root? I have to use Sudo under Terminal and there NOTHING wants to run, exept sudo apt-get  and sudo apt-cdrom - ( wich also says that it cant find any DEB packages. and there are DEFENATLY deb packages on there. I even copied it to the HD without any success.

Anything like this?

sudo -s
sudo passwd root

Somehow this doesnt work....  :(


THen I un tared the source and dbl clicked on a icon that looked like an EXE.
Wadda ya know the game launced.

Then I tried anothjer Source file but that had no Icon /EXE- type file.

How can I use Root /sudo to log in and then just have to right click to lunch app in synaptic?

THis I think is THE SINGLE MOST Important problem keeping Linux from going mainstream. Its an ABSOLUTE nightmare to install anything. ( Debian / Ubuntu REALLY tries and solves this - even RPM packages ) but it doesnt work flawlessly - Lots of condisions or I'm just REAL new and dont know the correct way - Hence this post ;)

UBUNTU TEAM,  I think the Splash screen ( 2 chicks and a guy ) really doesnt bring a Corporate feel to Ubuntu. - If it was up to me ( wich it aint ) I would do away with that.
wich leads to this question, I got the first Splash screen away and replaced it but how do I get the one away that loads up GNOME?

THe CD player found and configured my surround no problems.

Graphics. Do I need Drivers for the GeForce 5200 FX installed? it only goes to 1024x780 even if I put my Refresh rate down.

Love Gnome. ( use to think KDE is good ) but somehow...GNOME is just.....Gnome.
Clean and Fast.

Warty does make me REALLY want to switch from a Windows env. to Linux.
but my main issue here is the INSTALLING problem.
Please help.

---

### Post by wallijonn on 2004-11-08
You definitely want to head over to the HOWTO/FAQ section where most of your questions will be answered.

I will answer one though, Computer -> System Configuration -> Login Screen Setup -> Graphical Greeter.

To change it, go to [www.gnome.org](www.gnome.org) -> Arts & Themes -> 
&
[http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=10b4d3a4ad65bbc9093f59bbd3e16182](http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=10b4d3a4ad65bbc9093f59bbd3e16182)

(That's for a GDM which you can install through Computer -> System Configuration -> Login Screen Setup -> Graphical Greeter -> Install Theme)

---

### Post by kamstrup on 2004-11-08
ext2/3:
You can see what your filesystems are mounted as if you type "cat /etc/fstab" in a terminal.

Installing Packages:
Well, when I have a .deb or a .rpm I find myself resorting to the command line. To install a deb you do

sudo dpkg -i mypackage.deb

I also had my problems with apt-get until I found out that I had to use dpkg to install deb's I already had!

Graphics:
Post the contents of the Section called "Device" in your /etc/X11/XF86Config-4 .

Splash:
I don't have any screens with any persons on them..?

---

### Post by Slapdash on 2004-11-08
Thanks guys I'll try that.

I see....so the APT-GET is to go online, download the package and it's dependencies and then install it automatically?
I'll try the DPKG

it says ext2f when I boot up, but I'll check the fstab thing.


"Splash:
I don't have any screens with any persons on them..?"

You dont? I do. It's these half naked guy and two chicks ;) hehe. That wont fly with corporates if they want to have linux on their desktop.
Anyway doesnt really bother me at the moment but I'll download themes today and replace it.

Where do I copy those themes to for GNOME to recognize them or is it just backrounds etc. ? I see that there is an XML and another file in there.

---

### Post by Slapdash on 2004-11-08
ANother thing while we are at it ;)

How do I mount a my Windows Partision?

I read on the Wiki that mbfs # allows mounting Windows shares. Is that incld the partision or only shared files on that partision?

EDIT:Dont worry I found a HOW TO to try.

---

### Post by fng on 2004-11-08
Sollution for TOTEM:

You are missing some codecs. 
You can follow this how-to ( [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) )for installing mplayer.  It just plays everything.

---

### Post by kaput on 2004-11-08
The codecs *do* work with Totem. However, Ubuntu installs Totem with the Gstreamer backend by default. Try installing Totem-Xine and the codecs will work fine.

---

### Post by Slapdash on 2004-11-08
Thanks guys will try that.

UBUNTU gets 11 out of 10 for community support.  

 =D> 

especially given that I ask such elementry N00B questions ;)

---

### Post by andy_sp1ke on 2004-11-08
Yeah, get rid of the Gstreamer version using synaptic (computer - System Configuartion - synaptic package manager) , then add the repositories for universe and multiverse (settings - repositories, in the new window that opens add the two deselected ones for universe and click ok) then refresh and search for totem. Mark for removal TOtem Gstreamer and mark for installation Totem-Xine!! 

But follow the instructions for MPlayer, there was some good advice in a thread started by me that someone gave because I was stuck on the same thing! Its definitly worth getting MPlayer and XMMS.

---

