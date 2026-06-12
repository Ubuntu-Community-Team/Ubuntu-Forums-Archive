---
title: "Problem with links on desktop when using gedit and creating backup ( tilde ~ ) files"
date: 2021-05-02
forum: General Help
---

### Post by F W Adams on 2021-05-02
So first I have a text file and create a link to it from the desktop. This works fine.

If I then use that link to access the file ( let's say xxx.txt ) I end up in gedit with the file as expected. Then edit the file and save the edited version. Everything ok, then I have the edited version of the file as xxx.txt and the backup file as xxx.txt~. Also the original link on the desktop points to to the new file as it should.

But here's the problem, ubuntu has now created a new desktop link in addition to the original one pointing to xxx.txt~. With quite a few of these my desktop is getting cluttered up with links that I don't want. I can remove them of course but that's hardly the point, how to stop their creation?

I can't believe that more people don't find this annoying, or is it something that just I have got.

Using ubuntu 20.04.2 LTS

Any help appreciated.

---

### Post by Xian on 2021-05-02
The application will create a backup of a file (if option is enabled) only **within **the directory you are working.
 The backup file has no target location. It is directory specific. 

This holds true even with file links/shortcuts made to an object at a separate location. 

So in your case since you are editing the file _from_ the desktop shortcut the backup file will be saved to the desktop.
If you had previously saved a backup from the original file location then these backups will no longer match.

---

### Post by F W Adams on 2021-05-05
Yes, I can see what is happening. The backup files being in the desktop directory can be lived with but I suppose there is no way to stop the links to them automatically appearing on the desktop screen.

I wish I could get a program to execute from the desktop so I could front end all the file editing but on following several links could not get anything to work, as with many others. On 18.04 it was fine but not on 20.04. This would solve my problem. Suppose I will have to live with it.

---

### Post by Holger_Gehrke on 2021-05-05
What type of link are you putting on the desktop ? There's three types of links: hard links, symbolic links and .desktop files of type "link". With the latter two types programs can tell that these are links and can place their backups with the original files if they make the additional effort to do so. I don't know about gedit since I use XUbuntu which comes with mousepad as it's default editor (and mousepad doesn't seem to create any backup files ...), but both emacs and gvim will put their backups with the original file for symbolic links and .desktop files and Bluefish will do so for a desktop file.

Holger

---

### Post by ActionParsnip on 2021-05-05
Do other text editors do the same. Leafpad for example

---

### Post by F W Adams on 2021-05-05
Couldn't get emacs to work as you stated, perhaps I have misunderstood something.

Well, I had thought that it was the desktop that was not behaving as I would like but then changed my mind a bit and thought maybe replace gedit by emacs. But both gedit and emacs behave in what to me seems a very wrong and identical way. When faced by a link they deal with the link as if it was just a file, update it and make a ~ backup of it in the same directory. Then also update the file being pointed to as well.

Should they not be just reading the link and dealing only with what is pointed to.

This was with hard links, with soft links neither of them read the file linked to.

I enclose my testing in case I have made a mistake.

