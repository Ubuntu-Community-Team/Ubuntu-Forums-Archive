---
title: "Flash plugin problem with ARGB visuals causes crash"
date: 2007-02-14
forum: General Help
---

### Post by geck07 on 2007-02-14
Firefox crashes randomly when i load some sites and the debug message is:

[B][COLOR="Red"]The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 104 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/COLOR][/B]

also follow the discussion about this on :[https://launchpad.net/ubuntu/+source/firefox/+bug/14911](https://launchpad.net/ubuntu/+source/firefox/+bug/14911)

please help....

Geck0

---

### Post by geck07 on 2007-02-15
fixed the problem......
for those having the same problem...follow these instructions:

download install_flash_player_9.tar.gz from adobe website on ur desktop
untar it using:
    tar xvfz install_flash_player_9_linux.tar.gz

a few questions will be asked an the terminal will look like:

[B]
Copyright(C) 2002-2006 Adobe Macromedia Software LLC.  All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...



Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla
dir= /usr/lib/mozilla


----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/mozilla

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): y

Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): /usr/lib/firefox
dir= /usr/lib/firefox

WARNING: The Adobe Flash Player binary is a symbolic link.
         The installer will replace this symbolic link with the actual binary.



----------- Install Action Summary -----------

Adobe Flash Player 9 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n): n


Please log out of this session and log in for the changes to take effect.


The Adobe Flash Player installation is complete.
[/B]


Basically the trick is to install flash player to the firefox directory...

---

