---
title: "How would I start a program to run in a termianl window"
date: 2008-06-02
forum: General Help
---

### Post by DigitalDuality on 2008-06-02
d

---

### Post by Joe88 on 2008-06-02
You will need to create a command alias in a .bashrc file, you can either make the command to execute the program for a specific user (/home/*the user*/.bashrc) or for everyone who uses your computer (/usr/share/.bashrc).

e.g for everyone:

1.Open terminal
2.type: sudo gedit /usr/share/.bashrc
3. enter your password
4. when its open you can add an alias, heres one from my bash:

alias bluej='/home/joe/bluej/bluej'

the alias word is bluej, and when entered into the terminal this will execute the bluej executable, located in the /home/joe/bluej directory on my computer.

So entering this one word, will do the same thing as typing '/home/joe/bluej/blue into a terminal.

Make sure there no gaps between the command word,the equals, the ' and the first command character, otherwise the alias won't work.

-------------------------------------------------------------------------------------------------------------------------

Heres some more alias examples:

[COLOR="Red"]*** For a command line java alarm program ***[/COLOR]
alias alarm='java -jar /usr/share/javaAlarm.jar'

[COLOR="Red"]*** For the command : find / -name ***[/COLOR]
alias search='sudo find / -name' 

NOTE: this command needs super user permissions to look in some directories

Using this alias I could search for a file named thing by entering this into the terminal:

search thing

[COLOR="Red"] *** For the command : cd /home/joe/downloads && ls ***[/COLOR]
alias downloads='cd /home/joe/downloads && ls'

NOTE: && alows an alias to perform more than one function, so this alias will change to the download directory in my home folder and then list its contents

---

### Post by mali2297 on 2008-06-02
Check the man page for aterm:
> 
-e command [arguments]
    Run the command with its command-line arguments in the aterm window; also   sets the window title and icon name to be the basename of the program being executed if neither -title (-T) nor -n are given on the command line. If this option is used, it must be the last on the command-line. If there is no -e option then the default is to run the program specified by the SHELL environment variable or, failing that, sh(1).


Say you want to create a launcher for nano. Then use the command
```

aterm -e nano

```

---

### Post by DigitalDuality on 2008-06-02
d

---

