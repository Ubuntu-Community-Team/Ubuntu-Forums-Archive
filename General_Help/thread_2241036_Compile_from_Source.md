---
title: "Compile from Source"
date: 2014-08-23
forum: General Help
---

### Post by michael210 on 2014-08-23
Hallo Everyone,
I need to ask you some questions about compiling a source, sorry my English is not so good.
here i am going to show you some steps wich i found them on internet and i use them.
Its about compiling in my home directory.
step 1
```

mkdir -p /home/$USER/User-Install/Sources
mkdir -p /home/$USER/User-Install/usr
mkdir -p /home/$USER/User-Install/usr/bin
mkdir -p /home/$USER/User-Install/usr/lib
mkdir -p /home/$USER/User-Install/usr/include

```
step 2
```

cd /home/$USER/User-Install/Sources

```
step 3
```

wget http://download.videolan.org/pub/videolan/vlc/2.1.5/vlc-2.1.5.tar.xz

```
step 4
```

tar -xvf vlc-2.1.5.tar.xz

```
step 5
```

cd vlc*

```
step 6
```

export PATH=$PATH:/home/$USER/User-Install/usr/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/$USER/User-Install/usr/lib
export C_INCLUDE_PATH=$C_INCLUDE_PATH:/home/$USER/User-Install/usr/include
export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/home/$USER/User-Install/usr/include

```
step 7
```

./configure --prefix=/home/$USER/User-Install/usr

```
step 7
```

make

```
step 8
```

make install

```
step 9
```

/home/$USER/User-Install/usr/bin/vlc

```
and VLC works fine.
My questions are
1
at the step 6 this commands:
```

export PATH=$PATH:/home/$USER/User-Install/usr/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/$USER/User-Install/usr/lib
export C_INCLUDE_PATH=$C_INCLUDE_PATH:/home/$USER/User-Install/usr/include
export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/home/$USER/User-Install/usr/include

```
are the right one?
should be all of them used ?
or, should i use something else?
all i need is to know before running ./configure wich variables (or how you call them) should i run, and why.
Thank you all.

---

### Post by monkeybrain20122 on 2014-08-23
Way too complicated. You don't need to create those directories manually (all those mkdir commands are not needed, all these directories will be created automatically)

To install vlc in your home, just follow these steps:

first install some dependencies and build tools

```
sudo apt-get build-dep vlc
sudo apt-get install build-essential automake 
```
Then download the vlc tarball, extract it to say, ~/Downloads/vlc-2.1.5
```
cd Downloads/vlc*
./configure --prefix=$HOME
make -j4
make install

```

That's it.

1. If you choose prefix=$HOME it will be installed in your home directory (the executable in /home/yourusername/bin) If you don't put a prefix it will be install in /usr/local
and the last command has to be changed to
```
sudo make install 
```
But see 3 below.

2. make -j4 means using 4 threads, change 4 to the number of threads you use. e.g make -j2 uses 2 threads and make uses one.

3. If you install vlc in /usr/local you should install checkinstall from repo and replace the last step with
```
sudo checkinstall

```
then follow the prompts. It will create and install a .deb so that vlc will show up in the package manager (synaptic, software centre, muon etc) and you can remove it just like other packages.

---

