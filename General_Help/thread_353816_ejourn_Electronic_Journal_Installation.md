---
title: "ejourn Electronic Journal Installation"
date: 2007-02-05
forum: General Help
---

### Post by jhuff on 2007-02-05
I have downloaded and installed ejourn using the autopackage.  It seems  to install but then I can not figure out how to run it.  I have tried typing "ejourn" and "ejourn-gui" in terminal window, but nothing works. Has anyone successfully installed this program and got it running?

---

### Post by kingmonkey on 2007-02-05
Try eJourn

+ isnt it in the Applications list?

---

### Post by jhuff on 2007-02-05
"eJourn" did not work and I can't find it in the applications menu.

---

### Post by jhuff on 2007-02-06
I have tried installing the source file.  I can get the application to start but I get an error saying "Error, missing add.png" I click ok about 5 times and get the main window, however the program still does not function.  Below is terminal window output.  I am hoping someone could help me correctly install this program.

```
jah@ubuntu:~$ ejourn-gui
Settings be loaded...
Initting Months...
Threading the gdk..
/etc/gtk-2.0/gtkrc
/home/jah/.gtkrc-2.0
Fifo loc'ed!
Imaged
Failed to load main window icon
Main window prepared
Journals ready
PATH:/home/jah
Failed to load login window icon
Key:AES
User logged in
Initializing the background thread...
Image themed
Plugins loaded
Opened non-existent file....

(ejourn-gui:3830): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_write: assertion `buf != NULL' failed

(ejourn-gui:3830): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_write: assertion `buf != NULL' failed

(ejourn-gui:3830): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_write: assertion `buf != NULL' failed

(ejourn-gui:3830): Gdk-CRITICAL **: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed

(ejourn-gui:3830): Gdk-CRITICAL **: gdk_window_resize: assertion `GDK_IS_WINDOW (window)' failed

(ejourn-gui:3830): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_write: assertion `buf != NULL' failed

(ejourn-gui:3830): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_write: assertion `buf != NULL' failed

```

---

### Post by jhuff on 2007-02-06
Ok I got it working by reinstalling it using root privileges.  I can get it to run from the terminal window by typing "ejourn-gui"  But when I try to make a custom application luncher it will not start up using "ejourn-gui"  Does anyone have any ideas?

---

### Post by MrJones on 2007-03-12
Well, congratulations on installing eJourn, I have not been able to do that yet. I may have a useful tip on creating a launcher though; in the "Create Launcher" dialog, you can select what type of launcher it should be right at the top. Maybe it will work if you select "Application in Terminal"? I hope it does...

Meanwhile I have been trying a whole lot to get eJourn to work. First I tried to install the autopackage program, which failed miserably. Then I tried to install it from source, something I have never done before since this is my first Ubuntu week. I got the following error messages:
```
make: Circular src/objs.d <- src/objs.d dependency dropped.
cd src && make
make[1]: Entering directory `/home/ubuntu/eJourn/src'
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include `pkg-config gtk+-2.0 --cflags` `pkg-config gthread-2.0 --cflags` -c callbacks.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
callbacks.c:5:21: error: gtk/gtk.h: No such file or directory
In file included from callbacks.h:7,
                 from callbacks.c:7:
calendar.h:56: error: expected ‘)’ before ‘*’ token
calendar.h:60: error: expected ‘)’ before ‘*’ token
calendar.h:64: error: expected ‘)’ before ‘*’ token
calendar.h:67: error: expected ‘)’ before ‘*’ token
In file included from callbacks.h:8,
                 from callbacks.c:7:
edit.h:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_text_event’
edit.h:78: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_text_cursor_move_real’
edit.h:82: error: expected ‘)’ before ‘*’ token
edit.h:89: error: expected ‘)’ before ‘*’ token
edit.h:92: error: expected ‘)’ before ‘*’ token
edit.h:98: error: expected ‘)’ before ‘*’ token
In file included from callbacks.h:9,
                 from callbacks.c:7:
