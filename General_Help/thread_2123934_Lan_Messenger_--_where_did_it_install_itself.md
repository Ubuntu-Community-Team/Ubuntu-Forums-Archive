---
title: "Lan Messenger -- where did it install itself?"
date: 2013-03-09
forum: General Help
---

### Post by Rocket J Squirrel on 2013-03-09
I installed Lan Messenger ( [http://lanmsngr.sourceforge.net/index.php](http://lanmsngr.sourceforge.net/index.php) ) from the .deb but it didn't show up on any of the Lubuntu menus and I don't know where the executable went. I'd like to set up the launcher under LXDE's "Accessories" menu -- how can I do that?

---

### Post by Frogs Hair on 2013-03-09
Do you know if the application has a GUI or does it run in the terminal on Linux ?  If terminal based this would explain the lack of a menu entry.

---

### Post by tgalati4 on 2013-03-09
First find the name of the application:

```
apropos LAN
```

Then find the location of the program:

```
which lanmessenger
```

If not named lanmessenger then change it to what it is called.

To run it, type *lanmessenger* on the command line and see if it comes up.

---

### Post by Rocket J Squirrel on 2013-03-09
Thanks, all. The screenshots on the application's page at [http://lanmsngr.sourceforge.net/index.php](http://lanmsngr.sourceforge.net/index.php) certainly suggest that Lan Messenger has a gui. "apropos lan" did not bring up anything pointing to Lan Messenger. 

But I used "find" to look for recently modified files and it brought me to /usr/lib/lmc  In there was lmc.sh, but it doesn't run, just generates a "This is not a Canonical 'designed' product" and a couple of errors about null pixmaps. Looks to be a broken product.

---

### Post by tgalati4 on 2013-03-09
What is the contents of lmc.sh?

```
cat lmc.sh
```

---

### Post by Rocket J Squirrel on 2013-03-09
Good thinking.
```

jack@jack-Aspire-one:/usr/lib/lmc$ cat lmc.sh
 
#!/bin/sh
 appname=lan-messenger


 dirname=/usr/lib/lmc
 tmp="${dirname#?}"


 if [ "${dirname%$tmp}" != "/" ]; then
 dirname=$PWD/$dirname
 fi


 $dirname/whitelist $appname


 LD_LIBRARY_PATH=$dirname
 export LD_LIBRARY_PATH
 $dirname/$appname $*

```

Gives an appname but,

```

jack@jack-Aspire-one:/usr/lib/lmc$ lan-messenger
lan-messenger: command not found

```


(I hope I did the "code" part right. Dang, doesn't look like it.)

---

### Post by coldcritter64 on 2013-03-09
> **Rocket J Squirrel said:**
> ...
</code>


(I hope I did the "code" part right. Dang, doesn't look like it.)

They will work if you edit them to [noparse]```
<your-post-contents>
```[/noparse] tags. Cheers.

Edit: an easy way is to highlight the post contents and press the button marked with a # symbol in your editor, you may need to select the advanced editor for this function. This inserts the correct tags for you.

---

### Post by Rocket J Squirrel on 2013-03-09
Thanks for fixing the code.

---

### Post by QIII on 2013-03-09
@Rocket J Squirrel --

When you are composing your message initially, if you click the "#" button in the tool bars above the text box, the code tags will be added.  Place your text between them.

Best wishes!

---

### Post by tgalati4 on 2013-03-09
The downloaded debian package is for i386 which means 32-bit architecture.  Are you trying to run it on a 64-bit machine?

tgalati4@Mint14-Extensa /boot $ uname -a
Linux Mint14-Extensa 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 **x86_64 x86_64 x86_64 GNU/Linux**

---

### Post by Rocket J Squirrel on 2013-03-09
Excellent idea. 

```
jack@jack-Aspire-one:/usr/lib/lmc$ uname -aLinux jack-Aspire-one 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:20:02 UTC 2013 i686 i686 i386 GNU/Linux

```

---

### Post by tgalati4 on 2013-03-09
You are running i386 kernel which is 32-bit, so that is not the issue.

```
which lan-messenger
cd /usr/lib/lmc
sudo chmod +x lmc.sh
```

Can you cut-and-paste the exact output from:

```
./lmc.sh
```

---

### Post by Rocket J Squirrel on 2013-03-10
Thank you.

```
jack@jack-Aspire-one:/usr/lib/lmc$ which lan-messengerjack@jack-Aspire-one:/usr/lib/lmc$ cd /usr/lib/lmc
jack@jack-Aspire-one:/usr/lib/lmc$ sudo chmod +x lmc.sh
[sudo] password for jack: 
jack@jack-Aspire-one:/usr/lib/lmc$ ./lmc.sh
This is not a Canonical "designed" product.
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap





```
And it just hangs after that. ^C breaks me out. 
```
^Cjack@jack-Aspire-one:/usr/lib/lmc$ 
```

---

### Post by tgalati4 on 2013-03-10
I'm out of ideas at this point.

---

### Post by Rocket J Squirrel on 2013-03-10
Um, how about "broken installer or broken program?"

---

### Post by tgalati4 on 2013-03-10
The source code is available, so you could download it, install *build-essentials* and try to compile it.  You will quickly find the issue when a missing dependency shows up.  I quickly looked over the website, and I could not find a target Ubuntu distro that the system was built on.  So depending on how badly you need this service, You might try your hand at compiling, or send an email to the developers and point to this thread.

---

### Post by Rocket J Squirrel on 2013-03-10
"[...] or send an email to the developers and point to this thread."

Huh, yeah. I need a cross-platform (Windows & Linux) LAN-only IM-like  app. But I bet there are others. I'll look around and see what else is available.

Thanks to all for your assistance!

---

### Post by tgalati4 on 2013-03-10
Check out moodle.

---

### Post by Rocket J Squirrel on 2013-03-11
Moodle looks like a pretty big package of services. I can't determine whether they have a stand-alone cross-platform no-server IM app.

---

### Post by Rocket J Squirrel on 2013-03-15
It's me again. I have not gotten around to uninstalling Lan-Messenger yet. So I put this Netbook into Standby and carried it with me to a pub, where I am having lunch. I opened the laptop and was greeted with my Lubuntu login screen -- and, a popup in the lower left corner saying that "Lan-Messenger is connected." I logged on, and shortly thereafter the popup went away. There is still no entry for Lan-Messenger on any of the Lubuntu launch menus. And there is this:```
jack@jack-Aspire-one:~$ ps -e | grep lan 1031 ?00:00:27 irqbalance 179000:01:25 lan-messenger
```So it's running but there doesn't seem to be a way to get to it. Near as I can tell, anyway. Alt-tabbing doesn't show it. Suggestions?

---

### Post by tgalati4 on 2013-03-15
So it looks like it is running, but I've never used it so I don't know how to open a dialog window.  Moodle is an elearning package that allows a group to collaborate and learn, so I figured it has an internal messaging system.  Perhaps overkill for what you want to do.  

Perhaps there is a hot-key to bring up a dialog box?  Try Control-L or Control-M.  Control-L will bring up a URL box in Firefox and open a location on the Desktop, so don't use that.

Viewing their support forums is not encouraging:

[http://lanmsngr.sourceforge.net/forum/viewforum.php?f=6](http://lanmsngr.sourceforge.net/forum/viewforum.php?f=6)

---

### Post by Rocket J Squirrel on 2013-03-15
Aye, tgalati4 -- the forum has plenty of questions, few answers. Nevertheless, I will register and try my luck. I tried all ctrl-letter keys on the Lubuntu desktop and nothing happened. It must be a secret.

---

### Post by Rocket J Squirrel on 2013-03-15
But wait -- on Lubuntu's normally auto-hidden taskbar which pops up when the mouse cursor is at the bottom of the monitor, over on the right-hand side, which on Windows would be called the "system tray" or, more accurately, the "notification area," I see an new icon. Right-clicking on it, I see it is the Lan-Messenger icon, and it seems to provide the usual IM functions. Promising, this is. Why did I start to speak like Yoda?I'll install it on a Windows computer and see how it works out.

---

### Post by tgalati4 on 2013-03-15
Do or Do not.  There is no try.

---

### Post by Rocket J Squirrel on 2013-03-16
LOL. I finally gave up on Lan-Messenger. There must be a way to add recipients to the address book but I'll be darned if I can find it.

---

