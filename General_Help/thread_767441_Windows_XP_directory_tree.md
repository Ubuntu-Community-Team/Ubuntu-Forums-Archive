---
title: "Windows XP directory tree"
date: 2008-04-25
forum: General Help
---

### Post by gobuntu on 2008-04-25
Dear friends,

I use Ubuntu and like it a lot.

But I have left my Windows XP data directories as they were before the installaion. 

Those directories, of course can have several levels of subdirectories (folders and subfolders).

Now, in Ubuntu, I have created Links (shortcuts) to specific subfolders, for directly going to them by clicking an icon. It does work.

HOWEVER, one functionality that seems to be lacking is that when I use the UP arrow of the file-browser window, the UP arrow DOES NOT really climb-me up the  Windows XP directory tree, but instead I quickly end-up in My Ubuntu Desktop.

Actually, there is no File-Browser DOWN Arrow. There are other two arros called Back and Forward.

So, obviously, their use is of the arrows is functional for other than what I would hope it would, which is CLIMBING a directory tree up/down, that is because I don't really want to create too many short-cuts (one for each folder), because I know my file structure contents.

In Windows XP, there is the functionality that I believe is what I would like to have in Ubuntu, concerning the use of such arrows.

We would need then a Down-Arrow, and the UP-arrow would climb-up the tree, and the DOWN-arrow, of course, would climb-down.

I realize that, since the whole drive of XP is mounted unto the Linux file structure, I would eventually end-up in the Media folder of Ubuntu.

But this is not like that.

If there's a way I can obtain this sought-after functionality, please do advise.

Otherwise, does posting here lead to some investigation, and possible incorporation of this functionality by the develpers?

Or where should I post this for consideration?

Thanks!

---

### Post by ryanhaigh on 2008-04-27
This is because the link you are using is not the same as a shortcutin xp, its a symbolic link which basically acts like the 'shortcut' IS the file/folder it is linked to. So as far as nautilus knows UP the directory tree is back to where the symbolic link is.

For your purposes you probably want to make a launcher that opens nautilus at the location you want. This way the navigation you want to use will work as it does in xp. Right click on the desktop>create launcher and enter ```
nautilus /path/to/folder/you/want/to/open 
``` as the command, call it whatever you want.

---

### Post by gobuntu on 2008-04-27
Thank you very much, Ryan.

I believe what you explain and recommend will solve the problem.

I'll try it and report back if not so.:)

---

### Post by gobuntu on 2008-04-27
Hi again, friends.

Yes, creating a launcher as said by Ryan above does provide the functionality I was after.

I am replacing my links with launchers now.

ONE THING, though, the links don't want to move to the trash, so as to delete them, for I won't need them with the launcher.

So, how to delete the links (symbolic links to folders)?

Thanks!

---

### Post by ryanhaigh on 2008-04-27
Just use shift+delete, it will bypass the trash and completely remove the link. Works for all files as well as working on windows.

---

### Post by gobuntu on 2008-04-28
Thanks Ryan,

That way to delete the symbolic link worked.

I has to be 'selceted'first and appear highlighted, which does takes two steps: RightClick, and then Click elsewhere to vanish the usual Menu one gets whenever RightClicking on an object.

Also, needless to say, I have to be careful with this so as not to permanently delete something irrevocably.

I still wonder, though, what conditions need to be met to be able to Delete a symbolic link, as usual.

Probably being SuperUser?

But then the question arises, how come then I can delete it by the technique you described, without being SuperUser, or using sudo?

Thanks!

---

### Post by ryanhaigh on 2008-04-28
You should just be able to select it using the left click, unless you have your system setup to open things with one click, in which case you should be able to drag a selection rectangle around it.

---

### Post by gobuntu on 2008-04-28
Hi again, dear Ryan.

Actually, LeftClick OPENS the link, and RightClick OPENS the menu of options for the item, such as "Properties".

By "OPENS the link" I mean it actually opens the folder to which the link applies.

I don't recall having setup any special behavior, but I will check that out.

Anyhow, your tip of drawing a rectangle around the item to select is great. i don't even have to draw the entire rectangle: just hinting it does the job.

Many thanks!

---

