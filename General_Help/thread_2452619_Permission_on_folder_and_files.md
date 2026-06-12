---
title: "Permission on folder and files"
date: 2020-10-25
forum: General Help
---

### Post by kdmiller45 on 2020-10-25
Ubuntu 20.04 server
apache
php

I am installing a web application in /var/www/aztalker
and when I ftp the folders and file from the application, I assume they have been assigned the needed permissions
I know the aztalker folder should have www-data ownership but what permission would allow me to copy the files and folders and retain the permission assigned to each

as it is now I gave the aztalker  777 so I could copy everything but of course that leave me with having to correct many folders and files permission

Thanks

---

### Post by HermanAB on 2020-10-26
The traditional way to force ownership of files is with the Sticky Bit and SetGID bit:
[https://www.thegeekstuff.com/2013/02/sticky-bit/](https://www.thegeekstuff.com/2013/02/sticky-bit/)
[https://unix.stackexchange.com/questions/165865/forcing-owner-on-created-files-and-folders](https://unix.stackexchange.com/questions/165865/forcing-owner-on-created-files-and-folders)
[https://askubuntu.com/questions/626841/any-way-to-force-files-to-inherit-owner-permissions-from-parent-directory](https://askubuntu.com/questions/626841/any-way-to-force-files-to-inherit-owner-permissions-from-parent-directory)
[https://en.wikipedia.org/wiki/Setuid#setuid_and_setgid_on_directories](https://en.wikipedia.org/wiki/Setuid#setuid_and_setgid_on_directories)

---

### Post by scorp123 on 2020-10-26
> **kdmiller45 said:**
>  as it is now I gave the aztalker  777 so I could copy everything

So you threw security out of the window? Because "777" means that anything and anyone can overwrite the contents in that folder and infect it with viruses, worms and all kinds of malware. Or simply be a mean troll and erase everything in there that is important to you, just because they now can, thanks to your lax permissions and zero security.

That server is begging to be hacked now.

Please never do that. Ever. If you have to give a folder "777" permissions you're doing it absolutely wrong.

---

### Post by kdmiller45 on 2020-10-26
That was just so I could copy whatever to it, do you have the correct way of doing this

Keith

---

### Post by CelticWarrior on 2020-10-26
> **kdmiller45 said:**
> That was just so I could copy whatever to it, do you have the correct way of doing this

Keith

Please read post #2.

---

