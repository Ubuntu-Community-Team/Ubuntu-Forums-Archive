---
title: "How to create new symlinks in Lubuntu?"
date: 2013-08-30
forum: General Help
---

### Post by momist on 2013-08-30
This should be easy, and obvious.  However, I can't seem to find a quick and easy way to create new symlinks in Lubuntu.  PCManFM doesn't offer a symlink option in the right click thing, and I've never done it any other way before.

Thanks for any help you can give!

---

### Post by oldfred on 2013-08-30
I use Ubuntu, but since command line I would expect it to work.

I have mounted my data partition at /mnt/data and have a folder named Music. If I run it before renaming the current music folder it gives an error. Or you just can use a different name like music.
 #from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music

I have a bunch of folders so I do them all:
      
 #Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by vasa1 on 2013-08-30
> **momist said:**
> This should be easy, and obvious.  However, I can't seem to find a quick and easy way to create new symlinks in Lubuntu.  PCManFM doesn't offer a symlink option in the right click thing, and I've never done it any other way before.

Thanks for any help you can give!
As you've noticed, PCManFM doesn't allow for creating logical links. You have to use the terminal:  
```
ln -s "/home/vasa1/something/something_else/file_or_folder_name" "/home/vasa1/Desktop"
```What this does is to create a shortcut to "file_or_folder_name" on the desktop with the same name by default. I think you have to provide the full path. Avoid `~`. And both paths are enclosed in quotes to prevent funny things happening if there are spaces in the path. If you're sure there aren't going to be spaces, the quotes omitted.

---

### Post by Dennis N on 2013-08-30
> **vasa1 said:**
> As you've noticed, PCManFM doesn't allow for creating logical links. You have to use the terminal:  
```
ln -s "/home/vasa1/something/something_else/file_or_folder_name" "/home/vasa1/Desktop"
```What this does is to create a shortcut to "file_or_folder_name" on the desktop with the same name by default. I think you have to provide the full path. Avoid `~`. And both paths are enclosed in quotes to prevent funny things happening if there are spaces in the path. If you're sure there aren't going to be spaces, the quotes omitted.

Just to clarify if link name is to be different:

[B]ln -s link-target link-name
[/B]
The link name is second, the target is first. Specify the link name if you want a different link name from the file name. If both target and link are in the working directory, you can omit the paths and just use the target file name and link name.

If a link already exists, and you want to point it to a new target, add the option -f

**ln -sf new-link-target link-name**

Example:

[B]ln -sf seaside.jpg lubuntu-default-wallpaper
[/B]
retargets a link named lubuntu-default-wallpaper to point to seaside.jpg. In this example, the target and link would have to exist in the working directory.

Hope that helps.

---

### Post by vasa1 on 2013-08-31
> **Dennis N said:**
> .... So, in your example the link would be created in your home folder **and named Desktop**. ....
Hi, I tested the code before posting and I don't get a link called "Desktop". I get a logical link to the folder specified to the first part of the code. After reading your post, I tested it again. For example:
```
[09:54 AM] ~ $ pwd
/home/vasa1
[09:55 AM] ~ $ ln -s /home/vasa1/Pictures/Colors/html_colornames.asp_files /home/vasa1/Desktop
[09:56 AM] ~ $ cd Desktop
[09:59 AM] ~/Desktop $ ls -l
total 23784
-rw------- 1 vasa1 vasa1    21393 Aug 30 17:01 axisdirect-report.ods
-rw-rw-r-- 1 vasa1 vasa1   248171 Aug 21 22:08 CoromandelIntl21082013.pdf
drwxr-xr-x 2 vasa1 vasa1     4096 Jul 26 17:00 Daring Fireball: Markdown Syntax Documentation_files
-rw-rw-r-- 1 vasa1 vasa1    40286 Jul 26 17:00 Daring Fireball: Markdown Syntax Documentation.html
-rw-rw-r-- 1 vasa1 vasa1  8634114 Aug  7 15:48 Getting Started with Ubuntu 13.04.pdf
-rw------- 1 vasa1 vasa1  3631500 Aug 18 12:58 HelenForrest_Somesundaymorning
lrwxrwxrwx 1 vasa1 vasa1       55 Aug 31 09:56 html_colornames.asp_files -> /home/vasa1/Pictures/Colors/html_colornames.asp_files
-rw-rw-r-- 1 vasa1 vasa1 11643448 Aug  4 11:01 issue75_en.pdf
-rw-rw-r-- 1 vasa1 vasa1    88986 Aug 15 17:43 NineGARPstocks13082013.pdf
-rw-rw-r-- 1 vasa1 vasa1     2316 Aug  3 17:28 pwds - Sheet1.txt
drwxrwxr-x 2 vasa1 vasa1    12288 Aug 20 16:14 tempp
drwxrwxr-x 2 vasa1 vasa1     4096 Aug 24 11:58 YouTube
[10:00 AM] ~/Desktop $ 

```
So the code works for me. **There's one thing I forgot to mention and it maybe important given that OP specified PCManFM.** I don't use PCManFM as file manager or to manage my desktop. I use Thunar and xfce (on Lubuntu 13.04) as described in [http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how](http://askubuntu.com/questions/73017/thunar-as-default-file-manager-in-lubuntu-11-10-how) .

But I think making a logical link from a terminal has more to do with CLI than the "desktop" so I would have thought the code would be applicable even to a vanilla Lubuntu (with PCManFM). I think that I did check the code before switching to Thunar/xfce and it worked.

---

### Post by Dennis N on 2013-08-31
Tried:

dn@Roxanne:~$ ln -s ~/Desktop/secpanel.jpg ~/

and this created link secpanel.jpg in home folder, so you are correct! I was unaware of that auto-name option. My apologies. I will edit the post to reflect that.

Now fixed.

---

### Post by momist on 2013-08-31
Thanks, oldfred, vasa1 and Dennis N for helping me out with this.  Yes, the command line works for me, although to copy symlinks for several random files from various places into my, "LinksToWallpapers" folder, is a chore doing it that way.  What a pity that PCManFM doesn't have the right click shortcut, it would be so much easier.  I'll have to bookmark this solution though, as I will never remember the detail when I need to do it again, months down the line.

Problem solved, and thank you all.

---

### Post by danbh on 2014-07-27
Use drag and drop with Shift+Ctrl to create symlinks on lubuntu.

---

### Post by vasa1 on 2014-07-27
I have PCManFM 1.2.0 which is the default file manager in Lubuntu 14.04. Select a file in the file manager, click **Edit** and look for **Create Link...** .

---

