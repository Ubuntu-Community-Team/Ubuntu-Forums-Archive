---
title: "Get out Getty"
date: 2007-06-14
forum: General Help
---

### Post by thegino on 2007-06-14
Hi all, I got Six instances of Getty running in my process table read on ubuntu docs that I need one if I'm the only user which I am, I looked up on how to shut them off and said i need to navigate to /etc/inittab some thing like that, well I looked for it in the /etc/  but not there. Can any one tell me what file i have to change if not the (initab?) my spec are Ubuntu Feisty Fawn with KDE and KDE desktop.

Thanks

P.S. Is there a list of process that should not be running multiple instances for example i got hald-addon-keyb:event 1, 4 and 5, konqueror 

Thanks again

---

### Post by hikaricore on 2007-06-14
Virtual consoles don't take up much memory, and can be useful if you are having problems.
The comment about being the only user makes no sense as this is not how getty works.

If you absolutely must get rid of most of them their tty script files are located at:

/etc/event.d/

And they are named tty1-6 corresponding to Ctrl+Alt+F1-6 respectively.

They can be disabled by opening these text files individually and commenting out the "start on" lines with a # symbol.

But honestly if you don't absolutely need them gone, it's better to just leave well enough alone.

---

### Post by Rui Pais on 2007-06-14
hi,
gettys are spawned by the files /etc/event.d/tty* 
[COLOR="Gray"]
Just move the ones you don't want out of the way:
```
sudo mv /etc/event.d/tty6 /etc/
sudo mv /etc/event.d/tty5 /etc/
...
```

if you want them back, just put them again on /etc/event.d/
[/COLOR]
hth


EDIT:
A better method. 
Edit /etc/event.d/tty6 /etc/event.d/tty5 ... and change line: 
```
start on runlevel 2
```
for:
```
#start on runlevel 2
```

hth

---

### Post by hikaricore on 2007-06-14
Oh sure do it the easy way. :P

---

### Post by Rui Pais on 2007-06-14
> **hikaricore said:**
> Oh sure do it the easy way. :P

:)
sorry i didn't see your post. We answer at same time...

The advantages of move them away is to easily see the ones activates or not. Not sure if one must comment the 'start on' line or the 'exec ...' one. 
So, yes, i set for the easy way. 
:lol:

---

### Post by thegino on 2007-06-14
> They can be disabled by opening these text files individually and commenting out the "start on" lines with a # symbol.

*Did not seem to work tty1-tty6*

after restart

Left # on tty1 and kept tty2 alone, moved tty3-tty6

Rui Pais > sudo mv /etc/event.d/tty6 /etc/

*Worked*

Used gksu konqueror rather the Terminal to move files to a temporary folder

now i have one getty running for Virtual Console in case of problems, Thanks hikaricore and Rui Pais

---

### Post by Rui Pais on 2007-06-14
i think the way to work with comments is comment both the 'start' and the 'exec' lines... not sure, didn't try, but since exec command is there it should spawn the console (i think) 

anyway, i twice hikaricore words. 
tty don't waste almost any memory. It's better to leave at least 2 or 3 of them. Imagine that you have a borked X and need to run something on console. It it frozen, or require something in the meddle of a process having more consoles could be a need...

---

### Post by waltereo on 2008-05-04
> **Rui Pais said:**
> i think the way to work with comments is comment both the 'start' and the 'exec' lines... not sure, didn't try, but since exec command is there it should spawn the console (i think) 

anyway, i twice hikaricore words. 
tty don't waste almost any memory. It's better to leave at least 2 or 3 of them. Imagine that you have a borked X and need to run something on console. It it frozen, or require something in the meddle of a process having more consoles could be a need...

Not sure that getty didn't use that much memory.  I check the system  monitor and each getty process use 500k ....  6 process = 3 megs

So by leaving only 2 getty, you save 2 megs ...

---

### Post by Rui Pais on 2008-05-04
> **waltereo said:**
> Not sure that getty didn't use that much memory.  I check the system  monitor and each getty process use 500k ....  6 process = 3 megs

So by leaving only 2 getty, you save 2 megs ...

:)
well i personally stick with 3 (and remove 3)...

Just an update for the method on remove them. 
Move/remove the undesired tty it's not the best option.
Best it's edit the undesired ttyN and comment out line:
```
**#**start on runlevel 2
```
(this is put a # signal at beginning of line 'start on runlevel 2')

:)

---

