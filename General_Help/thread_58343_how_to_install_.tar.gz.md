---
title: "how to install .tar.gz"
date: 2005-08-19
forum: General Help
---

### Post by prophet of the pimps on 2005-08-19
dont laugh i know this is basic stuff but remember i have never used linux before and curretly i am trying out the live CD's. So how does one install .tar.gz files.

---

### Post by nad on 2005-08-19
You should not have to install source packages.

Use the synaptic package manager and get a feel for the system and what is available specifically for your version (dependencies will not be an issue).

If you double click the gzipped tarball, archive manager will start up and give you options to extract the files, or just view the readmes before extraction.

If you are looking to install a driver, please search these forums for your specific issue. It has probably been addressed to some degree.

---

### Post by Emerzen on 2005-08-19
I'm a newb myself, so I can sympathize w/ the question.  The previous post was good advice though, if you can install it through Synaptic, it's much easier.  Go to System>Admin.>Synaptic Package Manager.  Once it's open click reload, then search for the package you are looking for (try search by name 1st ,then name and description if you don't find it).  If it's there right click it>mark for install>apply.

If that fails, go to this website <http://ubuntuguide.org/#extrarepositories> and follow the steps.  If you aren't ready for the command line, you can do this through Synaptic/GUI.  In Synaptic go to Settings>Repositories>Settings>Check Show disabled software>close>Add>all the repositories listed at the ubuntuguide site above one by one.  (Many of them are already in Synaptic by default, but the multiverse is not and it's important for multimedia, at least).  Re-search for your package.

If that too fails you can add the Marrilat repositories (Pure Debian packages) but this is tricky.  If you need to do that, let me know and I'll send you the instructions.

To, finally, just answer your question:
1. In synaptic find and install "checkinstall" and "build-essential"
2. Open a terminal
3. Right click the pack and click "extract here" (I usually do this from the desktop)
4. Open the package and find the file labeled "install" (just install not install.sh) and read any instructions
5. Typically it's just: cd /wherever the extracted package is
6.  Type:   ./configure
7.  Type:    make
8.  Type:  sudo checkinstall nameofpackage

Using checkinstall converts it to a deb package that can be accessed through synaptic in the future/once it's installed.

Hope that helps, gets you started.

---

### Post by prophet of the pimps on 2005-08-20
thank you. well it is the application of my ISP. you need it to log on to the net.

---

### Post by nad on 2005-08-20
I would suggest contacting your ISP's support. After all, if you were using another operating system you can bet that they would walk you through the installation process.

But then again, I do not hesitate to speak my mind.

Please do not hesitate to post any further questions, problems, insight or replies from your ISP. I will help you any way I am able to. There may even be a thread here discussing installation for your ISP. Just use the search feature link above.

---

### Post by lakcaj on 2005-08-20
See this link for some info.  I'll add the following though:

1.  After you extract the contents of the .tar.gz file, and cd into the created directory, look for a file called INSTALL or README.  Read these, as they may contain information that is important before you install.

2.  Instead of running "make install" as root, use the checkinstall utility (it is available through synaptic) to make a .deb file (which is an ubuntu package) and install it with:

dpkg -i newly_created_package.deb

Anyway, for the rest of the info, see the following:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by CYHPT.net on 2005-09-15
Hi all,

Im new to this and searched for how to install tar.gz. Can someone tell me how to do it in the command line... I lost my way of using linux, now Im back to it again.

Thanks in advance.

---

### Post by joshuapurcell on 2005-09-15
tar xvzf somePackage.tar.gz    *#extract the package*
cd somePackageDirectory    *#change into the new directory*
more README (or more INSTALL)    *#find out what steps are needed for the package you want to install*
./configure -help   *#see if there are any arguments you would like to give/change*

*#these steps usually follow:*
make
make install

---

### Post by CYHPT.net on 2005-09-15
[QUOTE=joshuapurcell]tar xvzf somePackage.tar.gz    *#extract the package*
cd somePackageDirectory    *#change into the new directory*
more README (or more INSTALL)    *#find out what steps are needed for the package you want to install*
./configure -help   *#see if there are any arguments you would like to give/change*

*#these steps usually follow:*
make
make install[/QUOTE]

Thanks in advance.. now Im remembering something from before when I used to use linux. Thanks.... :)

---

### Post by jrzy on 2005-09-22
Hey everyone, I can definitely relate to this question.... I use KWiFi Manager for my laptop but am curious about [WiFi Radar](http://www.gnomefiles.org/app.php?soft_id=332) . I want to d/l it and install it but don't know the first thing to do after d/l.  It also states "Requirements This application requires GTK+ version 2.4.x. Other dependencies include:Python, PyGTK2 "What is this?? Do I already have this??

---

### Post by yhotg on 2005-09-24
hi.

what about kinstaller?

out that i can't get it to use checkinstall is very handy. U can tell it where to install, where to store the source, and after that u can uninstall with it (if u store the packages in another folder that is not tmp, lol)
btw anybody knows if i install a new version throught kinstaller or command line with checkinstaller i need to uninstall the old verion first?

---

