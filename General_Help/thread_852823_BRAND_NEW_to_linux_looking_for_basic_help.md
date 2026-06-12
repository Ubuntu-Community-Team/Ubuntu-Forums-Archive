---
title: "BRAND NEW to linux looking for basic help"
date: 2008-07-08
forum: General Help
---

### Post by tepinvic on 2008-07-08
Hi everyone, Im brand new to linux and ubuntu and im looking for a very basic guide to the terminal and useful commands that i will be using.

Also, Im very confused as to how all the files are organized. Where is exactly the ubuntu equivalent of the windows folder "program files"

Sorry in advance if this is to ridiculously noobish..

---

### Post by wannadumpwindows on 2008-07-08
A little bit about the terminal to get you moving.

[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by L337_K3y5 on 2008-07-08
> **tepinvic said:**
> Where is exactly the ubuntu equivalent of the windows folder "program files"


Well, different files for different categories of programs go into different directories, however to be obvious, they are all in filesystem.

---

### Post by scotcella on 2008-07-08
Also might be best to hang out in the Absolute Beginners Forum.

Some reading material:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

My advice is to spend a few weeks reading up on information and get familiar with terminology and get a feel for your OS. I suppose from then on you can get adventurous.

I mostly use my OS for work purposes which I write alot of documents for my students work. I don't use it for watching DVDs, listening to music or editing photos etc. 

If I could have a decent photo editing application I would be able to edit my photos but so far I haven't found one that meets my needs satisfactorily. So still dual boot into XP for this purpose. (Yes I know there is GIMP, but I actually find it very difficult to use)

So depending on your interests, look them up and do some experimenting on different applications that are available. Make sure things work etc etc.

---

### Post by cyclobs on 2008-07-08
what i do when i install games or such is make a 'games' folder in my home folder, then i put any games in there, most games needs a console to start so i just 'cd' to that directory then to any game directory then run ./(game bash file).

some games like wormux has a make install function that will automatically move all of the files into the right spot and add a launcher to the menu :)

hope that was of some what help

---

### Post by karasuman on 2008-07-08
I'm still pretty new to linux, so I understand where you're coming from.  You hardly even know what to ask, right?  :)

Here are a couple of things I found useful to know.

```
sudo anything
```

means you're performing whatever command as root.  You'll generally be asked for your password.  Anything that involves overwriting protected files, installing programs, etc. requires that you do it as sudo.  For instance,

```
sudo apt-get install oneko
```

gives you a fabulous little cat to chase your mouse around.  (This is actually really cute, easy to mess with, and gets you started with terminal commands, if you want to give it a try.)  Still using this as an example, to launch a program, you generally type the name of the program in the terminal.  Some programs have slightly weird things to launch under, but "oneko" isn't one of them.  So, to launch the program, 

```
oneko
```

Some terminal commands will have other variables you can specify to tell them how to do their job.  For instance, I run oneko as

```
oneko -tora -bg goldenrod -cursor 132 -position +100
```

which makes the cat have stripes (-tora), be a pretty color (-bg goldenrod), restore my default cursor when I'm done (-cursor 132), and not sit right on top of my mouse (-position +100).  Commands like this are usually program-specific, so the absolute best terminal command ever is

```
man whateverprogramyouneedtolearnhowtouse
```

This gives you the manual for the program.  Sometimes,

```
program name --help
```

does that, too.  When you're done reading, hit q to go back to the normal terminal window.  If you use a program (like oneko) that takes over your current terminal window when it runs, adding & at the end of the launch command will restore your ability to keep typing in the same window.

If you find that you have a sequence of commands that does something really cool (for instance, oneko -tora etc.) that you don't want to type all the time, you basically have two options.  For less complex things, you can right-click on one of your panels and add a custom launcher to it with what you'd type in the terminal as the command.  If this doesn't do what you want, you can open a text file, enter the commands as you'd enter them into the terminal, save the file, and then make the command on the launcher the path to that file.  Before this will work, though...

```
chmod +x file
```

I end up using this a lot.  It allows a file to be executed as a script.  You can either cd to the directory of the file and then put ./filename where file is or enter the entire path to the file.  For instance, if I want to run a program that's saved on beth/desktop/stuff/morestuff, I would do it like this:

```
cd Desktop
cd stuff
cd morestuff
chmod +x ./file
./file
```

That navigates to the file, makes it executable, and the executes it.

As for the nature of the file system...  Well, I still don't have that totally sorted out.  Basically, all of YOUR files (pictures, documents, etc.) go in your home directory, which you "own" and hence have total access to.  The other files are saved in places that are harder to get to.  :)  You can click on places -> home folder -> computer -> file system to see all of those files, and alt+h will show hidden folders.  In order to DO anything with these files, however, you have to have root permissions, which means doing things to them with sudo.

On the up-side, you don't NEED to access program files like you did in Windows.  You can run application as described above or by accessing them from the applications menu.  Right-clicking on "applications" gives you the options to customize that menu.  To get new programs, either apt-get install whatever, or use the Add/Remove programs feature under applications.  

I hope this helps.  :)  I still feel a little overwhelmed by all of this sometimes.

---

### Post by hyper_ch on 2008-07-08
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by bloom on 2009-01-22
in this site [http://tldp.org/](http://tldp.org/) you can find a lot of basic documentation, in particular for filesystem organization, i.e. which file goes in which directory, try to read this guide:  Linux Filesystem Hierarchy, this is the url for the file in pdf [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf)

italian translation:
in questo sito [http://tldp.org/](http://tldp.org/) trovi tanta documentazione di base, in particolare per l'organizzazione del filesystem, ovvero cosa va in quale directory, leggi questa guida: Linux Filesystem Hierarchy, questo è l'url per il file in pdf [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/Linux-Filesystem-Hierarchy.pdf)

good linux,
bloom

---

