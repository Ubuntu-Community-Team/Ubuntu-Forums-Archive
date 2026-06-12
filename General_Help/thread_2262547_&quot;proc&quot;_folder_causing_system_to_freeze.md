---
title: "&quot;proc&quot; folder causing system to freeze"
date: 2015-01-25
forum: General Help
---

### Post by gordon99 on 2015-01-25
I am using xubuntu 14.04.
Today I wanted to look inside the root folder using gkthunar. I then clicked on the 'proc' folder just to see what was inside but the system froze and the hardware started to race. I had to do a force shut down to free things up.
I re-booted and then tried to open the 'proc' folder again. I think it may have opened as the title /proc/ came up, but there was nothing on the screen and the system froze once again.
I would be pleased if someone could advise me what maybe wrong and how it may be cured.

---

### Post by Holger_Gehrke on 2015-01-25
The directory '/proc' is actually not a directory at all. Its the mount point of a virtual file system in which the kernel shows information on all running processes. So every currently running process in the system has a subdirectory named after the process number in /proc in which various information about the process is available. This file system is used by process management tools like ps or top. I don't know why your file manager froze, but the fact that the contents of this directory tend to change a lot and very often might have something to do with it. If I look in there at all, I usually do so using a shell and it's never caused any trouble, so far. But obviously it's a case of 'Look all you want, but don't touch !'

---

### Post by gordon99 on 2015-01-26
Holger, I have repeated the process of trying to open /proc. The screen again went blank with just the "/proc/" title and it again froze. I have no idea how important this directory is, or if it is doing its job correctly when I leave it alone, but I am concerned that the symptoms I have described are indicating something more serious. I regret I do not know what using a shell involves. If anyone else has suggestions as to what may be happening I would be glad to hear from you.

Since doing the above I went into terminal and typed 'gnome-open /proc'. This time the screen filled with files, most of them with a lock symbol on, but the mouse became inoperative. The bottom of the screen showed 'Loading folder contents' so I waited. However after 5 or so minutes I gave up and did a forcible shutdown.

---

### Post by prestonR on 2015-08-11
Hi,
I'm on Mint Mate 17.2 64bit (based on Ubuntu 14.04) and caja file manager behaves exactly in the same way. Most of the time the machine totally freezes if I try to open 'proc', sometimes I can get in and it freezes on the next action. Mouse dead, keyboard dead, time stops, all I can do is press and hold the power button. 
Apart from that everything works fine. On a second laptop running the same system this doesn't happen. 

Out of interest, [**[COLOR=#000000]gordon99,[/COLOR]**]("http://ubuntuforums.org/member.php?u=1280530") what's the hardware you're using? Mine's a single boot Macbook Pro 2009.

---

### Post by marshal-devilhunter on 2016-01-28
> **gordon99 said:**
> Holger, I have repeated the process of trying to open /proc. The screen again went blank with just the "/proc/" title and it again froze. I have no idea how important this directory is, or if it is doing its job correctly when I leave it alone, but I am concerned that the symptoms I have described are indicating something more serious. I regret I do not know what using a shell involves. If anyone else has suggestions as to what may be happening I would be glad to hear from you.

Since doing the above I went into terminal and typed 'gnome-open /proc'. This time the screen filled with files, most of them with a lock symbol on, but the mouse became inoperative. The bottom of the screen showed 'Loading folder contents' so I waited. However after 5 or so minutes I gave up and did a forcible shutdown.

/proc is actually a virtual filesystem which does not exist on hard disk. It's already running and is located on RAM I think.
Though I don't know why it freezes, But it happens to me also when I try to Open this folder using my File Manager.
After two tries with file manager I tried terminal command. Just type ...
```
ls /proc
```
... and you'll see what ever file and folder is inside the /proc directory. Just like this :
(Those numbers are running processes IDs, and each one is a folder !)
[IMG]http://s6.picofile.com/file/8235737642/Screenshot_tilda.png[/IMG] 

Then you can use the command below to enter each folder :
```
"filemanager-name" /proc/"file-or-folder-name"
```
Example :
```
caja /proc/acpi
```
Which I just used :D

I Hope this helps you, But I still don't know why our systems freeze when we enter that directory using file manager !

---

### Post by lisati on 2016-01-28
/proc is not a "real" folder - it does not actually exist on disk. It's stored in RAM, to help avoid reading from disk. It is also used to provide information about your system. Many of the "files" and "folders" it contains don't actually correspond to real, physical files.

---

### Post by The Cog on 2016-01-28
I'll take a wild and uneducated guess:
The GUI file manager hooks the OS wanting to know whenever the directory contents change, and spins up a new sub-process to list the current contents.
But the new subprocess causes a new process subdirectory to be created,
so the GUI is notified of the change, and spins up a new subprocess to list the changed contents,
but the new subprocess causes a new process subdirectory to be created,
so the GUI is notified of the change, and spins up a new subprocess to list the changed contents,
but the new subprocess causes a new process subdirectory to be created,
so the GUI is notified of the change, and spins up a new subprocess to list the changed contents,
but the new subprocess causes a new process subdirectory to be created,
...

---

