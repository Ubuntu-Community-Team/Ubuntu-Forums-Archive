---
title: "[SOLVED] Location of trash in directory structure?"
date: 2008-05-27
forum: General Help
---

### Post by Nameless Neko on 2008-05-27
Somehow, I managed to move a folder to trash where root has ownership of some of the files inside, so I'm stuck with an undeletable mozilla settings folder in my trash bin.  I'd like to get into the trash bin for my regular profile as root so I can delete the folder in question, but I can't figure out where it's at exactly.  Any ideas?

---

### Post by strabes on 2008-05-27
Please search the internet and these forums before asking a question. This question has been asked hundreds of times.

~/.local/share/Trash/files

```
sudo rm -r ~/.local/share/Trash/files/*
```

Be careful with the above command. Paste it in a terminal.

---

### Post by Nameless Neko on 2008-05-27
Thanks, and yeah, my bad about not searching.

---

