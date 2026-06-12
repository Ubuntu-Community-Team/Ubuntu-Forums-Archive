---
title: "Changing Hard Drive Owner"
date: 2007-08-17
forum: General Help
---

### Post by Chuckles8732 on 2007-08-17
Hi,

I am trying to create and delete files in my /usr/share/games folder(and other places), but the computer tells me I'm not the owner of the hard drive, that "root" owns it. I did some research, and a thread in another forum (well, I think it wasn't ubuntuforums) suggested changing root's password and logging in as root to make these changes. It's not convenient to have to do this to change files, but it was the only thing I could find. When I tried to log in as root, the computer told me that root is not allowed to log in from the regular login screen. (You've probably guessed by now that I just got Ubuntu (6.06 LTS), and am completely new to Linux.) I would like to actually change ownership of the drive to my user, but I don't know if i can follow a bunch of terminal commands which I'm sure I'm bound to get in reply. Oh, I guess i should mention the whole reason for this is to put .wad files in for prboom. I'm not sure what other info to put in, so I'll leave it at this for now. Please help!

---

### Post by kellemes on 2007-08-17
Use sudo.. it'll ask for **your** password.

"sudo whateveryouwanttodo"

---

### Post by Chuckles8732 on 2007-08-17
> **kellemes said:**
> Use sudo.. it'll ask for **your** password.

"sudo whateveryouwanttodo"

The only problem with that is that I don't know any terminal commands:(. I read that sudo lets you do anything to your computer, but I don't know how to move files using terminal.

---

### Post by merlinus on 2007-08-17
```

gksudo nautilus

```

will open nautilus (graphical file manager) with root privileges.

Be careful, though, because it will be easy to fry your system.

-merlin

---

### Post by Chuckles8732 on 2007-08-17
Thanks, I can move files all I want now. Even though I still can't get the normal Doom 2 wad to run in prboom :(

---

