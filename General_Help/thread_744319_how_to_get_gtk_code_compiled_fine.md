---
title: "how to get gtk code compiled fine"
date: 2008-04-03
forum: General Help
---

### Post by kingkong22 on 2008-04-03
The following code example:
#include <gtk/gtk.h>

int main( int   argc,
          char *argv[] )
{
    GtkWidget *window;

    gtk_init (&argc, &argv);

    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show  (window);

    gtk_main ();

    return 0;
}
~                       
I try to compile it after installing libgtk2.0-dev in my ubuntu V7.10, the compiler said:

gcc `pkg-config --cflags --libs gtk+-2.0` f.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
f.c:1:21: error: gtk/gtk.h: No such file or directory
f.c: In function ‘main’:
f.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
f.c:6: error: (Each undeclared identifier is reported only once
f.c:6: error: for each function it appears in.)
f.c:6: error: ‘window’ undeclared (first use in this function)
f.c:10: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)

So, what should I do ? thank you very much !

---

### Post by markekeller on 2008-04-03
It looks like either you misspelled the name of the library you're linking to (gtk+-2.0), or it's not installed properly.  Could either be the case?   There's a good chance that a lot of people browsing this board won't be able to help you much.  Try the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") board instead. ;)

---

### Post by mc4man on 2008-04-03
In most cases the path would be /usr/include/gtk-2.0/gtk

---

### Post by ibuclaw on 2008-04-03
try
```
 gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0 --libs gtk+-2.0`
```

Not sure where you are getting your tutorial or info from, but try [this site.]("http://library.gnome.org/devel/gtk-tutorial/stable/")
They'll give you enough information on programming in GTK+2.0

[EDIT]
Also, make sure that you have the right **-dev** packages installed too.
```
 apt-get install libgtk2.0-dev libgtkmm-2.4-dev libgtksourceview2.0-dev libpango1.0-dev 
```
Although your repository may have slightly different names.

Regards
Iain

---

### Post by kingkong22 on 2008-04-04
I just checked thoes packages, their versions are matching all in my hp dv6000. however,
compile the code and still get the following error msgs:

%> gcc -g f.c `pkg-config --cflags gtk+-2.0 --libs gtk+-2.0`

Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
f.c:1:21: error: gtk/gtk.h: No such file or directory
f.c: In function ‘main’:
f.c:6: error: ‘GtkWidget’ undeclared (first use in this function)

I think, pkg-config just can't produce the correct linking option in my system
-- after I used the specific paths for the headers & libraries and linking
ok. I just wonder why my system can't interpret pkg-config correctly. thanks.

---

### Post by ibuclaw on 2008-04-04
> **kingkong22 said:**
> 
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found


### EDIIT ###

Okay, I'm trying this again....

Type in:
```
 echo "$PKG_CONFIG_PATH" 
```

If that comes up blank.
Type in this:
```
 locate gtk+-2.0.pc 
```
And copy all but the **gtk+-2.0.pc** part of the line that was echoed.
Should be something like:

**/usr/lib/pkgconfig/**

Anyway. Type in this:
```
  export PKG_CONFIG_PATH=**/usr/lib/pkgconfig**:$PKG_CONFIG_PATH 
```
Replace what's in bold with whatever your path is.

And all should be fixed!
Try the echo command again, and it should be displayed.
```

:~$ echo "$PKG_CONFIG_PATH"
/usr/lib/pkgconfig:

```

Regards
Iain

---

### Post by kingkong22 on 2008-04-04
Excellent !!! it does job ! thank you so much !

---

