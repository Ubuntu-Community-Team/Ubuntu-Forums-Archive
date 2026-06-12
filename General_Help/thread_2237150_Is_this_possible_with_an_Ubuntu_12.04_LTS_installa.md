---
title: "Is this possible with an Ubuntu 12.04 LTS installation."
date: 2014-07-31
forum: General Help
---

### Post by arunb on 2014-07-31
Hi,

target OS: Ubuntu 12.04 LTS (32 bit- Desktop)

Here is what I am planning to do.

I would like to remove the Ubuntu desktop (Unity or Gnome) completely, after the computer boots up and linux OS is finished loading, a script is run, this script runs a GUI based program on the computer, so instead of the desktop appearing I would like my application to start and run.

The application is a full screen one, and needs all the functionality required for a GUI based application.

Also I am planning to run the above setup on a touch screen based computer, so other functionality such as touchscreen, on-screen keyboard (onboard installed already) must also be available. The user will not be able to run any other apps other than mine.

Please give some ideas about how I can do this...

thanks
a

---

### Post by sudodus on 2014-07-31
I have no solution, but maybe a couple of tips.

- There are kiosk computers with software that only runs a web browser, for example Webconverger. You can see how that is done.

- You might modify the guest session in Ubuntu to only run your application instead of starting with the desktop.

---

### Post by efflandt on 2014-07-31
I did something similar on a Raspberry Pi to effectively boot right into Quake3. Although, at that time all I could find to auto login was a ksh script along with changing the getty. And Quake3 on the Pi runs in the console (X not required).

If the gui program you are running requires X, then you need to launch it in some window manager, so you would need to look into how to automatically run a program (and whatever is required for touchscreen) when doing startx.

But I found an easier way to do the auto login [http://littlesvr.ca/linux-stuff/articles/autologinconsole/autologinconsole.php](http://littlesvr.ca/linux-stuff/articles/autologinconsole/autologinconsole.php)

Instead of just launching something at the end of .bash_profile, you would want a loop that would just rerun whatever if the user tried to exit to the shell. And you would not want any other getty in /etc/inittab, so they cannot Ctrl+Alt+F# or Alt+F# to a different virtual terminal.

---

### Post by arunb on 2014-07-31
So the application should ideally be run from a web browser, say like a web app ?? or should I develop a standalone application for the front end?? 

let me make it clear what I have in mind...

I have a C++ application that does some low level jobs like hardware access to serial ports etc. The C++ application receives commands from the front end web page and executes actions, results are posted back to the front end.

The other scenario is that a single application handles the front and the back end....

Please give some ideas...

thanks
a

---

