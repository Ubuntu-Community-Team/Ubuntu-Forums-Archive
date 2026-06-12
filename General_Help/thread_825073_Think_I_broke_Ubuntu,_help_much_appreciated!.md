---
title: "Think I broke Ubuntu, help much appreciated!"
date: 2008-06-10
forum: General Help
---

### Post by Aiello on 2008-06-10
Well, this is kind of a long story, so here it goes:

I had recently installed Cairo Dock to add some eye candy, as I was getting tired of gnome panels. The only thing missing for the dock was a main menu. Using this tutorial:[http://translate.google.com/translate?u=http%3A%2F%2Fwww.cairo-dock.org%2Fbg_topic.php%3Ft%3D407&sl=fr&tl=en&hl=EN&ie=UTF-8]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.cairo-dock.org%2Fbg_topic.php%3Ft%3D407&sl=fr&tl=en&hl=EN&ie=UTF-8") on the Cairo Dock forums, I attempted to make a gnome menu in the dock.
 
Everything was going well until I had to, I guessing move(?)(I'm still quite a newb), the script I installed during the tutorial into the folder with my custom Cairo theme (black and white) in it. This is the script I entered into a terminal: ```
 mv Appl_Menu.py ~ / .cairo-dock/themes / black and white / launchers 
```It kept saying that the directory I was trying to move it to (located at ~/cairo-dock/themes/black and white/launchers) could not be found. I tried using 'sudo' in front of the command, but that provided the same results. I got rather annoyed with it and it was late, so I closed the terminal and pressed icon on the gnome panel that brings up the shut-down, log off, ect. stuff. Except, for some reason, the shut-down option was missing. I didn't think much of it, so to get around this, I just logged off and used the shut-down button in my GDM screen. The computer shut down fine.

Now this is the part where weird things start to happen. I turn on the computer today and everything seems fine. I select Ubuntu from the grub screen, it loads the GDM screen, and I enter my user name and password. When I hit enter, I get this error message:```
You home directory is listed as :'/home/eric' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a fail safe session
``` It then gives me an option for yes or no. I select no, and it brings me back to the GDM screen. I re-enter my user name and password, hit enter, and the same warning comes up. This time, I click yes. I then get a new warning that says: ```
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being used. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
```It gives me an OK button, and I click it. It then seems to start to load only for another warning to pop up and say: ```
Your sessions only lasted less than 10 seconds. If you have not logged out yourself this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the fail safe sessions to see if you can fix this problem.

view details (~/.xsession-error file)

(process: 6006): Gtk-WARNING**: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see: http://www.gtk.org/setuid.html
Refusing to initialize GTK+

(process: 6010): Gtk-WARNING**: This process is currently running setuid or setgid. This is not a supported use of GTK+. You must create a helper program instead. For further details, see: http://www.gtk.org/setuid.html
Refusing to initialize GTK+

/ect/gdm/xsession: Begiinning session setup...
Can't create dir /home/eric/Desktop
Can't create dir /home/eric/Desktop
Can't create dir /home/eric/Templates
Can't create dir /home/eric/Public
Can't create dir /home/eric/Documents
Can't create dir /home/eric/Music
Can't create dir /home/eric/Pictures
Can't create dir /home/eric/Videos
 
(x-session-manager: 6003): libgnomevfs- WARNING**: Unable to create ~/.gnome directory: No such file or directory. Could not create per-user gnome configuration directory '/home/eric/.gnome2/': No such file or directory.
``` 
It then gives me an option to click OK. I do, and it sends me back to the GDM screen.

 I have tried to log in with the GNOME Failsafe session selected under 'Sessions', but it sends me through the same thing. Bottom live of this post is**_can this be fixed without a clean install?_**I have been using Ubuntu for almost 6 months now and I haven't had one problem with it until I did this. Any suggestions on how to fix this? Please?

-Thanks!!!!

---

### Post by sdennie on 2008-06-10
Is there a file named /home/launchers now?  If so, does it contain what was previously your home directory?

---

### Post by Habbit on 2008-06-10
Maybe your home dir got its permissions messed up. Try to reset its permissions through the root account with the chown command.

---

### Post by Aiello on 2008-06-10
Hm... accessing my Linux partition using the live cd shows that 'eric' (the user/folder that should be under home) is just sitting there in the very top of the file system, along with usr, root, home, ect. If I just drag and drop 'eric' into 'home', should I be all set?

---

### Post by sdennie on 2008-06-10
As long as the permissions are set correctly, that should work, yes.

---

### Post by Aiello on 2008-06-10
Think I should just run gksu nautilus in the alt+f2 box-diologe(don't have a better name for it) and just drag and drop?

---

### Post by sdennie on 2008-06-10
If you are more comfortable with gui tools that would probably do it.  From the commandline you could also run this command:

```

sudo mv /eric /home

```

---

### Post by Aiello on 2008-06-10
Ha! That worked! Thanks a ton!

---

### Post by sdennie on 2008-06-10
Glad that worked.  For future reference, if you typed the offending command exactly how you posted it above, I believe the spaces in the path are what caused the problem.  It should have been:

```

mv Appl_Menu.py "~/.cairo-dock/themes/black and white/launchers"

```

You need everything squashed together.  Also, you need the quotes so that "black and white" doesn't end up looking like multiple files.

---

### Post by Aiello on 2008-06-10
Thanks again! going to through a [SOLVED] infront of this now.

---

