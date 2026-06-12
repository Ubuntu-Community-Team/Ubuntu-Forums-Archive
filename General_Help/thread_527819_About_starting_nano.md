---
title: "About starting nano"
date: 2007-08-17
forum: General Help
---

### Post by satimis on 2007-08-17
Hi folks,


Each time on starting nano;

$ nano```

Error reading /home/satimis/.nano_history: Permission denied

Press Enter to continue starting nano.

```

I have to press [Enter] to start it.
$ ls -l /home/satimis/.nano_history ```

-rw-rw---- 1 root root 41 2007-08-17 14:51 /home/satimis/.nano_history

```

$ sudo cat /home/satimis/.nano_history ```

canonical
universe
canonical.com
cdrom

```


Pls advise how to fix this problem


satimis

---

### Post by aldenhg on 2007-08-17
This is probably a dumb questions, but have you tried ```
sudo nano /whatever/file/you/want/to/edit
yoursupersectretpassword
```
You shouldn't have to do that when you're editing a file that you have permission to, but if that's the case the nano executable might have the wrong permissions.

---

### Post by satimis on 2007-08-17
> **aldenhg said:**
> This is probably a dumb questions, but have you tried ```
sudo nano /whatever/file/you/want/to/edit
yoursupersectretpassword
```
You shouldn't have to do that when you're editing a file that you have permission to, but if that's the case the nano executable might have the wrong permissions.
Hi aldenhg,

$ ls -l /usr/bin/nano ```

lrwxrwxrwx 1 root root 9 2007-07-24 22:20 /usr/bin/nano -> /bin/nano
```

$ ls -l /bin/nano ```

-rwxr-xr-x 1 root root 163560 2007-02-07 19:32 /bin/nano

```

Shall I run;

$ sudo chmod 777 /bin/nano

???

TIA


B.R.
satimis

---

### Post by garas on 2007-08-17
try
```
$ sudo chown satimis /home/satimis/.nano_history
$ sudo chgrp satimis /home/satimis/.nano_history
```

---

### Post by dagnabit dang doohickey on 2007-08-17
Another option is to just delete your nano history file. A new one will be created the next time you run nano.

---

### Post by matigol on 2007-08-17
> **dagnabit dang doohickey said:**
> Another option is to just delete your nano history file. A new one will be created the next time you run nano.

I am OK.
maybe it's only a configuration file and maybe it can be deleted.

---

### Post by stchman on 2007-08-17
> **satimis said:**
> Hi folks,


Each time on starting nano;

$ nano```

Error reading /home/satimis/.nano_history: Permission denied

Press Enter to continue starting nano.

```

I have to press [Enter] to start it.
$ ls -l /home/satimis/.nano_history ```

-rw-rw---- 1 root root 41 2007-08-17 14:51 /home/satimis/.nano_history

```

$ sudo cat /home/satimis/.nano_history ```

canonical
universe
canonical.com
cdrom

```


Pls advise how to fix this problem


satimis

I had the same problem with the .kde folder, here is how you might be able to fix your problem:

```
sudo chown -R $USER:$USER ~/.nano_history

chmod -R 755 ~/.nano_history
```

Hope this helps.

---

### Post by satimis on 2007-08-17
> **stchman said:**
> I had the same problem with the .kde folder, here is how you might be able to fix your problem:

```
sudo chown -R $USER:$USER ~/.nano_history

chmod -R 755 ~/.nano_history
```

Hope this helps.
Hi stchman,


Your advice works here.  Thanks


$ sudo chown -R $satimis:$satimis ~/.nano_history
Password:
No complaint.

$ chmod -R 755 ~/.nano_history```

chmod: changing permissions of `/home/satimis/.nano_history': Operation not permitted

```

$ sudo chmod -R 755 ~/.nano_history
No complaint


$ nano
starting nano w/o complaint

But exiting nano, it prompted```

Error writing /home/satimis/.nano_history: Permission denied

