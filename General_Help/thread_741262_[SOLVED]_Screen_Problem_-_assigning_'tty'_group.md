---
title: "[SOLVED] Screen Problem - assigning 'tty' group?"
date: 2008-03-31
forum: General Help
---

### Post by ilych on 2008-03-31
Hello,

When I run screen with a non-root user in the admin group, I receive the following error:

> Cannot open your terminal '/dev/pts/0' - please check

My problem is also described in this [thread]("http://ubuntuforums.org/archive/index.php/t-90491.html"), where it is suggested

[QUOTE=nagilum]To solve this you can either change the permissions of that file each time you want to start screen or add the other user (for which you call 'su') to the 'tty' group. 'tty' has by default write permission to the /dev/pts/X files.[/QUOTE]

Nagilum's first suggestion works:
> chmod a+rw /dev/pts/0

But that is a temporary fix, and I don't want to type that every single time. So, how do I edit 'visudo' in /etc so that I can add the said admin user into the 'tty' group (which supposedly has default write permission to the /dev/pts/X files), as suggested by nagilum?

This problem occurs only on my VPS, which I have terminal access to (no GUI setup). Since I don't have this problem on any of my home Ubuntu computers, I tried checking 'visudo' in /etc, but I found no lines regarding the 'tty' group.

Any help greatly appreciated!
ilych

---

### Post by ilych on 2008-03-31
Thanks to Sinistrad and soundray on #Ubuntu, I solved my problem.

The user did not have write access to /dev/pts/X, because I was always SSHing to my server as root. I will avoid that in the future and SSH as a user. 

Sinistrad >> it's better to be a user and need root, than to be root and not need 
          it....or something like that ;)  Root is bad, use it when you need and never any other 
          time.

I'll heed the advice. Thanks again to the helpful Ubuntu community!

---

