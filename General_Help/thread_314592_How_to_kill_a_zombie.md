---
title: "How to kill a zombie?"
date: 2006-12-07
forum: General Help
---

### Post by finferflu on 2006-12-07
Hi people,
I was just wondering whether there was any way to kill zombie processes. I bet I'm not the only one to have asked such a stupid-sounding question.

I couldn't find any answer in the forums, so here I am...

---

### Post by taurus on 2006-12-07
Applications -> Accessories -> Terminal
```
ps -A
```
Look at the first column to see what the PID if the process is, then kill it with

```
sudo kill -9 1234
(assuming 1234 is the PID...)
```

---

### Post by finferflu on 2006-12-07
Ah, I've always heard that you can't kill a zombie, as the term itself suggests... So I guess I couldn't kill it with the command **killall**. Right?

---

### Post by linuchsan on 2006-12-07
no...you have to kill the parent, or restart the service

---

### Post by yabbadabbadont on 2006-12-07
> **finferflu said:**
> Ah, I've always heard that you can't kill a zombie, as the term itself suggests... So I guess I couldn't kill it with the command **killall**. Right?

You might have been able to if you added the "-9" parameter just like in the previous "kill" example.

---

### Post by finferflu on 2006-12-07
Ok, sorry for the anachronistic question, but how do I find out the zombie process? I know I've got 2 zombie processes because that's what **top** tells me, but I don't know what they are.

---

### Post by yabbadabbadont on 2006-12-07
I think, "ps -efw" will show some indication if a process is zombified.

---

### Post by finferflu on 2006-12-07
Actually, what I see is quite messy, and I don't really get what is going on...

---

### Post by kerry_s on 2006-12-07
In top look at the "S"(status)
R=running
S=sleeping or stoped
Z=zombie

Hit k & it will ask which pid, type the pid(the pid is under pid)

---

### Post by finferflu on 2006-12-08
Thanks! I've noticed that the zombie process is not always there in the list, though...

---

### Post by UltraSonicSite on 2006-12-08
What are, these so called "zombies".

---

### Post by finferflu on 2006-12-08
> On Unix operating systems, a zombie process or defunct process is a process that has completed execution but still has an entry in the process table, allowing the process that started it to read its exit status. In the term's colorful metaphor, the child process has died but has not yet been reaped.

When a process ends, all of the memory and resources associated with it are deallocated so they can be used by other processes. However, the process's entry in the process table remains. The parent is sent a SIGCHLD signal indicating that a child has died; the handler for this signal will typically execute the wait system call, which reads the exit status and removes the zombie. The zombie's process ID and entry in the process table can then be reused. However, if a parent ignores the SIGCHLD, the zombie will be left in the process table. In some situations this may be desirable, for example if the parent creates another child process it ensures that it will not be allocated the same process ID.

A zombie process is not the same as an orphan process. Orphan processes don't become zombie processes; instead, they are adopted by init (process ID 1), which waits on its children.

The term zombie process derives from the common definition of zombie&#8212;an undead person.

Zombies can be identified in the output from the Unix ps command by the presence of a "Z" in the STAT column. Zombies that exist for more than a short period of time typically indicate a bug in the parent program. As with other leaks, the presence of a few zombies isn't worrisome in itself, but may indicate a problem that would grow serious under heavier loads.

To remove zombies from a system, the SIGCHLD signal can be sent to the parent manually, using the kill command. If the parent process still refuses to reap the zombie, the next step would be to remove the parent process. When a process loses its parent, init becomes its new parent. Init periodically executes the wait system call to reap any zombies with init as parent.

from [http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)

Actually, I found the command I was looking for:

```

ps -A s
```

Which shows a column called STAT, in which you can identify a "Z" zombie process! But then when I do

```
kill -9 <PID>
```

The process is still there... I can't kill the zombie!

---

### Post by drewtown on 2006-12-08
try making your terminal fullscreen you may be able to see more process and pick up the zombie one.  If anybody knows how to scroll the top screen I would be interested too.

---

### Post by thomashauk on 2006-12-08
You need to kill the source of the zombie infection...

AKA the parent process

---

### Post by yabbadabbadont on 2006-12-08
I know some will consider this heresy but, just reboot once in a while.  That will get rid of them.  :D

---

### Post by Azakus on 2006-12-08
I don't know if you want to try it the GUI way, but the System Moniter (System>Administration>System Moniter) shows a GUI of the ps -A s info. Also, you can change the preferences (View>Dependencies {Ctrl+D}) to get the processes organized into subtrees by parent/child processes. That way, you can see which process started the zombified one.

---

### Post by kerry_s on 2006-12-08
> **yabbadabbadont said:**
> I know some will consider this heresy but, just reboot once in a while.  That will get rid of them.  :D

I would just let it go, once you start the app again it would be back. I noticed zombies are a common problem with gnome, i never get them in fluxbox.

---

### Post by Admoseley on 2007-11-18
I have the same curiosity. I type the following:

 ps -A |grep defunct


This gave me my 2 zombie processes running on my system.

the command sudo kill -9 27468 wont get rid of my processes though.

---

### Post by Admoseley on 2007-11-18
> **Azakus said:**
> I don't know if you want to try it the GUI way, but the System Moniter (System>Administration>System Moniter) shows a GUI of the ps -A s info. Also, you can change the preferences (View>Dependencies {Ctrl+D}) to get the processes organized into subtrees by parent/child processes. That way, you can see which process started the zombified one.

that did it... thanks! fixed it and no reboot! :)

---

