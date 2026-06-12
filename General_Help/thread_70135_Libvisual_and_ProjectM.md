---
title: "Libvisual and ProjectM"
date: 2005-09-29
forum: General Help
---

### Post by faddat on 2005-09-29
Hello, I'm wondering if there's anyone aware of .deb packages for libvisual and projectM.  I'm working to get these applications working on my ubuntu box, and compilation seems to result in a spiral of errors and warnings.  If there are no packages, I'd be interested in making them.  

How does one make packages for Ubuntu?

---

### Post by mcduck on 2005-09-29
I haven't seen .debs anywhere, but I managed to compile these myself with some succes. ProjectM plugin for xmms doesn't work, but libvisual version does.  I really don't know much about how to solve these things, but at least you now know it's possible to get those working.. 

It would be really nice to get these to repos. I don't think that would even be hard job for someone who knows what he's doing ;)

---

### Post by faddat on 2005-10-03
I found the .debs for both Libvisual and ProjectM and I have glorious milkdrop-style visualizations working very well on my Ubuntu box.  Here are the links:
ProjectM:
[http://d072.apm.etc.tu-bs.de/~jluebbe/debian/unstable/](http://d072.apm.etc.tu-bs.de/~jluebbe/debian/unstable/)
Libvisual:
[http://debian.telecoms.bg/debian/pool/main/libv/libvisual/](http://debian.telecoms.bg/debian/pool/main/libv/libvisual/)
Enjoy your visualizations :).

---

### Post by grimdestripador on 2006-12-18
[SIZE="4"]
The following Installs ProjectM Visualization (Milkdrop for Linux) for XMMS and AMAROK[/SIZE]

goto [http://xmms-projectm.sourceforge.net/]("http://xmms-projectm.sourceforge.net/")
and download the links on the left, or run the following URLs if they still work.

```

wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/libprojectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/libvisual-projectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-0.99.tar.bz2
wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-pbuffers-0.99.tar.bz2
```

[LIST=1]
[*]Make A Directory called "InstallProjectM" in your home folder.
[*]Extract Each downloaded file into ~/InstallProjectM
[*]Run the following CODE
[/LIST]

```
 ##Compiler tools##
	sudo apt-get install -y build-essential
	sudo apt-get install -y libglib1.2-dev
	sudo apt-get install -y libgtk1.2-dev
	sudo apt-get install -y libsdl1.2-dev
        sudo apt-get install -y libvisual-0.4-dev
        (optional) sudo apt-get install -y libvisual-0.4-0
        (optional) sudo apt-get install -y libvisual-0.4-plugins 
	sudo apt-get install -y xmms-dev

##Open GL Fonts##
	sudo apt-get install -y ftgl-dev

##Extract libProjectM and build##
	cd ~/InstallProjectM/libprojectM/
	./configure
	make
	sudo make install

##Extract libvisual-projectM and build##
	cd ~/InstallProjectM/libvisual-projectM
	./configure
	make
	sudo make install

##Extract xmms-projectM and build##
	cd ~/InstallProjectM/xmms-projectM
	./configure
	make
	sudo make install
```

---

### Post by tacomafish12 on 2007-04-04
when i go to run sudo apt-get install -y libsdl1.2-dev is gives me this error:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libdirectfb-dev (>= 0.9.22) but it is not going to be installed

after trying to get the dependencies i cant get them because they have missing dependencies.  This string continues until i reach libpng12-0.  This is the error i get for running sudo apt-get:

libpng12-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Ubuntu has a version newer and different than the libs needed for project m depend on.

Any suggestions?

---

### Post by gstast on 2007-06-16
after i past the code into the terminal 


I get this in my terminal

configure: error: OpenGL and Glu headers not found, the plugin cannot be build
stas@stas-desktop:~/InstallProjectM/xmms-projectM$ make
make: *** No targets specified and no makefile found.  Stop.
stas@stas-desktop:~/InstallProjectM/xmms-projectM$ sudo make instal

What am I doing wrong?

---

### Post by DarkMageZ on 2007-07-01
your problems start with when you run ./configure. you need to install the development libraries for the stuff it asks for.

simple solution to get projectm for libvisual and/or xmms is to grab the packages i've built. (only "supported" for *buntu feisty on i386).

(required for anything projectm)
[http://mirror.randumb.net/darkmagez/libprojectm/libprojectm_0.99-1_i386.deb](http://mirror.randumb.net/darkmagez/libprojectm/libprojectm_0.99-1_i386.deb)

(projectm for libvisual eg, rhythmbox/amarok)
[http://mirror.randumb.net/darkmagez/libprojectm/libvisual-projectm_0.99-1_i386.deb](http://mirror.randumb.net/darkmagez/libprojectm/libvisual-projectm_0.99-1_i386.deb)

(projectm for xmms)
[http://mirror.randumb.net/darkmagez/libprojectm/xmms-projectm_0.99-1_i386.deb](http://mirror.randumb.net/darkmagez/libprojectm/xmms-projectm_0.99-1_i386.deb)

---

### Post by 18x on 2007-07-18
> **grimdestripador said:**
> [SIZE="4"]
The following Installs ProjectM Visualization (Milkdrop for Linux) for XMMS and AMAROK[/SIZE]

goto [http://xmms-projectm.sourceforge.net/]("http://xmms-projectm.sourceforge.net/")
and download the links on the left, or run the following URLs if they still work.

```

wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/libprojectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/libvisual-projectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-0.99.tar.bz2
wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-pbuffers-0.99.tar.bz2
```

[LIST=1]
[*]Make A Directory called "InstallProjectM" in your home folder.
[*]Extract Each downloaded file into ~/InstallProjectM
[*]Run the following CODE
[/LIST]

```
 ##Compiler tools##
	sudo apt-get install -y build-essential
	sudo apt-get install -y libglib1.2-dev
	sudo apt-get install -y libgtk1.2-dev
	sudo apt-get install -y libsdl1.2-dev
	sudo apt-get install -y xmms-dev

##Open GL Fonts##
	sudo apt-get install -y ftgl-dev

##Extract libProjectM and build##
	cd ~/InstallProjectM/libprojectM/
	./configure
	make
	sudo make install

##Extract libvisual-projectM and build##
	cd ~/InstallProjectM/libvisual-projectM
	./configure
	make
	sudo make install

##Extract xmms-projectM and build##
	cd ~/InstallProjectM/xmms-projectM
	./configure
	make
	sudo make install
```

Also make sure that you have libvisual dev package installed. Configuring libvisual-projectM may generate the following error: conditional "HAVE_LIB_GL" was never defined.
To get around this use: ./configure --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11

---

### Post by aboutTOpullmyhairout on 2007-07-30
would it be possible to compile these using a stock edgy install ? reason i ask is i downloaded DarkmageZ packages wich were built for feisty, so when i went to install in edgy i had to download the feisty version of the particular packages it depended on . so i'm wondering if i compiled it on a stock edgy install would it still depend on the newer version of libgcc1, libstdc++, libc6, and gcc4.1base packages?

---

### Post by inverarity on 2007-09-06
Props to darkmagez...his packages worked like a charm and projectM is looking great in xmms right now.  thanks.

---