```

satimis

---

### Post by jamvegan on 2007-08-17
Hi, satimis,

> $ sudo chown -R $satimis:$satimis ~/.nano_history

The command that stchman suggested:
> sudo chown -R $USER:$USER ~/.nano_history
is literally how you should type it.  The bash shell resolves "$USER" to "satimis".  You could alternately run the command the way that you did, but without the dollar signs before your user name.  Running it the way that you did actually did nothing (though, unhelpfully, it failed silently).

This could be related to the issues in your other thread.  You should probably run:
$ ls -al
in your home directory.  Generally speaking, everything you see should be owned by you, not root (except for "..").  If you find other files, especially configuration files, that are owned by root, you should probably run the chown command on them, as well.

jamvegan

---

### Post by satimis on 2007-08-17
> **jamvegan said:**
> Hi, satimis,


The command that stchman suggested:

is literally how you should type it.  The bash shell resolves "$USER" to "satimis".  You could alternately run the command the way that you did, but without the dollar signs before your user name.  Running it the way that you did actually did nothing (though, unhelpfully, it failed silently).

This could be related to the issues in your other thread.  You should probably run:
$ ls -al
in your home directory.  Generally speaking, everything you see should be owned by you, not root (except for "..").  If you find other files, especially configuration files, that are owned by root, you should probably run the chown command on them, as well.

Hi jamvegan,


Ah I get it.  Tks


Performed following steps

$ ls -al | grep .nano```

-rwxr-xr-x  1 root    root         41 2007-08-17 14:51 .nano_history

```

$ sudo chown -R $USER:$USER ~/.nano_history
Password:
No complaint

$ chmod -R 755 ~/.nano_history
no complaint

ls -al | grep .nano```

-rw-------  1 satimis satimis      41 2007-08-18 09:26 .nano_history

```


$ nano
staring a blank document

on exiting, it did not complaint.


B.R.
satimis

---

### Post by kerry_s on 2007-08-18
nano? move up a notch> sudo apt-get install mc

mcedit
or
mcedit /path/to/file
or
mc

---

### Post by stchman on 2007-08-18
> **satimis said:**
> Hi stchman,


Your advice works here.  Thanks


$ sudo chown -R $satimis:$satimis ~/.nano_history
Password:
No complaint.

$ chmod -R 755 ~/.nano_history```

chmod: changing permissions of `/home/satimis/.nano_history': Operation not permitted

```

$ sudo chmod -R 755 ~/.nano_history
No complaint


$ nano
starting nano w/o complaint

But exiting nano, it prompted```

Error writing /home/satimis/.nano_history: Permission denied

```

satimis

$USER returns the user currently logged in.

---

### Post by satimis on 2007-08-18
> **stchman said:**
> $USER returns the user currently logged in.
Noted with tks.

satimis

---

### Post by satimis on 2007-08-18
> **kerry_s said:**
> nano? move up a notch> sudo apt-get install mc

mcedit
or
mcedit /path/to/file
or
mc
Hi kerry_s,


Tks for your advice.

I ran mc (midnight commander) for prolonged time in the past.  It is a powerful editor having file manager function.


Just tested it.

$ sudo apt-get install mc.

exited Fluxbox and restarted X


It is installed but wiping out other components on the "Tools" menu.  

Removed it.  It doesn't matter.  It is only a test.


B.R.
satimis

---

### Post by kerry_s on 2007-08-18
> **satimis said:**
> Hi kerry_s,


Tks for your advice.

I ran mc (midnight commander) for prolonged time in the past.  It is a powerful editor having file manager function.


Just tested it.

$ sudo apt-get install mc.

exited Fluxbox and restarted X


It is installed but wiping out other components on the "Tools" menu.  

Removed it.  It doesn't matter.  It is only a test.


B.R.
satimis

huh?? "tools" menu? why did you have to exit fluxbox & restart X?
i must be tired, i don't understand. what ever works for you. :)

---

### Post by satimis on 2007-08-18
> **kerry_s said:**
> huh?? "tools" menu?

Yes, I have a "Tools" menu for "screenshot" on Fluxbox

> 
 why did you have to exit fluxbox & restart X?

After installing "mc" I can't find it on the menu of Fluxbox.  After restarting X I found "mc" on the "Tools" menu.


satimis

---

### Post by kerry_s on 2007-08-18
> **satimis said:**
> Yes, I have a "Tools" menu for "screenshot" on Fluxbox


After installing "mc" I can't find it on the menu of Fluxbox.  After restarting X I found "mc" on the "Tools" menu.


satimis

sudo apt-get install scrot

xedit ~/.fluxbox/keys

Print :exec ~/.1  
Alt Print :exec ~/.2
Ctrl Print :exec ~/.3

.1
#!/bin/sh
xterm -geometry 30x0+0+0 -T "Full Screenshot" -e scrot %T.jpg 

.2
#!/bin/sh
xterm -geometry 35x0+0+0 -T "Wait 5 Screenshot" -e scrot -cd 5 %T.jpg 