### Post by michael210 on 2014-08-23
hallo @[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403")
1
I realy need to know some infos about step 6
2
what means  this:
> 
2. make -j4 means using 4 threads, change 4 to the number of threads you use. e.g make -j2 uses 2 threads and make uses one.

i just realized that its complicated, i installed audacious in the same way, but when i run:
```

/home/$USER/User-Install/usr/bin/audacious

```
says
> 
/home/michael/User-Install/usr/bin/audacious: error while loading shared libraries: libaudcore.so.2: cannot open shared object file: No such file or directory

but when i run:
```

ls /home/$USER/User-Install/usr/lib/

```
seems to be there:
> 
libaudcore.so    libaudcore.so.2.0.0  libaudgui.so.2      libaudtag.so    libaudtag.so.1.0.0  libvlccore.so    libvlccore.so.7.0.0  libvlc.so    libvlc.so.5.4.0  vlc
libaudcore.so.2  libaudgui.so         libaudgui.so.2.0.0  libaudtag.so.1  libvlccore.la       libvlccore.so.7  libvlc.la            libvlc.so.5  pkgconfig

what i am doing wrong?
Thank you

---

### Post by monkeybrain20122 on 2014-08-23
Actually there is no need to compile from source. The easiest way to get up to date vlc is to install from a ppa
[https://bugs.launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

```
sudo add-apt-repository ppa:mc3man/trusty-media
sudo apt-get update
sudo apt-get install vlc
```

This will install vlc and add a repository to your software sources so vlc will be upgraded like other packages when a new version comes out

---

### Post by steeldriver on 2014-08-23
*nevermind*

---

### Post by monkeybrain20122 on 2014-08-23
Step 6 is not necessary. I don't know where you get this from. My advice is just go the ppa route (or do the hard way with my instructions)

---

### Post by michael210 on 2014-08-23
you do not help me here, i realy need to learn to compile from sources not to add some PPA to my box.
Thank you anyway

---

### Post by monkeybrain20122 on 2014-08-23
how was I not helping you? I told you step by step how to compile and you asked me a step which I told you is completely unnecessary.

---

### Post by michael210 on 2014-08-23
sorry, my bad, i did not ment that, sorry.
i wanna learn how to compile a source without root, thats all.
i do thank you for your answears.
i found tham on internet ...a guy sayed that he does ol the time so, so i tought that its ok using them.
.
.
L.E:
about Audaciuos problem i fix it with:
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/michael/User-Install/usr/lib

```
but i still have no idee about what i am doing.
Thank you.

---

### Post by monkeybrain20122 on 2014-08-23
I also did it many times. What I gave you is the complete instructions.

In general ./configure --prefix=$HOME means installing in your /home/usrname directory and it doesn't require root

For more info and installing the developmental version using nonstandard libraries (e.g ffmpeg instead of avconv) take a look at Andrew.46's excellent tutorial 
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

---

### Post by michael210 on 2014-08-23
i did understanded you, but you, me not, sorry.
you sayed that i do not need thoughs commands from step 6, but after installing audacious in my home Directory, didn't started, i got that error
> 
 	 		 			 			 				/home/michael/User-Install/usr/bin/audacious: error while loading  shared libraries: libaudcore.so.2: cannot open shared object file: No  such file or directory 			 		
 	
 
which i also fixed with this command
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/michael/User-Install/usr/lib


```
so, in my opinion, i need to type some of this EXPORT comannds to have an working app, not?
thank you.

---

### Post by steeldriver on 2014-08-23
The 'export PATH' command allows your shell to find the binary executable that you just compiled when it's not in one of the standard system executable locations such as /bin, /usr/bin 

Similarly, the 'export LD_LIBRARY_PATH' command allows the binary executable to locate its run-time shared libraries when they are not in one of the standard system library locations as defined via ldconfig

The other two commands from 'Step 6' would only have significance when compiling other programs that use the libraries + headers from the locally-installed package - they shouldn't affect the running of any binary executable files

---

### Post by monkeybrain20122 on 2014-08-23
> **michael210 said:**
> i did understanded you, but you, me not, sorry.
you sayed that i do not need thoughs commands from step 6, but after installing audacious in my home Directory, didn't started, i got that error

which i also fixed with this command
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/michael/User-Install/usr/lib


```
so, in my opinion, i need to type some of this EXPORT comannds to have an working app, not?
thank you.

Well that is because you installed in a non standard place called /home/michael/User-Install/usr/ instead of just /home/michael/ 

If instead of step 2 (and skip all of step 1) you just do
```
./configure --prefix=$HOME 
```
as in my post you don't need to export anything. (directories like /home/michael/lib, /home/michael/bin and so on would be created automatically)

To start the program go to the directory /home/michael/bin and just click it or make a .desktop file and put it in /home/michael/.local/share/applications, the .desktop file should be in /home/michael/share/applications, so just copy and paste if you do --prefix=$HOME. the folder .local is hidden so you need to either press ctrl+h or choose show hidden files to see it.

BTW how do you install the dependencies if you have no root access at all?

---

### Post by michael210 on 2014-08-24
1
I do have root rights and i use them for
```

sudo apt-get build-dep app-name

```
2
I like to keep my files (programs) in that folder not just in $HOME, this means that i need to learn about thous EXPORT commands to prevent future problems by compiling in another path.
3
now which are the best options for me to evoid 2 problems:
**a)**
i wanna type in terminal 
```

audacious

```
not
```

/home/michael/User-Install/usr/bin/audacious

```
[B]b)
[/B]everytime after reboot when ai type
```

/home/michael/User-Install/usr/bin/audacious

```
i get this:
> 
/home/michael/User-Install/usr/bin/audacious:  error while loading  shared libraries: libaudcore.so.2: cannot open  shared object file: No  such file or directory

i fix it with:
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/michael/User-Install/usr/lib

```
How can ai evoid this.
Thank you all for your Help.

---

### Post by mc4man on 2014-08-24
In your current scenarios the exports in 6 aren't useful except when building audacious-plugins (which you made no mention of??

As far as the produced binaries (vlc, audacious
Just add  /home/[COLOR="#FF0000"]yourusername[/COLOR]/User-Install/usr/bin to your $PATH
One Ex. of system wide - 
sudo nano /etc/environment
Add to the end, screen shows
reboot
Or search out methods to add a bin per user...

As far as audacious/audacious plugins
When I used to build locally to /opt/aud/ there never was an ld issue. In this case, (to $HOME/) probably best to use the export in a terminal, use a .desktop where the env is set on the Exec= line, or create a wrapper script for audacious that adds/sets the ld path.

Otherwise you *could* add via a custom.conf though not sure if that presents any security risks.
Ex. - 
```
sudo nano /etc/ld.so.conf.d/custom.conf
```
add - (changing red to your username
```
# path for builds to $HOME
/home/[COLOR="#FF0000"]username[/COLOR]/User-Install/usr/lib
```
```
sudo ldconfig
```

In regards to audacious-plugins - 
if you use apt-get build-dep then you should remove  audacious-dev libaudcore2 packages afterwards (- before configuring/building.
Before configuring audacious-plugins run - 
export PKG_CONFIG_PATH=$HOME/User-Install/usr/lib/pkgconfig

As far as current audacious - it should use a few packages not currently in 14.04, that's something else for you to possibly look at..

---

### Post by michael210 on 2014-08-24
Thank you,
adding to **.bashrc** the following line at the end
```

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/michael/User-Install/usr/lib

```
solved the problem:
> 
                                                         /home/michael/User-Install/usr/bin/audacious:  error while loading   shared libraries: libaudcore.so.2: cannot open  shared object file: No   such file or directory                      

.
Now i need to find how to make my Terminal to run
```

audacious

```
when i type audacious say's
> 
The program 'audacious' is currently not installed. You can install it by typing:
sudo apt-get install audacious

but when i run
```

/home/michael/User-Install/usr/bin/audacious

```
works fine.
What should i do to make my terminal recognize 
```

audacious]

```
instead
```

/home/michael/User-Install/usr/bin/audacious

```
Thank you all.
.
.
L.E:
Ollleeeeeee,
i succided, i added the following line:
```

export PATH=$PATH:/home/michael/User-Install/usr/bin

```
and now when i type:
```

audacious

```
or
```

vlc

```
programs starts.
Thankkkk zouuuu allll.

---

### Post by mc4man on 2014-08-24
> **michael210 said:**
> 
.
Now i need to find how to make my Terminal to run
```

audacious

```
when i type audacious say's

but when i run
```

/home/michael/User-Install/usr/bin/audacious

```
works fine.
What should i do to make my terminal recognize 
```

audacious]

```
instead
```

/home/michael/User-Install/usr/bin/audacious

```
Thank you all.

Already told you - ( just look at screenshot
> **mc4man said:**
> 

As far as the produced binaries (vlc, audacious
Just add  /home/[COLOR="#FF0000"]yourusername[/COLOR]/User-Install/usr/bin to your $PATH
One Ex. of system wide - 
sudo nano /etc/environment
Add to the end, screen shows
reboot
Or search out methods to add a bin per user...




---

### Post by michael210 on 2014-08-24
Like i sayed, Thank you all

---

### Post by monkeybrain20122 on 2014-08-24
> **michael210 said:**
> Thank you,

.
Now i need to find how to make my Terminal to run
```

audacious

```
when i type audacious say's

but when i run
```

/home/michael/User-Install/usr/bin/audacious

```
works fine.
What should i do to make my terminal recognize 
```

audacious]

```
instead
```

/home/michael/User-Install/usr/bin/audacious

```
Thank you all.
.


Another way is to just make a symlink

```
sudo ln -s /home/michael/User-Install/usr/bin/audacious /usr/bin/audacious

```

same with vlc etc.

---

