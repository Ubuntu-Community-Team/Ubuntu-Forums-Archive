---
title: "$PATH differs with launch from menu vs. terminal"
date: 2007-05-29
forum: General Help
---

### Post by therealbrewer on 2007-05-29
I'm running Photran (fortran IDE) with Eclipse and the Intel Compiler for Linux. At compile time, Photran calls make which then calls ifort (Intel fortran compiler), so the compiler location needs to be on the path. Therefore I set the path in .bashrc by appending this:

source /opt/intel/fc/9.1.045/bin/ifortvars.sh
source /opt/intel/idb/9.1.045/bin/idbvars.sh

So now if I launch Photran from a terminal, make has no problem finding ifort. Next, I created a launcher like this:

Right-click Applications -> Edit Menus -> Programming -> New Item ->
Icon: /usr/lib/eclipse/icon.xpm
Name: eclipse
Comment: Launch eclipse
Command: eclipse

Now, however, when I use the launcher, make craps out and reports that it can't find ifort. If I then echo the $PATH from within Eclipse (i.e. in the Eclipse console), I see that the path only includes the default path, but not the /opt/intel/... stuff.

So, my questions are:

1) Are the .bashrc environment variables only relevant or applied when programs are launched from a terminal?

2) What is the correct way to set the path for a program launched from the menu? Should I use .profile, or /etc/.profile, or is this a design bug?

THANKS!

---

### Post by Blender on 2007-05-29
I have observed similar behavior, and while stupid, I guess there is a reason behind that. Or could really be a bug. Don't know, but I definitely don't like it :(

I'd suggest you write a script that does what you want and create a launcher to that script.

---

### Post by stylishpants on 2007-05-29
It is possible that your problem would be solved just by logging out and then logging in again.

In some cases it seems like there is a shell that gets started invisibly when you log in from your login manager, which is then used to start other processes (such as menu commands.)  Changes to your .bashrc are not seen by this shell, because it has not been restarted or had a 'source ~/.bashrc' command.

I'm not sure if this is actually how it works, but I have seen strange behaviour that fits this hypothesis.

---

### Post by therealbrewer on 2007-05-29
Well I guess I forgot to mention that logging out/logging back in doesn't help, nor does CTRL-ALT-BACKSPACE, nor does rebooting...

but thanks for the suggestions

---

