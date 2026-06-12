---
title: "404 error when adding additional repository"
date: 2013-10-01
forum: General Help
---

### Post by maryam2 on 2013-10-01
Hi 
I had 440 error when I added additional repository to my system.
I added that repository because I need it for installing new software on my system.
I read some text to guide for eliminating 440 error. it said that I should untick or disable the repository from "other software" in my "software source".
then I did that and I have no error now.
But this is my question. When I disabled that repository from software source, it doesnt make ill the installation process of my software?
Thanks alot

---

### Post by DuckHook on 2013-10-01
What was the additional repository? If you don't wish to tell us due to privacy, then was it official Ubuntu, Launchpad, major company (like Oracle VirtualBox) or someone's personal repository? If last, are you sure that it was Ubuntu-compatible?

If I understand your last question, you are asking if disabling a balky repository will break your software sources. This all depends on what the balky repo is. If it is a core Ubuntu repo, then it definitely will break your installs. But if it is outside of Ubuntu, then it won't harm your software sources. At most, it will prevent you from updating or installing any further apps from that repo.

Have I properly answered your question?

---

### Post by maryam2 on 2013-10-02
Hello
I want to install LUMASS. It is a software for spatial optimisation. But before that I must install the other open source software like
QT
VTK
GDAL
ORFEOTOOLBOX AND...
and also I must add launchpad repository 
> ppa:ubuntugis/ubuntugis unstable
ppa:otb/orfeotoolbox-stable-ubuntugis
 Thank you

---

### Post by Bucky Ball on 2013-10-02
Please provide a link to the instructions for installing the repo. 

