---
title: "gDesklets in Ubuntu 7.04"
date: 2007-04-20
forum: General Help
---

### Post by mabrito on 2007-04-20
Hello, im basically a Linux noob.

I just downloaded Ubuntu 7.04 and have the Beryl UI working on it as well. Im trying to install gDesklets and when I do the ./configure command I keep getting a C compile error. 

The error I get is this line: "Checking for C Compiler default output file name...Configure:error: C Compiler cannot create executables." It then says check the log file for more info. I did, and it says something about I need something from GNOME.

What does this mean and how do I go about fixing this?

---

### Post by ashz on 2007-04-20
just install glibc-devel, that is literally all u have to do...

best of luck

cheers
ash

---

### Post by vishnumrao on 2007-04-20
Easiest way to install gdesklets is through Automatix. 

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

You can use Automatix to install gdesklets and also many other useful noob stuff like adobe acrobat reader, realplayer, dvd ripper, multimedia codecs etc.

---

### Post by fossforus on 2007-04-20
Here's an easy way to install gDesklets on Feisty ...

1. Launch a terminal window from Applications -> Accessories -> Terminal
2. Type this command 'sudo aptitude search gdesklet gdesklets-data'
3. gDesklets can be found at Applications -> Accessories -> gDesklets

BTW some of the desklets are broken and don't work as expected. A couple of the weather desklets that have been fixed can be found at [http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets](http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets). Also check out [http://gdesklets.zencomputer.ca](http://gdesklets.zencomputer.ca).

Hope this helps! :)

---

### Post by mabrito on 2007-04-21
> **fossforus said:**
> Here's an easy way to install gDesklets on Feisty ...

1. Launch a terminal window from Applications -> Accessories -> Terminal
2. Type this command 'sudo aptitude search gdesklet gdesklets-data'
3. gDesklets can be found at Applications -> Accessories -> gDesklets

BTW some of the desklets are broken and don't work as expected. A couple of the weather desklets that have been fixed can be found at [http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets](http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets). Also check out [http://gdesklets.zencomputer.ca](http://gdesklets.zencomputer.ca).

Hope this helps! :) 

Ok I did that and got this output:
mabrito@mabrito-laptop:~$ sudo aptitude search gdesklet gdesklets-data
Password:
p   gdesklets                       - Architecture for desktop applets          
p   gdesklets-data                  - Applets for gdesklets                     
p   gdesklets-data                  - Applets for gdesklets    

and nothing shows up in Applications/Accessories/gDesklets.

---

### Post by taurus on 2007-04-21
```
sudo aptitude update
sudo aptitude **install** gdesklets gdesklets-data
```

---

### Post by mrazster on 2007-04-21
What happends if you simply type:

```
gdesklets
```

In terminal..?

---

### Post by mabrito on 2007-04-21
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude **install** gdesklets gdesklets-data
```

Thank you very much.

---

### Post by mabrito on 2007-04-21
Just out of curiosty. I installed the glibc-devel files like the ashz said to and got further into the ./configure command. I now get this error:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

What does this one mean? Might as well figure it out so it doesnt haunt me in the future.

---

### Post by taurus on 2007-04-21
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by ashz on 2007-04-22
> **mabrito said:**
> Just out of curiosty. I installed the glibc-devel files like the ashz said to and got further into the ./configure command. I now get this error:

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

What does this one mean? Might as well figure it out so it doesnt haunt me in the future.

Basically it means u have not got any C++ compiler so do what Taurus said in the above post, i should have thought about that when i told u to download the libraries earlier, my apologies!!

If u do what Taurus says it will give u everything necessary to compile gdesklets....look here for more info..

[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)

cheers
ash

---

