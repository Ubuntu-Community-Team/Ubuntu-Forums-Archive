---
title: "Location of files that are moved to trash by nautilus with root rights"
date: 2007-01-10
forum: General Help
---

### Post by _asc_ on 2007-01-10
Hello!

A friend of mine opened nautilus from a terminal with root rights. Then he selected a couple of files, right-clicked and moved them to the trash by mistake. The problem is that he could not find his files any more. They are not in the his .Trash directory and there isn't a even .Trash directory in /root.

I have tried this on my machine as well with the same result. I would have expected to find the file in the root's .Trash directory, but this directory does not exist.

Any ideas where these files are located? Could this be a bug which leads to the loss of these files?

---

### Post by CowzRule on 2007-01-10
Open Nautilus as root and browse to the folder "root"
hit Ctrl+h to show hidden files.
Look for folder ".Trash"
If that folder is there, then your file should be there also. If ".Trash" isn't there, then your files were deleted.

---

### Post by aysiu on 2007-01-10
They should be in /root/.Trash/

That's a hidden folder, though, so you may have to press Control-H to see it.

What command did your friend use to open Nautilus from the terminal with root rights? Was it this? ```
gksudo nautilus
``` or something else?

---

### Post by dexter on 2007-01-10
Sort of related question:

Is it possible to recover files that you deleted with the terminal 
- rm file
- mv file1 file2 and overwriting file2 ](*,)

---

### Post by _asc_ on 2007-01-10
[quote="CowzRule"]
Look for folder ".Trash"
[/quote]

The problem is that the /root/.Trash folder does not exist. I have checked with nautilus by pressing CTRL+H and from the command line using ls -la. That is why I'am thinking that this could be a bug, because it should not happen that the files are lost if you move them to the trash. As I have mentioned in my first post I have tried it myself with the same result. We are both running Edgy.

[quote="aysiu"]
What command did your friend use to open Nautilus from the terminal with root rights? 
[/quote]

He used 
```

su nautilus

```

@dexter
AFAIK, there is no way to recover the files if you have deleted them from the command line.

---

### Post by hugh_h_chen on 2008-05-20
old thread, problem must have been solved. update this for anyone like me with the same problem. in 2008 :-)

if you use root right in nautilus, the deleted file is in /root/.local/share/trash, i am using hardy version of ubuntu. go there to restore of delete them for ever.

so each account has it own trash. in the (account name).local/share/trash

---

