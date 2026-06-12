---
title: "Help with eee PC for a new Linux user"
date: 2007-11-05
forum: General Help
---

### Post by mcleblanc19 on 2007-11-05
Hello everyone,

Just got my eee Pc on Saturday,  What a nice little machine !

The only thing, I'm new with Linux and don't even know where to look for the OS version.  Ubuntu, Fedora, Red Hat????  The only thing I saw was Xandros....

I want to install Citrix client to take my office email from it.  After finding a way to unzip a file (tar), I succeeded in installing it but now, I get "error while loading shared librairies: libXm.so.3: cannot open shared object file: no such file or directory "

If I look on the Citrix server, I see that for x86 (I know the eee PC is x86), I need Open Motif and in another web site, I found that this would arrange the problem.

Now, If I go and try to download Openmotif, I need to know the Linux version (Ubuntu, Red Hat, Fedora, etc....).  No Xandros......  is this what I should look into?

Also, how can I do the ASCII codes or get a French keyboard???

Please help !! 

PS.  If there's a book you can suggest that I could find tricks in it, please do not hesitate cause I don't know where to go and I'm pretty good with Windows....   I'll learn.  It's been a long time that I wanted to try Linux.  

Thanks !!!!



:confused:

Marie-Claude Leblanc
[email]mcleblanc19@hotmail.com[/email]

---

### Post by fragos on 2007-11-05
There should be a higher level help function and that would normaly tell you.  You could also look on the manufacturers web site.

---

### Post by mcleblanc19 on 2007-11-05
I searched and searched and searched.  Nothing !

:(


Marie-Claude

---

### Post by Maestro23 on 2007-11-05
> **mcleblanc19 said:**
> I searched and searched and searched.  Nothing !

:(


Marie-Claude

When you booted up the computer, did you see a splash screen with Ubuntu, Xandros, RedHat, etc..?  You say you saw something about Xandros, if so... this is the OS on your system.
If Xandros is the OS, here's the link to their Support site: [http://support.xandros.com/](http://support.xandros.com/)

Here's your system's support link: [http://eeepc.asus.com/en/support.htm](http://eeepc.asus.com/en/support.htm)

Never used the OS or your machine (seems pretty cool though).  Best I can do, good luck.

---

### Post by mcleblanc19 on 2007-11-05
It's too fast.  I don't have time to read more than Intel.....  I say Xandros because it's what I can see from Asus web site on the eee pc web site.  Any other idea or a way to download openmotif that would fit on all versions?  Thanks for your help !


MC

---

### Post by Maestro23 on 2007-11-05
> **mcleblanc19 said:**
> It's too fast.  I don't have time to read more than Intel.....  I say Xandros because it's what I can see from Asus web site on the eee pc web site.  Any other idea or a way to download openmotif that would fit on all versions?  Thanks for your help !


MC

It looks as if Xandros is your OS installed.  You're going to have to dig into how Xandros does things man. Looks as if OpenMotif only comes in a source file.  Again, need to find out how to install from source in the Xandros OS. Installing something from source can be a pain in any Linux OS for someone new to linux.

Are you new to linux?  If so, you have a steep learning curve ahead of you with learning the OS and the machine.

Good luck man.

---

### Post by mcleblanc19 on 2007-11-05
Yep.  Brand new with Linux.  Usually I'm a quick learner but now....  since I don't work in computers....  even tougher....  

I'll look on Xandros web site.

Thanks !


Marie-Claude

---

### Post by patis on 2007-11-05
You would need to install a software package called libmotif3 which provides the missing library. Xandros is a Debian derivate and you should be able to install this package by opening a terminal and typing

```
apt-get install libmotif3
```

But I have no idea how software configuration is handled on the eee. If you are connected to the Internet you could try the above command to see what happens.

---

### Post by mcleblanc19 on 2007-11-05
I just tried and this is what I get (I entered it from /home/user)

E: Could not open lock file /var/lib/dpkg/lock - open (13 permissions denied)
E: Unable to lock the administration directory (/var/lib/lib/dpkg/), are you root?

---

### Post by patis on 2007-11-05
Ok, try this instead:

```
sudo apt-get install libmotif3
```

and enter your own password when asked for one.

Failing this, is there anywhere in the documentation any mention about a "root password"? If you knew it you could try the following

```

su
apt-get install libmotif3

```

Enter the root password after the "su" command.

If this doesn't work either, is there a GUI of some kind where you can install software from? If so, you should be able to install that package from there as well.

---

### Post by mcleblanc19 on 2007-11-05
Something happen but still did not work....

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libmotif3

I didn't find anything about a root password....  what is a gui??

Thanks a lot for trying to help me.  Really appreciated.



Marie-Claude

---

### Post by patis on 2007-11-05
That's not bad, it means that you have the priviledges to upgrade the software. Which command gave you this output (sudo...., or su.....)?

Now I'm curious. Could you please type the following and tell me what you get?

```
cat /etc/apt/sources.list
```

PS. GUI: Graphical User Interface, basically some program which is supposed to give you the possibility to install/remove software.

---

### Post by mcleblanc19 on 2007-11-05
I had the previous with sudo....  don't have a password for su....

with the new one I get 

deb [http://update.eeepc.asus.com/p701](http://update.eeepc.asus.com/p701) p701 main
deb [http://update.eeepc.asus.com/p701/en](http://update.eeepc.asus.com/p701/en)  p701 main

Does it help?


MC

---

### Post by kbracer on 2007-11-05
The eee does run the Xandros distro, but uses a custom desktop. Additional software, including the full KDE desktop, is loaded by adding the Xandros repositories to the sources list via command line use of sudo.

There is a good eee community forum that describes all of this located at...

[www.eeeuser.com](www.eeeuser.com)

Use the link in the bar at the top of that page to get into the forums where most of your questions have probably already been answered.

Good luck

---

### Post by patis on 2007-11-05
I believe the package you need is libmotif3 but is not available in the software repositories you have. As already suggested, try the eee forums; I think you'll have better support there.

Bon soir!

---

### Post by mcleblanc19 on 2007-11-05
i'll have a look at the site. Thanks a lot!

Bonsoir!!


Mc

---

### Post by mcleblanc19 on 2007-11-09
Hello,

Just wanted to let you know that it works !!!  I finally was able to go root and install Citrix.  Without any further installation, my Citrix client now works and I can access my Outlook from my eee.

Thanks for all your help !



Marie-Claude

---

### Post by tonythedog on 2007-11-15
Marie Claude
Good to hear that you got Citrix to work. This is exactly what I want to use the eee for. Please could you list the steps needed to do this in a step by step way for someone new to linux.
Many thanks for your help
Mike

---

