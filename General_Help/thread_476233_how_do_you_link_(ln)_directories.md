---
title: "how do you link (ln) directories"
date: 2007-06-17
forum: General Help
---

### Post by Nefarious on 2007-06-17
I set up a lamp and since I'm lazy dont want to leave my home directory to get to where I need to go so I was wondering how you go about hard/soft linking to a directory. ty

---

### Post by arvevans on 2007-06-17
Switch to a terminal screen (the dreaded Command Line Interface) and enter "man ln", use your arrow keys to scroll up/down in a man page, and "q" to exit the man page.

The resultant manual page will tell you all about using hard and/or symbolic links.

Depending on file or directory ownership and permissions, you may have to prefix your "ln" command with "sudo" and provide the administrative password.
_._

---

### Post by Nefarious on 2007-06-19
ehh... doesn't work... actually turns out I have a bad install disk and nothing is working as it should... although my incompetence isn't helping either.

ow well thanx anyways.

---

### Post by unnes on 2007-06-28
Thread hijack: I'm interested in knowing how to link directories too. I have no experience with symbolic links, but would like to link several mounted directories to my home directory (e.g. /mnt/hda1/users/unnes/music mapped to /home/music).

Any tips? I've checked out the** ls** man page, but, like many man pages, it's not entirely clear.

---

### Post by jack@tortuga on 2007-06-29
Try the man page for '**ln**', it should help. It's pretty easy, though. You type:

```
ln -s /path/to/original /path/to/link
```

Remember, a symbolic link ( or 'soft link' ) is just a 'shortcut' to the actual file/directory.


So, with your example, if you want to read/write files to /mnt/hda1/users/unnes/music, but you don't want to leave your home directory, just create a symlink in your home to point to the mounted filesystem:

```
ln -s /mnt/hda1/users/unnes/music  /home/music
```

---

### Post by Qu4k3R on 2007-06-29
Did it "worked" ?

---

