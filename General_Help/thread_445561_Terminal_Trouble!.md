---
title: "Terminal Trouble!"
date: 2007-05-16
forum: General Help
---

### Post by andhesays on 2007-05-16
Hi there,

I recently installed Ubuntu Studio and I love it. I have Beryl running and I have it dialed in perfectly. My only issue is I can't launch a terminal from the applications menu any more. It used to work fine. Now I have to type ctrl-alt f2 and get back into X Windows with ctrl-alt f2. 

What gives? Anyone have an idea? 

Any help would be appreciated. 

Thanks

---

### Post by Rui Pais on 2007-05-16
hi,
do you have the same problem with other terminals?
I think xterm is installed by default in all Ubuntu version. Check if it works.

If it works, try to launch your terminal (don't know which one Ubuntu Studio uses...) from xterm and see if you got any warnings or errors that can give a clue. 

I had that problem under gnome with gnome-terminal with one version of Edgy (the 32bits i think...) and i remember i could use xfce terminal normally (that have the same funcionality, with very few dependencies of xfce4) and much lighter and faster. 
Maybe you want to give it a try (sudo apt-get install xfce4-terminal).
eterm is another terminal, light and fast, that is independent of gnome and may work when gnome apps have problems.

good luck.

---

### Post by andhesays on 2007-05-16
xterm works. When I run gnome-terminal from an xterm screen, I get the following error: 

\The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


????????????????????????

Thanks for you response..

---

### Post by Rui Pais on 2007-05-16
hi again.
check this launchpad bugs to see if is your case:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

and

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/72956](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/72956)

the 1st seems to propose some solutions or workarounds.

good luck.

---

