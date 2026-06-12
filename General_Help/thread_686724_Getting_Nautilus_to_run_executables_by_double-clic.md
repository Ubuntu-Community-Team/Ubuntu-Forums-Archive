---
title: "Getting Nautilus to run executables by double-click"
date: 2008-02-03
forum: General Help
---

### Post by Rippy on 2008-02-03
Summary for those with short attention spans:

How can I get Nautilus to recognize and run executables, preferably by double-click? (i.e. the ones without file extensions)




I've just gotten Eclipse all set up perfectly, along with CDT for C++ programming. Eclipse has a kind of built-in console, which works nicely, but sometimes I want to test the executable in its own shell window to see how it reacts (for example, does it pause before exiting? Eclipse's console won't show that).

So I navigate to the folder containing the executable, double-click it, and... nothing. I tried opening the application with the custom command "gnome-terminal", still nothing. I did end up getting it to work, but I had to rename the file to a .py file extension, after which Nautilus recognized it as an executable text file and ran it just fine. It'd be a pain in the butt to do that every time though.

There's also the ./ command in the terminal but again, I'd like to be able to test it in its own shell window as well, and it's an even bigger pain to type in the whole folder tree to get there.

I remember trying to figure this out before without success. Anyone know if this can be done yet?

Thanks!

Rippy

---

### Post by markharding557 on 2008-02-03
in nuatilus right click your script or what ever select properties-permissions,check box-allow executing file as program.
file is now executable.
you would get more response if you didn't think we need greater attention span

---

