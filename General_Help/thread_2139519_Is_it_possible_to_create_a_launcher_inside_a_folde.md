---
title: "Is it possible to create a launcher inside a folder in Gnome 2?"
date: 2013-04-27
forum: General Help
---

### Post by vcrpcant on 2013-04-27
Hi,

Is it possible to create a launcher, inside a folder, in Gnome 2?

When I create a symbolik link and then click on it, Nautilus will show the path of the symlink below the toolbar. But, that's NOT what I want.
I want to click on it and then Nautilus show me the path of the original folder below that same tool bar.

I think it's sort of M$ Windows shortcuts.
After googling a bit, I've seen somewhere that it's possible to create launchers inside folders using nautilus, but I've don't see that when I right-click inside a folder using Nautilus.

I don't want to start a discussion about the pros and cons of symlinks, shortcuts or even hardlinks, that everything on linux is a file, etc.
I just want to know if it is possible or not.

Can anybody shed some light on this, please?

---

### Post by CatKiller on 2013-04-27
Do you mean a launcher or a link? Your post really isn't very clear about what exactly you're trying to achieve. A launcher is just a .desktop file, a text file with a formal structure. You can put them wherever you like.

You can create a launcher to open Nautilus at a particular path if you want.

---

### Post by ajgreeny on 2013-04-27
There will be a **.desktop** fille for almost every application on your machine already residing in /usr/share/applications and you can copy any of those to anywhere else you would like to.

Nautilus does not help in this very much as it calls .desktop files according to the name set in the text, eg nautilus.desktop may be seen in nautilus as **File-manager** or just **Files** but if you use terminal with **ls /usr/share/applications** the proper file name will show and you can then copy with the **cp** command.

---

### Post by CatKiller on 2013-04-27
If it's Gnome 2 you can drag-and-drop from menus and the panel, too.

---

### Post by vcrpcant on 2013-04-27
thanks for the replies

what I'm trying to achieve is this, imagine folders:
 /home/Bob/music/     (this is the "original" folder)
/home/Bob/data/mp3/     (this is the launcher/link/whatever you name it)

when I open folder /home/Bob/music/ I can see in Nautilus toolbar it's path (/home/Bob/music/)

what I want is to open the "launcher/link/whatever you name it" /home/Bob/data/mp3/ so Nautilus send me to /home/Bob/music/ and show it's path (/home/Bob/music/)

I know how to do it in the panel and in the Desktop (create launcher, location)
but I don't know how to do it inside a folder

meanwhile, I'm just creating launchers on the Desktop, then cut and paste inside the folder in question
I wish the option to create launchers existed when I right-click inside a folder using Nautilus

by the way, I'm still on ubuntu 10.04
i believe that that is already possible in latter versions

---

### Post by ajgreeny on 2013-04-27
Sorry, but now you have completely lost me!

Even after your detailed description, I still don't understand what you are trying to do, nor why.

Is the folder **/home/Bob/music/** just a link to folder **/home/Bob/data/mp3/ **or is that the wrong way round?  Where are the actual music files sitting, or have I still not grasped your problem?

---

### Post by vcrpcant on 2013-04-29
> **ajgreeny said:**
> Sorry, but now you have completely lost me!

Even after your detailed description, I still don't understand what you are trying to do, nor why.

Is the folder **/home/Bob/music/** just a link to folder **/home/Bob/data/mp3/ **or is that the wrong way round?  Where are the actual music files sitting, or have I still not grasped your problem?

thanks for keeping up with this:)

ok, let's see if now I can explain better:)

the actual files are in folder _**/home/Bob/music/**_

my goal is, using Nautilus, clicking on folder **/home/Bob/data/mp3/** and having _**/home/Bob/music/**_ opened AND Nautilus showing me the path to _**/home/Bob/music/**_ (this last part is the problem, because if I use a symlink Nautilus will show me the path to the the symlink [**/home/Bob/data/mp3/**] when I wanted to see the path for the target folder instead [_**/home/Bob/music/**_]

If you try it, you'll see

just like I said above, meanwhile I'm just creating launchers on the Desktop
then cut and paste inside the folder in question

but this has one big advantage, which is to get the launcher icon listed in the files group and not in the folders group (which the very handy symlinks don't)

another way of explaining this is:
I want to have some folder "A"
 and several icons/symlinks/launchers/"whatever is the correct name here" spread across the filesystem that when clicked on (using Nautilus) they all open folder "A" 
AND Nautilus shows me the path to folder "A" in it's path toolbar 
AND icons/symlinks/launchers/"whatever is the correct name here" get listed like normal folders by Nautilus

symlinks do all of this, except that Nautilus shows the path to them (and NOT to the target folder they point to) :(

---

### Post by CatKiller on 2013-04-29
Why not just bookmark any folders that you're interested in? That way it'll show up in the Places menu and the sidebar wherever you are in the filesystem.

---

### Post by vcrpcant on 2013-04-29
> **CatKiller said:**
> Why not just bookmark any folders that you're interested in? That way it'll show up in the Places menu and the sidebar wherever you are in the filesystem.

can't do that because they are too many
I've got a personal method of organizing my files and folders which is a litle bit uncommon

---

