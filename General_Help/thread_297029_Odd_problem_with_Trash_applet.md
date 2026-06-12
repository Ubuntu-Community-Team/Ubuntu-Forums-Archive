---
title: "Odd problem with Trash applet"
date: 2006-11-10
forum: General Help
---

### Post by jujoje on 2006-11-10
Hi,

I've got a strange problem with the trash applet on the gnome panel. 

The problem itself is quite simple: when I click on the applet it appears that the entire file system is in the trash. I can browse through it in nautilus and it all appears to go the the appropriate places. It also shows the entire file system in the Trash on the desktop.

However if I go to the .Trash folder in nautilus it is empty: there are no file in is at all. Similarly there are no files in it if I go there by the terminal and do ls -a. Also there are no files in the .Trash folder in the root directory.

So it appears to be empty except if I click on the .Trash icon on the menu bar. I am really very sure that I haven't managed to delete the file system by mistake :) Haven't deleted anything via the terminal and don't use nautilus as root so I've really no idea how it all got there, and if it's really there.

Any advice on what the hell going on here would be appreciated. It's really rather disconcerting to have everything sitting in the deleted items folder.

Julian

---

### Post by jujoje on 2006-11-12
Anybody?

Just to try and explain the problem a bit better:

It seems that the .Trash folder is working as expected; things are getting moved there fine and I can delete them fine. They also appear in the folder shown by the trash applet (trash: apparently). It's just that the trash on the Desktop and the applet are also showing the entire file system as being in there.

It's not fatal since I can delete stuff from the .Trash folder manually, but as I said before it is rather odd and slightly worrying.

Attached some screenshots as my explaination probably isn't particularly clear. One folder is .Trash and the other is the deleted items folder.

Any suggestions as to what's going on would be much appreciated,

Cheers,

Julian

---

### Post by PriceChild on 2006-11-12
Maybe removing the item, and then adding it again by right click>add to panel will reset it all to normal.

---

### Post by jujoje on 2006-11-12
I gave that a go and unfortunately it didn't work; the applet came back the same as before. The other thing I tried was deleting the .Trash folder in my home directory, after which the applet appeared empty until I restarted and the .Trash folder was recreated and the  trash applet once again appeared to have the file system in it.

---

