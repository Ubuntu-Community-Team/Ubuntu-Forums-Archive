---
title: "problems with gnome-terminal in edgy"
date: 2006-10-26
forum: General Help
---

### Post by BigJeep on 2006-10-26
I just did a clean install of Ubuntu Edgy and am having problems getting gnome-terminal to start.  The only things that I have done is replace the Xorg.conf file with the one from my dapper installation (to get my dual graphics cards and monitors to work), and install the nvidia driver.

When I try to run xterm it won't launch.  When i try to run it from xterm, this is the error I get

```
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

any ideas?

---

### Post by Dr. Nick on 2006-10-27
does it work with the default xorg in edgy? I noticed a few changes in syntax in parts of cxorg between dpper and edgy, may be part of the problem since xorg is mentioned in the error log

---

### Post by scotartt on 2006-10-27
I have the exact same problem. I am running dual monitors on edgy 64 bit, with an nvidia driver.

Error:
> The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by rumli on 2006-10-27
I had the same problem and found a solution in [this post]("http://ubuntuforums.org/showpost.php?p=1644324&postcount=7") on [this thread]("http://ubuntuforums.org/showthread.php?t=276354").  It seems to be a problem with Xinerama and nvidia-glx.

Try adding:
```

Section "Extensions"
	Option "Composite" "false"
EndSection

```
to your /etc/X11/xorg.conf file.

---