.3
#!/bin/sh
xterm -geometry 30x0+0+0 -T "Select Screenshot" -e scrot -sb %T.jpg


chmod +x ~/.1
chmod +x ~/.2
chmod +x ~/.3

~/.fluxbox/menu is>
/etc/X11/fluxbox/menu = sudo update-menus > click restart

~/.fluxbox/menu = update-menus > click restart

Fluxbox was my regular WM, not everything needs to be in the menus, learn to use your ~/.fluxbox/keys.
Alot of people use fluxbox here, don't be afraid to ask for tips, if there's a need, someone knows a easy way. :)

Edit: forgot, if you don't want to see the xterm for screen shots you can use this instead
scrot %T.jpg && xmessage "Screenshot done!"
scrot -cd 5 %T.jpg && xmessage "Screenshot done!"
scrot -sb %T.jpg && xmessage "Screenshot done!"

you might than want to pretty up xmessage.
xedit ~/.Xdefaults

.xmessage.form.okay.shapeStyle: rectangle
.xmessage.form.okay.background: gray
.xmessage.form.okay.foreground: black
xmessage*message*background: white
xmessage*defaultButton: okay
Xmessage.form.message.Scroll:  WhenNeeded

---

### Post by satimis on 2007-08-19
Hi kerry_s,


Tks for your advice.

> 
sudo apt-get install scrot

xedit ~/.fluxbox/keys

Print :exec ~/.1  
Alt Print :exec ~/.2
Ctrl Print :exec ~/.3

.1
#!/bin/sh
xterm -geometry 30x0+0+0 -T "Full Screenshot" -e scrot %T.jpg 

.2
#!/bin/sh
xterm -geometry 35x0+0+0 -T "Wait 5 Screenshot" -e scrot -cd 5 %T.jpg 

.3
#!/bin/sh
xterm -geometry 30x0+0+0 -T "Select Screenshot" -e scrot -sb %T.jpg


chmod +x ~/.1
chmod +x ~/.2
chmod +x ~/.3

up to here I'm clear.

> 
~/.fluxbox/menu is>
/etc/X11/fluxbox/menu = sudo update-menus > click restart

~/.fluxbox/menu = update-menus > click restart

Whether on Console/Xterm run above 2 commands?  Pls advise.  Thanks.

> 
Fluxbox was my regular WM, not everything needs to be in the menus, learn to use your ~/.fluxbox/keys.
Alot of people use fluxbox here, don't be afraid to ask for tips, if there's a need, someone knows a easy way. :)

Noted.  I only run Fluxbox on this server.

> 
Edit: forgot, if you don't want to see the xterm for screen shots you can use this instead
scrot %T.jpg && xmessage "Screenshot done!"
scrot -cd 5 %T.jpg && xmessage "Screenshot done!"
scrot -sb %T.jpg && xmessage "Screenshot done!"

Whether run above commands on Xterm?  What will be their difference?

> 
you might than want to pretty up xmessage.
xedit ~/.Xdefaults

.xmessage.form.okay.shapeStyle: rectangle
.xmessage.form.okay.background: gray
.xmessage.form.okay.foreground: black
xmessage*message*background: white
xmessage*defaultButton: okay
Xmessage.form.message.Scroll:  WhenNeeded
Whether add above lines on .Xdefaults?  TIA


B.R.
satimis

---

### Post by kerry_s on 2007-08-19
> Whether on Console/Xterm run above 2 commands? Pls advise. Thanks.

This depends on how you have your menu setup, the stock menu setup uses> /etc/X11/fluxbox/menu <so if you need to update it after a application install you run> sudo update-menus <in xterm to up date the menu with the new applications.

