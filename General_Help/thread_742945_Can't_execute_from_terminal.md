---
title: "Can't execute from terminal"
date: 2008-04-02
forum: General Help
---

### Post by Bumperklever on 2008-04-02
As a linux noob I installed Ubuntu 7.10 on my new PC yesterday. I got it all to work and as a first step I wanted to install a distributed computing application (Folding@Home).

After I downloaded the files and extracted them to "My Documents" I opened the Gnome Terminal. I used "chmod +x fah6" and and tried to run the program with "./fah6" . That only generates the error "no such directory found" instead of running the program. I got the program running on other linux distros I tried before chosing Ubuntu so I was a bit surprised to see this.

I tried "chmod 777 fah6" to make sure it was not an issue with user rights, and I also tried executing the commands with "sudo". Still no luck.

Can you please help me out, I've no clue what I'm doing wrong. I'm logged in as a "normal" user, not as root.

---

### Post by justleen on 2008-04-02
is it a directory perhaps?
"Normal" extractions would generate a folder containing the files. Did you change into that folder?

---

### Post by Bumperklever on 2008-04-02
Yes, with "dir" I can see the files that were extracted from the archive, so I am in the right directory.

---

### Post by justleen on 2008-04-02
and can you see a file called fah6, or is it fah6+something more?

---

### Post by 3rdalbum on 2008-04-02
What does the following command say:

```
file fah6
```

When you are in the directory that the file is in, of course. It might give you clues as to why it's not working, and it might give us clues too.

---

### Post by mali2297 on 2008-04-02
Do you use the 32bit or 64bit version of Ubuntu? Did you download a compatible version of the program?

EDIT:
Link:
[http://ubuntuforums.org/showthread.php?t=719835](http://ubuntuforums.org/showthread.php?t=719835)
(I knew I had seen this before...)

---

### Post by Bumperklever on 2008-04-02
ubuntu-7.10-desktop-amd64.iso

Is the version I downloaded (64 bit probably since it's compatible with my Core 2 Duo E8400).

I once heard mentioning that you can install 32 bit libraries as well ?? Might this solve my problem ?

---

### Post by mali2297 on 2008-04-02
Well, it did eventually work for the Madman, although it's a bit unclear how he did it. Be persistent.

---

