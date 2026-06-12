---
title: "Need bash script-writing help"
date: 2008-02-21
forum: General Help
---

### Post by peedeeramone on 2008-02-21
I thought I would mess around in creating a bash script to be run from the nautilus scripts launcher, but I need some help...

I want to create a script that will allow me to select all the files in the folder and launch them (as in to take a folder full of music files and play them all, or whatever file type you had).

I know to put the #! /bin/bash part at the beginning, but after that I'm clueless..

if anyone knows how to do this that would be cool, I'm sure its a simple line or two.


Also, just for the hell of it, if you have any nautilus scripts that are cool, or know of a site that has an accumulation of them that would be cool too.


mucho gracias

---

### Post by bodhi.zazen on 2008-02-21
Depends on what you are doing, start with the commands you would enter in the terminal.

You can easily use a for loop 

for i in /directory; do
<commands> # like echo $"i"
done

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc2)

 [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

 [http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

---