search_tab.h:57: error: expected ‘)’ before ‘*’ token
search_tab.h:61: error: expected ‘)’ before ‘*’ token
search_tab.h:65: error: expected ‘)’ before ‘*’ token
search_tab.h:69: error: expected ‘)’ before ‘*’ token
search_tab.h:72: error: expected ‘)’ before ‘*’ token
In file included from callbacks.c:7:
callbacks.h:12: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_main_pane_set’
callbacks.h:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_res_pane_set’
callbacks.h:22: error: expected ‘)’ before ‘*’ token
callbacks.h:25: error: expected ‘)’ before ‘*’ token
callbacks.h:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_window_main_close’
callbacks.h:32: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_srch_bar_key_release’
callbacks.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_srch_bar_btn_release’
callbacks.h:42: error: expected ‘)’ before ‘*’ token
callbacks.h:46: error: expected ‘)’ before ‘*’ token
callbacks.h:51: error: expected ‘)’ before ‘*’ token
callbacks.h:55: error: expected ‘)’ before ‘*’ token
callbacks.h:60: error: expected ‘)’ before ‘*’ token
callbacks.h:64: error: expected ‘)’ before ‘*’ token
callbacks.h:68: error: expected ‘)’ before ‘*’ token
callbacks.h:72: error: expected ‘)’ before ‘*’ token
callbacks.h:76: error: expected ‘)’ before ‘*’ token
callbacks.h:81: error: expected ‘)’ before ‘*’ token
callbacks.h:84: error: expected ‘)’ before ‘*’ token
callbacks.h:88: error: expected ‘)’ before ‘*’ token
callbacks.h:92: error: expected ‘)’ before ‘*’ token
callbacks.h:96: error: expected ‘)’ before ‘*’ token
callbacks.h:99: error: expected ‘)’ before ‘*’ token
callbacks.h:101: error: expected ‘)’ before ‘*’ token
callbacks.h:104: error: expected ‘)’ before ‘*’ token
callbacks.h:107: error: expected ‘)’ before ‘*’ token
callbacks.h:110: error: expected ‘)’ before ‘*’ token
callbacks.h:115: error: expected ‘)’ before ‘*’ token
callbacks.h:121: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_text_tag_click’
callbacks.h:130: error: expected ‘)’ before ‘*’ token
callbacks.h:134: error: expected ‘)’ before ‘*’ token
callbacks.h:138: error: expected ‘)’ before ‘*’ token
callbacks.h:142: error: expected ‘)’ before ‘*’ token
callbacks.h:146: error: expected ‘)’ before ‘*’ token
callbacks.h:152: error: expected ‘)’ before ‘*’ token
In file included from callbacks.c:8:
interface.h:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:10: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:16: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:17: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
interface.h:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from callbacks.c:9:
support.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:51: warning: type defaults to ‘int’ in declaration of ‘gchar’
support.h:51: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
support.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:66: error: expected ‘)’ before ‘*’ token
In file included from login.h:5,
                 from gui_al.h:35,
                 from callbacks.c:11:
support.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:51: warning: type defaults to ‘int’ in declaration of ‘gchar’
support.h:51: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
support.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:66: error: expected ‘)’ before ‘*’ token
In file included from gui_al.h:35,
                 from callbacks.c:11:
login.h:14: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_entry2_type’
login.h:19: error: expected ‘)’ before ‘*’ token
login.h:22: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lgn_on_login’
login.h:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lgn_on_cancel’
login.h:31: error: expected ‘)’ before ‘*’ token
login.h:35: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lgn_on_select_journ’
login.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_window_login_close’
In file included from callbacks.c:11:
gui_al.h:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:43: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:56: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:57: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:60: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:61: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:64: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:65: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:67: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:69: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:74: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:76: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:77: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:81: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:83: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:84: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:99: error: expected specifier-qualifier-list before ‘GtkWidget’
gui_al.h:108: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
gui_al.h:331: error: expected specifier-qualifier-list before ‘GtkWidget’
In file included from callbacks.c:12:
gui_io.h:51:28: error: gdk/gdkkeysyms.h: No such file or directory
In file included from callbacks.c:14:
about.h:8: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from callbacks.c:15:
fileChooser.h:5: error: expected ‘)’ before ‘*’ token
fileChooser.h:7: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from prefDialogue.h:5,
                 from callbacks.c:17:
support.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:51: warning: type defaults to ‘int’ in declaration of ‘gchar’
support.h:51: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
support.h:59: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:63: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
support.h:66: error: expected ‘)’ before ‘*’ token
In file included from callbacks.c:17:
prefDialogue.h:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
prefDialogue.h:14: error: expected ‘)’ before ‘*’ token
prefDialogue.h:19: error: expected ‘)’ before ‘*’ token
prefDialogue.h:23: error: expected ‘)’ before ‘*’ token
prefDialogue.h:28: error: expected ‘)’ before ‘*’ token
prefDialogue.h:31: error: expected ‘)’ before ‘*’ token
In file included from callbacks.c:18:
fileChooser.h:5: error: expected ‘)’ before ‘*’ token
fileChooser.h:7: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
callbacks.c:28: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_main_pane_set’
callbacks.c: In function ‘__srchWait’:
callbacks.c:45: warning: implicit declaration of function ‘gtk_entry_get_text’
callbacks.c:45: warning: implicit declaration of function ‘GTK_ENTRY’
callbacks.c:45: error: ‘_menu_srch_entry’ undeclared (first use in this function)
callbacks.c:45: error: (Each undeclared identifier is reported only once
callbacks.c:45: error: for each function it appears in.)
callbacks.c: At top level:
callbacks.c:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_srch_bar_key_release’
callbacks.c:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_srch_bar_btn_release’
callbacks.c:81: error: expected ‘)’ before ‘*’ token
callbacks.c:89: error: expected ‘)’ before ‘*’ token
callbacks.c:96: error: expected ‘)’ before ‘*’ token
callbacks.c:105: error: expected ‘)’ before ‘*’ token
callbacks.c:114: error: expected ‘)’ before ‘*’ token
callbacks.c:125: error: expected ‘)’ before ‘*’ token
callbacks.c:133: error: expected ‘)’ before ‘*’ token
callbacks.c:141: error: expected ‘)’ before ‘*’ token
callbacks.c:149: error: expected ‘)’ before ‘*’ token
callbacks.c:155: error: expected ‘)’ before ‘*’ token
callbacks.c:160: error: expected ‘)’ before ‘*’ token
callbacks.c:166: error: expected ‘)’ before ‘*’ token
callbacks.c:184: error: expected ‘)’ before ‘*’ token
callbacks.c:201: error: expected ‘)’ before ‘*’ token
callbacks.c:212: error: expected ‘)’ before ‘*’ token
callbacks.c:223: error: expected ‘)’ before ‘*’ token
callbacks.c:233: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_window_main_close’
callbacks.c:245: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_text_tag_click’
callbacks.c:279: error: expected ‘)’ before ‘*’ token
callbacks.c:315: error: expected ‘)’ before ‘*’ token
callbacks.c:362: error: expected ‘)’ before ‘*’ token
callbacks.c:420: error: expected ‘)’ before ‘*’ token
callbacks.c:452: error: expected ‘)’ before ‘*’ token
callbacks.c:515: error: expected ‘)’ before ‘*’ token
callbacks.c:535: error: expected ‘)’ before ‘*’ token
callbacks.c:546: error: expected ‘)’ before ‘*’ token
callbacks.c:558: error: expected ‘)’ before ‘*’ token
callbacks.c:591: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘on_res_pane_set’
make[1]: *** [callbacks.o] Error 1
make[1]: Leaving directory `/home/ubuntu/eJourn/src'
make: *** [src/objs.d] Error 2

```To me, being the newbie that I am, this sounds like I am missing one package, or at least the program that is executed by the "make" command is, and it can't find two other essential files. I installed the build-essential package earlier, but that didn't help either. Any suggestions?

---

### Post by Mr Al on 2007-05-10
I'm having the same problem as jhuff... anyone found a solution to this?

---

### Post by thinkbuddha on 2007-05-21
I'm having the same problem here. I'm completely new to all of this, but seem to have got it working. The AutoPackage, although it claims to have installed it, doesn't seem to do the trick. But the following worked for me.

1. Download the source code and unpack it to somewhere appropriate. 
2.In the terminal, install the following package:

```
sudo apt-get install libgtk2.0-dev
```

3. OK, now go to the eJourn directory and, as in the README, run the following (I ran it as root)

```
sudo ./configure --prefix=/usr
```

4. That worked OK, so then...

```
 sudo make
```

5. Taking this line by line, straight from the README again

```
sudo make install
```

6. All well and good (hopefully), so...

```
sudo make clean
```

7. Now when run 

```
ejourn
```

And it works! 

Right, now to have a poke around and see what I can do with it.

Good luck.

Will

---

### Post by Steve H on 2007-07-19
I´m having a real trauma getting this software to work. I keep getting the following error when i run the ¨make¨

```
make: Circular src/objs.d <- src/objs.d dependency dropped.
cd src && make
make[1]: Entering directory `/home/blah/Desktop/eJourn/src'
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include -c xml.c
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include -c io.c
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include -c simple.c
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include `pkg-config gtk+-2.0 --cflags` `pkg-config gthread-2.0 --cflags` -c callbacks.c
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include  `pkg-config gtk+-2.0 --cflags` `pkg-config gthread-2.0 --cflags` -c clipboard.c
gcc -g -O2  -Wall -fPIC -DENABLE_BINRELOC -I`pwd`/include   -c -o crypt.o crypt.c
crypt.c:2:20: error: gcrypt.h: No such file or directory
crypt.c:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘cipher1’
crypt.c: In function ‘encryptText’:
crypt.c:35: error: ‘gcry_error_t’ undeclared (first use in this function)
crypt.c:35: error: (Each undeclared identifier is reported only once
crypt.c:35: error: for each function it appears in.)
crypt.c:35: error: expected ‘;’ before ‘error1’
crypt.c:38: error: ‘error1’ undeclared (first use in this function)
crypt.c:38: warning: implicit declaration of function ‘gcry_cipher_setiv’
crypt.c:38: error: ‘cipher1’ undeclared (first use in this function)
crypt.c:39: warning: implicit declaration of function ‘gcry_cipher_setctr’
crypt.c:40: warning: implicit declaration of function ‘gcry_cipher_setkey’
crypt.c:41: warning: implicit declaration of function ‘gcry_cipher_encrypt’
crypt.c:42: warning: implicit declaration of function ‘gcry_cipher_close’
crypt.c: In function ‘decryptText’:
crypt.c:48: error: ‘gcry_error_t’ undeclared (first use in this function)
crypt.c:48: error: expected ‘;’ before ‘error1’
crypt.c:51: error: ‘error1’ undeclared (first use in this function)
crypt.c:51: error: ‘cipher1’ undeclared (first use in this function)
crypt.c:54: warning: implicit declaration of function ‘gcry_cipher_decrypt’
crypt.c: In function ‘encryptFile’:
crypt.c:61: error: ‘gcry_error_t’ undeclared (first use in this function)
crypt.c:61: error: expected ‘;’ before ‘error1’
crypt.c:64: error: ‘error1’ undeclared (first use in this function)
crypt.c:64: error: ‘cipher1’ undeclared (first use in this function)
crypt.c: In function ‘decryptFile’:
crypt.c:118: error: ‘gcry_error_t’ undeclared (first use in this function)
crypt.c:118: error: expected ‘;’ before ‘error1’
crypt.c:121: error: ‘error1’ undeclared (first use in this function)
crypt.c:121: error: ‘cipher1’ undeclared (first use in this function)
crypt.c: In function ‘createKey’:
crypt.c:193: warning: implicit declaration of function ‘strlen’
crypt.c:193: warning: incompatible implicit declaration of built-in function ‘strlen’
make[1]: *** [crypt.o] Error 1
make[1]: Leaving directory `/home/blah/Desktop/eJourn/src'
make: *** [src/objs.d] Error 2

```

Anyone got any ideas what these errors mean??

All help appreciated.

Many Thanks

:)

---

### Post by katja on 2007-07-31
I'm getting the same error as the previous poster - does anyone know how to get past this?  Thank you :).

---

### Post by katja on 2007-08-01
Ok - I installed libgcrypt11-dev; after this I managed to install eJourn without any problems and, so far, it works fine :).

---

