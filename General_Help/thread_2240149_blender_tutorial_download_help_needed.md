---
title: "blender tutorial download help needed"
date: 2014-08-18
forum: General Help
---

### Post by ortermagic on 2014-08-18
I am wondering if it's possible to download Mr Hirsigs student blender tutorials. I see it's possible if you have itunes but unfortunatley I do not think its possible to get itunes to work in my ubuntu machine. I dont think there is a ubuntu itunes app .... am I wrong?

The following is the link I am reffering to...[http://gryllus.net/Blender/3D.html](http://gryllus.net/Blender/3D.html)

---

### Post by sotiris2 on 2014-08-18
Since these videos appear to be creative commons , yes there is a way. Its a bit of hacky way though. I cannot understand why he has not made them available through a more open platform that itunes.

Anyways open up firefox , system monitor , and your file browser. In system monitor check firefox's id , usually a 4 digit number but could be bigger, say [COLOR=#ff0000]1456[/COLOR].

In the file browser go all the way up to the root (/) filesystem. Tap Alt+UParrow a few times to achieve that. Then go to the /proc folder and enter the folder which is the id of firefox  (in our example [COLOR=#ff0000]1456[/COLOR]). Finally enter the fd folder. There's a bunch of files here. Start playback of vimeo video in Firefox. A file will appear say its named [COLOR=#00ff00]17[/COLOR] , probably will have a thumbnail as well. If you hit refresh (F5) it will keep growing in size. When it stops growing , the full video has been downloaded. Now trying to copy streaming videos in the file browser usually fails so we will use the terminal. 

Make a new folder inside Videos either via nautilus or command line named Blender (be careful with caps if you make the folder with all caps or no caps at all you must change the commands below). The command to create the directory in terminal is.
```
mkdir ~/Videos/Blender


Open up a terminal via Alt+Ctrl+T and input the following
[code]sudo cp /proc/[COLOR=#ff0000]1456[/COLOR]/fd/[COLOR=#00ff00]17[/COLOR] ~/Videos/Blender/"descriptive name"
```
This will copy the file to your Videos folder with the name descriptive name. You should replace that with whatever name you want, probably the video title. Do put the name inside " " especially if you want the name to have spaces. And don't forget to replace [COLOR=#ff0000]1456[/COLOR] and [COLOR=#00ff00]17[/COLOR] with the actual numbers you see in your system. First time you use it will ask you for your password. It won't show you *** as you type but it is 'receiving' normally, just write and press enter.

If  you go to the Blender folder you 'll find the files have a little lock on them and you can't play them. To resolve that type in terminal
```
sudo chown -r [COLOR=#800080]user[/COLOR] ~/Videos/Blender
```
Replace [COLOR=#800080]user[/COLOR] with your username, if not sure you can find it out via
```
whoami
```
You can copy all videos you want there and run it once and it will 'fix' all of them. Or you can run it after every copy.

---

### Post by ortermagic on 2014-08-18
Oh Thankyou Sotiris2, It worked...as far as proc, i made the file in videos as you suggested, but so far have not been able to take ownership see below
```
ortermagic@ortermagic:~$ mkdir ~/Videos/Blender
ortermagic@ortermagic:~$ sudo cp /proc/2398/fd/73 ~/Videos/Blender/01-01-BlenderDefaultScene
[sudo] password for ortermagic: 
ortermagic@ortermagic:~$ sudo chown -r ortermagic ~/Videos/Blender
chown: invalid option -- 'r'
Try 'chown --help' for more information.
ortermagic@ortermagic:~$ whoami
ortermagic
ortermagic@ortermagic:~$ 



```
any idea where i'm going wrong?

---

### Post by ubudog on 2014-08-18
Try using chown -R or chown --recursive, instead of (lowercase) -r.

---

### Post by ortermagic on 2014-08-18
Ubudog you nailed it, using chown-R did the trick. thank you and sotiris2 both.
I have a query however...Will the number for firefox in the system monitor change with every access? It seems to be doing that, When I checked the ff later it became 
14238 instead of the original 2398 can you explain why that should be?

---

### Post by ubudog on 2014-08-18
Those numbers are PIDs (process identifiers) used to temporarily identify the process.  Once you close Firefox, its PID is no longer associated with it, and the next time you open it, it will be assigned a different, higher PID until it reaches a maximum value and starts over again.

For more see:
[http://en.wikipedia.org/wiki/Process_identifier#Unix-like](http://en.wikipedia.org/wiki/Process_identifier#Unix-like)

---

### Post by ortermagic on 2014-08-18
Thank you for the clarification and the link. I have successfully acquired one of the videos, all I have to do now is lasso the others in the set :KS

---

### Post by ortermagic on 2014-08-20
I just thought I might as well clarify,
> Since these videos appear to be creative commons , yes there is a way.  Its a bit of hacky way though. I cannot understand why he has not made  them available through a more open platform that itunes.
To the people who helped me, I wish to send a follow up, just to say that I am grateful to you both for the lesson in extracting from "proc" well worthwhile knowledge.
My real reason for posting is to tell you that I emailed Neal and he sent me a direct link for the full set.

---

