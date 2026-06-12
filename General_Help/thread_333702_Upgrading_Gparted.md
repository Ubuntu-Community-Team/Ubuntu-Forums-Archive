---
title: "Upgrading Gparted"
date: 2007-01-07
forum: General Help
---

### Post by mhenriday on 2007-01-07
For reasons beyond the scope of this posting - OK, I was trying (vainly, as it turned out) to partition my hard disc to make running a dual-boot **Ubuntu-Windows** system possible - I've had occasion to make extensive use of **Gparted** these last few days. The default version provided by **Ubuntu 6.10** is 0.2.5-1.1-ubuntu1.1 ; I've been using the live CD version 0.3.3. It would be more convenient to avoid the need to frequently re-boot my computer while working with **Gparted** ;I should thus be grateful for help in updating the default version supplied in **6.10** to the latest version which was released in December. What I need help with is _installing_ the new version, after downloading it - how do I get it to replace the present version so that I can access it via **System&#8594;Administration&#8594;Gparted** ?...

Thanks.

Henri

---

### Post by bruenig on 2007-01-07
First, I will say that generally, unless you are partitioning non mounted partitions, like auxiliary data partitions, getting it on 6.10 won't really matter because you will have to go to live cd anyways.

Also, I am wondering what sort of functionality exists in the latest one that doesn't exist in the 6.10 version that is giving you problems?

But here is how I would do it,

First remove the current one and make sure you have all the tools to compile and just to make sure you have all the dependencies for gparted use build-dep
```
sudo apt-get remove gparted
sudo apt-get install build-essential
sudo apt-get build-dep gparted
```

Second, download the new one
```
wget http://superb-east.dl.sourceforge.net/sourceforge/gparted/gparted-0.3.3.tar.gz
```

Third, extract and change into the extracted directory
```
tar xf gparted-0.3.3.tar.gz
cd gparted-0.3.3/
```

Now configure it and install it
```
./configure
make
sudo make install
```
If there is an error in the configure and since I haven't done this myself I can't be sure that there won't be, the make and make install won't work. But I think that there should not be an error because of the build-dep.
Also note that it may not show up in system>administration but it should show up in the menus somewhere, I am not sure where.

---

### Post by mhenriday on 2007-01-08
Thanks, **bruenig**, for your speedy reply ! To deal first with your (implied) questions, the reason I want to upgrade from the 0.2.5 version presently installed on my computer to the latest 0.3.3 version is that I have an, admittedly diffuse, impression that it is much easier to work with the live CD version (i e, that fewer of the options are greyed out) than the installed, and I presumed, perhaps erroneously, that this was due to the improvements that had been made to **Gparted** since the release of the earlier version. You must understand that I am an utter novice, if not to computers, at least to **Linux** systems, and thus to **Ubuntu** and **Gparted**. For example, I don't really understand why I should have to use the live CD to modify the partitions on my hard disc, if I have the same (or a similar) programme already installed. Can you explain this to me ?...

More questions : when I click on download at sourceforge.net, I am offered a choice between saving the **Gparted** tarball to a disc or extracting it with the archive manager. Based upon my **Windows** experience, I should have expected that extracting this archive in this manner would have _installed_ the files, but this doesn't seem to be the case. If I have understood correctly, further procedures, such as those you describe above, are necessary in **Ubuntu**. Is this the case, and is it also the case for other programmes, like OpenOffice.org, which I should like to update ?...

What exactly does the command «build-essential» do (as you can see, I _am_ a complete novice when it comes to **Ubuntu** !) ? What exactly does «build-dep gparted» do, and more equally important, _where_ does it do it ? Where is the gparted directory, which I presume is the result of extracting with «tar xf gparted-0.3.3.tar.gz», placed ? (And by the way, should this command be «tar xf gparted-0.3.3.tar.gz», as you write, or should it be «tar xvzf gparted-0.3.3.tar.gz», which form I have also seen, or does executing these two lead to precisely the same consequences ?)

