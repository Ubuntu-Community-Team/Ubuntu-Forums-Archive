---
title: "Installing Dreamweaver with Wine"
date: 2007-03-27
forum: General Help
---

### Post by geovino on 2007-03-27
I have just installed Wine and I want to install Dreamweaver8. How do I install it?
I'm using Edgy

---

### Post by IcemanV9 on 2007-03-27
Two methods (gui or cli):

Open the nautilus, then double-click the exe file to install Dreamweaver8.

Or, open the terminal, type wine <dreamweaver>.exe

---

### Post by geovino on 2007-03-27
this is what I get:
davek@davek-desktop:~$ wine dreamweaver.exe
wine: could not load L"c:\\windows\\system32\\dreamweaver.exe": Module not found
davek@davek-desktop:~$ wine <dreamweaver>.exe
bash: dreamweaver: No such file or directory
davek@davek-desktop:~$ 

I used this method from [http://blog.publicidadpixelada.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/](http://blog.publicidadpixelada.com/how-to-dreamweaver-running-on-ubuntu-in-10-easy-steps/)

andI think  I've done everything but I'm missing something. What could it be?

---

### Post by IcemanV9 on 2007-03-28
Ah! After reading the link, you are basically copy everything from Win32 side to Ubuntu side; not installing. :)

Try to launch Dreamweaver with a full path:

```
wine ~/.wine/drive_c/Program Files/Macromedia/dreamweaver.exe
```

Again, I am not sure if the path is correct for you. Please check it to be sure.

---

### Post by geovino on 2007-03-29
In program files I have a Dreamweaver 8 file instead of the Macromedia file

here's what happens:

davek@davek-desktop:~$ wine ~/.wine/drive_c/Program Files/Dreamweaver8/dreamweaver.exe
wine: cannot find '/home/davek/.wine/drive_c/Program'
davek@davek-desktop:~$ wine ~/.wine/drive_c/Program Files/Dreamweaver 8/dreamweaver.exe
wine: cannot find '/home/davek/.wine/drive_c/Program'
davek@davek-desktop:~$ 

What else can I try?

---

### Post by Gillingham on 2007-03-29
If you are using gnome, just have a look to see if you have a wine menu item under the applications menu.  You *may* find it their.  Certainly some of the programs I have installed using wine have.

---

### Post by IcemanV9 on 2007-03-29
Oy! I forgot that Unix does not understand space between "Program Files". Sorry about that.

```
wine ~/.wine/drive_c/Program\ Files/Dreamweaver8/dreamweaver.exe
```

---

### Post by geovino on 2007-03-29
Tried that... can't find it. I'll have to double check all the steps and make sure all the files were copied to the correct directories. I know I'm close, probably missing one link somewhere.

---

### Post by geovino on 2007-03-30
I checked every step and ran the recode to convert the reg file and I get this message:

davek@davek-desktop:~$ recode ucs-2..ascii macromedia-reg-key.reg
recode: macromedia-reg-key.reg failed: Untranslatable input in step `ISO-10646-UCS-2..ANSI_X3.4-1968'
davek@davek-desktop:~$ 


this reg key is the problem how can I correct this? 

and where do I run the 
$ wine regedit yourfile.reg   in Wine?

Here's the registry entry for macromedia in windows:

Windows Registry Editor Version 5.00



[HKEY_LOCAL_MACHINE\SOFTWARE\Macromedia\Dreamweaver\8\Registration]

"Cached Serial Number"="DWD800-00418-67237-13495"

"Cached Execution Level"=dword:00000000

"Cached Is Registerable"=dword:00000001

"Cached Is Trial"=dword:00000000

"Cached Is License Good"=dword:00000001

"Cached Splash Resource"=dword:00001b72

"Location"="C:\\Program Files\\Macromedia\\Dreamweaver 8\\Dreamweaver.exe"

I think my problem is getting this converted to ascii properly. What am I missing?

---

### Post by geovino on 2007-03-31
> **IcemanV9 said:**
> Ah! After reading the link, you are basically copy everything from Win32 side to Ubuntu side; not installing. :)

Try to launch Dreamweaver with a full path:

```
wine ~/.wine/drive_c/Program Files/Macromedia/dreamweaver.exe
```

Again, I am not sure if the path is correct for you. Please check it to be sure.

Here's what happens in the terminal:

davek@davek-desktop:~$ wine ~/.wine/drive_c/Program Files/Macromedia/dreamweaver.exe
wine: cannot find '/home/davek/.wine/drive_c/Program'
davek@davek-desktop:~$ 


I double checked all the files and they are in their proper directories in the .wine folder but I'm missing a link somewhere. What else could it be? the registry entry may be in the wrong palce and it didn't export it correctly. Any clues?

---

### Post by spankymasterc on 2007-03-31
Another alternative would be a Virtual machine if you are interested PM and i will give u all the deatails its EASY not much u gotta do but run a .deb pakage and your done 

P.s all u need is a windows Xp cd u dont even need a valid serial i will help you out if you are interested....

---

### Post by geovino on 2007-03-31
Sure, I'm interested... let me now how.

Thanks

---

