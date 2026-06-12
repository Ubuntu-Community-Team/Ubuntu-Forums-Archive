---
title: "Error when running Firefox through VNC"
date: 2007-06-07
forum: General Help
---

### Post by srunni on 2007-06-07
Hi,

When I try to run Firefox through VNC, I get ```
X Error: BadRequest (invalid request code or no such operation) 1
  Major opcode:  146
  Minor opcode:  2
  Resource id:  0x2600001
Xlib:  extension "XInputExtension" missing on display "kakkarot.local:1.0".
Failed to get list of devices
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 190 error_code 1 request_code 146 minor_code 23)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Does anyone know if there's a solution to this problem?

Thanks in advance for the help!!

---

### Post by thesnizz on 2007-06-08
I am also having this problem and would like to know how to resolve it.

I'm using vnc4server as my vnc server and Kubuntu 7.04 as my distribution. 

Thanks

---

### Post by srunni on 2007-06-08
Yeah, that's exactly what I'm using - vnc4server and Kubuntu Feisty. I set up the VNC service using the tutorial at [http://ubuntuforums.org/showthread.php?t=259448](http://ubuntuforums.org/showthread.php?t=259448) .

---

### Post by thesnizz on 2007-06-13
Bump.

Does anyone have any ideas?

Thanks

---

### Post by srunni on 2007-06-14
One other thing that should be mentioned is that basic graphical programs like xclock and xload work just fine.

---

### Post by thesnizz on 2007-06-20
I was having problems with all GTK+ applications (including FireFox) but seem to have resolved them by doing the following:

[LIST]
[*]Downloading vnc4server 4.1.2 from realvnc.com
[*]Installing it by running the command "vncinstall /usr/local/bin"
[*]Installing the package "libstdc++2.10-glibc2.2" from the package repository
[*]Starting the vncserver by using the command "vncserver -geometry 1024x768 -fp /usr/share/fonts/X11/misc"
[/LIST]

Hopefully vnc4server 4.1.2 is added to the repositories soon as it seems to have been the solution.

Hope this helps you as well!

---

### Post by srunni on 2007-06-22
I think it might've been added actually, since I'm not having the issue anymore.

---

### Post by geek.de.nz on 2007-08-12
This issue was still there for me. After a bit of googling and looking i found out that making your /etc/xinetd.d/Xvnc file look like this helps:

service Xvnc
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = -inetd :1 -query localhost -geometry 1024x768 -depth 16 -once -fp /usr/share/X11/fonts/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES
        port = 5901
}

---

### Post by fatmano on 2007-11-27
Not sure if you are still having the issue, but I was having the same issue and it was because I was ssh tunneling and not passing the -X to ssh.
ssh -X -p<myPort#> -L 5901:localhost:5901 <userName>@<machineToShow>

machineToShow> vncserver :1

Then locally fire up vncviewer and when it asks for server I use 127.0.0.1 :1

HTH

-eo

---

### Post by srunni on 2007-11-28
I haven't tried in a while - I'll give it a shot.

---