These questions are no doubt elementary for those familiar with **Ubuntu** and **Linux** systems, but for novices like myself the answers are not immediately obvious. If you know of any relevant tutorials available on the net that can help provide a background for better understanding these matters, I should be most happy to hear about them !...

Thanks again for your help !...

Henri

---

### Post by bruenig on 2007-01-08
Alright well first the reason the options are greyed out is because you cannot mess with mounted partitions. Your root partitions, the one ubuntu is on is mounted, obviously, else ubuntu wouldn't be running. And any other partitions that you can see are automatically mounted at boot. Since you can't unmount them (doing so would mean you would effectively unmount your operating system), you can't modify them without live cd.

The first three commands are apt-get commands. The Synaptic Package Manager which I presume you are familiar with is a front-end for that. When you click to install a package in synaptic, it actually does apt-get (or it may do aptitude but those are similar enough to not worry about the menutiae in this context). So apt-get remove will remove the package. apt-get install will install a package. So you are removing gparted. Then installing build-essential. The build-essential package gives you all the tools necessary to compile things, which since you were getting the source from gparted and not the ubuntu repositories, you would have to do that. The build-dep is an apt-get command that installs all of the dependencies for a package. A dependency is something that a package depends on in order to work. Since the dependencies for the gparted in the repositories are likely similar if not exactly the same, I build-dep in order to make sure there won't be any problems trying to install the other one.

Alright now for the tar.gz. A tar.gz file is a compressed archive. Now tar xf whatever.tar.gz extracts the archive and puts it in a directory right beside the tar.gz file. So if you extract a tar.gz which is on the desktop, the directory should be put there unless you specify otherwise which can be done but for this context is probably unnecessary to demonstrate how. You can use the archive manager to extract it or you can use the tar command. I gave the tar command because it is easier to tell someone to copy and paste a command then try to explain how to click around to do something. tar zxvf whatever.tar.gz does the same thing. The z basically means that it is a tar.gz file (because there are some tar.bz2 files and for those you would use j instead of z) but if you don't include the z it still figures it out and extracts accordingly so it is unnecessary. The v means verbose so it will tell you exactly what is going on and list a whole bunch of things. I don't usually care since I know what is going on so I just leave it out.

Once you extract a directory, what you need to do is run a script in there called configure. What this script does is make sure everything on your computer is ok to install it. It checks for the dependencies it needs to install like I mentioned before and you can also give some options for it, but again not really important now. Once you run the configure script you run make and sudo make install to actually install it.

Generally, you shouldn't need to do this. The ubuntu repos have pretty much everything  you need and it is much easier to open up synaptic package manager or just use apt-get to get it than to go through all of this for each additional piece of software.

---

### Post by mhenriday on 2007-01-12
Thanks for the explanation, **bruenig** ! Just to see if I could get the procedure you outlined above to work, I removed gparted-0.2.5-1.1-ubuntu1.1 and downloaded and installed gparted-0.3.3.tar.gz. Everything seemed to go smoothly and two sub-directories called /home/mhenriday/gparted-0.3.3.tar.gz and /home/mhenriday/gparted-0.3.3, respectively are now found on my machine. But, just as you indicated might prove to be the case, the **Gparted** icon is no longer found under **System&#8594;Administration**, but rather under **Applications&#8594;System Tools**. However, in contrast to previously, when I click this icon,  the programme no longer starts; instead I now get a message to the effect that root privileges are required to run** Gparted** ! While the programme can be made to run by using the command «sudo gparted» in the console, for a person as used to a GUI as I am, it would be nice to be able to run it by simply clicking on the appropriate icon on a menu. Do you know any way that I can get the icon under  **Applications&#8594;System Tools** to run with a simple click, so that I don't have to resort to the command line in the console ?...

Henri

---

### Post by mrfuzzemz on 2007-01-24
If you edit the command in the GParted link by adding gksudo so that it looks like this: 
```

gksudo gparted
```

for example then you will be prompted for root password before Gparted runs.

Hope this helps

---

