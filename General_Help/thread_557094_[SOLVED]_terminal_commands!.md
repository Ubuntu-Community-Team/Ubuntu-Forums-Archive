---
title: "[SOLVED] terminal commands?!"
date: 2007-09-22
forum: General Help
---

### Post by dougleduck on 2007-09-22
I want to a command that will shorten folder path names.

e.g. if I want to cd to /home/user/Desktop/ to use something like

cd desk

---

### Post by ifconfig on 2007-09-22
Hi

How about 'cd ~/Desktop'?
The tilde "~" is the same as the current users home directory "/home/user".

// Magnus

---

### Post by buuntuu! on 2007-09-22
no idea if you can do it, 
but for your example: try *cd ~/Desktop*
you know about tab-complete, do you?

---

### Post by Lord Illidan on 2007-09-22
Tab complete is indeed useful, to use it, just type the first few letters of the command and press TAB.

---

### Post by ajgreeny on 2007-09-22
You can also add an alias to the hidden .bashrc file in your home folder.
Open it with gedit and look for the lines:-

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

Under that add:-

alias dt='cd /home/username/Desktop'

Now when you want to cd to Desktop just type dt in terminal and there you will be.  It is also incredibly useful for other aliases; I have them for other OS installations on my machine that I don't want to always mount at bootup, winXP and Linux Mint, so I now mount them when needed with just the commands "win" and "lin" as shown here, and "win-" and "lin-" to unmount.

alias win='sudo mount /dev/hda1 /media/hda1/ -t ntfs -o nls=utf8,umask=0222'
alias win-='sudo umount /media/hda1/'
alias lin='sudo mount /dev/hdb1 /media/hdb1/ -t ext3'
alias lin-='sudo umount /media/hdb1'

This facility is so useful you should learn to make full use of it and save a lot of repetitive typing in terminal for all sorts of things.

---

### Post by dougleduck on 2007-09-22
the alias thing is on the way but I also want to be able to use it for moving an copying files from one place to another,

So I need the new folder path shortcut to give commands the original path as an arguement.

On another system you could use setenv (this is a cshell command I think)

setenv desk='/home/user/Desktop'

and then you can use for example

cd $desk

or 

mv file.exe $desk

---

### Post by ajgreeny on 2007-09-22
Should still be possible with alias, I think, provided you move or copy files to the same place often enough, eg:-

alias move='sudo mv (or cp) path_to_file(s) new_path_to_file'

or something similar.  It will then ask for password, of course, but should be easy enough to do, just change the pathways or whatever appropriately.  I can't see any simple way to do it for many and varied file copies or moves to and from different folders, but if you do the same moves each time you can even use the *.* in the alias to move all files, of course.  It just needs a bit of lateral thinking about the alias command.

---

### Post by dougleduck on 2007-09-22
not really the flexibility I want from it, I don't want to have to write a new alias for every command.

How about getting c shell commands to work in bash? Is this easy?

---

### Post by dougleduck on 2007-09-22
I've found the solution.

all you need is to pick the name your want the directory to be known as e.g. desk then

desk=/home/user/Desktop/

then just use cd $desk

or

mv file.exe $desk

etc.

This just substitutes for the path.

---

### Post by ajgreeny on 2007-09-22
Was that substitution in your .bashrc file or somewhere else?  it seems like a terrific option that I was totally unaware of and would like to use in future.

---

### Post by dougleduck on 2007-09-22
i put it in .bash_aliases.

---

