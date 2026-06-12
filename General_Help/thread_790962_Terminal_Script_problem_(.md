---
title: "Terminal Script problem :("
date: 2008-05-11
forum: General Help
---

### Post by dudeman123 on 2008-05-11
Hello everyone, I am new!

Ok so now my problem:

I have made a script to uninstall windows service pack 3 from ubuntu.
(here it is)
[http://rafb.net/p/jnsI1586.html]("http://rafb.net/p/jnsI1586.html")
(It's a lot of code)

and when I run/execute it, it says:
> rm: cannot remove `/media/HP_PAVILION/WINDOWS/ServicePackFiles/i386/agt0406.dll\r': No such file or directory
rm: cannot remove `/media/HP_PAVILION/WINDOWS/ServicePackFiles/i386/agt0406.hlp\r': No such file or directory
rm: cannot remove `/media/HP_PAVILION/WINDOWS/ServicePackFiles/i386/agt0407.dll\r': No such file or directory
rm: cannot remove `/media/HP_PAVILION/WINDOWS/ServicePackFiles/i386/agt0407.hlp\r': No such file or directory

On and on like that. There is no "\r" in my script, so why is it there? Thank you.

---

### Post by dudeman123 on 2008-05-11
never mind I have fixed it by using

chmod a+x SCRIPTNAME

then executing it.

---

