---
title: "Installing drivers! help"
date: 2008-06-09
forum: General Help
---

### Post by sale666 on 2008-06-09
Hello im an lets call it "ubuntu noob" i have experience in computers and i understand a lot of stuff but i do not understand how to install drivers! 

what i will do is dual-boot xp and ubuntu
xp for games and ubuntu for everyday general use...
this is my config:

2GB geil ultra @ 800mhz
Amd athlon 64 X2 6000+ (2 c0res @ 3.0ghz)
Nvidia 8800 Gtx
Asrock alive-NF6G-vsta  Motherboard
2 Hdd's
Seagate 500gb 32mb cache (will be xp c: for games)
Seagate 200gb 8mb cache (will be ext3 or ext2 or whats best for ubuntu)

Now my question is how do i install all the drivers for my configuration! i cannot find them! 

I wana set this up and start using ubuntu right away!
btw i will download 8.04 the new version!

Thanks for your time!:popcorn:

---

### Post by kpkeerthi on 2008-06-09
You only need driver for the GPU (Nvidia 8800 Gtx) you have. Ubuntu installs an open source driver (nv) by default. But this driver lacks 3D capabilities. If you need 3D capabilities, you can install a proprietory nvidia driver (provided by nvidia) from System -> Admin -> Hardware drivers.  Just select the driver listed there and Ubuntu will do the rest. Good luck.

---

### Post by kpkeerthi on 2008-06-09
Oh. I forgot to mention that most of the drivers are already built-into Ubuntu **kernel** and will be automagically loaded as required by your hardware to keep them working. Isn't linux smart?

---

### Post by sale666 on 2008-06-09
> **kpkeerthi said:**
> Oh. I forgot to mention that most of the drivers are already built-into Ubuntu **kernel** and will be automagically loaded as required by your hardware to keep them working. Isn't linux smart?


Yeh thats really smart =)... i like this :D...
so all is installed allready... as for the nvidia driver do i have first to download the driver? or is it allready there?

and one off topic thing... 
can i remove the password asking thing because i never use passwords for my pc its not that i work for Nasa that some 1 wants to see whats in my pc :):lolflag:

---

### Post by kpkeerthi on 2008-06-09
> **kpkeerthi said:**
> You only need driver for the GPU (Nvidia 8800 Gtx) you have. Ubuntu installs an open source driver (nv) by default. But this driver lacks 3D capabilities. [COLOR="Red"]If you need 3D capabilities, you can install a proprietory nvidia driver (provided by nvidia) from System -> Admin -> Hardware drivers.  Just select the driver listed there and Ubuntu will do the rest.[/COLOR] Good luck.

...

---

### Post by kpkeerthi on 2008-06-09
> **sale666 said:**
> 
and one off topic thing... 
can i remove the password asking thing because i never use passwords for my pc its not that i work for Nasa that some 1 wants to see whats in my pc :):lolflag:

After you login to ubuntu desktop, Open a terminal from Applications -> Accessories -> Terminal and type this command
```
passwd
```
When it prompts to enter a *new* password, just press <enter> key
[B]
But I seriously suggest you DON'T do this. You've been warned.[/B]

---

### Post by kpkeerthi on 2008-06-09
There is an option to auto-login. You can enable it from System -> Admin -> Login Window -> Security Tab -> Enable auto login and enter your User Id.

---

### Post by sale666 on 2008-06-09
> **kpkeerthi said:**
> ...

Now im imbarrased :D sorry for that stupid question bout nvidia... looool XD

...

Gr8 i needed the auto login and the no passwd! (btw why shouldnt i do that? will it do something to the system?
now all will work gr8!

Thanks for your time people! =)

---

### Post by MariusSilverwolf on 2008-06-09
It's not recommended to remove the password from the system for one primary, overwhelming, understated reason; it's for your own good.

