---
title: "How do I open .rar files?"
date: 2006-11-09
forum: General Help
---

### Post by Mooseus on 2006-11-09
I have tried to open .rar files but I can't with archive manager. I was going to try another program - Unace, but I have no idea how to install it because it is in a .tgz file. I can extract the file, but I don't know how to install the program. Is there a command that installs .tgz files?

Thanks

---

### Post by dcstar on 2006-11-09
> **Mooseus said:**
> I have tried to open .rar files but I can't with archive manager. I was going to try another program - Linunace, but I have no idea how to install it because it is in a .tgz file. I can extract the file, but I don't know how to install the program. Is there a command that installs .tgz files?

Thanks

You have to install the **unrar** package, it's in the Multiverse (non-free) Repository (IIRC) so you have to add this to your list (do a search for instructions on how to do this).

I actually installed this just two days ago myself!

---

### Post by Peepsalot on 2006-11-09
Personally I prefer 7zip for all my archiving needs.  It supports pretty much any archive format as far as I know.

```
sudo aptitude install p7zip-full
```

Edit: Well, I think I'm confused here.  7z in windows includes it's own GUI and supports most archives.  However I think the linux version leaves it to other frontend programs like gnomes archive manager to provide the GUI, and in that case only provides 7z functionality.

---

### Post by kedgek on 2006-11-12
hi guys! i'm a newbie so pardon the stupidity.  

i've downloaded and installed the p7zip package.  unfortunately i can't seem to find the program anywhere! how do i use this program to extract my beloved rar files?  desperate...

---

### Post by nix4me on 2006-11-12
install unrar like the other guy said...then double click the rar file.  It will open in archive manager.

nix4me

---

