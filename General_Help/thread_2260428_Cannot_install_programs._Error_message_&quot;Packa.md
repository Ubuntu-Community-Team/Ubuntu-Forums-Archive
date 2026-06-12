---
title: "Cannot install programs. Error message: &quot;Package dependencies cannot be resolved&quot;"
date: 2015-01-11
forum: General Help
---

### Post by ryan4 on 2015-01-11
I get the following error when trying to install any programs using Ubuntu Software Center:

"Package dependencies cannot be resolved"

When trying to install LibreOffice Impress, I get the above error with the following:

The following packages have unmet dependencies:

libreoffice-impress: Depends: libreoffice-core (= 1:4.2.7-0ubuntu2) but 1:4.3.0-0ubuntu1~precise1 is to be installed
                     Depends: libreoffice-draw (= 1:4.2.7-0ubuntu2) but 1:4.2.7-0ubuntu2 is to be installed


What is going on?

---

### Post by CantankRus on 2015-01-11
What Ubuntu release are you using...
```
lsb_release -a
```

and your enabled sources
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

...and maybe more info like 
[LIST]
[*]freshinstall/upgrade
[*]any third party repositories previously used
[/LIST]

---

### Post by grahammechanical on 2015-01-11
Libreoffice Impress is part of the default install of Libreoffice. Did you remove Impress?

---

### Post by ryan4 on 2015-01-13
```
ryan@ryan-X75A:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
ryan@ryan-X75A:~$ 
ryan@ryan-X75A:~$ 
ryan@ryan-X75A:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://ca.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
ryan@ryan-X75A:~$

```

I installed Ubuntu almost 2 years ago on this computer. I don't know anything about 3rd party repositories. As to Impress being part of LibreOffice, it must not have been installed with LibreOffice. I don't like to install more than I use, and I have never needed to use Impress until now. So I am guessing that I chose not to install it with LibreOffice.

---

### Post by ryan4 on 2015-01-14
Does anyone have any idea what might be causing my problem (other than my own lack of knowledge about Linux and motivation to learn how it all works)?

---

### Post by Bashing-om on 2015-01-14
ryan4; Humm ..

Strange and curious.
You are on trusty, so why is " 1:4.3.0-0ubuntu1~precise1 is to be installed " ??
Any hints here ?
```

apt-mark showholds

```

And what is actually installed ?
```

apt-cache policy  libreoffice-core
apt-cache policy  libreoffice

```

as we have :
> 
You have searched for packages that names contain libreoffice-core in suite(s) trusty-updates, all sections, and all architectures. Found 1 matching packages.

Exact hits

Package libreoffice-core

trusty-updates (editors): office productivity suite -- arch-dependent files 
1:4.2.7-0ubuntu2: amd64 i386


Gotta be a cause that the precise version is holding on

[INDENT][INDENT]seek and we shall find
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-01-15
> **ryan4 said:**
> 
I installed Ubuntu almost 2 years ago on this computer. I don't know anything about 3rd party repositories. As to Impress being part of LibreOffice, it must not have been installed with LibreOffice. I don't like to install more than I use, and I have never needed to use Impress until now. So I am guessing that I chose not to install it with LibreOffice.

Well you may not know about "3rd party repositories" but you used one while on Precise - as in here
[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases)

You can remove all LO packages from that ppa, update your sources & re-install trusty versions
or
enable the ppa for trusty, update sources, upgrade, then use ppa-purge to return to trusty versions
or
go here & download & install the impress package manually- 
i386 - [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234957](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234957)
amd64 - [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234956](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234956)

---

### Post by ryan4 on 2015-01-15
```
ryan@ryan-X75A:~$ apt-mark showholds
ryan@ryan-X75A:~$ apt-cache policy  libreoffice-core
libreoffice-core:
  Installed: 1:4.3.0-0ubuntu1~precise1
  Candidate: 1:4.3.0-0ubuntu1~precise1
  Version table:
 *** 1:4.3.0-0ubuntu1~precise1 0
        100 /var/lib/dpkg/status
     1:4.2.7-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
ryan@ryan-X75A:~$ apt-cache policy  libreoffice
libreoffice:
  Installed: (none)
  Candidate: 1:4.2.7-0ubuntu2
  Version table:
     1:4.2.7-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
     1:4.2.7-0ubuntu1 0
        500 http://security.ubuntu.com/ubuntu/ trusty-security/universe amd64 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
ryan@ryan-X75A:~$ 


```

