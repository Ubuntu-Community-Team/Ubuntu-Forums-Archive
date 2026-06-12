---
title: "Amaya"
date: 2007-06-25
forum: General Help
---

### Post by anv on 2007-06-25
I installed Amaya and when running it:

$ amaya
05:35:08 PM: Deleted stale lock file '/home/****/.amaya-xousia'.

(amaya:5811): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 8391 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(((help)))

---

### Post by hughh on 2007-07-02
I got something very similar:

[INDENT]hugh@Ubuntu:~$ amaya
09:40:26 PM: Deleted stale lock file '/home/hugh/.amaya-hugh'.
09:40:26 PM: Warning: Mailcap file /home/hugh/.mailcap, line 1: incomplete entry ignored.
09:40:26 PM: Warning: Mailcap file /etc/mailcap, line 1: incomplete entry ignored.

(amaya:19916): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7508 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/INDENT]

Then I saw the first post by happybrick [here]("http://ubuntuforums.org/showthread.php?t=376779&highlight=amaya").  I followed the suggestion of installing version 9.55 and it seems to be working now.

---

### Post by arvevans on 2007-09-16
Me Too:

[INDENT]arv@arv-desktop:~$ amaya
08:53:30 PM: Deleted stale lock file '/home/arv/.amaya-arv'.

(amaya:6126): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7556 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
arv@arv-desktop:~$ amaya --sync
08:54:04 PM: Deleted stale lock file '/home/arv/.amaya-arv'.

(amaya:6293): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 15226 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
arv@arv-desktop:~$ 
[/INDENT]

Running AMD X2 64-bit 3200 CPU, 1GB RAM, VIA Motherboard Chipset (onboard graphics) but with 32-bit Ubuntu-Gnome instead of 64-bit Ubuntu (same failure though when I was running the 64-bit version of Ubuntu-Gnome).  System is stable and all other applications run just fine.

Amaya comes up on the screen stays for about 1/4 second and then disappears.  The above error messages were obtained by launching Amaya from a command line.

Arv
_._

---

### Post by arvevans on 2007-09-16
**Solved**.  I should have read a bit further before posting.  Upgrading to the latest version from the Amaya web site fixed everything.  The version on the Ubuntu mirror sites seems to be broken, but the new release is good.
Arv
_._

---

