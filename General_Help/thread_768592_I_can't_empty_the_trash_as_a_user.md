---
title: "I can't empty the trash as a user"
date: 2008-04-26
forum: General Help
---

### Post by Fazz Munkle on 2008-04-26
And I can't access my user account's trash from "sudo nautilus" or from the terminal.

I had copied a file off of a CD to my user's home folder. Apparently parts of it were locked, no permission to change files. For soem reason I could move it to the Trash, but when I go to empty the trash nothing happens. When I attempt to delete the file within the trash I get this error:

Error while deleting.
There was an error deleting players
Error removing file: Permission denied
Cancel | Skip All | Skip

I don't know where the .Trash folder is for the user's account. I know where the root .Trash folder is, but that has nothing to do with this. And I've found outt hat Nautilus is the only program that knows where the trash is at "trash:///"

I'm getting really frustrated that I cannot just delete these files even from within root. And I'm finding absolutely nothing on this error through Google or on the help pages.

To reiterate: Folder of files in user's Trash. Unable to empty trash or delete files as user. Unable to find user's .Trash folder in root to either change permissions or delete with root privileges. Help, please.

---

### Post by olskar on 2008-04-26
sudo rm -r /home/<your username>/.local/share/Trash/*

---

### Post by sisco311 on 2008-04-26
The Trash folder is a hidden folder(the folders name begins with a period) in your home directory. You can press Ctrl+H in nautilus or select Show Hidden Folder from the View menu to list the hidden folders.

You can open nautilus in the .Trash folder:
```
gksu nautilus ~/.Trash
```

in Hardy Heron the Trash is in ~/.local/share/Trash/files/
```
gksu nautilus ~/.local/share/Trash/files/
```

You can delete the content of the folder from the terminal:
```
sudo rm -fr ~/.Trash/*
```

Hardy Heron:
```
sudo rm -fr ~/.local/share/Trash/files/*
```

---

### Post by Fazz Munkle on 2008-04-26
Oh my god... I can't believe it was that simple. LOL

Thank you so much! :)

---

### Post by SOULRiDER on 2008-04-26
Its good you git it working, could you please mark the thread as solved from the Thread Tools menu? Also, the tags are meant to make searching simple, so a good tag would be "empty trash" and not "8.04" or "solved" :p just a suggestion to whoever added them.

---

### Post by Fazz Munkle on 2008-04-26
Huh, all I see are these options:

Thread Tools
Show Printable Version Show Printable Version
Email this Page Email this Page
Subscription Subscribe to this Thread
Add a Poll Add a Poll to this Thread

Am I missing something? I was looking for the "solved" option, but did the best I could with the tags.

---

### Post by SOULRiDER on 2008-04-26
The option may be elsewhere on these new forums =/

---

### Post by Marcel-X on 2008-09-26
I copied some files from a dvd and deleted them later. Now I'm stuck with some files in the Trash that are read only. They can not be found in ~/.local/share/Trash/files/ or /root/.local/share/Trash/files.

In Nautilus the path trash://// will show them. With "gksudo nautilus" the path trash:/// tells me "/home/<username>/trash: could not be found"

I'm running 8.10 alpha6. Any help will be appreciated.

---

### Post by Steve H on 2008-09-28
> **sisco311 said:**
> The Trash folder is a hidden folder(the folders name begins with a period) in your home directory. You can press Ctrl+H in nautilus or select Show Hidden Folder from the View menu to list the hidden folders.

You can open nautilus in the .Trash folder:
```
gksu nautilus ~/.Trash
```

in Hardy Heron the Trash is in ~/.local/share/Trash/files/
```
gksu nautilus ~/.local/share/Trash/files/
```

You can delete the content of the folder from the terminal:
```
sudo rm -fr ~/.Trash/*
```

Hardy Heron:
```
sudo rm -fr ~/.local/share/Trash/files/*
```


Thanks I'd been having the same problem, just had one folder in the Deleted Items but couldn't get it to be removed.I couldn't find the "hidden" folder for the deleted items either.

The Nautilus shortcut worked a treat!!

---

### Post by eitreach on 2008-10-18
I have had this problem through many releases now. "Empty Trash" just doesn't work - but I have found that shift-delete works. 

How come this has been a problem for so long? It shouldn't take a workaround to use a supposedly native feature in Nautilus.

---

### Post by Steve H on 2008-10-20
It might have something to do with the inherited permissions of the folder before it gets sent to the trash:/// folder.

Just a guess but worth considering...

:D

---

