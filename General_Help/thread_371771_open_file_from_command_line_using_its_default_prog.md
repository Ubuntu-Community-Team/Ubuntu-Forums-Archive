---
title: "open file from command line using its default program"
date: 2007-02-27
forum: General Help
---

### Post by mr tim esquire on 2007-02-27
Hi as im getting fond of the command line i think this is one id like to know:
If you open a nautilus files have open with default applications when you double click them.
But on the command line you have to type the name of the program you want and then the file you want to open.  
Is there a way to open a file with its ´default´ program from the command line?

another question here:
programs seem to be installed in many different directories in linux like /usr/bin or /usr/local/bin.  Why are they put in gidderent places and where can i find a comprenhensive list of all the programs i have installed and what you need to type from the command line to run them?  

one last one if i have a program (?binary?) installed in my home folder will i only be able to ru i from my home folder

thanks very much for any help super geek friends
tim

---

### Post by WW on 2007-02-27
> ...if i have a program (?binary?) installed in my home folder will i only be able to ru i from my home folder
You can run it from anywhere, as long as you give the path to the command.  Suppose the program is called **foo**, and you have it in your home directory.  This should work anywhere:
> ~/foo
A more conventional strategy is to create a subdirectory called **bin** in your home directory, and put your commands there.  Then add ~/bin (or equivalently, $HOME/bin) to your PATH with a command such as:
> export PATH=$PATH:$HOME/bin
You can put that command in the file **.bashrc** to ensure that your private bin directory is part of your path whenever you start up a new terminal.

---

### Post by Ramses de Norre on 2007-02-27
> **mr tim esquire said:**
> Hi as im getting fond of the command line i think this is one id like to know:
If you open a nautilus files have open with default applications when you double click them.
But on the command line you have to type the name of the program you want and then the file you want to open.  
Is there a way to open a file with its ´default´ program from the command line?
```
gnome-open *file*
```

> **mr tim esquire said:**
> programs seem to be installed in many different directories in linux like /usr/bin or /usr/local/bin.  Why are they put in gidderent places and where can i find a comprenhensive list of all the programs i have installed and what you need to type from the command line to run them?

That's just how things are on linux... And can you possibly imagine how long such a list would be?? There are sites that explain certain commands but all.. I guess you'll learn them if you need them.

---

### Post by Fafnr on 2007-11-01
Is there any way of making an alias of the gnome-open command smart?
I aliased gnome-open to "do" (easy to remember - default open - and short.) however, bash no longer tab-completes nicely.
For instance:
soren@soren-laptop:~/Ruby/doc$ ls
classes      files                fr_file_index.html    index.html
created.rid  fr_class_index.html  fr_method_index.html  rdoc-style.css

soren@soren-laptop:~/Ruby/doc$ gnome-open in
tab-completes to:
soren@soren-laptop:~/Ruby/doc$ gnome-open index.htm
which is what I want.
My alias, however:
soren@soren-laptop:~/Ruby/doc$ do in
in                      initctl                 install-info
includeres              inkscape                installkernel
index_gem_repository    inkview                 install-menu
indxbib                 innochecksum            install-sgmlcatalog
info                    innotop                 installvst
infobrowser             inputattach             instmodsh
infocmp                 insmod                  invest-chart
infokey                 install                 invoke-rc.d
infotocap               install-docs            
init                    installed_alternatives  

Anything I can do?

Regards,

Søren Andersen

---

