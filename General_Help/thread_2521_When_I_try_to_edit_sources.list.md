---
title: "When I try to edit sources.list"
date: 2004-10-29
forum: General Help
---

### Post by akamjballar on 2004-10-29
Hello, I was trying to install jedit, on the site it says to chmod the file, and then edit it. I set the chmod to 777, and I am still not able to edit the file. This is the error I get:
[IMG]http://awptical.com/aptget.jpg[/IMG]

---

### Post by luiska on 2004-10-29
hi

Permission to edit the /etc/apt/sources.list is the key

I do the following from the command line which work for me:

sudo gedit /etc/apt/sources.list
password:

Hope it helps
Luiska

---

### Post by akamjballar on 2004-10-29
Why do I get this error?

```
root@ubuntu:/home/gurjit # apt-get install jedit
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
```

---

### Post by aschlapsi on 2004-10-29
Maybe you are running synaptic at the same time. You'll have to close synaptic when you want to use apt-get.

---

### Post by akamjballar on 2004-10-29
Thank you!

---

### Post by akamjballar on 2004-10-29
I finally have jedit installed via apt-get. Now I run the program from the menu. But it just loads for a few seconds, then nothing opens. I dont know whats wrong. It doesn't open anything at all. Please help

---

### Post by akamjballar on 2004-10-29
Never mind, I found out the problem. But I don't know how to fix it.

```
root@ubuntu:/home/gurjit # jedit
[error] main: Exception in thread "main"
[error] main: java.awt.AWTError: Cannot load AWT toolkit: gnu.awt.gtk.GtkToolkit not found in [file:/usr/share/jed
[error] main: it/jedit.jar, core:/]
[error] main:    at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at ja
[error] main: va.awt.Component.getToolkit() (/usr/lib/libgcj.so.4.0.0)
[error] main:    at java.awt.Component.getFontMetrics(jav
[error] main: a.awt.Font) (/usr/lib/libgcj.so.4.0.0)
[error] main:    at org.gjt.sp.jedit.gui.SplashScreen.SplashScreen() (Unkno
[error] main: wn Source)
[error] main:    at org.gjt.sp.jedit.GUIUtilities.showSplashScreen() (Unknown Source)
[error] main:    at org.gjt.sp.
[error] main: jedit.jEdit.main(java.lang.String[]) (Unknown Source)
root@ubuntu:/home/gurjit #
```

---

### Post by akamjballar on 2004-10-29
Wow, I fixed my problem again. NOw I am getting another problem. I tried fixing this one, but its too complex for me.

```
root@ubuntu:/home/gurjit # jedit
Warning: -mx32m option not RECOGNIZED by java-sablevm wrapper.
A not recognized option will be just passed to SableVM.
Note that we don't know if we should expect an argument here!
It almost _surely_ will result in an errors when the param is followed
by an argument. Refer to 'man java-sablevm' and 'man sablevm'.
Unknown option: -mx32m
Usage: jedit [<options>] [<files>]
        <file> +marker:<marker>: Positions caret at marker <marker>
        <file> +line:<line>: Positions caret at line number <line>
        --: End of options
        -background: Run in background mode
        -nobackground: Disable background mode (default)
        -gui: Only if running in background mode; open initial view (default)
        -nogui: Only if running in background mode; don't open initial view
        -log=<level>: Log messages with level equal to or higher than this to
         standard error. <level> must be between 1 and 9. Default is 7.
        -newplainview: Client instance opens a new plain view
        -newview: Client instance opens a new view (default)
        -plugins: Load plugins (default)
        -noplugins: Don't load any plugins
        -restore: Restore previously open files (default)
        -norestore: Don't restore previously open files
        -reuseview: Client instance reuses existing view
        -quit: Quit a running instance
        -run=<script>: Run the specified BeanShell script
        -server: Read/write server info from/to $HOME/.jedit/server (default)
        -server=<name>: Read/write server info from/to $HOME/.jedit/<name>
        -noserver: Don't start edit server
        -settings=<path>: Load user-specific settings from <path>
        -nosettings: Don't load user-specific settings
        -startupscripts: Run startup scripts (default)
        -nostartupscripts: Don't run startup scripts
        -usage: Print this message and exit
        -version: Print jEdit version and exit
        -wait: Wait until the user closes the specified buffer in the server
         instance. Does nothing if passed to the initial jEdit instance.

Report bugs to Slava Pestov <slava@jedit.org>.
root@ubuntu:/home/gurjit #
```

---

### Post by luiska on 2004-10-29
Hi Again

I am not familiar with jedit but it seems to be more programming orientated. 

For just editing your sources.list you can really use a much simpler editor. 

Make sure you are only trying with one program or command at a time to access the the apt package database.

Louis

---

### Post by jdong on 2004-10-29
Oh yeah, **do NOT** chmod a system file to 777! That's just plain foolish. root always has 777 access to files, no matter their permissions. If you're sudo'ed or rooted and still get errors,  chmod will not help you out.

---

### Post by fng on 2004-10-29
simple console editor : nano, pico
simple gui editor : bluefish

---

### Post by akamjballar on 2004-10-29
I like bluefish, but it doesn't have a built in compiler. I really need a compiler too, I was looking forward to installing eclpise. If someone can tell me how, it would be cool. :)

---

### Post by akamjballar on 2004-10-29
Can someone please help me how to install eclipse. I really need something to code in Java. :)

---

### Post by gionix on 2004-11-25
[QUOTE=akamjballar]Can someone please help me how to install eclipse. I really need something to code in Java. :)[/QUOTE]

Hi 
Installing eclipse is quite simple, all you need is jdk (use jdk 1.4.2) and Eclipse zip file (You can download it from [http://www.eclipse.org](http://www.eclipse.org)). Install the jdk and then unpack eclipse. If you have installed the jdk in usr/local/java and eclipse in your home directory you can run eclipse by launching 

/home/your_home_dir/eclipse/eclipse -vm /usr/local/java/jre/bin/java -vmargs -Xms100M -Xmx384M

-vm tells to eclipse where is located the jvm and -Xms and Xmx are the parameter for the minum and maximum memory allocation (I run Eclipse on a pc with 512 Mb).

About Jedit:

I have the same problem, but I resolved it unistalling all libgcj, obviously you have to install the jdk and set the JAVA_HOME envinroment variable.
 
I hope this can help you.

---

