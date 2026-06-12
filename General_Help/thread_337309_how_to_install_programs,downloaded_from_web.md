---
title: "how to install programs,downloaded from web"
date: 2007-01-12
forum: General Help
---

### Post by seanstakes on 2007-01-12
i downloaded a couple of programs from the web with file extensions of .tar.bz2, i extracted them cause they were opened with the archive manager, and...then what? there's no simple install file or something.....read the readme's they say something about /configure and /make  install but i dont understand which program i have to open to type /configure and /make install.....help?

---

### Post by apjone on 2007-01-12
> **seanstakes said:**
> i downloaded a couple of programs from the web with file extensions of .tar.bz2, i extracted them cause they were opened with the archive manager, and...then what? there's no simple install file or something.....read the readme's they say something about /configure and /make  install but i dont understand which program i have to open to type /configure and /make 
install.....help?

what programs.

open a terminal
change to the directory
type:

./configure
make
sudo make install

and you may need to create a Icon on the desktop or run the program from the command line

---

### Post by NeoLithium on 2007-01-12
Make sure you also have the essential compiling tools installed.
```

sudo aptitude install build-essential

```

---

### Post by ~LoKe on 2007-01-12
Yeah, that's pretty much the basics.  I'll give an example, with how I'd do it.

1.  Download your file.  In this case, I'll use... **mpd.tar.bz2**
2.  Extract your file.  You could use the file roller, but I'll use the terminal.
```
tar xzf mpd.tar.bz2
```
3.  cd into the directory.
```
cd mpd
```
4.  Just in case, get the essential building tools.
```
sudo apt-get install build-essential
```
5.  Configure.
```
./configure
```
6.  Install.
```
sudo apt-get install checkinstall # only need to do this once
```
```
make && sudo checkinstall
```

Done.  Now you can launch your application.
7.  Launch.
```
mpd
```

---

### Post by seanstakes on 2007-01-12
the problem is im using my windows computer atm which is connected to the internet, my ubuntu computer is elsewhere in the house, i usually just trans port files on my usb back and forth. ok i just opened a terminal on my other computer now how do i change it to a directory (you mean the directory that i extracted the files to?)

---

### Post by ~LoKe on 2007-01-12
> **seanstakes said:**
> the problem is im using my windows computer atm which is connected to the internet, my ubuntu computer is elsewhere in the house, i usually just trans port files on my usb back and forth. ok i just opened a terminal on my other computer now how do i change it to a directory (you mean the directory that i extracted the files to?)

Well, it depends on where the directory is.  If it's in your home folder, you'd type..
```
cd ~/thedirectorythefilesarein
```
Example:
```
cd ~/mypackage
```
If it's on your desktop..
```
cd ~/Desktop/mypackage
```

---

### Post by ENN0 on 2007-01-12
are those codes typed into the terminal?and is there readme in the file with those codes?

---

### Post by LeslieL on 2007-01-12
I know it's possible for you to install programs this way, but it sounds like you really need to start a bit further back. Get used to what you have first. Get to know your way around the terminal. There are excellent beginner's guides out there. Start with the Ubuntu community Wiki - look at the top right of this page and click on its tab. Read, mark, learn and inwardly digest what you find there. Then start playing with new programs.

If there's any way you can attach your Ubuntu machine to the Internet, do it! (Got a long ethernet cable?)

And to change directories the command is cd. To list the contents of a directory, ls. 

Good luck :)

---

### Post by NeoLithium on 2007-01-12
Those are all typed in terminal; I'm not sure if there's any readme aside from what usually comes with the program inside the tarball on how to install them.

---

### Post by seanstakes on 2007-01-12
well i think its my home folder, is the home folder the one that named after your login?

---

### Post by seanstakes on 2007-01-12
> **LeslieL said:**
> I know it's possible for you to install programs this way, but it sounds like you really need to start a bit further back. Get used to what you have first. Get to know your way around the terminal. There are excellent beginner's guides out there. Start with the Ubuntu community Wiki - look at the top right of this page and click on its tab. Read, mark, learn and inwardly digest what you find there. Then start playing with new programs.

