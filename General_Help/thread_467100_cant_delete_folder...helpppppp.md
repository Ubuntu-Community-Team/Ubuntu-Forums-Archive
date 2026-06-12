---
title: "cant delete folder...helpppppp"
date: 2007-06-07
forum: General Help
---

### Post by Irti on 2007-06-07
ok i was tryin to screw around a bit with the main fonts.....and i tried to create a folder .font on the desktop so i cud l8er paste it directly in the home folder....now i cant delete the folder........it shows a lock and a cancel sign on it.............plsssssssssss help.......

---

### Post by bashologist on 2007-06-07
Before you forcefully delete something you should figure out what's wrong. Is the folder empty? Try this:
```
sudo ls .font
ls -al | grep font
```
If you're want to forcefully remove the folder then use the rm command carefully.

---

### Post by taurus on 2007-06-07
Try using root to remove it.

```
gksudo nautilus
-or-
sudo rm filename
```

---

### Post by Irti on 2007-06-07
ok...this is wat actually happened......i wanted to install a font......the website said tht i just hav to axtract the font file and paste it on the .font folder in my home folder.......so i tried searchin for .font in the home folder ...it wasnt there...so i made a folder on the desktop...and named it .font..and extracted the files into it...now the prob is that it doesnt show up wen i navigate to my destop on the terminal....so wen i try deleting it it says "no such file or directory"...although i can c it right there on my desktop...also..the icon isnt tht of a folder nemore......its just a blank white icon with a lock and a cancel icon on it.................plzzzzz help...cud u also tell me if i can close a program using the terminal

---

### Post by Irti on 2007-06-07
ok...this is wat actually happened......i wanted to install a font......the website said tht i just hav to axtract the font file and paste it on the .font folder in my home folder.......so i tried searchin for .font in the home folder ...it wasnt there...so i made a folder on the desktop...and named it .font..and extracted the files into it...now the prob is that it doesnt show up wen i navigate to my destop on the terminal....so wen i try deleting it it says "no such file or directory"...although i can c it right there on my desktop...also..the icon isnt tht of a folder nemore......its just a blank white icon with a lock and a cancel icon on it.................plzzzzz help...cud u also tell me if i can close a program using the terminal.................

---

### Post by bashologist on 2007-06-07
Can you stop making new threads? Maybe you would get an answer if you used proper english. Nobody wants to read this something like this. Maybe somebody is kind enough to translate your posts.

---

### Post by esavato on 2007-06-07
Make sure when you are "searching" for the file to add the -a mod to ls..
```
ls -a
```
This will show the "hidden" files (those that start with a.)  You may have to sudo to delete that file on your desktop.  Go into the terminal --> Accessories --> Terminal and cd to your desktop then
```
sudo rm -f .fonts
```

---

### Post by BatsotO on 2007-06-07
yes .. dong b panic, it just a font folder. Take a deep breath and let it out slow...

---

### Post by Irti on 2007-06-07
@ bashologist........ok dude........what are you getting so fired up about???.........cool down man........i aint commiting no sin man..........................@ esavato...its not showing up even in the hidden folders .........what do i do ( hope this makes you happy............@bashologist)

---

### Post by hillbilly on 2007-06-07
Try > ls -la ~/Desktop/
If you see a .font directory over there, then do > rm -rf ~/Desktop/.font

Else try
> sudo ls -la ~/Desktop/ and then if you see a .font directory do > sudo rm -rf ~/Desktop/.font


If that doesn't work tell us how you extracted the file and what options you gave !

---

### Post by Irti on 2007-06-07
ok its basically like this......i downloaded a .tar.gz file.....which had the microsoft segoe ui font...........i had to extract it to a .font folder in my home folder....so i checked for a .font folder in my home folder...but i could not find it....so i made a folder called .font on the desktop and i extracted it to that folder.....and now i cannot move that folder...and i cant delete it either.....the icon has also changed automatically...........its not a folder icon...its just a white page icon with a cancel and a lock emblem....i've uploaded the screenshot...u can see it.....its the .font named icon....i cant see it in terminal...nor in nautilus...i've tried all the mentioned methods....with no luck

---

### Post by dagrump on 2007-06-07
Try rt.clicking on it, & go to properties>permissions & see if you change it to read/write. Then drag it to the trash.

---

### Post by hillbilly on 2007-06-07
how did you create the folder ?  what was the login in which you created the folder ?
post the output of 
> $/> id
$/> ls -la ~/Desktop

---

### Post by Irti on 2007-06-07
this is the output......i created the folder by right clicking then clicking on create folder............i am the only user on this comp...i mean there is only one account on this comp


irti@irti-Linux:~/Desktop$ id
uid=1000(irti) gid=1000(irti) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(irti)
irti@irti-Linux:~/Desktop$ ls -la
total 9360
drwxr-xr-x  2 irti irti    4096 2007-06-07 23:40 .
drwxr-xr-x 44 irti irti    4096 2007-06-08 00:21 ..
-rw-r--r--  1 irti irti  412686 2007-06-07 04:34 57352-aero.tar.gz
-rw-r--r--  1 irti irti 8251528 2007-06-07 04:50 nuoveXT-aero.tar.gz
-rw-r--r--  1 irti irti  886884 2007-06-07 23:40 Screenshot.png
irti@irti-Linux:~/Desktop$

---

### Post by cookies on 2007-06-07
.files/folders are hidden

To delete a LOCKED HIDDEN file go to

Accessories > Terminal

And type

```

sudo nautilus

```

Next, go to View > Show Hidden Files in the file manager window that should pop up.

Right click the .font folder and try to Move To Trash it.

To kill an application from the Terminal type

```

sudo killall -9 APPLICATIONNAME

```

Hope it helps.

---

### Post by Irti on 2007-06-08
ok...its solved.....i typed in xkill in the terminal and clicked on the icon on the desktop and its gone...hehe...thanx ppl

---

### Post by bapoumba on 2007-06-08
Threads merged.

---

