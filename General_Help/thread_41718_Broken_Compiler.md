---
title: "Broken Compiler"
date: 2005-06-14
forum: General Help
---

### Post by petrol on 2005-06-14
:-x I am in over my head. I needed libmotif3 for the ICA client. This required that I load a newer version of libc6. I found libc6_2.3.2.ds1-22_i386.deb and promptly installed it. I am now getting errors that my C compiler can't make executables. I reinstalled libc6_2.3.2.ds1-20ubuntu13_i386.deb. Now when I try to compile it doesn't find gcc:

<username>@petrol2:~/downloads/ayttm-0.4.6$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH



<username>@petrol2:~/downloads/ayttm-0.4.6$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 3:3.3) but it is not going to be installed
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.4.1.19) but it is not going to be installed
  libmotif3: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I need libmotif to be left alone for ICA. I am just all kinds of confused. If you have recovered from this compiler mess please share :grin:

---

### Post by Xian on 2005-06-14
What happens when you run this command:

```
$ sudo apt-get -f install
```

---

### Post by petrol on 2005-06-14
It tries to take off libmotif3. Would having a broken dependancy prevent me from installing? Can I remove this dependancy in a DB? :-? Is this something I need to make a choice on?

---

### Post by Xian on 2005-06-14
[QUOTE=petrol]It tries to take off libmotif3. Would having a broken dependancy prevent me from installing? Can I remove this dependancy in a DB? :-?[/QUOTE]
Yeah, it's trying to tell you that libmotif has broken deps, and that sure will prevent APT from performing further installations. AFAIK the only method to get past this is to either let APT resolve the broken package or install what is causing it to be in that state, which I think you mentioned is a version of libc6.

You might try letting APT resolve that broken dep, install the build-essential package, and then go back and see if you can reset the lib6 and libmotif packages. Next you would attempt the compile again and hopefully get past that configure error.

---

### Post by petrol on 2005-06-14
After installing libc6_2.3.2.ds1-22_i386.deb apt wants to remove a ton of stuff. 

<username>@petrol2:~/downloads/ayttm-0.4.6$ sudo apt-get -f install Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  build-essential g++ g++-3.3 libc6-dev libstdc++5-3.3-dev

Is "reseting the package" a RTFM thing?

---

### Post by Xian on 2005-06-14
Sorry, it was a long shot at best but the only alternative I could come up with other than to just let APT resolve the deps itself and leave you without the needed versions on your system.

The only other binary thing you can do is not use APT, and just install what you need using the rpm command with the no-deps options, but I do not even suggest that you follow this route as you won't ever be able to use APT again without facing the same issue, and then it is also not possible to say what other issues might arise.

You could also try to find a source rpm (SRPM) for that libc6 package, rebuild it on your box, and then use the dep alien command to convert it, and try to see if it will fit in APT using that procedure. This is not risky at all but could be time consuming and leave you in a position that is no different from now. I'm not as familiar with rebuilding source deb files but that would also be a route to investigate.

A lot of this is just me thinking out loud...typing.... :)

---

### Post by petrol on 2005-06-14
From what it sounds like I have to choose between running the citrix ICA client and using apt. It seems like this would have been a show stopper for more people. At this point I am able to compile and run the ICA client, so I am farther than I was before. I am just unable to use apt. Is there a way to get it to ignore specific dependancies? Is this something that I need to wait for the current version to be in the repositories? ](*,)

---

### Post by Knome_fan on 2005-06-14
This may be a dumb question, but I just checked synaptic and libmotif3 is available in hoary, so why did you need to install some other version of libmotif3 that required an other libc?

Also, simply using a non-hoary libc6 certainly isn't a very good idea, as you probably have figured out yourself by now. If you really need an other, newer version of libmotif3, compiling it yourself (using dpkg-buildpackage if possible) is probably a much better option.

---

### Post by Xian on 2005-06-14
[QUOTE=petrol]Is there a way to get it to ignore specific dependancies? Is this something that I need to wait for the current version to be in the repositories? ](*,)[/QUOTE]
There's a way to get it to ignore packages but that doesn't affect the deps that it sees. Maybe someone else has an idea, but I've just never heard of such a functionality.

---

### Post by Xian on 2005-06-14
[QUOTE=Knome_fan]If you really need an other, newer version of libmotif3, compiling it yourself (using dpkg-buildpackage if possible) is probably a much better option.[/QUOTE]
Yeah, that's what I was getting at. Sorry, but I'm still getting used to these deb resources myself (I've got a RPM build background). If the process is similar then you might have an answer right there.

---

### Post by petrol on 2005-06-15
This is what I get when I set libc6 back to the ubuntu version and go the synaptic route:

Package libmotif3 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

You can see my sources file above.

---

### Post by Knome_fan on 2005-06-15
I just checked and its in the multiverse repository.

Do you have multiverse enabled in your source.list?

---

### Post by petrol on 2005-06-15
From what I can tell the multiverse ones are at the bottom. This is my current sources list.

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Marillat
# deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by Knome_fan on 2005-06-15
Ah, I think I know where the problem is. You only have the backports multivers repository, not the "normal" hoary one.

Simply add:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

and 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security multiverse

to your sources.list and libmotif3 should be there (I hope :-)

---

### Post by petrol on 2005-06-15
Big ups to Knome_fan!!! I saw that I had two repositories missing. I don't know how I could have missed it in the noob guide...

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

I was able to load them in synaptic and the citrix client works.
Also much thanks to Xian for the help. \\:D/  :grin:

---

