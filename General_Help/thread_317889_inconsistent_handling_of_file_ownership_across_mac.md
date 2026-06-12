---
title: "inconsistent handling of file ownership across machines"
date: 2006-12-13
forum: General Help
---

### Post by madmaxx on 2006-12-13
Hi

I use an external USB drive (ext3) for backups and want to recover some
files from the laptop onto the desktop. The files are owned by my laptop login 'laptop'. -- To not mess private and business data on my desktop, I set up an additional user called 'private' to put the files there.

When I connect the USB HD while logged in as 'private', the files from the HD show up as owned by the original user 'laptop', which at first sounded reasonable to me. So you would have to do all the chown,chmod stuff to make them usable under 'private'. Fine, BUT...

On my friend's desktop (he's on Dapper, I am on Edgy) the exact same files from the HD show up as if owned by him/under his login 'friend'! And he directly access them and everything...

I am puzzled. :-k 

Q1: Why is there a difference in ownership for the same files connected from an external drive to different machines?

Q2: What should be the normal behavior? 
a) files retain original ownership wherever, or 
b) files get ownership from currently logged-in user, machine-independent?

Q3: Where can I change this behavior of the system?

Thanks a lot for your help!
madmaxx

---

### Post by bernied on 2006-12-13
File ownership in a filesystem is recorded by number, not by name. Have a look at all your users in /etc/passwd (I've shown my own user record as an example, not from a ubuntu machine):
```
$ sudo cat /etc/passwd
.
.
bernie:x:1001:408::/home/bernie:/bin/bash
.
.
```so bernie is my username, x means the password is encrypted in the /etc/shadow file, 1001 is my user ID, 408 is the only group I am in (you should have more than this), then there is my home directory and my default shell.

Generally (if i remember correctly), the first user on a ubuntu system will get the number 1000. So if you save a file in an ext3 filesystem, then move that file to another system where user 1000 has a different name, then they will be the owner. This arrangement was clearly not designed for detachable file storage.

---

### Post by madmaxx on 2006-12-14
Thanks a lot for the detailed explanation, Bernie. Much appreciated.
Still I find it a somewhat irritating arrangement that different
user names on different machines might just be allowed to access
(own) your files. As you said, not designed for the USB age. ;) 
madmaxx

---

### Post by bernied on 2006-12-14
As a general rule, if someone has physical access to a storage device, they can read/write to it. The only thing you can do for physical security is encrypt the data, but even that doesn't stop them from writing over the top of it.

BTW, I was wrong about the group thing. That group is my main group, but I am in others, as defined in the /etc/group file.

---

