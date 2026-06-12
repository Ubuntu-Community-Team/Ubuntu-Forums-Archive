---
title: "Where are Aspell dictionaries located in Ubuntu 18.04?"
date: 2019-04-29
forum: General Help
---

### Post by swarup on 2019-04-29
I've been using Aspell for years in Ubuntu. Now having installed Ubuntu 18.04, although Aspell is installed and I have installed the Hindi and Bengali dictionaries, but I am unable to locate them. I need to install my personal word list into the dictionaries.

Here is how I used to do it in Ubuntu 14.04:

```
cd /home/swarup/Desktop/aspell6-hi-0.02-0
&#65279;preunzip hi.cwl
[Replace hi.cwl in the distribution with my hi.cwl]
&#65279;prezip -f hi.wl
&#65279;./configure
&#65279;make
sudo make install
```

But in Ubuntu 18.04 I need to know where the Hindi dictionary is, so that I can implement the above sequence of commands.

---

### Post by Impavidus on 2019-04-29
I don't know about aspell dictionaries, but to list all files in a package, use```
dpkg -L <package name>
```In your case```
dpkg -L aspell-bn
dpkg -L aspell-hi
```It's probably in /usr/share/aspell.

You can also use synaptic.

---

### Post by swarup on 2019-04-29
I tried it, and it provided a long list of places where aspell-hi files are located. And I went to all those places. but I didn't yet find the exact file I need. That file is called hi.wl
Is there a terminal command for finding the location of a single specific file? That will probably get me what I need.

Add: I found a command for this online, and executed it:

```
~$ find -iname hi.wl* 
./Aspell H & B [my copies]/aspell6-hi-0.02-0/hi.wl~
```

The file it found was my own hi.wl file-- the one I am wanting to install in the spellchecker dictionary. This all makes me think the format may have changed in the Aspell program. Otherwise the find command should have found a hi.wl file somewhere in the file system. And that I would have swapped out with mine.

With the command you had provided, among the file locations was this one: /usr/share/aspell/hi.cwl.gz. This is I believe the downloaded Hindi word list-- not the installed version. Would this file be the actual installed file? That is, could this be the file I need to replace? I had doubt about this, as it is a compressed file mostly like just for storage of the list and not for its actual use in the program, right?

---