From the Lumass site (not in English so don't understand it) there is one tell-tale sign. lumass.exe. Exe files are not for Linux. Are you sure this is even compatible with Linux, as suggested by DuckHook???

As also noted, no, disabling the Lumass repository will not disable anything else. All will still be as normal.

---

### Post by Elfy on 2013-10-02
The information all appears to be here

[http://code.scenzgrid.org/index.php/p/lumass/source/tree/3ae3372087b90109dc268b63add7a7359b473612/INSTALL](http://code.scenzgrid.org/index.php/p/lumass/source/tree/3ae3372087b90109dc268b63add7a7359b473612/INSTALL)

[https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable](https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable)

---

### Post by maryam2 on 2013-10-02
yes I'm sure
and this is LUMASS installation guide
```
   [COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] installation guide[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]+++++++++++++++++++++++++[/SIZE][/FONT]
 

 

 [FONT=Courier New, serif][SIZE=2]Requirements / Prerequisites[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]============================[/SIZE][/FONT]
 

 [COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] is currently only available for Linux operating systems. However, it is[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]entirely built on cross-platform libraries and could potentially [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**run**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] on other[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]operating systems and platforms as well. [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] is being developed and tested [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]on (K)Ubuntu Linux, and the remainder of this installation guide refers to an[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]Ubuntu installation. Please adjust the described steps accordingly to meet the[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]requirements of your favourite Linux distribution (and feel free to share any[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]adjusted installation guides for other distributions / operating systems!).[/SIZE][/FONT]
 

 

 [FONT=Courier New, serif][SIZE=2]required 3rd party software libraries / packages[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]================================================[/SIZE][/FONT]
 

 [COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] relies on a number of other open source software libraries, which are[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]required (except rasdaman/PostgreSQL) to successfully build [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2]. [/SIZE][/FONT] 
 

 [FONT=Courier New, serif][SIZE=2]Qt                      version > 4.6; (core, gui, and XML components)[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]GDAL                    see launchpad repository: unbuntugis-unstable [/SIZE][/FONT] 
                         [FONT=Courier New, serif][SIZE=2]<https://launchpad.net/~ubuntugis/+archive/ubuntugis-unstable>[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2](see below for information how to add the repository to your[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]sources.list)[/SIZE][/FONT]
                          
                         [FONT=Courier New, serif][SIZE=2]Packages: libgdal1-dev; recommended: gdal-bin [/SIZE][/FONT] 
                          
 

 [FONT=Courier New, serif][SIZE=2]Orfeo Toolbox           see launchpad repository: unbuntu-gis-unstable[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]<https://launchpad.net/~otb/+archive/orfeotoolbox-stable-ubuntugis>[/SIZE][/FONT]
                          
                         [FONT=Courier New, serif][SIZE=2]Packages:  libotb3-dev, otb-bin-qt[/SIZE][/FONT]
                          
 

 [FONT=Courier New, serif][SIZE=2]VTK                     has to be installed from source ((release) package >= 5.10);[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]make sure you compile VTK with the following options set to ON:[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]VTK_USE_GUISUPPORT; VTK_USE_QT; VTK_USE_QTCHARTS; VTK_USE_RENDERING;[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]rasdaman                this package is optional and only useful, if you intend[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]to use the [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] modelling framework; if you're only [/SIZE][/FONT] 
                         [FONT=Courier New, serif][SIZE=2]interested in spatial optimisation, you don't need this [/SIZE][/FONT] 
                         [FONT=Courier New, serif][SIZE=2]package; see rasdaman.org for download, compilation and[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]installation details as well as for rasdaman features[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]PostgreSQL              only required when rasdaman is going to be used with the[/SIZE][/FONT]
                         [FONT=Courier New, serif][SIZE=2]modelling framework [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]			[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]lp_solve,[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]liblpsolve55-dev        required for [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2]' optimisation component [/SIZE][/FONT] 
 

 [FONT=Courier New, serif][SIZE=2]cmake,[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]cmake-curses-gui        build system packages used to compile [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] (s. below)[/SIZE][/FONT]
 

 

 [FONT=Courier New, serif][SIZE=2]For Orfeo and GDAL you have to add the respective launchpad-repository[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2](see URL above) to make the packages available via your package manager. [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]You will also need the 'build-essentials' package for compiling [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] from [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]source. Installing the above mentioned packages should resolve most of the [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]library dependencies. [/SIZE][/FONT] 
 

 

 [FONT=Courier New, serif][SIZE=2]Adding launchpad repositories[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]=============================[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]You can add launchpad repositories using apt from the commandline:[/SIZE][/FONT]
 

    [FONT=Courier New, serif][SIZE=2]e.g. $ sudo apt-add-repository <ppa repository>[/SIZE][/FONT]
    
 [FONT=Courier New, serif][SIZE=2]So to add the ubuntugis-unstable and orfeotoolbox-stable-ubuntugis repositories enter the following [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]two commands and follow the given instructions each time:[/SIZE][/FONT]
 

    [FONT=Courier New, serif][SIZE=2]$ sudo apt-add-repository ppa:ubuntugis/ubuntugis-unstable [/SIZE][/FONT] 
 

    [FONT=Courier New, serif][SIZE=2]$ sudo apt-add-repository ppa:otb/orfeotoolbox-stable-ubuntugis[/SIZE][/FONT]
     
 [FONT=Courier New, serif][SIZE=2]Then update the package information[/SIZE][/FONT]
 

    [FONT=Courier New, serif][SIZE=2]$ sudo apt-get update[/SIZE][/FONT]
     
 [FONT=Courier New, serif][SIZE=2]Now choose your favourite package manager to install the relevant packages (including[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]any dependencies) for the particular libraries.  [/SIZE][/FONT] 
 

 

 

 [FONT=Courier New, serif][SIZE=2]Building [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] from source[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]===========================[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]1. create a directory for [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2]' binary files [/SIZE][/FONT] 
 

    [FONT=Courier New, serif][SIZE=2]$ mkdir [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**lumass**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2]-bin[/SIZE][/FONT]
    [FONT=Courier New, serif][SIZE=2]$ cd [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**lumass**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2]-bin[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]2. [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**run**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] ccmake to configure the software and generate the Makefile[/SIZE][/FONT]
 

    [FONT=Courier New, serif][SIZE=2]$ ccmake /path/to/[/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**lumass**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2]/source/directory[/SIZE][/FONT]
 

    [FONT=Courier New, serif][SIZE=2](inside the ccmake UI)[/SIZE][/FONT]
 

    [FONT=Courier New, serif][SIZE=2]- Press [c] to configure[/SIZE][/FONT]
    [FONT=Courier New, serif][SIZE=2]- adjust any path entries if required (you can safely ignore [/SIZE][/FONT] 
      [FONT=Courier New, serif][SIZE=2]'OTB_APPLICATION_LAUNCHER-NOT') [/SIZE][/FONT] 
    [FONT=Courier New, serif][SIZE=2]- set RASSUPPORT to OFF, if you don't want to build [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] with rasdaman [/SIZE][/FONT] 
      [FONT=Courier New, serif][SIZE=2]support) [/SIZE][/FONT] 
    [FONT=Courier New, serif][SIZE=2]- Press [c] to configure (again)[/SIZE][/FONT]
    [FONT=Courier New, serif][SIZE=2]- Press [g] to generate the Makefile and exit ccmake[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]3. call make (you may want to use multiple cores during the build by specifying  [/SIZE][/FONT] 
    [FONT=Courier New, serif][SIZE=2]the -j options)  [/SIZE][/FONT] 
 

    [FONT=Courier New, serif][SIZE=2]$ make -j 4 			# &#8592; uses 4 cores[/SIZE][/FONT]
 

 [FONT=Courier New, serif][SIZE=2]4. you're good to go now![/SIZE][/FONT]
     
 

     
 [FONT=Courier New, serif][SIZE=2]Updating [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] source code[/SIZE][/FONT]
 [FONT=Courier New, serif][SIZE=2]===========================[/SIZE][/FONT]
 

 [COLOR=#000000][FONT=Courier New, serif][SIZE=2]**LUMASS**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] is being continously updated and extended. If you want to update to [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]the most recent version, change into the [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**lumass**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] source directory and pull [/SIZE][/FONT] 
 [FONT=Courier New, serif][SIZE=2]from the remote [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**lumass**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] repository[/SIZE][/FONT]
 

   [FONT=Courier New, serif][SIZE=2]$ [/SIZE][/FONT][COLOR=#000000][FONT=Courier New, serif][SIZE=2]**git**[/SIZE][/FONT][/COLOR][FONT=Courier New, serif][SIZE=2] pull origin master[/SIZE][/FONT]
    
 [FONT=Courier New, serif][SIZE=2]Then follow the build instructions (see above) from step 2.[/SIZE][/FONT]


```

---

### Post by Elfy on 2013-10-02
I had a quick check for the ubuntugis/ubuntugis-unstable  ppa.

That worked for raring, I've not looked at any of the other ppa's mentioned nor packages as I'm on Saucy.

There's not anything wrong with the ppa here.

You need to look further into it as to why it's failing for you.

It will help people help you if they knew what version of buntu you're trying to get this to work with.

> I read some text to guide for eliminating 440 error. it said that I should untick or disable the repository from "other software" in my "software source".
then I did that and I have no error now.That will happen - the thing causing the error has been disabled. You'll not be able to install lumass though.

---

### Post by maryam2 on 2013-10-02
Excuse me my english isn't good, you mean I can't install LUMASS if I remove 440 error by disabling PPA address in software source?
I worked UBUNTU 12.10 and I'm new on it.

---

### Post by Elfy on 2013-10-02
ok - had time to dig a bit deeper now.

Looks like the last version available for those 2 ppa's is for Precise which is 12.04.

You can fiddle with the source file to point at precise if you want to.

But I'd not be sure about any other dependencies it might want - no guarantee they'd be available.

It looks to me like you need to build lumass from source - no mention of that in the install page.

---

### Post by mania2 on 2013-10-02
You mean I must ignore this error.
What do you suggest me.

---

### Post by Elfy on 2013-10-02
> **mania2 said:**
> You mean I must ignore this error.
What do you suggest me.
The PPAs won't work as they are with 12.10. 

What you do is up to you. 

It is possible to edit the source list to use precise instead of quantal, but you could get more problems.

In addition please see my PM to you.

---

### Post by Bashing-om on 2013-10-02
mania2; Hi !

Here is a thought and what Elfy may be pointing to.

Check and see if the other packages you want to install are also available for 12.04.
The simpler solution in my mind and to keep a stable operating system is to install version 12.04.
Mixing versions can lead to dependency issues that have no good solutions.
Then add the packages from those 3rd party vendors (yuk) that you need.

[INDENT][INDENT]hey, it is a thought
[/INDENT][/INDENT]

---

### Post by DuckHook on 2013-10-02
Forum admins/mods like *Bucky Ball* and *Elfy* are very busy, so they often post short concise replies without the long-winded explanations that retired guys like me can indulge in. If I may be so bold, here is the long version of his advice (@Elfy: feel free to correct me if I stumble):

1. The good news is that LUMASS is actually built for Ubuntu.
2. The bad news (in your case) is that it was built based on an older version of Ubuntu that you do not have installed.
3. Furthermore, it uses Launchpad repositories that may or may not be up to date and which are, in any case, built for this same older version of Ubuntu. Based on *Elfy's* research, this older version is 12.04, which would make sense because 12.04 is designed to last until 2015.
4. Since you run 12.10, you have three choices:
a) You can install 12.04 which will allow you to use all PPAs without Ubuntu complaining when you add them to your sources list,
b) You can use special tricks to fool 12.10 into treating 12.04 PPAs as usable, but this is prone to problems,
c) You can download the source code for LUMASS, compile it along with all of its dependencies and run it as a complete app. Because you will have compiled it for 12.10, it should run without any problems at all.

Given your lack of experience with Ubuntu, I would suggest choice (a). You do not have the knowledge yet to pull off either (b) or (c).

---

