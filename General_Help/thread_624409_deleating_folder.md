---
title: "deleating folder"
date: 2007-11-26
forum: General Help
---

### Post by Kedster on 2007-11-26
i am having trouble deleting a folder on my desk top

---

### Post by Kedster on 2007-11-26
please help

---

### Post by oneadvent on 2007-11-26
explain.

what do you mean? is an error coming up?

---

### Post by Kedster on 2007-11-26
it comes up with Error "Not on the same file system" while deleting ect...

---

### Post by oneadvent on 2007-11-26
um...is it a shared drive some sorts? If so there should be an unmount on it if your right click.

(or eject.)

---

### Post by Kedster on 2007-11-26
no it is not shared it is just a regular folder i can make links off of it but i can not deleat them either

---

### Post by oneadvent on 2007-11-26
alright, well if you want to delete it, and it wont let you, heres how to do it.

THIS WORKS BUT IS DANGEROUS. PLEASE BE CAREFUL WITH IT!

```
cd /home/USER/Desktop/
rm -rf FOLDER

```

If you do not have many things in the folder do this:

```
cd /home/USER/Desktop/
rm -rfi FOLDER

```

Let me know what happens

---

### Post by Kedster on 2007-11-26
This is what i typed in " cd /home/USER/Desktop/Link to My Music"   and this is what it said  "bash: cd: /home/USER/Desktop/Link: No such file or directory"    no go so far

---

### Post by oneadvent on 2007-11-26
post the result of this:

```
cd ~/Desktop
ls
```

---

### Post by superwad on 2007-11-26
> **Kedster said:**
> This is what i typed in " cd /home/USER/Desktop/Link to My Music"   and this is what it said  "bash: cd: /home/USER/Desktop/Link: No such file or directory"    no go so far

If the folder has spaces in the name, like "My Music", you need to do it like this:

```
cd /home/USER/Desktop/My\ Music/
```

or

```
cd "/home/USER/Desktop/My Music/"
```

---

### Post by Kedster on 2007-11-26
k now what

---

### Post by superwad on 2007-11-26
So, you were able to cd into the directory you're having troubles with?

If you can do that, still post the results of:

```
ls -l ~/Desktop
```

---

### Post by Kedster on 2007-11-26
still no go can u give me step by step the folder name is "Link to My Music"

---

### Post by oneadvent on 2007-11-27
```
cd home/USR/Desktop/
rm -rfi Link\ to\ My\ Music

```

That should remove that folder, however, you should really learn how it works.

---

### Post by superwad on 2007-11-27
Ok, open up Terminal or Konsole or whatever terminal emulation program you have.

Then type in:

```
cd ~/Desktop
```

Then type in:

```
ls -l >> fileList.txt
```

Then post the contents of the file "fileList.txt" that was just created.

---

### Post by ryanVickers on 2007-11-27
boot the live CD and you can do anything - the combined power of root and not running a "grounded" OS is incredible... :p

---

### Post by oneadvent on 2007-11-27
so what happened?

---

### Post by Kedster on 2007-11-27
iit still tells me im not in the right file system

---

### Post by Kedster on 2007-11-27
lets start over wen i try put a folder in the trash bin it tells me i am not in the right file system

---

### Post by oneadvent on 2007-11-27
So did you try the live cd like the person suggested above?

---

### Post by Kedster on 2007-11-27
no i do not have the cd right now

---

### Post by oneadvent on 2007-11-27
I would suggest you burn one and try it.

If that is not possible. Maybe it would help if you let us know how the folder got there.

---

### Post by ryanVickers on 2007-11-27
It really is the ultimate solution for file management ;)

---

### Post by oneadvent on 2007-11-27
It would be the best way, but if he doesn't have it and cant burn it then that is out....

however, if you can burn it, it would only take a couple hours to get from bit torrent. (thats the best way, IMO)

Josh

---

### Post by Kedster on 2007-11-28
ok well my awsome marvelos naboir is the actuall user of this account and he did the install of ubuntu and a ew xp then all my music was on the xp partition and he made a link on my ubuntu desktop not i and not delete it. i deleted all the music out of it i think but the folder wont go i made a copy of the music and put it in a another partion thats whay i wanna delete that link because it dont link to any thiin

---

### Post by oneadvent on 2007-11-28
use the cd. It is really the best option.

---

