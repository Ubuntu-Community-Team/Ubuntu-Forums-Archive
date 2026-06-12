---
title: "Problems with libc6"
date: 2006-09-10
forum: General Help
---

### Post by Kasper42 on 2006-09-10
Hello!

I am currently trying to install the programs easypmp_0.12-1_i386.deb and libx11-6_1.0.0-8-i386.deb. Both of these programs tell me "Error dependancy is not satisfiable:libc6." 

When I have previously had these dependancy errors installing .deb files, I would go to synaptic and install the dependancy. However, this time when I go to synaptic I can see that libc6 is already installed. 

I installed libc6-dev to see if this would change anything but it did not :( I also tryed reinstalling libc6 in synaptic, this also did not change the error.

Please help!

Kasper

---

### Post by lukew on 2006-09-10
Sounds like you need a newer version of libc6. 

What is the full error message?

The version in my system is 2.3.5-0.

Luke

---

### Post by Kasper42 on 2006-09-10
Hi Luke,

Thanks for the reply!

I have 2.3.6-0ubuntu20 (according to synaptic, it also tells me it is the newest version.)

All the error says is "Error:dependancy is not satisfiable:libc6" That is all that is shown in the deb file installer.

Kasper

---

### Post by lukew on 2006-09-10
Ubuntu is Debian base....Slow & Stable!!

You will find that a later version is required than present in the repos. Try and google for it.

What are you installing anyway? I only as as I ran into a dep for a newer version of libc6 trying to install xmess.sdl, which was not in the repos. I presume you are trying to install something which is not in the repos?

I did find the website which has it but can not find it :(.. will keep trying though and post if i get it!

Luke

---

### Post by lukew on 2006-09-10
Am I thick or what.... it was libc.so.6 for xmess.sdl :o....

Luke

---

### Post by lukew on 2006-09-10
[http://packages.debian.org/unstable/admin/cruft](http://packages.debian.org/unstable/admin/cruft)

---

### Post by Kasper42 on 2006-09-10
Thanks Luke for your help so far.

I followed your instructions and tried to install cruft, cruft told me the same error I had before "Error:dependancy is not satisfiable:libc6."

So I googled around and found [this]("http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libc6")

I tryed the stable libc6 on that page but it told me I have a later version already installed. I then when on to try to install the "testing" one. When I downloaded this I got "Error:dependancy is not satisfiable:tzdata" So, I downloaded tzdata from [here]("http://packages.debian.org/unstable/libs/tzdata")

When I installed that I get the error...

"dpkg:error processing /tmp/tzdata_2006-all.deb(--install):
trying to overwrite '/usr/share/zoneinfo/zone.tab', which is in package locales
dpkg-deb: subprocess paste killed by signal (Broken Pipe)"

I guess it is giving me this error because tzdata is unstable and will not run on my machine.

Kasper

---

### Post by Kasper42 on 2006-09-14
I'm still stuck with this...:( Has nobody got any ideas?

Is there nothing I can do?
[This person seems to be having similar problems]("http://www.ubuntuforums.org/archive/index.php/t-220414.html")

Please help!

Kasper

---

### Post by Rui Pais on 2006-09-14
> **Kasper42 said:**
> Hello!

I am currently trying to install the programs easypmp_0.12-1_i386.deb and libx11-6_1.0.0-8-i386.deb. Both of these programs tell me "Error dependancy is not satisfiable:libc6." 

hi,
you are getting those errors because those apps are for debian sid and not for ubuntu... 
they are trying to get wrong dependency packages versions.

Maybe trying to get the code from [here]("http://martin.ellis.name/pmplib/pmplib_0.12.orig.tar.gz") and compile it. 

Or try to make a deb for ubuntu 
(If you dont know how, it's easy download code, install checkinstall with apt or synaptic, do .config && make and if you got no errors, checkinstall -D to create the Ubuntu deb. Sometimes works...)

---

### Post by Anduu on 2006-09-15
***Do not*** try to update libc6 from any source other than the Ubuntu official repos.

Rui Pais is correct...your only real option is to download the source for the app and compile it yourself.

---

### Post by Lievre on 2006-11-26
Hello, I have a similar problem, trying to install GRASS 6.2 on my Ubuntu machine.
It is a .deb package and I get the same error of libc6 dependency not satisfiable. 

Can someone (Rui Pais ?) explain in more details how to rebuild a deb package for Ubuntu, as Rui Pais said with checkinstall  ?

Thank you very much!

---

### Post by Rui Pais on 2006-11-26
Lievre where do you get that grass? 
(damn it i don't smoke... 8-[ )

Ok, i assume that you need/want to have the last GRASS on earth (;)) but you are aware that there is an ubuntu version, 6.0, available for dapper and edgy. 
If thats the case you need to get the source code for the latest version of GRASS and compile using checkinstall to make a deb for ubuntu, (you can use the deb you get somewhere and change the file 'control' to accept ubuntu libc6 version, but thats risky and you can get other unmet dependencies).

Get GRASS code [here]("http://grass.itc.it/grass62/source/grass-6.2.0.tar.gz") ([md5sum]("http://grass.itc.it/grass62/source/grass-6.2.0.md5sum")).

Get checkinstall and if don't have the compiler environment:
```
sudo aptitude install build-essential checkinstall
```

Decompress the code to a folder, move there and run (as normal user):
```
./configure 
```
if you got any error maybe you probably will need to get some extra -dev packages. With luck everything runs fine at first.

After it finishes **without errors**, run:
```
sudo checkinstall -D
```
and that will make you a deb for your Ubuntu version.

If it fails on that last step (some apps do) that usually means that for some reason the script fail to automatically build the deb package.  

You can do the deb manually. [Here an excellent Ubuntu Howto]("http://doc.gwos.org/index.php/Deb_Guide").

Good Luck.

---

### Post by Lievre on 2006-11-30
Indeed, this grass is not for smoke... Thank you, I tried that.
When doing ./configure, I got this error:

checking for location of Tcl/Tk includes...
checking for tcl.h... no
configure: error: *** Unable to locate Tcl includes.

I serched for a file tcl.h, it exists, in:
/usr/include/tcl8.4/tcl.h

I tried to install some other -dev packages with Tcl in the name..., but it don't work.
tcl-8.4-dev is installed, also blt-dev, tclx8.4-dev, tk8.4-dev.

How do I know which package is missing, or how to tell this computer where is this tcl.h file he's looking for?

Thanks

---

### Post by Rui Pais on 2006-11-30
hi,
grass is a funny name... i only knew it's purpose after a google search.
 
About your problem, well maybe it needs an older version. There is a 8.3 on repos. try:
```
sudo apt-get install tcl8.3-dev
```

to see it it satisfy the dependency [SIZE="2"][SIZE="1"](damn it still sounds i'm making jokes about grass addiction...) [/SIZE][/SIZE]

---

### Post by Lievre on 2006-11-30
well, I did:
./configure --with-tcltk-includes=/usr/include/tcl8.4/
and it was OK, but then it stopped with the same error for PostgreSQL...
I have to find now where is this "PostgreSQL includes"

Thank you

---

### Post by Rui Pais on 2006-11-30
Hi, [check here]("http://grass.itc.it/grass61/source/REQUIREMENTS.html") for requirement to compile it.

PostgreSQl is listed as optional, so you can skip that passing some flag to ./configure too. Just check the README that must be on source folder.

Anyway, if you want to include it, you can use synaptic to easily search for needed packages. 
Try a search for sql or postgre and locate packages that have an -dev on the name. 

I usually install one by one of those i suspect are needed with aptitude, that make it easy to uninstall it in case that it didn't in fact satisfy the dependency, to avoid leave unneeded packages on my system. 
Aptitude do a cleaner job then apt-get or synaptic.

---

### Post by Lievre on 2006-11-30
yes, it worked!
I finally did:
./configure --with-tcltk-includes=/usr/include/tcl8.4/ --with-postgres-includes=/usr/include/postgresql/

Now I have to install the .deb

Thank you for your help, and remember: "Don't walk on the grass, ..."
;-)

---

### Post by Rui Pais on 2006-11-30
:lol:

glad it worked.

Now that you make a grass deb with you bare hands you could walk on it with you bare feet ;)

have fun Lievre.

---

### Post by Lievre on 2006-12-04
Well, it still don't work :-(
Finally I did :
```
CFLAGS="-g -Wall" sudo ./configure --with-cxx --with-gdal=/usr/bin/gdal-config --with-tcltk-includes=/usr/include/tcl8.4/ --with-postgres-includes=/usr/include/postgresql/
```
and this was OK but then with
```
make
```

I get:
 
```

GRASS GIS compilation log
-------------------------
Started compilation: lundi 4 décembre 2006, 18:21:21 (UTC+0100)
--
Errors in:
/media/sda7/proglinux/grass-6.2.0/lib/datetime
/media/sda7/proglinux/grass-6.2.0/lib/gis
/media/sda7/proglinux/grass-6.2.0/lib/gmath
/media/sda7/proglinux/grass-6.2.0/lib/linkm
/media/sda7/proglinux/grass-6.2.0/lib/driver

```
and so on all folders are listed, and finally:

```

Finished compilation: lundi 4 décembre 2006, 18:29:07 (UTC+0100)
(In case of errors please change into the directory with error and run 'make')
make: *** [default] Erreur 1

```

Can someone help me? I read that *** means a fatal error, and [default] is probably the folder affected (here the entire folder...!?), but what is this *error 1* ? And what to do?

Thank you

---

### Post by Rui Pais on 2006-12-04
hi again Lievre,
what ubuntu do you have, edgy, dapper or older?

although i haven't no need for grass i tried to see if it compiles well on my Dapper with your exact options (copy+past) and it has go without a problem, producing a nice deb that after installed it at least [run]("http://homepage.oniduo.pt/rui.pais/linux/screenshot-34.jpg") till a window. Since i don't have the faintest idea how to use it i'll assume it works without much more testing.

If you are on a Dapper, try a make clean before a new attempt of make. If you are on a edgy, tomorrow i can try to see if it compiles on my edgy.

Sorry to know that things don't worked after all. T
hat damn error is everything less self explanatory...

---

### Post by Lievre on 2006-12-07
Damn, my last message was not saved.

It's dapper, by the way. According to your picture, it is indeed working in your computer. 
What am I doing wrong? 
Are there specific requirements regarding the folder in which I should work?
I tried "make" and "sudo make", none worked. 
I tried "make clean" and "make distclean".

Well, thank you anyway for your help.

---

### Post by Lievre on 2006-12-07
Well, I went into the directories listed 
"lib/gis"
and then make

That is the error message:
```

/usr/bin/ld: ne peut trouver -lgrass_datetime
collect2: ld a retourné 1 code d'état d'exécution
make: *** [/media/sda7/proglinux/grass-6.2.0/dist.i686-pc-linux-gnu/lib/libgrass_gis.6.2.0.so] Erreur 1

```

---

### Post by Lievre on 2006-12-07
It means (roughly):

/usr/bin/ld: cannot find -lgrass_datetime
collect2: ld returned 1 code of execution state
make: *** [/media/sda7/proglinux/grass-6.2.0/dist.i686-pc-linux-gnu/lib/libgrass_gis.6.2.0.so] Error 1

---

### Post by Rui Pais on 2006-12-07
> **Lievre said:**
> It means (roughly):

/usr/bin/ld: cannot find -lgrass_datetime
collect2: ld returned 1 code of execution state
make: *** [/media/sda7/proglinux/grass-6.2.0/dist.i686-pc-linux-gnu/lib/libgrass_gis.6.2.0.so] Error 1

Hi,
sorry i don't to see why it fails :(

did it gives any error prior to that error message, on compile phase?

Maybe delete that code and decompress it again to a new folder
(btw, try to make it on a local disk, by the path on your post looks like you compile on some removable device... 
shouldn't be a problem, but maybe the thing gets confused somehow...)

check too if you got some residual grass packages from older installs. 
Use synaptic to see if something is installed, broken or some residual conf files are listed. Check manually, using something like slocate, for files like "libgrass*" (libgrass_datetime.so or libgrass_gis) on yor system. 
Remove any if finded.

The correct commands are:
```
CFLAGS="-g -Wall" sudo ./configure --with-cxx --with-gdal=/usr/bin/gdal-config --with-tcltk-includes=/usr/include/tcl8.4/ --with-postgres-includes=/usr/include/postgresql/
```
that by now shouldn't give any errors.
```
make
```
(no sudo needed)

```
checkinstall -D
```
(not sure it needs sudo but in theory shouldn't be needed)

hope that helps in anyway.

---

### Post by Lievre on 2006-12-13
Well, I started it all again with:
- using the latest release (released yesterday): grass-6.2.1 and
- working in the home directory /home/src (I was working not on a removable device but on a logical partition of my hard disk)

And it worked fine!!!

Just one remark: sudo was needed for checkinstall -D

Thank you very much for your continuing help, Rui Pais, now I can use this grass ;-)

---