If there's any way you can attach your Ubuntu machine to the Internet, do it! (Got a long ethernet cable?)

And to change directories the command is cd. To list the contents of a directory, ls. 

Good luck :)

well the modem im using on my windows laptop has got ports on the back which allow it to connect to other computer elsewhere,hmm....ethernet cable? long and is it blue? if so i got plenty, but problem is the room is use my laptop and the room my other computer is like 15m which i think all my cables fall short.

---

### Post by ~LoKe on 2007-01-12
Yes.  Each line is type separately into the terminal.  I you really want it to be automated, you'll have to tell me the name of the folder and I'll write you a script.

---

### Post by ~LoKe on 2007-01-12
> **seanstakes said:**
> well i think its my home folder, is the home folder the one that named after your login?

Yep.

**EDIT:** Also, your package will have instructions.  So, cd into the directory, then type this:
```
less INSTALL
```
It'll output text, and pretty much give you the steps to install.  Read it, it helps.

---

### Post by Delkster on 2007-01-12
> **apjone said:**
> what programs.

This was the key question so far.

Seanstakes, what you have downloaded are generic source code packages of the programs. It should be possible to install them almost everywhere (in Unix/Linux anyway) but it's not the easiest nor always the best way of doing things.

It may well be that the programs you want to install have already been packaged specifically for Ubuntu. If that's the case, it's probably better to install them with Ubuntu's tools than from the generic source packages.

So, I repeat apjone's question: What programs?

---

### Post by seanstakes on 2007-01-12
ok what programs, an Mpeg player(MPlayer-1.0rc1), a CD burning program(brasero) and the win32 codecs package.

i cannot install them, they are sitting on the desktop all those 3 files.

~loKe they are sitting on the desktop, which is pretty easy to find :)

---

### Post by ~LoKe on 2007-01-12
Hold on...all those packages are very common and have .deb files. =/
Why not just download those?

**EDIT:** Type this into your terminal one line at a time:
```
sudo apt-get install mplayer brasero w32codecs
```

---

### Post by seanstakes on 2007-01-12
how am i suppose to get the install if im not connected to the web on that computer?, and wont be for awhile, i typed it in a bunch of words came out reading packages then it said.
E:/ cannot find package mplayer
E:/cannot find package brasero
E:/ cannot find package w32 codecs

and i still dont understand how to use the cd~/? thing its giving a file not found error.

---

### Post by seanstakes on 2007-01-13
um,...anybody?

---

### Post by Dr Small on 2007-01-13
To cd to the desktop, type:
```
cd ~/desktop
```

That's very simple.

---

### Post by Delkster on 2007-01-14
I'll try to give you detailed instructions for compiling programs from the source code but in order to be able to do that you'll need the compiler packages and other such utilities first. They aren't installed by default. If you could use apt (or Synaptic) you could get them all by installing the "build-essential" package. Those packages are also located on the original install/live cd so you could probably install them from there without a network connection. If you have apt set up so that it looks for packages on the cd, you can probably just have the cd in the drive, launch Synaptic, find the build-essential package and install it.

Note, though, that even if you have the build-essential package installed, you may still need more stuff in order to compile specific programs. The build-essential package just packs together (by using dependencies) some things that are very commonly needed for compiling almost any programs from the source code, but many applications have other external requirements in addition to that. If you have build-essential installed and still run into errors at any stage of the compilation, it's likely that you're missing something that's required for compiling that specific program from source. It wouldn't be very hard to obtain everything required for the compilation if you had a network connection but that's not very helpful in this case since the lack of a connection is the root of the entire problem.

All in all, things are generally a lot easier and more convenient in Ubuntu if you have a working internet connection on your Ubuntu computer. Is it completely impossible to get that computer connected to the internet, even temporarily? You could install the programs over the network and then move the modem (or whatever) back into the other computer, but installing just about anything is just that much more convenient on Ubuntu with an internet connection.

In any case, I'll try to give some pointers for compiling programs from source. Note, though, that it's actually quite likely that your installation is lacking something that's needed for compiling those programs, so even if you do everything correctly, things may fail. Even so, this may help you understand a little more about how folders (or directories, as they're traditionally called in that context) work on the command line.


