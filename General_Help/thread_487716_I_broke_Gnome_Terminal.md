---
title: "I broke Gnome Terminal"
date: 2007-06-29
forum: General Help
---

### Post by mwk001 on 2007-06-29
Hi i'm new to linux and don't know much about it but somehow I broke the Gnome Terminal. However, I am able to use Xterm right now.  Any help would be appreciated.

---

### Post by MCSE_Crossover on 2007-06-29
What do you mean by you "broke" it? It won't launch? Is the text garbled? More detail and we can assist you better! :)

---

### Post by mwk001 on 2007-06-29
it won't launch at all, i've tried to re-install it but it still doesn't work

---

### Post by bronze on 2007-06-29
What happens if you type "gnome-terminal" in xterm, then?

---

### Post by mwk001 on 2007-06-29
it says "The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
(Details: serial 105 error_code 2 request_code 78 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)"

Thanks again for your help

---

### Post by MCSE_Crossover on 2007-06-29
sudo aptitude reinstall gnome-terminal ??

try that...

---

### Post by mwk001 on 2007-07-02
I tried the reinstall that you told me to do but that also did not work, it still says "starting terminal" but it never actually opens. Any other suggestions? thanks again for your help

---

### Post by MCSE_Crossover on 2007-07-02
What were you doing when this actually broke? Can you retrace your steps?

---

### Post by mwk001 on 2007-07-02
from what I can remember it stopped working when my co-worker was installing a windows vm. It might have also been before that when my co-worker was helping me set up my linux box as a domain.

---

### Post by khedron on 2007-07-02
Have you tried to purge it and then install it again? This reloads all the configuration files, so has a better chance of working.
```
sudo aptitude purge gnome-terminal && sudo aptitude install gnome-terminal
```

---

### Post by MCSE_Crossover on 2007-07-02
I believe that gnome-terminal is part of the ubuntu-desktop metapackage, so purging the whole program might remove other stuff as well. If you do go that route make sure you note what other stuff you may have to reinstall.

---

### Post by mwk001 on 2007-07-02
just tried that also, everything purged and then re-installed like it was going to work but gnome terminal still won't open

---

### Post by MCSE_Crossover on 2007-07-02
reinstall? :P

---

### Post by mwk001 on 2007-07-02
sorry i meant I purged it then installed like khedron suggested that I try. it still won't open though. thanks again for your help.

---

### Post by khedron on 2007-07-02
Looks like it might be [this bug.]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232") Are you using Xinerama with the nvidia driver with composite turned on?

---

### Post by mwk001 on 2007-07-03
honestly i don't know if i'm using "Xinerama with the nvidia driver with composite turned on" how do I check for this?

---

### Post by khedron on 2007-07-03
Try
```
pgrep xinerama
```Does it come up with a number, or nothing?

Edit: also, do this:
```
grep 'Composite' /etc/X11/xorg.conf
```Does it  print out anything? If not, look at [this post]("http://ubuntuforums.org/showpost.php?p=1644324&postcount=7") in [this thread]("http://ubuntuforums.org/showthread.php?p=1644324") and do what it says.

Hope this helps - if it doesn't then your problem isn't to do with this bug.

In the meantime you could try using Konsole, KDE's version of gnome-terminal.

---

### Post by mwk001 on 2007-07-09
Just wanted to say thanks for all your help. It turned out I did have that same bug.

---

### Post by khedron on 2007-07-09
Unlucky for you :(. Fortunately there are lots of terminal programs, so you should be able to find a replacement.

(A bit of shameless plugging here: try **yakuake** - it's a console that hides at the top of the screen and rolls down when you press its hotkey. I find it very useful, as it's always there so I don't have to wait for it to start up when I feel the urge.)

It's a KDE application, though, so I'm not sure whether it plays nice with Gnome. Give it a try, anyway.

---

