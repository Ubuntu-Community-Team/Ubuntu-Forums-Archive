---
title: "Evolution in Xubuntu 16.10"
date: 2016-10-18
forum: General Help
---

### Post by brashley46 on 2016-10-18
will not start correctly. from the terminal I get 
```

brashley46@rossdesktop2:~$ evolution
libEGL warning: DRI2: failed to authenticate

(evolution:19802): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
libEGL warning: DRI2: failed to authenticate
Xlib: sequence lost (0x100ad > 0xae) in reply type 0x0!

(WebKitWebProcess:19833): Gdk-ERROR **: The program 'WebKitWebProcess' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 173 error_code 2 request_code 0 (core protocol) minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
libEGL warning: DRI2: failed to authenticate
Xlib: sequence lost (0x100ad > 0xae) in reply type 0x0!

(WebKitWebProcess:19960): Gdk-ERROR **: The program 'WebKitWebProcess' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 173 error_code 2 request_code 0 (core protocol) minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
libEGL warning: DRI2: failed to authenticate
Xlib: sequence lost (0x100ad > 0xae) in reply type 0x0!

(WebKitWebProcess:20040): Gdk-ERROR **: The program 'WebKitWebProcess' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 173 error_code 2 request_code 0 (core protocol) minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(evolution:19802): webkit-editor-WARNING **: WebKitWebProcess (page id 2) for EWebKitEditor crashed


```

I need evolution to deal expeditiously with emails on my chorus' IMAP email account.

---

### Post by brashley46 on 2016-10-18
Rebooting solved it. Amazing.

---

### Post by mörgæs on 2016-10-18
Good, please mark the thread 'solved'.

---