if you customize your menu and still want the debian menu, you can change the include to> ~/.fluxbox/menu <which will put the menu file in ~/.fluxbox/* so you don't need root to update, you just run> update-menus <and the new applications will be added to the debian menu.

> Whether run above commands on Xterm? What will be their difference?

this is just another way to run scrot. "scrot" is a command line screen shooter. when you run "scrot" from key bindings you might want to know when it's done, so using> scrot %T.jpg && xmessage "Screenshot done!" <will take a screen shot and then display a message to let you know it finished. normal scrot use would be something like> scrot 1.jpg <which takes a screenshot of the whole screen. you can run the commands in xterm to see what it does, there are many ways to do it, those are just some of the ways i've used it, you might come up with your own way. :)

```
Whether add above lines on .Xdefaults? TIA
```

yes, those are xdefault settings to change the look of a applicaton, in this case xmessage, the stock xmessage look is a little ugly, that cleans it up alittle. run> xmessage "how do i look" <in terminal to see what it looks like now. xmessage can be useful for displaying all kinds of messages or displaying the output of commands. 
example: say you want to see the ".xsession-errors" file on start up, you simply add> xmessage -file ~/.xsession-errors &<and it will display the ".xsession-errors" file at startup. in your case you might want to display a log at startup.example> xmessage -file /var/log/(the log) & <provided you have permission, will disply the log at startup. i have a friend who leaves himself messages, so he can remember what he was doing last.anyways

there's are alot of useful stuff that's part of X, there already installed might as well use them for something. good luck & have fun

---

### Post by satimis on 2007-08-20
Hi kerry_s,

> This depends on how you have your menu setup, the stock menu setup uses> /etc/X11/fluxbox/menu <so if you need to update it after a application install you run> sudo update-menus <in xterm to up date the menu with the new applications.

if you customize your menu and still want the debian menu, you can change the include to> ~/.fluxbox/menu <which will put the menu file in ~/.fluxbox/* so you don't need root to update, you just run> update-menus <and the new applications will be added to the debian menu.


this is just another way to run scrot. "scrot" is a command line screen shooter. when you run "scrot" from key bindings you might want to know when it's done, so using> scrot %T.jpg && xmessage "Screenshot done!" <will take a screen shot and then display a message to let you know it finished. 

Noted and thanks.

> 
normal scrot use would be something like> scrot 1.jpg <which takes a screenshot of the whole screen. you can run the commands in xterm to see what it does, there are many ways to do it, those are just some of the ways i've used it, you might come up with your own way.

This is the command I need.  On this PC, a LAMP server, I only make screenshot on the forms completed for download tech documents on Internet needed for fine-tuning the server.  I won't do graphic editing here.

> 
```
Whether add above lines on .Xdefaults? TIA
```

yes, those are xdefault settings to change the look of a applicaton, in this case xmessage, the stock xmessage look is a little ugly, that cleans it up alittle. run> xmessage "how do i look" <in terminal to see what it looks like now. xmessage can be useful for displaying all kinds of messages or displaying the output of commands. 
example: say you want to see the ".xsession-errors" file on start up, you simply add> xmessage -file ~/.xsession-errors &<and it will display the ".xsession-errors" file at startup. in your case you might want to display a log at startup.example> xmessage -file /var/log/(the log) & <provided you have permission, will disply the log at startup. i have a friend who leaves himself messages, so he can remember what he was doing last.anyways

there's are alot of useful stuff that's part of X, there already installed might as well use them for something. good luck & have fun
Noted.

Thanks again for your detail advice.


B.R.
satimiks

---

### Post by kerry_s on 2007-08-20
> This is the command I need. On this PC, a LAMP server, I only make screenshot on the forms completed for download tech documents on Internet needed for fine-tuning the server. I won't do graphic editing here.

you might want to crank up the quality then, for easier reading, no blurry text.
scrot -q 100 1.png

a little slow, barely noticeable, but its the best pic quality. :)

---

### Post by RedSquirrel on 2007-08-20
> **kerry_s said:**
> This depends on how you have your menu setup, the stock menu setup uses> /etc/X11/fluxbox/menu <so if you need to update it after a application install you run> sudo update-menus <in xterm to up date the menu with the new applications.

Minor correction:

On Ubuntu, the default menu is /etc/X11/fluxbox/fluxbox-menu. It is updated automatically when you install software (or it should be, if it's working properly ;)). Hence, there should be no need to run 'sudo update-menus' after you install something.



> **kerry_s said:**
>  if you customize your menu and still want the debian menu, you can change the include to> ~/.fluxbox/menu <which will put the menu file in ~/.fluxbox/* so you don't need root to update, you just run> update-menus <and the new applications will be added to the debian menu.

That's one way to do it. Another way is to include /etc/X11/fluxbox/menudefs.hook instead. This is the Debian menu (just applications, not the Fluxbox stuff such as Restart, Logout, etc.).

```
[submenu] (Debian Menu)
[include] (/etc/X11/fluxbox/menudefs.hook)
[end]

```It is updated automatically when you install software.

---

### Post by kerry_s on 2007-08-20
Ahh RedSquirrel, now you come to save my A**. i was straining to remember. :lolflag: Thanks

---