Now, I know you're thinking, that's crazy, I'm the only one who uses my system, nobody else is going to go wild on me.  That may be all well and good and true.  You're a smart user, you're not going to go hog-wild installing things that could cause problems, and you know malware is more difficult to catch on Linux than on Windows.

But!

The use of the password also serves to protect required system files.  You know how, in Windows, you can access the Windows folder and the Program Files folder and make all the changes you want and effectively kill your system without ever needing administrator access?  Well, to avoid a similar situation in Ubuntu, write access to system folders is allowed only through the use of root access.

Root access is granted through the use of the sudo command on the command line (sudo apt-get, for example) or through the gksudo GUI prompts (asking for a password before letting Synaptic download/install packages).  By protecting these system files, the chances of you causing irreparable harm is significantly reduced.

We know you're not likely to bring down your system inadvertently.  We know you're going to be smart and not go randomly deleting or altering files just to see what happens.  We know you're going to do your research and check the guides and the wikis and double and triple check instructions before you start trying to do anything requiring making custom changes.

We know that.  The OS doesn't.

---

### Post by sale666 on 2008-06-09
Wow thanks for explaining to me! thats a full answear to a lot of my questions actualy! i will not be removing the password since now i know that its made for the system files! thank you!

Since im a new linux user and want to learn and use linux but i do not have any experience in this stuff im doing my best to understand the way it works!

I needed to know how this drivers are being installed now i know i need to go to hardware and it will install itself

I know the password protects the system and not ME as user.

all i need now is to learn this commands
the sudo,su,yum,apg get,jada jada jada theres 1 trilion comands that i do not understand what are for...
you know where i could learn all of them?

im getting my self all the info about how to set up the system so  i can do stuff by myself!

really appreciate your help!

---

### Post by MariusSilverwolf on 2008-06-09
The commands you listed come from a variety of sources, including differing Linux distributions and versions of the same distribution.

But to touch on the ones you can expect to use regularly with Ubuntu (and when running from the terminal, which looks and feels much like the command prompt in Windows)

sudo:  The is an acronym for Super User DO.  It enables a standard user temporary access to administrative-level functions.  It prefaces the command you wish to run with elevated priviledges, and will prompt for a password.  The password entered will be the same password you established during installation, so if your username is "Joe" and your password is "12345", the password you would enter after a sudo command line would be "12345".  The graphical equivalent is a password prompt when accessing system-level functions, such as accessing restricted drivers or changing network settings.

apt-get:  You may also see the alternative "aptitude", depending on the build of the Debian-based distribution.  This is the terminal command used for checking for new versions of software, updating the software, and removing older versions.  The graphical equivalent is the Synaptic Package Manager.

You will often see instructions in How-To's that include the following lines of code:

sudo apt-get update
sudo apt-get upgrade

This is the equivalent of running Windows as a standard user and temporarily gaining Administrator access to run Windows Update from the command prompt.  The graphical method would be to access Synaptic, reload the repository information, and then run Update Manager.  The terminal method is, simply, faster.

The Ubuntu community documentation is extensive, albeit overwhelming to somebody new to the environment.  Read through it, digest what you can, then come back for more when you're hungry again.  And if all else fails, ask questions.  We're (almost) all here to help one another.

---

### Post by kpkeerthi on 2008-06-10
> **sale666 said:**
> Wow thanks for explaining to me! thats a full answear to a lot of my questions actualy! i will not be removing the password since now i know that its made for the system files! thank you!

Since im a new linux user and want to learn and use linux but i do not have any experience in this stuff im doing my best to understand the way it works!

I needed to know how this drivers are being installed now i know i need to go to hardware and it will install itself

I know the password protects the system and not ME as user.

all i need now is to learn this commands
the sudo,su,yum,apg get,jada jada jada theres 1 trilion comands that i do not understand what are for...
you know where i could learn all of them?

im getting my self all the info about how to set up the system so  i can do stuff by myself!

really appreciate your help!

[http://www.linuxcommand.org](http://www.linuxcommand.org) is an excellent place to start.

---

