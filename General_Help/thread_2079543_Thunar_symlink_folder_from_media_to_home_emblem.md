---
title: "Thunar symlink folder from /media to /home emblem"
date: 2012-11-02
forum: General Help
---

### Post by crazyg4merz on 2012-11-02
Recently I've just reinstalled my xubuntu 12.04 with separate /media/budiman partition for my media files and /home partition for my configuration files. I symlinked the folders like videos,musics, etc to my /home partitions. Before that I deleted media folders in /home partitions so I don't get folders already exist problems.
This is how I did that:
sudo chown -R budiman:budiman /media/budiman
sudo chmod -R 644 /media/budiman

The problem is now I've got an error said the folder permission needs to be fixed when I open the permission tab in the folder properties. What's wrong with my commands?

And I proceed to the symlinking process. Did it with:
ln -s /media/budiman/* /home/budiman/

Another problem is thunar recognized the folders as media folders and changed the folder icons like the original icon. But it display an ugly symlink emblem on the folders. How can I remove that emblem?
Please anyone help me. Thanks :-)

---

### Post by crazyg4merz on 2012-11-02
UPDATE:
Ok I've managed to solve the folder permission problem by doing this command:
```
cd /media/budiman
```
```
find . -type d -exec chmod +x {} \;
```
Got this tutorial from google search, those commands mean chmod all directory in there to be executeable because directories are meant to be executeable. Learn that just now :)

Now my question is half solved. I really want to know can I remove that ugly symlink emblem from Thunar? Or is there any other better alternative for Thunar that can do that?
Need some assists from u guy, please. Thanks

---

### Post by crazyg4merz on 2012-11-02
Already 140+ people viewing but no answer. Please at least let me know if my problem is solve-able or no :-(

---

### Post by Toz on 2012-11-02
I don't believe there is a configuration option on thunar to affect the symbolic link emblem display in thunar. 

However, it is just an icon that is overlayed on the folder icon. The icon file name is emblem-symbolic-link.{png|svg} (png or svg AFAICT). It depends on the icon theme that you are using. The following can help locate these files:
```
locate emblem-symbolic-link | grep icon
```
Renaming these files should remove the link emblem.

Note, that this will prevent the symbolic link icon from displaying anywhere in thunar. It will make it difficult to identify which folders are linked and which are real.

------

Example: I use the Faenza icon set. /usr/share/icons/Faenza/emblems lists all available icon sizes:
```
$ ls /usr/share/icons/Faenza/emblems/
16  22	24  32	48  64	8  96  scalable
```
Each folder has a emblem-symbolic-link.png. Renaming this file eleminates the symbolic link graphic.

Before:
[ATTACH]226591[/ATTACH]

After:
[ATTACH]226592[/ATTACH]

What icon theme are you using?

---

### Post by crazyg4merz on 2012-11-03
This is just what I needed. Thanks!
I like changing themes. Now I think I'm gonna remove it from all my themes :-) 
But I think losing on all symlinks are not a good idea. Can I resize the image to smaller icon? so it won't block all the folder view?

---

### Post by pqwoerituytrueiwoq on 2012-11-03
you can use the bind option for mounting and create the link with /etc/fstab so the folders in /home/$USER will appear to be actual folders but be on another partition/disk

---

### Post by crazyg4merz on 2012-11-03
Thanks for the reply pqwoerituytrueiwoq. But does binding means all my folders in /media partitions shown in /home? Including my /.wine folder? How can I do it? Does it means whenever I put files into my /home/budiman goes to my /media/budiman/ partition? Please assist me step by step if u don't mind. I have /home/budiman as my home and /media/budiman/blablabla as my media data. I want that /blablabla can be shown in /home/budiman and whatever I put in /home/budiman/blablabla goes to /media/budiman/blablabla also. Need your help guys. Thanks in advance :-)

---

### Post by oldos2er on 2012-11-03
Please don't bump your post more than once every 24 hours.

---

### Post by sandyd on 2012-11-03
For example, if you have /media/budiman/videos/ (Before doing these steps, you HAVE to rm the links from the home folder first!)

Use
```
mount --bind /media/budiman/videos /home/budiman/videos
```

Instead of linking

---

### Post by crazyg4merz on 2012-11-03
@oldos2r sorry I don't know there's such a rule for bumping. Won't do it again :-) 
@sandyd thanks mate! Will try it soon. I think this question is now solved.
Thanks for helping me guys :-)

---

