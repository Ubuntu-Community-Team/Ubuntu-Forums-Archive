---
title: "Home folder and desktop merged"
date: 2016-05-24
forum: General Help
---

### Post by clrpaolo on 2016-05-24
Hi everyone, I need some help. I have Ubuntu 14.04 LTS and Unity as desktop enviroment. The files and folders that I have under Home are showing up on the desktop, and if for example I delete the Music folder from the desktop, it will also be deleted from the Home folder. If I create a new file or folder in the Home folder it will also show up on the desktop.  In the Home folder there used to be a desktop icon, but now that icon is gone. It's as if the desktop and the Home folder have merged or become the same. 

I also want to add that yesterday I made some directories in the terminal using mkdir, everything worked fine and certainly I didn't make any type of link between the desktop and the home folder. Today as I started my computer I found this problem. Maybe I did something wrong without realising it. 

If anyone knows how I can solve this issue it would be great. Thank you.

---

### Post by howefield on 2016-05-24
If you open the hidden file .bash_history you should see the history of commands that you have used in the terminal. Might help if you copy and paste back here the ones that are relevant to what you did so others have an understanding of what you did.

Open the file manager and press Ctrl + h keys (or from the menu options - view > show hidden files) to show hidden files, you should see .bash_history in there. Double click to open.

---

### Post by clrpaolo on 2016-05-24
Maybe i have clue about what could have gone wrong. Yesterday I also tried the command echo, i was doing an exercise that was on a book (the linux command line). I must have typed a few very simple lines using that command. I think i did everything according to the book, I got the results i was supposed to get. I didn't notice anything wrong but maybe something did go wrong. I am away from my computer right now, I'll do as you asked and show you the history of the commands later. Thank you very much for the help.

---

### Post by oldfred on 2016-05-24
Did you do a move of all the directories?

Post this also:
cd Desktop
ls -l
cd ..
ls -l

---

### Post by grahammechanical on 2016-05-24
Did you use the alias command and make the Desktop folder an alias for the Home folder?

---

### Post by Frogs Hair on 2016-05-24
To look at the user directory confg. open home/hidden folders/.config /user-dirs.dirs . The text file will open in gedit and can be edited.

---

### Post by clrpaolo on 2016-05-24
My work is keeping me busy till late. As soon as i'm back home, I'll check everything. I have been using Ubuntu for around 3 years, I have never had any problem with terminal commands before. 

Though I haven't sorted it out yet I feel so happy to get this response. Thank you people, your help is superb :)

---

### Post by clrpaolo on 2016-05-24
My reply to all of you:

**howefield**: unfortunately the .bash_history file doesn't have any of the terminal commands i used yesterday and i may know why. When the problem showed up i used an application (timeshift) to change the settings of my system back to what they were before the accident, it wasn't successful, and maybe that erased the the recent history.

