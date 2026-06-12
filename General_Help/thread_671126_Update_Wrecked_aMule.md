---
title: "Update Wrecked aMule?"
date: 2008-01-18
forum: General Help
---

### Post by Ingla on 2008-01-18
Hi.[COLOR="Red"]

JUST EDITED THIS: VLC Player also broken (same error messages as aMule)[/COLOR]

I'm running Feisty and just got a bunch of new updates with the Update Manager (18 Jan). Some had to do with the xorg server.

Anyway, aMule won't start. Hitting the icon yields nothing. Typing "aMule" in terminal brings: 

----------------------------------------------------------------------------------------------------------------------
Initialising aMule
Checking if there is an instance already running...
No other instances are running.

(amule:5846): Gtk-WARNING **: Unable to locate theme engine in module_path: "lighthouseblue",
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 397 error_code 11 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
---------------------------------------------------------------------------------------------------------------------

I don't understand this exactly.

Does anyone know how to fix this (precise commands)?

Any help appreciated.

Thank you.

---

### Post by Harry_Callahan on 2008-01-18
same problem too :

(amule:8078): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(amule:8078): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
The program 'amule' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.

---

### Post by Ingla on 2008-01-19
Hi.

It's fixed! The devs caught it. There's a new update for the xorg server. The system doesn't call for a reboot, but you need it after updating.

After the update, VLC worked. aMule didn't, but that is fixed by killing any running instance of aMule OR, as in my case, by deleting the file called mulelock from the /home/.amule folder.

All's well that ends well.

---

