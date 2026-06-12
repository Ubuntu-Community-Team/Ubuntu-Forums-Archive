---
title: "how  run a C executable by double clicking its icon?"
date: 2008-06-14
forum: General Help
---

### Post by jto on 2008-06-14
I'm using the Ubuntu Heron version of Linux, and I'd like to double click an icon for a C executable and get it to run in a terminal window. 

When I double click the .exe file of the following C program:

#include <stdio.h>
main()
{
  printf("hello\n");
  getchar();
} 

nothing happens - not even an error message.

Ironically, I can get the program to run from a launch icon with the command:

gnome-terminal -e /media/disk/python24/abs/./hello.exe

Also, I can get an icon for a Python program to run (after a window appears asking me if I want to run it). 

The simple Python program I used is:

#!/usr/bin/python
# hello.py 6-3-08 jto
print "hello"
raw_input()

So, to summarize, I can get a Python program, but not a C executable, to run by double clicking its icon.

Thanks in advance for any help.

jto

---

### Post by ModelM on 2008-06-14
Is the file executable? Right click on the icon, select "properties", select the permissions tab & see that "Allow executing file as program" is checked.

The ".exe" filename extension means nothing in Linux. Each executable file must be explicitly marked as such.

---

### Post by jto on 2008-06-14
> **jto said:**
> I'm using the Ubuntu Heron version of Linux, and I'd like to double click an icon for a C executable and get it to run in a terminal window. 

When I double click the .exe file of the following C program:

#include <stdio.h>
main()
{
  printf("hello\n");
  getchar();
} 

nothing happens - not even an error message.

Ironically, I can get the program to run from a launch icon with the command:

gnome-terminal -e /media/disk/python24/abs/./hello.exe

Also, I can get an icon for a Python program to run (after a window appears asking me if I want to run it). 

The simple Python program I used is:

#!/usr/bin/python
# hello.py 6-3-08 jto
print "hello"
raw_input()

So, to summarize, I can get a Python program, but not a C executable, to run by double clicking its icon.

Thanks in advance for any help.

jto
When I right click on the icon and select properties, I see that the "allow executing file as program" is preceded by a box that is tinted orange and had a minus sign in it. When I try clicking it, the minus sign turns to a check momentarily and then back to a minus sign. I notice that if I double click the box, that clears the box. Then if I click the box, a check appears momentarily and then turns into the minus sign again.

I guess nothing's simple. By the way, I also entered chmod +x hello.exe on the command line. Any other ideas?

Thanks.

---

### Post by mike2357 on 2008-06-14
Your program actually is running, but it has no place to send its output to.  I was able to prove this with the following:

#include    <stdio.h>
main()
{
FILE    *fp;    
FILE    *fopen();

fp = fopen("./out", "w");
fprintf(fp, "Hello, world.\n");
fclose(fp);
}

When I double-clicked on the program, it created a file called out with contents of Hello, world.

To run a non-gui program like this from Nautilus, type <ALT>-F2, make sure "Run in terminal" is checked, and type in the full path to your program.

Also see
[https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html")

---

### Post by jto on 2008-06-14
> **mike2357 said:**
> Your program actually is running, but it has no place to send its output to.  I was able to prove this with the following:

#include    <stdio.h>
main()
{
FILE    *fp;    
FILE    *fopen();

fp = fopen("./out", "w");
fprintf(fp, "Hello, world.\n");
fclose(fp);
}

When I double-clicked on the program, it created a file called out with contents of Hello, world.

To run a non-gui program like this from Nautilus, type <ALT>-F2, make sure "Run in terminal" is checked, and type in the full path to your program.

Also see
[https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html")
Thanks much for the explanation and suggestion. I guess I was making it more complicated than it needed to be. jto

---

