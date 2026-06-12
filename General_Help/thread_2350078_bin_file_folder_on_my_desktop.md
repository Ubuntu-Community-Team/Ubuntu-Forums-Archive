---
title: "bin file folder on my desktop"
date: 2017-01-21
forum: General Help
---

### Post by freddyfields on 2017-01-21
Hey all.  Recently i  broke the screen on my laptop., only half worked .  I blindly highlighted and dragged items to left half of screen.  Anyways, got a used laptop and swapped out the harddrives.  On my desktop is a bin file folder.  When rearranging the items, i accidently dropped a desktop folder on bin.  When i open it, theres nothing there.  So what is this folder and what happened to the folder i dropped in it?  I can see a bin when i click my file system folder, but i cant find the missing desktop folder.  Im hesitant to delete cause im in fear it might be important

---

### Post by yancek on 2017-01-21
Not sure I understand your post.  Which directory can you not find?  The one you had on the Desktop?  So what was it?  The bin directory contains binary files which are extremely important and with it, you'll have a difficult time using your computer at all.  A partial list of what it contains:  T[LEFT][COLOR=#242729][FONT=Arial]he shells like bash and commonly used commands like[/FONT][/COLOR]  cp, mv, rm, cat, ls.
[/LEFT]

You would not be able to move or copy and link, file or directory to bin as a normal user.  Not sure from your post exactly what you did?

---

### Post by SeijiSensei on 2017-01-21
It's possible that he's talking about $HOME/bin, where users can place custom binaries.  On a 14.04 machine where I built a copy of ffmpeg from source, the binaries are located in $HOME/bin, and a pointer to that directory appears at the beginning of my PATH. On a vanilla 16.04 machine, I don't have that directory nor the corresponding entry in $PATH.

---

### Post by Impavidus on 2017-01-21
Or he's talking about a folder with a bin shaped icon. That's the trash can, which is often visible on the desktop.

---

### Post by ajgreeny on 2017-01-21
The **/home/username/bin** directory only appears in your pathway (find that with command echo $PATH) if it actually exists; the user has to create it manually as it is not a default folder in any home folder when the OS is installed. However, like yancek I am totally confused by freddyfields's post.

Your only real consolation that I can think of is that the system /bin folder is root owned so you could not have moved it unless you were using root permissions, and I trust that was not the case.
You might, however, have moved the bin folder that was in your home, if you had one, but as long as you did not delete it it will still be lurking somewhere.
Have a look with command ```
find -type d -iname bin
```

---

