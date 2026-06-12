---
title: "How to open files from terminal"
date: 2008-06-09
forum: General Help
---

### Post by mman426 on 2008-06-09
Hey, I am kinda new to linux and I am just starting to use the terminal for more things and I was wondering if there is a way to open files, such as pictures, videos, and music, from the terminal. I was wondering because in the cmd prompt in windows (which I also just started using) you can open a file by just typing in the name of that file. Thanks in advance for any help.

---

### Post by wdaniels on 2008-06-09
In the Gnome desktop you can use the command gnome-open for this, e.g.

```
gnome-open mypicture.jpg
```

The generic equivalent, which should work for all Linux desktops that work with freedesktop.org standards, is [xdg-open]("http://portland.freedesktop.org/xdg-utils-1.0/xdg-open.html").

---

### Post by VMC on 2008-06-09
> **mman426 said:**
> Hey, I am kinda new to linux and I am just starting to use the terminal for more things and I was wondering if there is a way to open files, such as pictures, videos, and music, from the terminal. I was wondering because in the cmd prompt in windows (which I also just started using) you can open a file by just typing in the name of that file. Thanks in advance for any help.

Yes, almost everything. The GUI part is just that, a graphics layered interface.
In fact sometimes it pays to start a program using the Terminal. 

Case in point. It's fixed now, but Wine kept failing. I started it through the Terminal.
For example:
wine C:\\"Program Files"\\ImgBurn\\ImgBurn.exe

Will start ImgBurn using Wine and I can see any errors that may occur. Even though ImgBurn has its own log file that displays errors. Using the Terminal reveals more information that may be of value for trouble shooting.

---

### Post by mman426 on 2008-06-09
> **wdaniels said:**
> In the Gnome desktop you can use the command gnome-open for this, e.g.

```
gnome-open mypicture.jpg
```

The generic equivalent, which should work for all Linux desktops that work with freedesktop.org standards, is [xdg-open]("http://portland.freedesktop.org/xdg-utils-1.0/xdg-open.html").

Thanks that works perfectly, I really like to open from the terminal because I don't want to use the mouse and I want to increase my typing speed because right now it is pretty slow when I work in the terminal. I also figure that working in the terminal is the best way to learn the terminal, so I use it for pretty much everything now

---

### Post by wdaniels on 2008-06-09
> **mman426 said:**
> I really like to open from the terminal because I don't want to use the mouse and I want to increase my typing speed because right now it is pretty slow when I work in the terminal. I also figure that working in the terminal is the best way to learn the terminal, so I use it for pretty much everything now

That attitude will serve you well in Linux :)

---

### Post by tayl90mm on 2009-02-26
Hello,  I am a total newbie to ubuntu.
when i enter the command "gnome-open LOTR Evenstar.wma" nothing happens. could you please help. 
               thanks.

---

### Post by punx45 on 2009-02-26
> **tayl90mm said:**
> Hello,  I am a total newbie to ubuntu.
when i enter the command "gnome-open LOTR Evenstar.wma" nothing happens. could you please help. 
               thanks.

spaces (among other carachters) in filenames arent directly supported in the command line.  you need to "escape" the carachter (basically tell the interpreter its part of the file name rather than serving some other function).   the escape carachter is \  so it should look like

LOTR\ Evenstar.wma 

i think double quotes work too.   also, you can have the terminal auto complete your entry so you could type LOTR then press tab, and it will fill in the rest for you, including escaped carachters.   i use this alot for torrents since the name of most are so rediculously long :-/

if thats not the problem, then the wma file format might be

---

### Post by adult swim on 2009-02-26
another terminal trick is that you can enter in ```
gnome-open LO
``` and then hit the tab key.  if there is only one file in the directory that you are in that begins with the letters LO, it will complete the filename for you.

---

### Post by punx45 on 2009-02-26
and if there are files that are similar, it will fill in up to the point where the similarities end :)

---

### Post by abhilashm86 on 2009-02-26
well there are many applications for specific tasks to open files from terminal
feh- for viewing pictures
moc- for audio
mplayer- for video

---

### Post by c0mput3r_n3rD on 2009-06-30
hey tayI90mm, you can also use what's called the wild car ( * ). so you can type gnome-open LOTR* 
and it should open the file that starts with LOTR and ends in anything else.  The same can be used for extensions, such as..

mv *.jpg pictures

which would move any file with a .jpg extention into your pictures directory.

hope that helps a lil.

and btw the double quotes does work which i prefer to use.  you should also get into certain naming conventions that don't use a space but an "_" or an "-" or capitalzing the first letter of the each word after the first (programming style ;)   )

---

### Post by drinkblot on 2009-12-25
Is there anyway to open files with specific programs through terminal? For instance, vlcplayer? 

Thx

---

### Post by crtlbreak on 2009-12-27
> **drinkblot said:**
> Is there anyway to open files with specific programs through terminal? For instance, vlcplayer? 

Thx


yes
```
vlc /path/to/file
```

or 

```
ooffice /path/to/file
```

or 

```
gedit /path/to/file
```

will all tell the application to open the corresponding file.
hope this helps?

---

### Post by midcommander on 2010-08-13
Now, it's a progress.

To open file using default application (with root access)

```
 sudo gnome-opem /path/to/file 
```

To open file using non-default application

```
 sudo AppName /path/to/file 
```

But how about open application using portable application, will this code work out?

```
 sudo /path/to/AppName /path/to/file 
```

Well, anyway, I have no idea what is the application file or what is the extension for executed program for linux (similar to .exe file) because i have no idea how to find out where the short cut for application in main menu (such nautilus firfox mplayer, etc) will end up is.is it addressing file or addressing folder?

---

### Post by wdaniels on 2010-08-17
> **midcommander said:**
> But how about open application using portable application, will this code work out?

```
 sudo /path/to/AppName /path/to/file 
```

Yes. But normally you would not want to launch apps with sudo. There is no reason to run something as root unless it has to modify the system config. In fact, it is better not to.

Also, apps that are installed by proper Debain/Ubuntu packages should already be located in the "search path" so you do not need to specify the full path for the app if it is /bin /usr/bin /usr/local/bin for example. Run:

```
echo $PATH
```

...to see the list of paths that are automatically searched.

Things under /bin are very fundamental programs that the system organisation makes sure are available during boot. Things under /usr/bin are most of the usual apps installed by packages. Anything installed by the administrator manually (i.e. not packaged) should go under /usr/local/bin. I think other distros sometimes put that stuff under /opt. Anyway, most of the time there is nothing under /usr/local/bin or /opt.

You will also see /sbin and /usr/sbin folders, which is like "bin" only for sysadmin tools (i.e. the ones you might need to run with sudo).

> **midcommander said:**
> Well, anyway, I have no idea what is the application file or what is the extension for executed program for linux (similar to .exe file) because i have no idea how to find out where the short cut for application in main menu (such nautilus firfox mplayer, etc) will end up is.is it addressing file or addressing folder?

If you look under Perferences->Main Menu you can find the relevant app, right-click and select "Properties" then you will see the command for launching that app.

---

