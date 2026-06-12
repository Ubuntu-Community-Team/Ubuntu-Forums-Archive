---
title: "skype not working"
date: 2014-03-11
forum: General Help
---

### Post by nebula12 on 2014-03-11
hello
i have just installed kubuntu 12.04 and i tried to download skype               [http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)
(i chose ubuntu 12.04 distribution, it did not have an option for kubuntu)
and when i open the deb file i get Error: wrong architecture 'i386'

---

### Post by raja.genupula on 2014-03-11
what is your system bit type ? 32 bit(x84) or 64 bit( AMD) ?

---

### Post by TheUninvited on 2014-03-11
you should download it from ubuntu software center you should already got that program installed.

It's an icon with a bag on the sidebar.

---

### Post by nebula12 on 2014-03-11
there is no skype in the software center
when i had ubuntu 12.04 i opened the deb file and then skype appeared in the software center and i could then download it
my system is 64 bit

---

### Post by Lars Noodén on 2014-03-11
You have to hop through some hoops to get it but the instructions are available:

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

However, once you have done that, I would very much encourage you to install an SIP client along side Skype.  That won't interfere with Skype and will give you more options.  Unlike Skype's protocol, SIP is an open standard and that prevents lock-in to any one product or company, but the discussion of open standards is a whole separate topic.  SIP clients to look at include Ekiga, Linphone, Blink and Jitsi.  I find the sound quality better with some of them than with Skype.

---

### Post by nebula12 on 2014-03-11
i try      [COLOR=#333333][FONT=UbuntuMono]sudo dpkg --add-architecture i386
and i get 

[/FONT][/COLOR]    [COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]dpkg: error: unknown option --add-architecture


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by Lars Noodén on 2014-03-11
Add/remove arch works for me on x86_64.

What architecture do you have just now?

```

uname -a

```

---

### Post by nebula12 on 2014-03-11
3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Lars Noodén on 2014-03-11
Ok.  It looks like the guide is not written for 12.04 and that there have been changes to [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html) since then.  Try --foreign-architecture instead.  

```

sudo dpkg --foreign-architecture i386 

```

---

### Post by nebula12 on 2014-03-11
i skipped the first command that didn't work and tried the next 2 and they worked ( [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) ) 
skype seems to be ok now
do u think there will be a problem?
i needed the architecture command because i have a 64bit system?

---

### Post by Lars Noodén on 2014-03-11
Yes, presumably it's because you have a 64-bit system.  However, maybe that step is not needed.

---

### Post by nebula12 on 2014-03-11
thank you very very much! ;)

---

### Post by monkeybrain20122 on 2014-03-11
Kubuntu comes with muon package manager you can just add Canonical's Partner repo by checking a box in sources or something (sorry I don't use kde now so can't be more precise but it is easy to figure out) then you can install Skype from the repo. Don't make things more complicated than it has to be. :)

---

### Post by Lars Noodén on 2014-03-11
Now that I look, Synaptic also has a checkbox to add Partner repositories.  Either way, the guide also works.

---

