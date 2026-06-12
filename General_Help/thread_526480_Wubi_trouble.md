---
title: "Wubi trouble"
date: 2007-08-15
forum: General Help
---

### Post by tone3p on 2007-08-15
Hi there.

My first post here...

I installed Ubuntu 'via' Wubi with Win XP as a host
which went fine and was using it for a week or more, 
but then it started NOT to boot - only this message 
is that pops up:

[B][COLOR="Blue"]Find --set -root --ignore -floppies /wubi/boot/grub/menu.lst
Error 17: File not found[/COLOR][/B]

Would appreciate a solution...  :confused: 

Thanks for any answer.

tone3p

---

### Post by dougfractal on 2007-08-15
are these any help
[http://ubuntuforums.org/showthread.php?t=522572](http://ubuntuforums.org/showthread.php?t=522572)
[http://ubuntuforums.org/showthread.php?t=522573](http://ubuntuforums.org/showthread.php?t=522573)

---

### Post by Johnny K on 2007-08-15
I had the same problem. I read somewhere that defragmenting the drive that Wubi is on might help. It didn't work for me, but it's worth a shot.

If you can't get Wubi to work, try [Unetbootin](http://lubi.sourceforge.net/unetbootin.html). It worked for me when Wubi wouldn't. Just make sure you read everything very carefully. There's a point where it asks you how to install it. You'll want to install it on its own partition (I think it's the first choice when you get to that screen). Be very carefully not to tell it to "use whole disk" or anything like that, because doing so will wipe out Windows and all your files. It's probably a good idea to back everything up beforehand, just to be safe.

If you're unsure about something while setting up UNetbootin, just let me know.

---

