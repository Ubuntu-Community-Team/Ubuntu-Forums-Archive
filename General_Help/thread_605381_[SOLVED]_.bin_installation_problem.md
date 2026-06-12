---
title: "[SOLVED] .bin installation problem"
date: 2007-11-07
forum: General Help
---

### Post by Go_Bucks on 2007-11-07
I am having a problem installing gvSIG GIS software on a new Gutsy installation on AMD64. The file is a .bin. I have previously (recently) installed this same download on another computer running Feisty with no problems whatsoever... I simply clicked on the .bin and the install process started nearly identically to installing the .exe version on a Windows machine. Trying to install on this one (using run in terminal) the terminal says that it is unpacking, and then I get a double error message, both of which say the following:

"./launcher-Linux: error while loading shared libraries: libXi.xo.6: can not open shared object file: no such file or directory".

Then the terminal closes. 

I have looked and looked and can't find libXi.xo.6 anywhere in the repositories or on the internet. Can anyone help with that?

---

### Post by studo77 on 2007-11-07
Bumping this, i also have a .bin fil which i do not know how to install. I might be trying use a java-install instead. But at some point i will run into software delivered only as .bin.

and then i want to know...

---

### Post by TheExplorer on 2007-11-07
Seems to me that ubuntu gutsy doesn't support .bin programs. I also couldn't install thunderbird manually (I always download tar.gz from mozilla.com). Installed it from Synaptic and noticed an interesting thing in its name: thunderbird-version-**nobinonly **or smth like that. Wtf? :(

---

### Post by pedrobedro on 2007-11-07
I'm having the same problem trying to install realplayer. I've read everything I can find and still get nowhere :confused: I've only been using Ubuntu for a few weeks and it updated itself to Gutsy Gibbon from Feisty Fawn quite successfully although the computer it's running on isn't exactly up to date, my other one broke and I'm not rebuilding it till after Christmas as my grandkids want presents :lolflag:
   Edit:- I've just right clicked on the .bin file on the desktop and opened it and it's put a folder on there with the executable and some other folders in it. If I move it somewhere else where it should be will it work

---

### Post by karth on 2007-11-07
> I have looked and looked and can't find libXi.xo.6 anywhere in the repositories or on the internet. Can anyone help with that?
I can't check by myself right now, but you should better look for "libxi" instead, in the repos.

---

### Post by Go_Bucks on 2007-11-07
After I posted the original post I checked in usr/bin and libXi.xo.6 is present (as a link to another library)... the exact same setup as present on my feisty machine where I had no problem installing.

I really need to get that program installed to have the same workflow on my laptop as on my desktop.

---

### Post by Go_Bucks on 2007-11-07
bump

---

### Post by Maestro23 on 2007-11-07
> **Go_Bucks said:**
> bump

So libc6 is installed?

Can you link me to the download?  I'm running Gutsy 64-bit. I've never use the program, but will see errors I run into.

---

### Post by Go_Bucks on 2007-11-07
If you could figure it out I would be very appreciative. The download is at:

[http://www.gvsig.gva.es/index.php?id=gvsig11&L=2](http://www.gvsig.gva.es/index.php?id=gvsig11&L=2)

I am using the 1.1 stable file with installation prerequisites.

---

### Post by Maestro23 on 2007-11-07
> **Go_Bucks said:**
> If you could figure it out I would be very appreciative. The download is at:

[http://www.gvsig.gva.es/index.php?id=gvsig11&L=2](http://www.gvsig.gva.es/index.php?id=gvsig11&L=2)

I am using the 1.1 stable file with installation prerequisites.

Ok. I'll download it and see what I can come up with.  Might not get to it tonight though, you might solve before I get back.:)

---

### Post by Go_Bucks on 2007-11-08
bump

---

### Post by Maestro23 on 2007-11-08
> **Go_Bucks said:**
> bump

Getting ready to mess with this.  This is where I'm at right now.  After I executed the .run file, a window popped up asking where I wanted to install the Java run-time environment.  I picked my /home directory. Then got the 1st screenshot below.

To Install:
> sudo chmod +x  gvsig-1_1-linux-i586-withjre.bin

./ gvsig-1_1-linux-i586-withjre.bin

EDIT: Install was a SUCCESS.  No problems whatsoever. See 2nd screenshot.

---

### Post by Go_Bucks on 2007-11-08
Thanks, but what you just did was apparently a terminal version of what I was doing. Your commands give me the same output as before:

```
marcus@marcus-laptop:~$ ./gvsig-1_1-linux-i586-withjre.bin
Unpacking...
Launching instalation program....
./launcher-Linux: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory

./launcher-Linux: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory


marcus@marcus-laptop:~$ 

```

---

### Post by Go_Bucks on 2007-11-08
FYI - again, I DO have the library mentioned in the error. See screenshot.

---

### Post by Maestro23 on 2007-11-08
> **Go_Bucks said:**
> Thanks, but what you just did was apparently a terminal version of what I was doing. Your commands give me the same output as before:

```
marcus@marcus-laptop:~$ ./gvsig-1_1-linux-i586-withjre.bin
Unpacking...
Launching instalation program....
./launcher-Linux: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory

./launcher-Linux: error while loading shared libraries: libXi.so.6: cannot open shared object file: No such file or directory


marcus@marcus-laptop:~$ 

```

Yeah, I knew those were the commands you used, that was for the benefit of the other guy who said he had no clue how to execute a  .run file.

Double check your libc6 package.

Edit: I'll do some more googling.

---

### Post by Go_Bucks on 2007-11-08
I have libc6 and libc6-i386 installed.

---

### Post by Maestro23 on 2007-11-08
> **Go_Bucks said:**
> I have libc6 and libc6-i386 installed.

Install** libc6-dev** and see what happens.

---

### Post by Go_Bucks on 2007-11-08
> **Maestro23 said:**
> Install** libc6-dev** and see what happens.

Earlier I tried reinstalling those libraries and, after your suggestion, I tried installing libc6-dev. Didn't work. I received the same error.

I am totally perplexed.

---

### Post by Go_Bucks on 2007-11-08
I'm on the verge of compiling source code... but am concerned about all of that program's dependencies.

---

### Post by Go_Bucks on 2007-11-08
Oh, Maestro. If you have another suggestion I am all ears. Just an FYI, I am rebooting into Windows as I have some work to do there, so I won't be able to try anything you suggest right away.

---

### Post by Maestro23 on 2007-11-08
> **Go_Bucks said:**
> I'm on the verge of compiling source code... but am concerned about all of that program's dependencies.

Yeah, got me stumped here as well.  And with this program, I fear it will be a dependency nightmare. But if you really need/want the program, might be something you will just have to do.

Sorry I have not been a greater help man.

---

### Post by Go_Bucks on 2007-11-08
> **Maestro23 said:**
> Yeah, got me stumped here as well.  And with this program, I fear it will be a dependency nightmare. But if you really need/want the program, might be something you will just have to do.

Sorry I have not been a greater help man.

It's alright. You tried... that's all that counts (I feel like stirring music should be playing in the background as I write that).

I do NEED that program though. There is no escaping Windows/ArcGIS without the map-making ability of that program, unless one of the other GIS programs improves. There are FAR better overall GIS programs for Linux (they can all work on the same files), but none of them can make great final maps like gvSIG.

---

### Post by Maestro23 on 2007-11-08
> **Go_Bucks said:**
> It's alright. You tried... that's all that counts (I feel like stirring music should be playing in the background as I write that).

I do NEED that program though. There is no escaping Windows/ArcGIS without the map-making ability of that program, unless one of the other GIS programs improves. There are FAR better overall GIS programs for Linux (they can all work on the same files), but none of them can make great final maps like gvSIG.

Well, I wish you luck man.  I will stay subscribed to this thread in case something pops into my head.  Also I'll know when you DO get this thing running.:)

Good luck man.:guitar:

---

### Post by Go_Bucks on 2007-11-09
Stupid me... I didn't realize I needed Java installed prior to attempting to install program. Once I did that it worked.

Thanks again Maestro.

---

