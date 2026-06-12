---
title: "newbie question; encountering endless list of 'dependency is not satisfiable' errors"
date: 2006-11-18
forum: General Help
---

### Post by jlebouton on 2006-11-18
Hello, total newbie question.  I'm trying to install r-base-core_2.4.0-0dapper2_i386.deb on a brand-new installation off the UBUNTU PC CD-ROM installation disc.

I downloaded the r .deb file (named fully above), ran the .deb file, and immediately got an error message: "Error: Dependency is not satisfiable: zlib-bin"

So like a good scout I went looking for zlib-bin, downloaded THAT .deb file, and ran it.  I immediately got an error message, "Error: Dependency is not satisfiable: libc6".

So like a good scout I went looking for libc6 on the web.  Found it, downloaded it, and ran it.  I immediately got an error message, "Error: Dependency is not satisfiable: tzdata".

So like a good but slightly cranky scout I went looking for tzdata.  Found tzdata_2006n-1_all.deb, downloaded it, ran it, and ALL DEPENDENCIES ARE SATISFIED for this installation... but the install bombed out because the installation tried to over-write a file named "zones" and was denied permission.

I don't feel like a good scout anymore so i'm wimpering like a an Ubuntu-whipped human being... can anyone explain to this technophobic newbie what's going on?  help....

---

### Post by loell on 2006-11-18
are you on edgy? 

what is r-base-core_2.4.0-0dapper2_i386.deb?

unsatisfiable dependency occurs, when a library needed for that package is not on your system, and cannot be found on the repository

---

### Post by catlett on 2006-11-18
The only way to ensure that a program will work is to install the program through Synaptic Package Manager. Whenever you go outside the repositories, you run the risk of incompatable libraries. 
Windows is different. There is only one windows. There are hundreds of linux's. There isn't a 'base' linux that distros build off of. Linux is just the kernel. A distro is all the other stuff added on. Even then different distros may use different versions of the kernel.
This may help with installations but once you go outside the repositories, nothing is guaranteed. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by CatKiller on 2006-11-19
If you'd like to see the list of dependencies for **r-base-core**, look [here]("http://packages.ubuntu.com/dapper/math/r-base-core"). Of course, those packages may have unmet dependencies too. Which is why you'd use a package manager like **Synaptic** or **Aptitude**. Read the link that catlett posted, and you'll see that it's really easy most of the time.

Is the problem that you don't have an Internet connection on your Ubuntu computer?

---

### Post by jlebouton on 2006-11-19
Thanks for the good information.  catlett's link explains the install process perfectly, and CatKiller's link to r-base-core dependencies list is very helpful, too.

now... my happy new Ubuntu machine is a laptop with only a lowly modem for internet connectivity, and I haven't been able to get it to work.  I have therefore been downloading additions to Ubuntu on my Windows machine over a dialup connection.  (Let's not discuss anything about my newfound freedom from Windows as I'm likely to snivel a bit...)

Given that information, and all I've gleaned from the reading above, this is what I understand that I need to do now, please correct me if I'm wrong:

1) download each of the 18 packages listed as "depends" individually onto my Windows computer, 
2) copy all the packages to my flash drive, 
3) copy the files from the flash drive to the Ubuntu laptop  
4) convince Synaptic to see the new packages? via file-add downloaded packages?
5) there will be an available r-base package to install, which will result in much rejoicing and even dancing in the streets. 

Or is there an alternative, given that my Ubuntu machine isn't internet-connected?

---