**oldfred**: I ran the commands you gave me and this is what i got:
```

user@user-Motherboard-H61MAT-A-E:~$ cd desktop
bash: cd: desktop: No such file or directory
user@user-Motherboard-H61MAT-A-E:~$ ls -l
total 40
drwxr-xr-x 13 user user 4096 May 12 11:38 Documents
drwxr-xr-x  3 user user 4096 May 14 21:52 Downloads
-rw-r--r--  1 user user 8980 Apr 14 15:30 examples.desktop
lrwxrwxrwx  1 user user   38 May 19 22:05 Link to Music -> /mnt/01D17DF60EB53B00/Users/User/Music
lrwxrwxrwx  1 user user   41 May 19 22:06 Link to Pictures -> /mnt/01D17DF60EB53B00/Users/User/Pictures
drwxr-xr-x  3 user user 4096 May 19 22:04 Music
drwxr-xr-x  4 user user 4096 May 24 10:42 Pictures
drwxr-xr-x  2 user user 4096 Apr 14 15:40 Public
drwxr-xr-x  2 user user 4096 Apr 14 15:40 Templates
drwxr-xr-x  2 user user 4096 Apr 14 15:40 Videos
user@user-Motherboard-H61MAT-A-E:~$ cd ..
user@user-Motherboard-H61MAT-A-E:/home$ cd
user@user-Motherboard-H61MAT-A-E:~$ clear
user@user-Motherboard-H61MAT-A-E:~$ cd desktop
bash: cd: desktop: No such file or directory
user@user-Motherboard-H61MAT-A-E:~$ ls -l
total 40
drwxr-xr-x 13 user user 4096 May 12 11:38 Documents
drwxr-xr-x  3 user user 4096 May 14 21:52 Downloads
-rw-r--r--  1 user user 8980 Apr 14 15:30 examples.desktop
lrwxrwxrwx  1 user user   38 May 19 22:05 Link to Music -> /mnt/01D17DF60EB53B00/Users/User/Music
lrwxrwxrwx  1 user user   41 May 19 22:06 Link to Pictures -> /mnt/01D17DF60EB53B00/Users/User/Pictures
drwxr-xr-x  3 user user 4096 May 19 22:04 Music
drwxr-xr-x  4 user user 4096 May 24 10:42 Pictures
drwxr-xr-x  2 user user 4096 Apr 14 15:40 Public
drwxr-xr-x  2 user user 4096 Apr 14 15:40 Templates
drwxr-xr-x  2 user user 4096 Apr 14 15:40 Videos
user@user-Motherboard-H61MAT-A-E:~$ cd ..
user@user-Motherboard-H61MAT-A-E:/home$ ls -l
total 4
drwxr-xr-x 23 user user 4096 May 24 21:48 user
user@user-Motherboard-H61MAT-A-E:/home$ 
```

**grahammechanical: **the alias command is a command that i know very well and i'm 100% sure i didn't use it.

**frogs hair: **I have opened the file user-dirs.dir and this is what's in there:
```

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by howefield on 2016-05-24
> **clrpaolo said:**
> 
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

Try changing the line

```
XDG_DESKTOP_DIR="$HOME/"
```

to 

```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

The file should look like..

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

### Post by clrpaolo on 2016-05-24
Thank you howefield, i'm going to do it now and let you know.

---

### Post by clrpaolo on 2016-05-24
Howefield, i did it, restarted the computer and it just worked!!!! :)

And the desktop icon that was also in the home folder and that was gone, now is back. I definitely learned something today. 

I just wished i could understand exactly which command line made the mess. I was doing that just to learn the commands. I was using commands like echo $(ls) or echo $USER that i took straight from the book and retyped just as they were to do as an exercise. I must be more careful in the future.

Anyway it's sorted.

Thank you howefield and thanks to everyone else!! :)

---

### Post by lisati on 2016-05-24
On a side note, Ubuntu, and linux in general, is case sensitive. Ubuntu considers **desktop** and **Desktop** to be different.

---

### Post by clrpaolo on 2016-05-24
Hi lisati, yes it is case sensitive and the command line is also a powerful tool. I must be more careful. At least mistakes make you learn. Since i have been using ubuntu my computer skills have improved a lot, i can do things i never thought of when i was using only windows. I have had some problems these years, not very big problems really. And It's always been good to go through them and learn. It's been worth it thopugh. Hopefully i won't repeat the same mistakes again.

---

### Post by howefield on 2016-05-25
> **clrpaolo said:**
> Thank you howefield and thanks to everyone else!! :)

You are welcome, it is good to learn and try new things, you might have a look at how you can put yourself in a position where borking your installation isn't a show stopper, for instance backing up your home folder, cloning your disk/partition, copies of you important data, ect ect.

---

### Post by clrpaolo on 2016-05-25
I always back up my home folder and my most important files. Cloning is something i haven't done yet and certainly need to. The one thing i have never done so far is the installation. I watched it so many times being done online. I began with 12.04 then upgraded to 14.04, but i have always had somebody else doing it for me. The reality is that i have been playing safe too much! There's a laptop that was bought years ago, the hardware is in good shape and hardly ever used, the problem is Vista which has never worked so well. I strongly adviced not to purchase vista, but i wasn't listened to. Maybe when I have more spare time i should ask the forums, give the specs, see what kind of advice I get, and if possible try the installation there.

---

