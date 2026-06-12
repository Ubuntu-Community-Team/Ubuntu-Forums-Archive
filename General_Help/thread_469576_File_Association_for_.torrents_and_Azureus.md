---
title: "File Association for .torrents and Azureus"
date: 2007-06-10
forum: General Help
---

### Post by Keshyden on 2007-06-10
I have been googling for a while now and I cannot seem to find a way to do this. I have set .torrent files to open in Azureus, but when I open one (clicking or via Firefox), Azureus opens but it does not give the download box. It just opens. Any help would be great!

Thanks. ;)

---

### Post by zvacet on 2007-06-10
Torrent file>properties<open with>Azureus

---

### Post by Keshyden on 2007-06-10
> **zvacet said:**
> Torrent file>properties<open with>Azureus

I have done that. It only opens the Azureus program but Azureus does nothing with the torrent.

I am using the version that came with Automatix if that makes any difference.

---

### Post by Septicaemia on 2007-06-29
I'm having the same problem. So freaking annoying! If anyone has a fix please post it!

---

### Post by MCSE_Crossover on 2007-06-29
I have read and experienced myself nothing but problems with Automatix. I would uninstall Azureus and install it manually (or with synaptic). I would recommend using Automatix. It makes future upgrades not so good.

sudo aptitude purge azureus && sudo aptitude install azureus

---

### Post by jasonfriend on 2007-06-30
hi, i'm new here,

but i figured this out. i did this:

1. installed azureus through automatix
2. went to "Edit Menus" to find out path for Azureus
3. the path was '/opt/azureus/azureus"
4. right-clicked .torrent file > Properties
5. went to "Open With" tab
6. click "Add"
7. at the bottom, choose "Use a custom command"
8. enter "/opt/azureus/azureus"
9. Click "Add"
10. back in "Open With" tab, select "azureus" radio button
11. Click "Close" (File Properties will close)
12. double-click torrent file
13. enjoy!

hope this helps

i switched to Ubuntu Linux just a week ago, so expect me here a lot more often, we can help each other out :D

---

### Post by Zer0Nin3r on 2007-06-30
The download dialog box isn't behind the program itself is it?  Perhaps you may have to move or minimize a window to get to it.

---

### Post by jasonfriend on 2007-07-05
> **Zer0Nin3r said:**
> The download dialog box isn't behind the program itself is it?  Perhaps you may have to move or minimize a window to get to it.

i don't think so,... at least not for me back when i had the problem...

---

### Post by Prisma on 2007-07-08
> **jasonfriend said:**
> hi, i'm new here,

but i figured this out. i did this:

1. installed azureus through automatix
2. went to "Edit Menus" to find out path for Azureus
3. the path was '/opt/azureus/azureus"
4. right-clicked .torrent file > Properties
5. went to "Open With" tab
6. click "Add"
7. at the bottom, choose "Use a custom command"
8. enter "/opt/azureus/azureus"
9. Click "Add"
10. back in "Open With" tab, select "azureus" radio button
11. Click "Close" (File Properties will close)
12. double-click torrent file
13. enjoy!

hope this helps

i switched to Ubuntu Linux just a week ago, so expect me here a lot more often, we can help each other out :D

thanks for the info. But you have to do that every time you want to open a torrent file and that is not practical. however it did work. :) i hope that ubuntu and gnome developers will fix this soon. it looks like this issue is due to gnome's absurd inability to let you choose defaults applications for certain file types.  :rolleyes:  absurd, considering we are living in 2007 and is the most basic feature other operating systems already have.

---

### Post by jasonfriend on 2007-07-08
> **Prisma said:**
> thanks for the info. But you have to do that every time you want to open a torrent file and that is not practical. however it did work. :) i hope that ubuntu and gnome developers will fix this soon. it looks like this issue is due to gnome's absurd inability to let you choose defaults applications for certain file types.  :rolleyes:  absurd, considering we are living in 2007 and is the most basic feature other operating systems already have.

Glad it helped:)
From what I know, you don't have to do it everytime, the association is not for the specific torrent file, but for the ".torrent" extension (at least that's how it's working on mine)

---

### Post by jasonfriend on 2007-07-09
just a note...

i will be posting in the name of "jasonmeansfriend" from now on...

---

