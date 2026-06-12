---
title: "Gnome-terminal"
date: 2006-10-14
forum: General Help
---

### Post by heinouskyle on 2006-10-14
I just built a new computer and installed Edgy, but now I'm not able to use gnome-terminal. Xterm and aterm work fine, but I like gnome-terminal better.

I tried removing and installing the package with apt-get. I didn't get any errors, but gnome-terminal still doesn't work.

I don't know what else to try. Any ideas?

EDIT: I just tried running gnome-terminal from xterm, and it says this ```
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

I don't know what this means exactly, but I would guess that it has something to do with my xorg.conf customizations. I have two video cards, a Geforce 6200 LE in the PCI-E slot and an MX 420 PCI card.

---

### Post by heinouskyle on 2006-10-16
Nothing?

---

### Post by theslut on 2006-10-22
[http://ubuntuforums.org/showthread.php?t=276354&highlight=gnome+terminal](http://ubuntuforums.org/showthread.php?t=276354&highlight=gnome+terminal)

seems you need composite set to false in the xorg.conf

---

### Post by spidernik84 on 2006-10-22
> **theslut said:**
> [http://ubuntuforums.org/showthread.php?t=276354&highlight=gnome+terminal](http://ubuntuforums.org/showthread.php?t=276354&highlight=gnome+terminal)

seems you need composite set to false in the xorg.conf

Did that but no way...still crashing. At last this enabled fglrx acceleration correctly :(

---

### Post by spidernik84 on 2006-10-24
Forgot to add that i've got an ati x1600 running with fglrx correctly, and beryl + xgl.
This is my output...any clue? :(

```
Thread 1 (Thread -1226443088 (LWP 10413)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77a7323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ef41b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7f5a530 in ?? () from /lib/ld-linux.so.2
No symbol table info available.
#5  0x080f6d10 in ?? ()
No symbol table info available.
#6  0x90000001 in ?? ()
No symbol table info available.
#7  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

---

