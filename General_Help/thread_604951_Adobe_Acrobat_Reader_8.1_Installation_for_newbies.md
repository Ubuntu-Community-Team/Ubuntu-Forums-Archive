---
title: "Adobe Acrobat Reader 8.1 Installation for newbies"
date: 2007-11-06
forum: General Help
---

### Post by jfank on 2007-11-06
This is a 3 very simple installation step of installing the Windows version of the newest release of Adobe Acrobat Reader version 8.1.  This 3 step procedure has been tested on Ubuntu, Kubuntu, Xubuntu, and was a success.  This was mostly tested on the Intel 32-bit system, and worked perfectly.  I had a couple of friends test these 3 simple steps on their AMD 64-bit system, and it was a success.  Now with the problems of the 64-bit system there is no guarantee of a successful installation.  So far the people that have the 64-bit installation did inform me of success.  

With these 3 very simple steps all you have to do is copy and paste the 3 different script codes into the Terminal.  If you do encounter any problems with the installation please post a reply on this topic explaining the problem, and what the terminal gave you for the error.  Thank you, and I hope this 3 very easy installation process works for you.  Those of you with the 64-bit system; please make sure you post a reply with the problem, and I will help you or someone else that visits this forum will help you.

STEP 1
> echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free" | sudo tee -a /etc/apt/sources.list

STEP 2
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

STEP 3
> sudo aptitude install acroread acroread-plugins acroread-escript

It may take some time for all of the files to download.  This of course depends on the speed on internet you are using, and the computer system you have.  When I installed this program onto my computer it took a tad bit longer than usual, because I was connected to the internet through the router using the wireless connection, and several other computers, and the Xbox 360 video game system running at the same time.

This program is NOT NEEDED to read the PDF files, because ALL versions of Ubuntu comes with a program that will read even the most current formats of the PDF file.  Thank you for viewing this topic, and I as well as others hope these steps work perfectly with no errors.

Also for those of you that are newbies please click on the link below to learn different items of running a Linux Operating System.  I myself have to look at this website several times, because I am a newbie to the world of Linux.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Adobe_Reader_Gutsy_amd64.2Fi386]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Adobe_Reader_Gutsy_amd64.2Fi386")

---

### Post by jfank on 2007-12-11
I do want to add to this thread that I am currently doing some research on installing Adobe Acrobat Reader Professional.  Even though there is programs made for Linux to make and write PDF files; I will do my best to see how to get the professional version to work without the use of CodeWeavers.  It might take some time, or if anyone knows how to do it post in here.  I've seen it asked on many other threads, however no program answer givin.

---

### Post by MoToR on 2007-12-14
Hi, could you (or anyone else) please explain what exactly do STEP 1 & STEP 2 do?

---

### Post by r-mo on 2007-12-14
STEP 1 adds the third-party medibuntu repository to your software sources, it just says append the line: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free to the file /etc/apt/sources.list

STEP 2 does a few things
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

it downloads a signature key for the repo to authenticate the packages you download are really cominng from that repository (the wget command)

It adds it to your approved key (apt-key add)

and it updates your package list (apt-get update)

The | is a very useful character when working in the terminal.  It says feed whatever is output from this command into the next one.

---

### Post by jfank on 2007-12-14
The sudo apt-get update should always be done after installing programs to your operating system to make sure that any linked files or missing files in the repositories can be updated.  r-mo is right this is one of the most inportant things to do.  As far as explaining it thank you r-mo, because I never did read to see what step one and step two fully did.  Now I also myself fully know what those steps do.  I knew part of it just not all of it.  Thank you again, and anyone that uses these steps if there is a problem where it don't work please post a message on here about it so we can find a solution to the problem and fix it.

---

### Post by MoToR on 2008-02-11
Thanks **r-mo** and **jfank**.

---

### Post by Charles2008 on 2008-02-12
I get this error when I try to reinstall adobe reader.  ```
acroread:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
```

