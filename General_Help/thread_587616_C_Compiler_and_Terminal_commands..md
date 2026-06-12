---
title: "C Compiler and Terminal commands."
date: 2007-10-22
forum: General Help
---

### Post by eXeCuTeR+ on 2007-10-22
Hmm...Where do I get a C compiler? I'm a C programmer.

And BTW,
my 'sudo apt-get install...' commands seem to work but they don't seem to create or do anything..
For example:
I type: sudo apt-get install build-essential
This is what I get:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
***It gives some more info here but it's in Hebrew,but you won't understand :D***
***Anyways, it types something with 0s...like 0 will be removed for example (im trying to translate it from hebrew)

```
But nothing happens.
I can't see any different, but I'm sure something is going on.


Just to remind you,
I'm still looking for a C compiler :D
If I'm supposed to download it from the Synaptic, please tell me how, I have no clue how to download it from there.

Thanks :)

---

### Post by g2g591 on 2007-10-22
it says its already the newest version, you have it installed. Both synaptic and those commands work for installing/removing/upgrading your packages.  If you want to find out how to use it, use the terminal command "man cc" , that will give you a nice short manual. If you want a quick rundown of the options, use "cc --help" . You can also use that sort of command (man whatever or whatever --help) to give a short manual of most terminal programs

---

### Post by eXeCuTeR+ on 2007-10-22
But how can I use this thing now?
Well,
my main question is this: What does it do?

BTW,
How's geany as a compiler?
I downloaded as a tar.gaz file and how do I open it and install it now?
Please help me with that.

---

### Post by rfruth on 2007-10-22
Getting a compilation error from GCC ?

---

### Post by Maestro23 on 2007-10-22
> **eXeCuTeR+ said:**
> But how can I use this thing now?
Well,
my main question is this: What does it do?

BTW,
How's geany as a compiler?
I downloaded as a tar.gaz file and how do I open it and install it now?
Please help me with that.

Installing Software in Ubuntu: Section 4 -Installing from Source

[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

---

### Post by loell on 2007-10-22
> I'm a C programmer.

now that you have the Gnu C Compiler, I think you will like to have a  C  IDE

you can install anjuta IDE

```
sudo apt-get install anjuta
```

---

### Post by eXeCuTeR+ on 2007-10-22
No, I'm not getting a compliation error from GCC, I just wanna try Geany.

Maestro23,
Thanks, I'm gonna try it now.

loell, Sorry but I just started working with Linux.
IDE? What's that?

BTW,
I tried to type the command and it showed this thing:
```

...
E: Couldn't find package anjuta

```

BTW,
I tried to install Geany and it didn't work.
I navigated to the folder and typed: ./INSTALL
and apparently it didn't work.
I also tried to type sudo make install and it didn't work too.

How can I install this? it's a tar.gz file - I extracted it BTW and then only navigated to the folder.

---

### Post by lgcabarcas on 2007-10-22
./configure
make
sudo make install

or whatever says on the INSTALL or README file in the directoy, regurlary the comands and order you have to folllow to compile the software, are on those files, if not the procedure should be the standard mentioned on first instance

---

### Post by Maestro23 on 2007-10-22
> **lgcabarcas said:**
> ./configure
make
sudo make install

or whatever says on the INSTALL or README file in the directoy, regurlary the comands and order you have to folllow to compile the software, are on those files, if not the procedure should be the standard mentioned on first instance

Just to add to lg's post.

Geany is in the ubuntu repo's.  Can be installed by:

> sudo apt-get install geany

*If you are not finding packages in Synaptic, you might need to enable Universe and Multiverse repo's.  Can do so by going to : System >> Admin>> Software Sources

*Also, installing from source can be a pain in the *** for a person new to linux.  Can run into dependency he**

---

### Post by maldojr88 on 2007-10-22
wat loell is trying to tell u is that u want an IDE
its like a Graphical Compiler...meaning u open up a program
and here u see stuff like compile...debug...u have space
to write ur code..you have a workspace...
the program puts magic words(those recognized by C) 
in blue...etc....this is what i think that u want....
do wat he says to install it

---

### Post by g2g591 on 2007-10-22
as for an IDE (integrated development environment) I recommend Kdevelop
[[IMG]http://img521.imageshack.us/img521/3596/kdevelopau7.th.png[/IMG]]("http://img521.imageshack.us/my.php?image=kdevelopau7.png")

---

