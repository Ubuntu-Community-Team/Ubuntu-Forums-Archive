---
title: "Moved the home directory"
date: 2006-12-18
forum: General Help
---

### Post by final_transit on 2006-12-18
Hi,

Thru the graphical interface, System > Administration > Users and groups, I changed the properties for the account I was logged in.

I changed home directory from "/home/xyz" to "/media/sda2/xyz"

Now I cant login to GUI, and  there is no root account too.

How do I fix this?
Thanks in advance :)

---

### Post by Irony on 2006-12-18
This is just a guess but if you can access your /etc/passwd file via a live CD you should find a line that looks like;

[PHP]username:x:1000:1000:realname:/home/username:/bin/bash[/PHP]

Presumably if you changed home it will look like;

[PHP]username:x:1000:1000:realname:/media/sda2/xyz:/bin/bash[/PHP]

So change it back.

---

### Post by Dubbayoo on 2006-12-18
login to the cli and make sure the perms are the same on both.

---

### Post by final_transit on 2006-12-18
Hey Irony and Dubbayoo!

Thanks for the solutions! it worked.

1. changed the perm to 777 for editing the passwd file
2. edited using vi (used it for the first time)
3. chmod back

sweet. thanks again,
Namaste.

---

### Post by final_transit on 2006-12-18
> **Irony said:**
> This is just a guess but if you can access your /etc/passwd file via a live CD you should find a line that looks like;

I tried doing that, but I couldnt mount the hd at all !

Although the problem was solved (using vi), can you tell me how to access the hard disk from the live cd?

cheers

---

### Post by Irony on 2006-12-19
Right click on the desktop and choose create new folder.

Then in terminal;

*Applications > Accessories > Terminal*

Then paste in;

[PHP]sudo mount /dev/hda3 /home/username/Desktop/nameoffolder[/PHP]

Where hda3 is whatever your actual partition is and username is probably ubuntu on a live CD.

Now look in the folder and you should see your files.

Now do in terminal;

[PHP]gksudo gedit /home/username/Desktop/nameoffolder/etc/passwd[/PHP]

This will open the password file.

---

