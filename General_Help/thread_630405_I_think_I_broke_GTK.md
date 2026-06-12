---
title: "I think I broke GTK"
date: 2007-12-03
forum: General Help
---

### Post by kyp4 on 2007-12-03
I am still pretty new to Ubuntu/Linux so I am hoping that my problem has a relatively simple solution. I recently installed Gutsy and all was well and I installed many applications and libraries. Most recently I am making my first attempt at working on an open source project and so I got the source code for gnome-games but in the process of setting things up I seem to have broken GTK and can no longer run any GUI program that uses it. I am not sure exactly what it was I did that broke things as I only discovered the problem after doing a bunch of things. Here are the things I have done:

Downloaded code for:
gnome-games
gnome-common
glib-2.2.3

I then followed the install process for those projects (./autogen.sh, ./configure, make, make install) However I may have instead installed gnome-common and glib from synaptic, I can't remember. I also think I did a apt-get build-dep for gnome-games. Presently they all build fine except gnome-games, in which I get many compilation errors, but I am not concerned about those at this point, only getting things running again. Anyways I get the same error anytime I try to run a GTK application:

symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled

I assume this is some version issue with libgtk or libglib. I have tried to upgrade/reinstall these libraries from apt-get (command line because I cannot start synaptic because it aparently uses GTK), but it just says I have the latest version so nothing needs to be done. I have searched around the internet for this problem but have found nothing useful or that applies.

Ideally I'd like to get to the point where I can tinker with the gnome-games code without disrupting the installs of other apps, but right now I am just concerned with getting GTK to work again since I can't even use Firefox! Any help would be greatly appreciated.

---

### Post by kyp4 on 2007-12-04
OK, after about 8 hours of internet searching and experimentation I finally figured out what the problem was and how to fix it. I am quite relieved that I did not have to resort to reinstalling Ubuntu and I actually learned a lot about how Linux handles libraries and packages in the process.

The problem was that in configuring and compiling various libraries in order to tinker with gnome-games (such as gnome-common, glib, and gtk) I added a bunch of shared libraries to /usr/local/lib and these libraries were older and/or not compatible with other already-installed gtk components. Ubuntu apparently loads first into its dynamic linker cache those libraries which appear in /usr/local/lib and so those (incorrect) versions of the libraries will be used even if other (correct) versions of the same libraries exist in /usr/lib. As such installing/reinstalling the libraries with apt-get updates only the libraries in /usr/lib, which aren't used anyway. To compound the problem the library that was reported to be causing the problem (which varied throughout my experimentation but included libgtk-x11, libgmodule, and libgobject) in the error message was not always the library at fault.

In the end I solved the problem by simply removing from /usr/local/lib those libraries which I knew had been the result of my tinkering (and then of course I ran "sudo ldconfig" to refresh the cache) which left only the correct libraries in /usr/lib.

I have learned to be more careful when configuring and compiling source code, and in retrospect it would have paid off to learn more about working on projects in Linux before diving in and screwing things up. I think that before I attempt to work on gnome-games again I will take the time to read about working on open source project under Linux and how to correctly maintain an isolated working environment.

---

### Post by InFeh on 2008-04-02
Though this post is old, I'd like to thank you for your eight hours spent researching. My entire GTK had crashed, which included the X server; I was stuck with only the shell. I'm not much of an avid digger myself, but googling my error(symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled) led me to this thread, and in desperation I "rm -rf"-ed the entire /usr/local/lib folder, which restored my X11 functionality.

So yes, thanks alot.

---

### Post by Amackera on 2008-04-12
Thank you sir! That was exactly my problem.

I think the most annoying thing about this whole process was the lag of debugging information given from the system. Thank goodness your post here is now the #1 hit on Google!

Cheers!

---

