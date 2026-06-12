---
title: "What am I missing? Ubuntu 12.04 64-bit packages with shared objects static libraries"
date: 2012-10-17
forum: General Help
---

### Post by burgundy on 2012-10-17
Recently I started compiling some old 32-bit libraries/applications on a new installation of Ubuntu 12.04 64-bit with Eclipse Juno.

When it came time to link with the proper gtk-x11-2.0, gdk-x11-2.0, xml2, and jpeg libraries Eclipse started to complain and my search began.

After looking for and installing every possible development, multiarch, multilib package I could find, Eclipse still insisted it couldn't find the required libraries.

Upon closer inspection, I noticed how Ubuntu sorts its libraries and packages.  Everything that mattered appeared to be in /usr/lib/i386-linux-gnu or /usr/lib/x86_64-linux-gnu.

Only the x86_64-linux-gnu directory had static lib*.a files I wanted for my application.

This is when I decided to make sure I was properly looking for the shared object files that were in the i386-linux-gnu directory.

Still Eclipse claimed it couldn't find the libraries I needed.

Then as an experiment I manually added a ".so" instead of a ".so.0" link to the libraries I wanted.

Suddenly, Eclipse could find all the libraries, but I'm left with a less than ideal solution.

Maybe I should be posting this in some Eclipse forum, but I'm wondering why I need to manually create links to libraries without the ".0" at the end so that Eclipse can find them.

Is there a g++ linker option/flag I'm missing?  I don't have much experience with shared objects and Eclipse.

What am I not seeing?  What did I miss?

Thanks

---

