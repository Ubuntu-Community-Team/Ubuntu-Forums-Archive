---
title: "how on earth?"
date: 2007-06-26
forum: General Help
---

### Post by nate22 on 2007-06-26
how on earth do i install things? (VERY NEW TO LINUX) i have all theses .exe files and error messages keeps showing up saying couldn't display blah blah blah


so i went off and downloaded the newwest firefox version for linux and still get the same error...

so how am i supposed to add new programs?

---

### Post by S29K on 2007-06-26
First off, '.exe' files are generally MS Windows programs....not linux binaries.  To use these you have jump through a few hoops to emulate Windows which is not likely what you want.

To install applications in Ubuntu, simply click on Applications -> Add/Remove to fire up a program that will give you oodles of choices of things to install on your Ubuntu machine.

There are more applications available than those shown here but a very good sampling of the more common ones can be installed as I described.

I'm not sure which version of Firefox you are trying to load but Ubuntu comes with Firefox already installed and it will automagically update to the latest stable release version with the Update Manager.

---

### Post by toxigenicpoem on 2007-06-26
Try using the Applications > Add/Remove feature for first time users. There is a GREAT repository for applications. 2ndly you can get a little more software, with the added expense that you *MAY* need to complete other steps by using System>Administration>Synaptic Package Manager.

If you downloaded FireFox for Linux, then it should be a .run file. Did you right click on the file, go to properties, then to permissions, and check the box "Allow executing file as program", linux can run a multitude of files as applications, NOT just 'binary' applications, so this is a saftey precaution.

And thirdly :) if you are trying to install native windows .exe files, you need to familerize your self with WINE, which allows windows program to run under linux, [http://www.winehq.org/](http://www.winehq.org/). But thats another story in its self :popcorn:

---

### Post by zach12 on 2007-06-26
some exe files don't work at all on wine

---

### Post by zach12 on 2007-06-26
if you can't find it on add or remove progams use the dep installer it not too hard

---

### Post by toxigenicpoem on 2007-06-26
Like Zach said, some exe files don't work with WINE, most notibly anything with .NET framework wont work with WINE, instead you want to use MONO to run a .NET application, however and now we are diving furthur into this but not totally of topic, if a windows .EXE uses both the .NET framework AND windows API, then right now its pretty much hopeless to run, eventually MONO and WINE will merge projects to create a hybrid environment.

---

### Post by nate22 on 2007-06-26
the ubuntu i have has fiirefox 1.5 sumthin which is wayy outdated, i hhacve downloaded firefox 2.0
and it is saved ina .tar.gz format

ive reas up and saw some ehre that to install softwear you should get something called gDEbi

i used add/remove and have installed Gdebi

but cant seem to find it anywear

---

### Post by dabl on 2007-06-26
> **nate22 said:**
> i hacve downloaded firefox 2.0


Ubuntu is a Debian Linux distribution, and uses "packaged" applications -- you would be wise to stop downloading software for awhile, and instead install your packages from the repositories, until you have developed the knowledge and necessary skills to deal with downloaded tarballs.  Otherwise, I fear your Linux experience will soon turn sour.  The current release of Firefox, GoogleEarth, and most other popular applications are in the repositories and you can install them with "Administration>Synaptic". :D

---

### Post by Shazaam on 2007-06-26
> **nate22 said:**
> the ubuntu i have has fiirefox 1.5 sumthin which is wayy outdated, i hhacve downloaded firefox 2.0
and it is saved ina .tar.gz format

ive reas up and saw some ehre that to install softwear you should get something called gDEbi

i used add/remove and have installed Gdebi

but cant seem to find it anywear


Lol don't worry it's there. Some Linux apps don't have what is called a "GUI" or graphical user interface bundled with them like Windows or Mac apps. Usually you would use what is called a "Terminal" to access such programs. Here is a good site that lists common terminal commands...[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

Be CAREFULL as you can trash an installation by blindly typing in commands that you don't understand.
But don't freak out you can comfortably run Linux without the terminal until you get used to it. As stated in the other posts relax, poke around in the help file on your pc, and get familiar with Ubuntu before you go putting commands into the terminal. You will soon find that linux is a lot of fun to use and customize.

---

### Post by phidia on 2007-06-26
Just a note on apps you can't find. press the Alt + F2 keys at the same time and a "Run Application" box will open up You then type the app name there. 
For GDebi all you really need do is right click on a package file and you should see a menu item "Open with GDebi Package Installer".

---

### Post by eentonig on 2007-06-26
> Firefox/2.0.0.4 (Ubuntu-feisty)

What version of Ubuntu are you using?

Open a terminal (\Applications\Accesoires\Terminal) and type

> uname -a
This should give you some mambo/jambo that will allow us to tell you if you need to upgrade.

The first posts in these thread were the best. Stop downloading and use "Add/Remove.." (or eventually Synaptic (\System\Administration\Synaptic Package Manager) to install software for a while.

And try to do some 'light' reading. The links in my signature are pointing to some very beginner-friendly sites.

---

### Post by nate22 on 2007-06-26
yea thanks all im absolutly in love w/ ubuntu!

idk why mayb its the rebel in me always wanting to be in the minority of things and doing thigs people arnt used to do

but ubuntu is realy fun to work with

im still learning the ins and outs 

but heres my next problem.

i had windows b4 and saved coupled games on my  external hdd (world of warcraft) i put the file into my desktop..now how do i run it?\

im using the ubuntu 6.06 server edition... is this a good idea? or should i switch?

the main reason i switched to ubuntu as stated was that im running a server off my comp..but nothing TOO major

---

