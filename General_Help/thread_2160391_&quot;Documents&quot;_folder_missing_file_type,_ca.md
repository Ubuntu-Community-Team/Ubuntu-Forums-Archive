---
title: "&quot;Documents&quot; folder missing file type, cannot be opened"
date: 2013-07-06
forum: General Help
---

### Post by Luxx on 2013-07-06
I don't know how long this has been going on. I moved the Documents folder to another folder on my desktop and then later moved it back again.
I also did this with the downloads, Pics, Music folders, etc. All the other folders are fine, but "Documents" can no longer be opened.
I get a message saying the file type is unknown. I tried to right-click and re-associate it with nautilus, but the option is not available. 
I have stuff in there I need to get out. Anybody have an idea how I can open it again?

---

### Post by BreezyBrooke on 2013-07-06
**NEVER MOVE OR REMOVE THE DEFAULT FOLDERS IN HOME!!!! THEY WILL BREAK!!! **

Seriously, when you move the folders, as far as I'm aware, all symlinks to the folders break and apps that rely on those folders will no longer have automatic access to them. so you will have to manually point apps to them. I did that once to the Downloads folder where I deleted it by mistake and ever since nothing would download to it. I had to manually point everything, like Firefox, to the folder every time I downloaded. I have no idea if there is a fix, I ended up reinstalling my computer. So never mess with those folders. You can create shortcuts to them, but never move or delete them.

---

### Post by Irihapeti on 2013-07-06
I would question what the previous poster is saying. I've done a number of installs where initially Documents, Pictures, Music etc did not exist at all and I had to create them manually. I've not had those problems.

I wonder if the OP has not actually copied Documents back to the home directory but is trying to open a symlink that doesn't point anywhere. To check, open a terminal (ctrl-alt-t in most cases, or from the menu) and run the following commands:
```

cd
ls -l
```
The first command makes sure that you're in your home directory. If you know that you are, you can omit it.
(that's lower-case l, not figure 1, in both cases)

What does the line for "Documents" say?

---

### Post by Luxx on 2013-07-06
At the time I was only concerned with copying the content of the folders from another drive. I never imagined the folder would never open again and the contents would be lost!

---

### Post by BreezyBrooke on 2013-07-06
[**[COLOR=#C61919][B]@Irihapeti**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=346442")

I wasn't kidding. True, I may be a fluke case, but I did mess up my home folder once and nothing would automatically use the folders like I demonstrated with Downloads. So I may be wrong here, but I was right in my moment of annoyance and terror that month ago.

---

### Post by Luxx on 2013-07-06
-rwxr-xr-x  1 user user       277 2013-03-10 20:09 Documents.desktop

which seems a bit different from the other folders, which look like this:

drwxr-xr-x  5 user user     28672 2013-07-06 18:23 Downloads
drwxr-xr-x  2 user user      4096 2013-02-24 19:53 Music
drwxr-xr-x  2 user user      4096 2013-03-10 18:19 Pics
drwxr-xr-x  2 user user      4096 2010-05-19 20:11 Videos

---

### Post by Irihapeti on 2013-07-06
> **BreezyBrooke said:**
> [**[COLOR=#C61919][B]@Irihapeti**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=346442")

I wasn't kidding. True, I may be a fluke case, but I did mess up my home folder once and nothing would automatically use the folders like I demonstrated with Downloads. So I may be wrong here, but I was right in my moment of annoyance and terror that month ago.

No problem. I'm not doubting it happened to you, and I can well imagine that it would be extremely scary. I'm just not sure that it's a general principle, that's all. Perhaps I could have worded it better.

Hopefully the OP will come back with the answer to my question, and that will give us a better idea of what might be going on.

---

### Post by Irihapeti on 2013-07-06
Then that's not a folder at all. It's a .desktop file which is usually used for starting up a program. It can be opened in a text editor.

I hope you still have the copy of the documents folder somewhere else, or a good backup, because I think they are going to be your only options.

---

### Post by monkeybrain2012 on 2013-07-06
Open your home directory in Nautilus, either do "ctr h" or go to View > Show hidden files and locate the hidden directory .config, open it and open the file user-dirs.dirs with the text editor (right clicking) You should find the line 

```
XDG_DOCUMENTS_DIR="$HOME/Documents"

```
If instead you have just   
```
XDG_DOCUMENTS_DIR="$HOME/" 
```

It may be the source of your problem, in that case just add back "Documents" as above (without quotations) and see if that helps.

---

### Post by Luxx on 2013-07-06
The entry in the .config was showing just

XDG_DOCUMENTS_DIR="$HOME/"

but changing it to 

XDG_DOCUMENTS_DIR="$HOME/Documents"

had no effect. Still getting the message "Could not display "home/user/Documents".
The file is of an unknown type.

Then there are options [Select Application] & [OK]

There are no applications showing in the menu. I have to go to Other Applications and the only thing I can find there is Files, but that doesn't work.

---

### Post by monkeybrain2012 on 2013-07-06
It seems that your Documents folder is somewhere else rather than in your home. If you have moved it around within your file system (not to an external drive) then you should be able to find it and put it back to your home (now that after editing user-dirs.dirs it is reassociated with nautilus)
Do

```
sudo updatedb
locate Documents
```

The first commad updates your database to reflect recent changes, the second locates the item.

---

### Post by Luxx on 2013-07-07
I see it in my home folder where it belongs, but my computer doesn't. It still thinks it is in a folder on my desktop, where is hasn
t been for weeks. Yet that is where terminal is finding it.

---

### Post by Luxx on 2013-07-07
I see it in my home folder where it belongs, but my computer doesn't. It still thinks it is in a folder on my desktop, where is hasn
t been for weeks. Yet that is where terminal is finding it.

---

### Post by Luxx on 2013-07-07
My computer thinks my Documents folder is a desktop configuration file. I found another folder, Examples, that it thinks is a desktop configuration file as well, but I can still open that one and access the files inside.

---

### Post by mc4man on 2013-07-07
Try opening this Documents.desktop in a text editor like gedit.  If so what does the Exec= line say (if anything

---

### Post by efflandt on 2013-07-07
Maybe instead of copying the ~/Documents/ directory to your desktop you only created a "Documents.desktop" link to your Documents directory. However in X that would just show "Documents" (or whatever Name= in that file), not the ".desktop" extension. Look at that contents of Documents.desktop with a text editor and see if that gives any clue where your Documents directory went. Or you can install "Main Menu" (alacarte) and open .desktop files with that.

Did you delete your Documents directory after you "thought" you moved it and did you empty your trash since you did that?

---

### Post by Luxx on 2013-07-13
Well, what's confusing me is that I dragged it. I didn't copy and paste it. When I dragged it, there wasn't one left behind to delete, yet what I thought was my folder is just a link and the folder seems to be gone. I have no idea what happened to it. I created another one but as far as the stuff I had in the old folder, I guess sometimes you just have to start from scratch.

Thank you for trying to help me sort it out.

---

