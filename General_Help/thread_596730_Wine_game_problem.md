---
title: "Wine/ game problem"
date: 2007-10-29
forum: General Help
---

### Post by ploik on 2007-10-29
hi everyone. I currently installed wine, and am tryin to install heros of might and magic v. The problem is that every time i install the game and try to start or open it, it auto closes befor it even starts. just for info, my comp specs are:
1.5 GB ram
100GB HD space
ATI all in wonder video card 9600

I have both the original CD, and an iso. ive burned the iso to a cd, and mounted it in uuntu, same thing, except i wont even read it. Just as a little etra help, can you tell me how to mount iso files inubunt? The ain prolem is how to play heros of might and magic v though. List anyways tat any of you found on how to play please. Thank you n advance for all your help.
          Ploik

---

### Post by Lacrimstein on 2007-10-29
From appdb.winehq.org:

   * If the setup program asks for 'setup.exe', kill it, and then run 'killall -9 IKernel.exe'
    * Open the file 'video/intro.xml' in the game folder and remove the first two 'item . . . item' blocks
    * Place d3dx9_25.dll in Wine's windows/system32 directory
    * This game needs a crack
    * If you want to use a resolution higher than 1024x768, run 'regedit' and add the key 'HKEY_CURRENT_USER\Software\Wine\Direct3D', then add the string value 'VideoMemorySize' and set it to the amount of video memory you have

perhaps this might help.

Always go to that website before you get a game to check if it works with wine, or for steps how to  make it work

---

### Post by Lacrimstein on 2007-10-29
btw, you can get the dll file at dll-files.com

---

### Post by Maestro23 on 2007-10-29
Have checked over at the Wine DB: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3233](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3233)

---

### Post by Lacrimstein on 2007-10-29
And to mount an ISO file:

sudo mount <isofile.iso> <mountpoint> -t iso9660 -o loop

---

### Post by ploik on 2007-10-29
im kinda new to ubuntu, so can you please go into a little more depth (i.e. i dont know how to kill a program, and when you said this game needs a crack, are we creating it? or do i need to download one?)
Thank you so much for posting so fast though, Ive barely had ubuntu far 3 days, and i love it.
and thank you for telling me how to mount, ill give it a try (does it need a path? ot is that the mount point?)

---

### Post by Lacrimstein on 2007-10-29
Yes, the ISO mount needs the full path, unless you are running it from the directory the iso is in. . The game CD is protected by safedisk or something like it, and wine can't emulate that yet, so you need a crack - just download one. To kill a process, do this:

ps -e | less            //this command runs ps with the option e, which lists all currently running processes, and pipes it into less, so that the output won't get cut off. find the process you want to kill, and memorize its PID number

kill -9 <pidnumber>     //this command kills the process. the -9 option tells the system that the process is to be killed immediately

---

### Post by Lacrimstein on 2007-10-29
mountpoint is also a path, but to a directory rather than a file

---

### Post by ploik on 2007-10-29
Thank you for your help. When i installed hommv, it didnt ask for a setup.exe, so i dont know what to kill (im trying to install as we speak) and i tried to run killall -9 IKernel.exe, but it said no programs killed. the item...item blocks, what does that exactly mean? i deleted the xml files, restored them, deleted the files in between, now i restored them, what exactly do i delete? i placed the .dll file no problem :) Do i download the crack now? and where can i find it? (site) and where do i put it (path in c: drive). and finally, resolution, i dont want to change, this is already enough trouble, or do i have to change it? 

And once more, im TERRIBLY sorry for all the questions, i know it must be annoying, but believe me, i am VERY grateful. I just want to be precise.
thank you once again,
                      Ploik

---

### Post by Lacrimstein on 2007-10-30
Well, if it didn't ask for setup, you don't have to kill anything :)

I can't help you get a crack, b/c it is illegal to do so. When you get it, read the directions it provides - usually you have to replace the original game .exe file with the crack exe (by renaming it)

As for the resolution, try running the game first - if it works, then its all cool. If it doesnt, then you will have to change it. Usually it is given as a command line argument to the game .exe.

---