---

### Post by ryan4 on 2015-01-15
> **mc4man said:**
> Well you may not know about "3rd party repositories" but you used one while on Precise - as in here
[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases)

You can remove all LO packages from that ppa, update your sources & re-install trusty versions
or
enable the ppa for trusty, update sources, upgrade, then use ppa-purge to return to trusty versions
or
go here & download & install the impress package manually- 
i386 - [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234957](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234957)
amd64 - [https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234956](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-prereleases/+build/6234956)

Which is easiest? I use the Installer because I am not a "computer person." But my problem is not just with LibreOffice or Impress, I am unable to install anything right now.

---

### Post by ryan4 on 2015-01-19
Is anyone free to respond to the issue I am having installing programs?

---

### Post by Bashing-om on 2015-01-20
ryan4; Hey,

Still try'n to hang with you .

> **ryan4 said:**
> Is anyone free to respond to the issue I am having installing programs?

Not quite free enough to the point that I am able to give my full focus to this. 

We can not tell you what to do, just present some options. But, in my opinion the better thing is to try and ppa-purge 'libreoffice' and come up on the repository version .
It is your system, the way you use your system with the apps you want on your system -> you make the call as presented by mc4man as to what you want to do. Then we respond to your decision .

[INDENT][INDENT]all in a day's work
[/INDENT][/INDENT]

---

### Post by ryan4 on 2015-01-21
Okay, I will work on these suggestions when I have some time and report back. It may take me a day or so as I need to look up all these different things to figure out what it means. Thanks again for your help everyone.

---

### Post by Bashing-om on 2015-01-21
ryan4; Good 'nuf;

We are here to help, but we can not tell you what to do. It is great you are doing your homework.
As and if you have questions and concerns, by all means ask ... we will do our best to answer.

[INDENT][INDENT]a well thought out question
[INDENT][INDENT][INDENT]gets a better response
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ryan4 on 2015-01-21
I removed LibreOffice with the following:
```

sudo add-apt-repository ppa:libreoffice/ppa --remove
sudo apt-get update
sudo apt-get purge libreoffice*


```

Then I installed LibreOffice Writer and Impress using the Software Center. It solved the above problem, but I now have a new problem which I did not have before.

If I try to open ODT files, I am forced to exit LibreOffice. I have no trouble with DOCX files. I have no problems with Impress. But most of my files are ODT files so I need to be able to open them. Any ideas here?

---

### Post by ryan4 on 2015-01-25
In addition to my problem with ODT files, if I save as a DOCX (which is what I did since I could not use ODT) and reopen my file it is blank or empty. I just lost 4 hours of work this way. Boo.

---

### Post by mc4man on 2015-01-25
Assuming you're all squared away maybe try this - 
Go to .config/libreoffice/4 & rename the user folder to user.bak Then try using writer to open a odt file & see..

---

### Post by ryan4 on 2015-01-27
mc4man,

I tried your suggestion and there is no change. If I open libreoffice and try to save an ODT file I get the following error:

Error saving the document Untitled1:
Write Error.
Error writing file.

---

### Post by mc4man on 2015-01-27
Well that's unfortunate. Try using writer in a guest session & see if it works there. If it does then the issue is somewhere in your config's, if it also errors in a guest session then it's a system problem which *may* be easier to rectify.

---

### Post by ryan4 on 2015-01-27
I get the same problem in a guest session.

---

### Post by mc4man on 2015-01-27
What I'd probably do is add back the LO pre-release ppa, update sources & do a dist-upgrade. You could simulate the dist-upgrade first if desired
```
sudo  apt-get -s dist-upgrade
```
If the sim looks ok then go ahead with it. That will give you trusty packages for all installed LO packages you have. 

Then you could recheck writing/saving an .odt, hopefully it works.
At that point you could keep the pre-release packages or install ppa-purge & use it to downgrade back to trusty repo versions.
```
sudo ppa-purge ppa:libreoffice/libreoffice-prereleases
```

Do note:
That ppa page is sorta specific about using, maybe read the page & follow that method first instead of a dist-upgrade. (you can always do a dist-upgrade later if need be
Then check writer & odt, see if it works, ect.

---

### Post by ryan4 on 2015-01-28
How do I > add back the LO pre-release ppa, update sources & do a dist-upgrade ?

---

