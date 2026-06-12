---
title: "Help with configuring sudoers file"
date: 2008-03-27
forum: General Help
---

### Post by GordonFreeman on 2008-03-27
Hi,
I want to start a program (called hotkeys) after logging in, so I inserted in the autorun a entry which calls "sudo hotkeys" but by default I have to enter my password.
So I heard that it is possible to change the sudoers file (with sudo visudo) so that I can run this program as root by calling "sudo hotkeys" without the need to enter my password.

After a little bit of research I tried the following line (I entered it at the bottom of the file):

gordon   ALL=NOPASSWD: /usr/bin/hotkeys

gordon is my user name on this machine



but when I enter now "sudo hotkeys" in a terminal the application launches without the need of a password but crashes immediately and in the terminal is a error report about an invalid pointer for free() in glibc.
So I assume the line above is missing something.

Can you help me with the configuration of the sudoers file? I really don't know what kind of information you could need to help me here, but if you tell me I'll post it here.


Thank you very much!

---

### Post by bwhite82 on 2008-03-27
Take out those lines. Simply chown the binary or script. First locate where on disk it resides:

> sudo updatedb && locate hotkeys

(Probably in /usr/bin)

Then chown the file:

> sudo chown gordon /usr/bin/hotkeys (assuming its in that dir)

---

### Post by GordonFreeman on 2008-03-27
Thank you, but this does not solve the issue, because the application needs to be running as root (then it cannot oben instantiate the SMBIO table which it needs to change the display brightness via hotkey). And unfortunately the program has to be started after X because it displays an on-screen-display and putting it in rc.local gets just ignored.

---

### Post by pointone on 2008-03-27
Your sudoers file looks fine, and the error you describe sounds like an application problem rather than a sudo problem. Did it used to work fine before when you had to provide a password?

Another solution could be to set the SUID bit on the executable:

```
sudo chown root /usr/bin/hotkeys
sudo chmod u+s /usr/bin/hotkeys
```

This makes it run as root for anyone, though.

---

### Post by Toet on 2008-03-27
I think you need the Host_Alias

```
Host_Alias <ALIAS> = <yourmachinename>
```

Where <ALIAS> is an alias to the machinename (make it up yourselves) and <yourmachinename> is the name of your machine (as it shows up in front of your prompt in a terminal session). Leave out the <>.

It would be something like:
```
Host_Alias GORDONPC = gordonspc
```

Then put the following lines where you have yours:

```
gordon     ALL=(ALL) ALL
gordon GORDONPC=NOPASSWD: /usr/bin/hotkeys
```

---

### Post by GordonFreeman on 2008-03-27
Ok, I'll try it.

And the app can basically be launched by everyone, but on my laptop I need it with root rights because it needs to do some stuff with smbios, as mentioned above.
The app runs finde when I provide the password and it runs fine when I deactivate sudo passwords for everything and everyone (commenting out the %sudo line in the sudoers file).

---

### Post by GordonFreeman on 2008-03-27
Using a Host alias didn't work, so I tried chmod u+s, but then I get this:

```

gordon@gordon-xps:~$ sudo chmod u+s /usr/bin/hotkeys
gordon@gordon-xps:~$ hotkeys

(process:6307): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

```

What does this mean?



Edit:
When I start it with the -Z flag (no splash screen while loading) it starts but then I get the could not instantiate SMBIOS table message again, although its running as root when I'm looking at it with ps aux|grep hotkeys

---

### Post by pointone on 2008-03-27
FYI, the host alias isn't necessary if "ALL" is used, which allows "gordon" to run the command on all hosts.

You can remove the SUID bit with "sudo chmod u-s /usr/bin/hotkeys", since it didn't seem to like that.

The only other thing I can think of is the environment. What happens if you run "sudo /usr/bin/env /usr/bin/hotkeys"?

---

### Post by GordonFreeman on 2008-03-27
> **pointone said:**
> FYI, the host alias isn't necessary if "ALL" is used, which allows "gordon" to run the command on all hosts.

You can remove the SUID bit with "sudo chmod u-s /usr/bin/hotkeys", since it didn't seem to like that.

The only other thing I can think of is the environment. What happens if you run "sudo /usr/bin/env /usr/bin/hotkeys"?
sudo /usr/bin/enc /usr/bin/hotkeys seems to work, I'll reboot and try it again to make sure, but it looks good :)

---

### Post by GordonFreeman on 2008-03-27
I removed the superuser bit and added the following line in the sudoers file:
gordon ALL=NOPASSWD: /usr/bin/env

then rebooted and tried "sudo /usr/bin/env /usr/bin/hotkeys", no password needed but again it crashed with the invalid pointer message.


