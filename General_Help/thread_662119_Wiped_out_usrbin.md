---
title: "Wiped out /usr/bin"
date: 2008-01-08
forum: General Help
---

### Post by adamup on 2008-01-08
Ok, let the ridicule commence...this is an extremely embarassing rookie mistake. I managed to wipe out my /usr/bin directory.  How would I go about restoring what was there?

---

### Post by PinkFloyd102489 on 2008-01-08
Did you do it with the GUI or with the terminal?

---

### Post by adamup on 2008-01-08
The terminal. I was in the process of copying a script into that folder and apparently mistyped because the folder is now gone.

---

### Post by nowshining on 2008-01-08
what command did u type? u need sudo / root priveleges to do a wipe out of that folder by default, so um.. :/

---

### Post by adamup on 2008-01-08
Yes, I used sudo because I was trying to copy into that directory, which requires root privileges. But that's a moot point now :(

---

### Post by nowshining on 2008-01-08
and it's sort of hard to do, u need rm -rf do do that, or so, u did use

mv right

example,

sudo mv /home/username/myscript /usr/bin/myscript

however u don't need to move scripts into /usr/bin for them to work,

u just need to make sure they are executable (un-executable by default),

right - click - properties - permissions

find allow execute and check it, if it needs root, u can add a certain command in sudoers to execute without asking for a pw everytime, if not, then just when asked when double clicking it as to whether run, run in terminal, etc.. it should ask for sudo in terminal.

:)

I also suggest making in ur home folde a script directory for easier access to ur scripts. I got several.

:)

---

### Post by PinkFloyd102489 on 2008-01-08
If you're like me, he was probably wanting to execute them simply by typing the command name instead of cd'ing to a directory and then sh'ing the script.


I can understand where you're coming from, just dont see how you managed to delete the dir.

---

### Post by gilgongo on 2008-01-08
I'm not sure, but you *may* be able to boot with a rescue disk, then simply mount your hard drive and copy /usr/bin onto it from the disk. Having said that, it may be better to use the rescue disk to copy off any data you need to save, then just re-install.

Either way, do you have an Ubuntu install CD?

---

### Post by adamup on 2008-01-08
I think I used cp.  I think it was something like...

sudo cp script.sh /usr/bin/ .

I'm not really sure what happened.

Thanks for the other tips though. Clearly I shouldn't have been screwing with that directory. Still, any ideas on how to restore what was in there?

---

### Post by adamup on 2008-01-08
Yep I have the Ubuntu Install CD.  You think I could boot up the live CD and copy the directory onto my hard drive?

---

### Post by nowshining on 2008-01-08
u just copied it, u were in the directory right? and to execute it in terminal

sh nameofscript


oh and when u do scripts u don't have to put .sh if u don't want to, linux doesn't associate that much or rely on extensions like windows does.

how do u EXACTLY know that /usr/bin/ has been deleted?

filesystem - /usr/bin

can u go there ??

---

### Post by adamup on 2008-01-08
Ok, I discovered that the bin directory hasn't been deleted; it's somehow been moved to a directory in my home directory.  So instead of it being at /usr/bin it's at /home/username/dir/bin. I tried to copy it back to /usr but you need root privilege to do that. Tried sudo -- it can't be found obviously because it's been moved. Tried running sudo by copying it to /home/username then running it from there:

./sudo [command] [options]

only to get 

sudo: must be setuid root

So basically, I have the directory intact but can't copy back to its correct location without sudo.



Edit: Never mind. I figured it out. Just added the new bin directory to my PATH variable and can copy it back to the correct location.  Thanks everyone for the help.

---

### Post by PinkFloyd102489 on 2008-01-08
Boot up into Recovery Mode and move it.


When Ubuntu is starting up, hit Escape when it counts down from 3. Then boot into the first kernel from the top that says Recovery at the end. It'll boot into a root console.

---