Please advise,

Thanks,

Charles

---

### Post by Charles2008 on 2008-02-12
My previous post was trying to install from Synaptic.  This is the output from after following step three from above.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  acroread 
The following NEW packages will be automatically installed:
  acroread-escript 
The following NEW packages will be installed:
  acroread-escript acroread-plugins 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.3MB/48.3MB of archives. After unpacking 120MB will be used.
The following packages have unmet dependencies:
  acroread: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

The pdf viewer that comes with Ubuntu 7.1 was unable to print pdfs.  It would freeze up.   
Only able to print with adobe reader.  

Thanks 

Charles

---

### Post by darkruler on 2008-03-13
2 **Charles2008**:

Here is the solution to your problem:

1) You need to manually download fresh versions (these are supposed to be 1.18.3) of *libpango1.0* and *libpango1.0-common*.

Links:

[http://packages.ubuntu.com/gutsy-updates/libpango1.0-common]("http://packages.ubuntu.com/gutsy-updates/libpango1.0-common")
[http://packages.ubuntu.com/gutsy-updates/libpango1.0-0]("http://packages.ubuntu.com/gutsy-updates/libpango1.0-0")


2) You need to manually install each of them. Note that you have to install *libpango1.0-common* prior to *libpango1.0* installation.
```

dpkg -i libpango1.0-common_1.18.3-0ubuntu1_all.deb
dpkg -i libpango1.0-0_1.18.3-0ubuntu1_i386.deb
```

---

### Post by jcobban on 2008-03-13
I have encountered this same problem in installing Adobe Acrobat Reader, but, as a newbie, I don't know exactly how I am supposed to do the download.  I follow the hyperlinks to the libpango files, click on the download hyperlink, which takes me to a list of mirrors.  When I select a mirror the package file is displayed in the browser!

I am a Ubuntu newbie, and almost a UNIX newbie.  I just got fed up with Windows and decided to migrate.  I tried a another distro but I like the Ubuntu philosophy and I am willing to put up with a few rough edges on the installation process for software.  After all you don't install software all that often once you get the system working. Perhaps someone could explain to me why I can't just download the rpm from the Adobe site?

---

### Post by cherry316316 on 2008-04-08
for hardy heron 
```

The following packages have unmet dependencies:
  acroread: Depends: libldap2 which is a virtual package.

```

---

### Post by taliosfalcon on 2008-04-11
So..slight problem getting the plugin working, i've installed everything via apt-get, however it added nothing to my plugins folder, and doing an updatedb then slocate nppdf.so brings up absolutely no results, so I can't make the link myself...suggestions?

---

### Post by cherry316316 on 2008-04-18
> **jfank said:**
> I do want to add to this thread that I am currently doing some research on installing Adobe Acrobat Reader Professional.  Even though there is programs made for Linux to make and write PDF files; I will do my best to see how to get the professional version to work without the use of CodeWeavers.  It might take some time, or if anyone knows how to do it post in here.  I've seen it asked on many other threads, however no program answer givin.

did u get the professional version running on linux ??/

is there a way , we can modify the windows professional version and install it on linux ?

---

### Post by cherry316316 on 2008-04-25
for hardy, you have to change the gusty in the key line to hardy.

kindly correct the line or make another paragraph , so that the new baby
using hardy don't get into problem

---

### Post by jfank on 2008-06-03
> **cherry316316 said:**
> did u get the professional version running on linux ??/

is there a way , we can modify the windows professional version and install it on linux ?

No sadly I never did find a way to get it to work without using codeweavers.  That is the only to get it to work from what I have found.  I'm sorry I didn't update this information sooner.

I tried to change the gusty to hardy, but it is having problems letting me edit my thread.  I will try to get it changed within the next couple of days.  I need to do some work to my OS to get everything working correctly.

---

### Post by ahmadzainul on 2008-06-09
thank you, it is very usefully for me. Kiss bye all :popcorn:

---