I'll start another thread to try and get a program written by me to execute from the desktop.

 
felix@felix:~$ 
felix@felix:~$ mkdir tmp2
felix@felix:~$ cd tmp2
felix@felix:~/tmp2$ mkdir xxx
felix@felix:~/tmp2$ gedit xobj
felix@felix:~/tmp2$ ln xobj xxx/lobj
felix@felix:~/tmp2$ ls -l xobj xxx/lobj
-rw-rw-r-- 2 felix felix 9 May  5 14:34 xobj
-rw-rw-r-- 2 felix felix 9 May  5 14:34 xxx/lobj
felix@felix:~/tmp2$ gedit xxx/lobj
felix@felix:~/tmp2$ ls -l xxx
total 8
-rw-rw-r-- 2 felix felix 15 May  5 14:37 lobj
-rw-rw-r-- 1 felix felix  9 May  5 14:37 lobj~
felix@felix:~/tmp2$ ls -l
total 8
-rw-rw-r-- 2 felix felix   15 May  5 14:37 xobj
drwxrwxr-x 2 felix felix 4096 May  5 14:37 xxx
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ emacs xxx/lobj
felix@felix:~/tmp2$ ls -l xxx
total 8
-rw-rw-r-- 1 felix felix 20 May  5 14:39 lobj
-rw-rw-r-- 2 felix felix 15 May  5 14:37 lobj~
felix@felix:~/tmp2$ ls -l
total 8
-rw-rw-r-- 2 felix felix   15 May  5 14:37 xobj
drwxrwxr-x 2 felix felix 4096 May  5 14:39 xxx
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ rm xxx/*
removed 'xxx/lobj'
removed 'xxx/lobj~'
felix@felix:~/tmp2$ ln -s xxx/lobj xobj
ln: failed to create symbolic link 'xobj': File exists
felix@felix:~/tmp2$ ln -s xobj xxx/lobj
felix@felix:~/tmp2$ ls -l -s xobj xxx/lobj
4 -rw-rw-r-- 1 felix felix 15 May  5 14:37 xobj
0 lrwxrwxrwx 1 felix felix  4 May  5 14:42 xxx/lobj -> xobj
felix@felix:~/tmp2$ gedit xxx/lobj
felix@felix:~/tmp2$ emacs xxx/lobj
felix@felix:~/tmp2$

---

### Post by Holger_Gehrke on 2021-05-05
'ln' without the '-s' option creates a hard link. Hard links are indistinguishable from 'normal' file names - as a matter of fact normal file names are hard links, which is the reason hard links can't point to files on other file systems; the second column in the output of 'ls -l' is the number of hard links or names of a file. So it's not surprising at all that programs that create backups will place them in the same directory as the hard link; it's just a normal file name as far as they are concerned.

Symbolic links - created with 'ln -s' are another matter. Those use the space in the inode normally used for the list of blocks of the file to store a string containing the path and name of the file they point to and have a different file type as shown by the 'file' command
```

$ mkdir ~/ttt
$ cd ~/ttt
$ ln -s ~/src/gladetut.py test.py
$ ls -l
drwxrwxr-x   2 holgeh holgeh  4096 Mai  5 18:52 ./
drwxr-xr-x 105 holgeh holgeh 53248 Mai  5 18:51 ../
lrwxrwxrwx   1 holgeh holgeh    28 Mai  5 18:52 test.py -> /home/holgeh/src/gladetut.py
$ emacs test.py  [COLOR=#00ff00]# here the right file was opened by emacs; I added a line with a comment at the end of the file and saved; a later check with less showed that line being there[/COLOR]
$ ls -l ~/src/gladetut.*
-rw-rw-r-- 1 holgeh holgeh 654 Mai  5 18:53 /home/holgeh/src/gladetut.py
-rw-rw-r-- 1 holgeh holgeh 638 Sep 23  2020 /home/holgeh/src/gladetut.py~
$ls -l test*
lrwxrwxrwx 1 holgeh holgeh 28 Mai  5 18:52 test.py -> /home/holgeh/src/gladetut.py

```
So it's just as I said: if you edit a file through a symbolic link, emacs puts the backup with the 'real' file (and names it by appending '~' to its name; actually it moves the original file to the backup name and creates a new file with the original name ...).

I'm really surprised by emacs not reading the symbolically linked file on your system. The connection between a symbolic link and the linked file is handled by the kernel. A program would have to try to do that handling itself and severely mismanage things to get it wrong.

Holger

---

### Post by F W Adams on 2021-05-06
I think I must have made a mistake before over the soft links, now I am getting emacs working the same as you ( what we call properly ) but not gedit, see below. However it does mean that by leaving gedit and going for emacs I can avoid the backups going to ~/Desktop.

So if I can't get my better solution of running a free choice of scripts or executibles on the Desktop I can do that.

```
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ ls -l ~/x*
-rw-rw-r-- 1 felix felix 29 May  6 09:57 /home/felix/xobj
-rw-rw-r-- 1 felix felix 20 May  6 09:54 /home/felix/xobj~
felix@felix:~/tmp2$ ls -l
total 4
lrwxrwxrwx 1 felix felix 16 May  6 09:54 test.py -> /home/felix/xobj
-rwxrwxr-x 1 felix felix 25 May  6 09:57 test.py~
felix@felix:~/tmp2$ emacs test.py
felix@felix:~/tmp2$ ls -l ~/x*
-rw-rw-r-- 1 felix felix 35 May  6 10:01 /home/felix/xobj
-rw-rw-r-- 1 felix felix 29 May  6 09:57 /home/felix/xobj~
felix@felix:~/tmp2$ ls -l
total 4
lrwxrwxrwx 1 felix felix 16 May  6 09:54 test.py -> /home/felix/xobj
-rwxrwxr-x 1 felix felix 25 May  6 09:57 test.py~
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ 
felix@felix:~/tmp2$ gedit test.py
felix@felix:~/tmp2$ ls -l ~/x*
-rw-rw-r-- 1 felix felix 41 May  6 10:02 /home/felix/xobj
-rw-rw-r-- 1 felix felix 29 May  6 09:57 /home/felix/xobj~
felix@felix:~/tmp2$ ls -l
total 4
lrwxrwxrwx 1 felix felix 16 May  6 09:54 test.py -> /home/felix/xobj
-rwxrwxr-x 1 felix felix 35 May  6 10:02 test.py~
felix@felix:~/tmp2$
```

---

