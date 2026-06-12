---
title: "[SOLVED] GtkRadiant &amp;quot;GL_INVALID_ENUM&amp;quot;"
date: 2007-05-10
forum: General Help
---

### Post by noerrorsfound on 2007-05-10
I compiled GtkRadiant using the instructions from [https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING](https://zerowing.idsoftware.com/svn/radiant/GtkRadiant/trunk/COMPILING) because the Linux RPMs they provided were not compatible with 64 bit.

When I open it, I get an error saying this:
> runtime error: OpenGL error: GL_INVALID_ENUM - An unacceptable value is specified for an enumerated argument.

The error is so long that it did not all fit on 1024x768 so I have a screenshot for both the top and bottom.

Top part of error dialog:
[http://img2.freeimagehosting.net/uploads/0decacf117.png](http://img2.freeimagehosting.net/uploads/0decacf117.png)

Bottom:
[http://img2.freeimagehosting.net/uploads/c7f1c83d3f.png](http://img2.freeimagehosting.net/uploads/c7f1c83d3f.png)

It asks me if I want to break into the debugger. If I click *Yes* then GtkRadiant closes. If I click no then the same error pops up again, and if I click no again then the program will stay open but when I close it **Ubuntu crashes to the terminal and then goes to the login screen**.

---