> **seanstakes said:**
> well i think its my home folder, is the home folder the one that named after your login?

Yes. More specifically, your home folder is /home/yourusername

On the command line, you're always "located" in one folder, and the commands you give pertain to that folder unless you specify otherwise in your command. That folder is called the current working directory (directory is an older and traditional name for what's nowadays usually called a 'folder' in the computer world).

When you open a new terminal, its working directory is usually set to your home directory. You can also see that in the command prompt; it consists of your username, the hostname of the computer, and after the colon, your working directory, finally postfixed with a $ sign. What's shown between the colon and the dollar sign is your current working directory. On the command line ~ denotes your home folder, so if your working directory is your home folder, your prompt will probably look approximately like this:
```
username@hostname:~$ 
```

To change your current working directory (i.e. the folder in which you issue your commands), use the "cd" command. More specifically, in order to "move into" directory named blah you'd use the command "cd blah" (note the space between the cd command and the name of the directory). For example, since you can use ~ to refer to your home folder, you could enter "cd ~" to move into your home directory. Note that you don't have to do that in this case: when you open the new terminal, the working directory should already be set to your home folder so your commands are already going there.

Usually source package files have a name of the form programname-x.y.z.tar.bz2 where programname is, unsurprisingly, the name of the program, and x.y.z is the version. The ending is usually either .tar.bz2 or .tar.gz. When you extract such a package, usually what comes out will be a folder called programname-x.y.z -- that is, the same as the name of the archive but without the ending.

The commands used to compile and install the program (after you've extracted it from the source package) are usually given in that directory (in the above example, programname-x.y.z), so after extracting the archive you'll need to open a terminal and navigate into that directory, then enter the commands for compiling and installing the program.

If you've extracted the contents of the source package into your home folder, do this:

1. Open the terminal.
2. The source code should now be in the folder programname-x.y.z (check the correct name of the folder from the name of the original archive, or just find it out in the file browser), which in turn should be located in your home folder. Since your current working directory is your home folder, you could enter the source code folder with the following command:
```
cd programname-x.y.z
```
If you get an error, either the name of the folder is wrong or it isn't located in your home folder after all.

If things went right, you'll just get a new prompt that should now reflect your new working directory:
```
username@hostname:~/programname-x.y.z$ 
```

3. Here you can enter the commands to compile the program. First you'll run the configure script that will tune the compilation process to suit to your system and checks that everything's okay for the actual compilation. Initiate the script with the following command:
```
./configure
```
It will probably print out a lot of text, reporting what it's doing as it proceeds with the checks.

4. Wait until the configure script finishes. If there's no 'error' somewhere near the end of the output, things probably worked more or less okay. You can now try to compile the program from the source code with the following command:
```
make
```
This will probably also produce a lot of output -- much more than configure.

5. Make finished and there are no errors shown near the end of the output? Great, the thing is probably now compiled! You can install the program with the following command:
```
sudo make install
```
The program may or may not have placed launcher icons in the menus. If it didn't place any, you can launch the application from the command line. For example, in order to start MPlayer you'd enter "mplayer" on the command line. You can add icons into the menus yourself if you want to. You're more or less done now.

---

### Post by tommcd on 2007-01-14
Can't he just download the packages (mplayer, w32, brasero, from the ubuntu package repository? 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
eg, assuming he's on edgy:
[http://packages.ubuntu.com/edgy/graphics/mplayer](http://packages.ubuntu.com/edgy/graphics/mplayer)
[http://packages.ubuntu.com/edgy/gnome/brasero](http://packages.ubuntu.com/edgy/gnome/brasero)
or will this not take care of the required dependencies?

---

### Post by Delkster on 2007-01-15
> **tommcd said:**
> Can't he just download the packages (mplayer, w32, brasero, from the ubuntu package repository? 
...
or will this not take care of the required dependencies?

It would, but only at the point of installation (with GDebi), and it would do it by obtaining the required packages from the repositories (or a CD, but for example mplayer depends on several packages from universe and multiverse that aren't on the Ubuntu CD), which it obviously can't do because there's no network connection available on the computer.

---

