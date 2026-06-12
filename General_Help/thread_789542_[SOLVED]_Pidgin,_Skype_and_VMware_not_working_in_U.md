---
title: "[SOLVED] Pidgin, Skype and VMware not working in Ubuntu 8.04"
date: 2008-05-10
forum: General Help
---

### Post by uroskriznar on 2008-05-10
I upgraded to Ubuntu 8.04 and noticed that Pidgin is not working. When I try to run it, nothing happens. I had a Skype plugin installed in the previous version of Ubuntu, but noticed that Skype can not be instaled in Hardy. Does anyone know what could be the problem??? This is bi0ggest problem that I face right now!!!

Some add-ons in firefox are also not compatibale yet, but this will get solved in time, and VMvare workstation also doesn't work.

I would be grateful if anyone knows how to fix these problems.

---

### Post by luisromangz on 2008-05-10
Have you tried running those programs from the command line to see what their outputs are?

VMWare probably needs a reinstall, as the kernel version has changed with the upgrade, and the VMWare kernel module is created when the program is installed for the current kernel.

---

### Post by uroskriznar on 2008-05-11
When I run PIDGIN and VMware in terminal I get these messages, but it is a little to complicated for me.

uros6@uros6-desktop:~$ pidgin
The program 'pidgin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 11 error_code 5 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

Any suggestions???

---

### Post by luisromangz on 2008-05-11
Ok, the vmware output says how to solve the problem itself, running /usr/bin/vmware-config.pl as su should do the trick.

The pidgin one is quite more obscure, but I found this thread ([http://ubuntuforums.org/showthread.php?t=656926](http://ubuntuforums.org/showthread.php?t=656926)) using google, and it seems that may have to do with the skype plugin (do you have it installed?)

---

### Post by uroskriznar on 2008-05-11
luisromangz thanks. I solved the problem with Pidgin. I had to delete the Skype plugin and now it seems to work fine.

---

### Post by BigBrownChunx on 2008-05-11
You also might want to try upgrading the plugin, since later versions fix this problem.

---

