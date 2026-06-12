---
title: "Installing new linux programs from the internet"
date: 2008-06-13
forum: General Help
---

### Post by The KB Stockpiler on 2008-06-13
I thought that one half of the advantage to Linux was the free programs. Would someone please refer me to the information on how to install programs that the distro didn't come with like the one's on the inter net? All I know how to do is down-load the zip files.Also can the same be done with mandriva or is it made imposable so you you have to buy the applications from them?                                   
                                          Thank You the kb stockpiler

---

### Post by cariboo on 2008-06-13
What kind of programs are you trying to install? If you open synaptic (System-->Administration-->Synaptic Package Manager) there are 10,000+ packages listed. You should be able to find something to install in that listing.:)

Mandriva if I remember correctly is rpm based, but they should have something similar to synaptic for package management.

Jim

---

### Post by overdrank on 2008-06-13
> **The KB Stockpiler said:**
> I thought that one half of the advantage to Linux was the free programs. Would someone please refer me to the information on how to install programs that the distro didn't come with like the one's on the inter net? All I know how to do is down-load the zip files.Also can the same be done with mandriva or is it made imposable so you you have to buy the applications from them?                                   
                                          Thank You the kb stockpiler

HI and what program or app are you looking for? Have you search synaptic or add and remove. 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
Mandriva uses rpm for installation and you can enable repos also to find what you are looking for.

Echo lol :)

---

### Post by drs305 on 2008-06-13
[How to install ANYTHING in Ubuntu!:  ]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by The Tronyx on 2008-06-13
I am not sure if I understand your question completely.  There is a lot of software in the repositories that does not come installed on the distribution.  These packages can be access via Synaptic Package Manager. 

Ubuntu is a Debian-based.  This means that there are packages which include dependencies and can be installed easily (most of the time).  The files you are looking for would be referred to as .deb packages and can be installed using "sudo dpkg -i <packagename.deb> .

As far as other programs, there is always compiling from source.  For further instructions on compiling from source, see [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware) .

It should be noted that you always want to pay close attention just what it is you install and download as there is no assurance of quality or security with regard to installing unsupported software.

For additional information on software management and installation in Ubuntu you may want to refer to [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement) as it will help to fill in many of the blanks that come with such a short post.

Hope that helps and welcome to Ubuntu! :guitar:

---

### Post by paulderol on 2008-06-13
.deb files are the kinds of packages that you can install without issue, just double click on those, and gdebi will open up for you and install the program, which you may then have to start from the terminal, or create a menu item for it yourself.

.rpm files and other formats for different package management systems can be converted [in MOST cases] through a program called alien, which converts .rpms and a couple of other formats into .deb or vice verse. 

from the terminal type

```
sudo apt-get install alien
man alien

```
the man page should help you with syntax options and parameters, but it's set to generate .deb files by default. 

so, if you wanted to do this to a package, extract the archive to your desktop, then, in the terminal type
```

cd ~/Desktop
alien -v -T package.rpm 
```

the first moves you from your home directory to your desktop, the second begins alien in verbose mode (-v) [so it will let you know what's going on] and Test mode (-T) [so it will test the package for successful transfer]

if you're trying to install from source code, you will need to install the subversion libraries and assorted build tools. the build-essentials metapackage i think has all of these in it. 

hope that helps.

---

### Post by Pjotr123 on 2008-06-13
This is how you install applications in Ubuntu:
[http://ubuntutip.googlepages.com/installingapplications](http://ubuntutip.googlepages.com/installingapplications)

You'll agree: it's easier than installing in Windows.  :-)

---

### Post by aysiu on 2008-06-13
Searching for software through a web browser and downloading it off a website should be a last resort. Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by The KB Stockpiler on 2008-06-13
Thank you all for the responses. My first operating system was naturally windows so I compare the linux distros to it. I tried to get on the inter net with Ubuntu but I couldn't get any actual information on how to use dial-up.I don't use any media that requires cable,DSL isn't available in Rochester NY and wireless is a cancer causing, equipment burdening disappointment. I installed Mandriva because I heard it had all the drivers that were needed.I wanted to play some games that I couldn't on Mandriva Gnome and I couldn't remember if they were on Ubuntu Gnome or Mandriva K whatever. So I was fooling around with the live Ubuntu distro and finally figured out how to use dial-up.All you have to do is configure the dial up in the network application and mark the box in the dial log box with a check mark  to connect the modem and disconnect the modem. The port is the first one offered I believe.You don't have to ping anything or use set serial. Everything that is needed comes with the official Ubuntu distro. All you really might need is a serial modem.like everyone said the dial up provider didn't know anything about anything but My computer works fine on Idial .net when they say they don't support linux. So any way the K whatever Mandriva release had a version of asteroids I wanted to play and I miss the pinball game on windows when I'm on Mandriva. Other than games I wanted a spell checker that worked on every thing not just the word processor like "As you Type or" Accuspell." Another thing if you have one phone line you don't want to tie it up so a down loadable thesaurus would be nice.I also wanted to learn how to  Make web pages with Html and css. 
                                    Thanks again for getting me started. 
                                            the kb stockpiler

---

### Post by theevilone on 2008-06-15
can somebody tell me how to download google earth. the mis-spelled version will not open. when downloaded from google can not find an application to download it.

I do not understand how people said this is better than windows. with windows click and stuff is downloaded, with this os you have to be a software engineer.

---

### Post by theevilone on 2008-06-15
ok now I downloaded google earth from the package manager now I can not find it. no searchers will turn it up.

where did it go?

---

### Post by overdrank on 2008-06-15
> **theevilone said:**
> ok now I downloaded google earth from the package manager now I can not find it. no searchers will turn it up.

where did it go?

Hi and welcome, some times you have to restart x before it will show in applications. Anyway you can use the keys alt, F2 and enter the command googleearth. It should start then and as you type it should show you what is the next letter.

---

### Post by theevilone on 2008-06-17
google earth still not working. I reinstall still nothing. but this message.

Could not open location 'file:///home/theevilone/googleearth'

now what?

when I documents and click on the file I get this.

Couldn't display "/home/theevilone/GoogleEarthLinux.bin".There is no application installed for this file type

can not find a application.

---

### Post by oldos2er on 2008-06-17
Right-click on the googleearth.bin file, click Properties, Permissions, and check the box 'Allow executing file as program'. Then double-click it again.

---

### Post by aysiu on 2008-06-17
Just paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install googleearth
```

---