Here is the output:
```

sudo /usr/bin/env /usr/bin/hotkeys -Z
*** glibc detected *** /usr/bin/hotkeys: free(): invalid pointer: 0xbfb44eeb ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb744ad65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb744e800]
/usr/bin/hotkeys[0x804abbc]
/usr/bin/hotkeys[0x804bec6]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb73f7050]
/usr/bin/hotkeys[0x804a551]
======= Memory map: ========
08048000-08050000 r-xp 00000000 08:03 1226772    /usr/bin/hotkeys
08050000-08051000 rw-p 00008000 08:03 1226772    /usr/bin/hotkeys
08051000-08072000 rw-p 08051000 00:00 0          [heap]
b7100000-b7121000 rw-p b7100000 00:00 0 
b7121000-b7200000 ---p b7121000 00:00 0 
b7242000-b724c000 r-xp 00000000 08:03 457027     /lib/libgcc_s.so.1
b724c000-b724d000 rw-p 0000a000 08:03 457027     /lib/libgcc_s.so.1
b724d000-b7270000 rw-p b724d000 00:00 0 
b7270000-b7292000 r-xp 00000000 08:03 1225197    /usr/lib/libpng12.so.0.15.0
b7292000-b7293000 rw-p 00021000 08:03 1225197    /usr/lib/libpng12.so.0.15.0
b7293000-b72b1000 r-xp 00000000 08:03 1225281    /usr/lib/libexpat.so.1.0.0
b72b1000-b72b3000 rw-p 0001e000 08:03 1225281    /usr/lib/libexpat.so.1.0.0
b72b3000-b731f000 r-xp 00000000 08:03 1225295    /usr/lib/libfreetype.so.6.3.16
b731f000-b7323000 rw-p 0006b000 08:03 1225295    /usr/lib/libfreetype.so.6.3.16
b7323000-b7324000 rw-p b7323000 00:00 0 
b7324000-b7351000 r-xp 00000000 08:03 1224651    /usr/lib/libpangoft2-1.0.so.0.1800.3
b7351000-b7352000 rw-p 0002c000 08:03 1224651    /usr/lib/libpangoft2-1.0.so.0.1800.3
b7352000-b7366000 r-xp 00000000 08:03 1225807    /usr/lib/libz.so.1.2.3.3
b7366000-b7367000 rw-p 00013000 08:03 1225807    /usr/lib/libz.so.1.2.3.3
b7367000-b737c000 r-xp 00000000 08:03 1225091    /usr/lib/libICE.so.6.3.0
b737c000-b737e000 rw-p 00014000 08:03 1225091    /usr/lib/libICE.so.6.3.0
b737e000-b737f000 rw-p b737e000 00:00 0 
b737f000-b7386000 r-xp 00000000 08:03 1225105    /usr/lib/libSM.so.6.0.0
b7386000-b7387000 rw-p 00006000 08:03 1225105    /usr/lib/libSM.so.6.0.0
b7387000-b73d4000 r-xp 00000000 08:03 1225156    /usr/lib/libXt.so.6.0.0
b73d4000-b73d8000 rw-p 0004c000 08:03 1225156    /usr/lib/libXt.so.6.0.0
b73d8000-b73d9000 rw-p b73d8000 00:00 0 
b73d9000-b73dd000 r-xp 00000000 08:03 1225126    /usr/lib/libXdmcp.so.6.0.0
b73dd000-b73de000 rw-p 00003000 08:03 1225126    /usr/lib/libXdmcp.so.6.0.0
b73de000-b73e0000 r-xp 00000000 08:03 1225115    /usr/lib/libXau.so.6.0.0
b73e0000-b73e1000 rw-p 00001000 08:03 1225115    /usr/lib/libXau.so.6.0.0
b73e1000-b7525000 r-xp 00000000 08:03 490667     /lib/tls/i686/cmov/libc-2.6.1.so
b7525000-b7526000 r--p 00143000 08:03 490667     /lib/tls/i686/cmov/libc-2.6.1.so
b7526000-b7528000 rw-p 00144000 08:03 490667     /lib/tls/i686/cmov/libc-2.6.1.so
b7528000-b752b000 rw-p b7528000 00:00 0 
b752b000-b75e7000 r-xp 00000000 08:03 1225351    /usr/lib/libglib-2.0.so.0.1400.1
b75e7000-b75e8000 rw-p 000bc000 08:03 1225351    /usr/lib/libglib-2.0.so.0.1400.1
b75e8000-b75ea000 r-xp 00000000 08:03 490670     /lib/tls/i686/cmov/libdl-2.6.1.so
b75ea000-b75ec000 rw-p 00001000 08:03 490670     /lib/tls/i686/cmov/libdl-2.6.1.so
b75ec000-b75ed000 rw-p b75ec000 00:00 0 
b75ed000-b75f0000 r-xp 00000000 08:03 1225361    /usr/lib/libgmodule-2.0.so.0.1400.1
b75f0000-b75f1000 rw-p 00002000 08:03 1225361    /usr/lib/libgmodule-2.0.so.0.1400.1
b75f1000-b762b000 r-xp 00000000 08:03 1225399    /usr/lib/libgobject-2.0.so.0.1400.1
b762b000-b762c000 rw-p 0003a000 08:03 1225399    /usr/lib/libgobject-2.0.so.0.1400.1
b762c000-b7630000 r-xp 00000000 08:03 1225132    /usr/lib/libXfixes.so.3.1.0
b7630000-b7631000 rw-p 00003000 08:03 1225132    /usr/lib/libXfixes.so.3.1.0
b7631000-b76a6000 r-xp 00000000 08:03 1224101    /usr/lib/libcairo.so.2.11.5
b76a6000-b76a8000 rw-p 00074000 08:03 1224101    /usr/lib/libcairo.so.2.11.5
b76a8000-b76e3000 r-xp 00000000 08:03 1224490    /usr/lib/libpango-1.0.so.0.1800.3
b76e3000-b76e5000 rw-p 0003b000 08:03 1224490    /usr/lib/libpango-1.0.so.0.1800.3
b76e5000-b76e7000 r-xp 00000000 08:03 1225124    /usr/lib/libXdamage.so.1.1.0
b76e700Aborted (core dumped)

```


You can find the hotkeys package with "aptitude show hotkeys", I would try a newer version of the package but I couldn't find a homepage for this package.

---

