---
title: "I want to delay auto-starting a program"
date: 2008-04-22
forum: General Help
---

### Post by dryder on 2008-04-22
Hi,
FEISTY (and HARDY)
I want to delay the auto-startup of a a program as it should minimise to the systray (panel) but gets loaded before panel - resulting in nowhere for it to minimize to.

Is it possible and please, if so how?, to auto-start not the program but a script that calls the program and have the script with a counter in it to delay execution of the start instruction? Something like, in sessions, auto start my-script
my-script
for count = 1 to *nn*
next
.../program-name -s (-s parameter minimises it)

Ideas please? Thanks in advance,

David

---

### Post by sdennie on 2008-04-22
You could use a script like this:

wait-for-panel.sh:
```

#!/bin/bash

while ! pgrep gnome-panel > /dev/null ; do
    sleep 1
done

sleep 1

exec $@

```

That wakes up once a second to see if gnome panel is running.  If it is, it waits one more second and then runs whatever arguments you gave to the script.  You can use the script like this:

```

wait-for-panel.sh the_command_to_run -arg1 -arg2

```

---

### Post by dryder on 2008-04-22
Thanks vor,

I've created the .sh script as per your post - not sure what 
exec $@
does?? Sorry if this is elementary. Tried for a man page and google but nothing was obvious.
Also - where should it go? /usr/init.d?

The program in Sessions is:
/usr/bin/efax-gtk -r
but 
/usr/bin/efax-gtk -rs
is what I want (s minimizes to panel but the program always loads before panel).

So may I ask, should the command in sessions be  
../wait-for-panel.sh efax-gtk -rs
??

Many thanks for helping - I'm still learning .... as we all are .

David

---

### Post by sdennie on 2008-04-22
"exec $@" basically means to stop running the script and run the arguments of the script ($@ just means "everything after the script name on the command line")

What I would recommend doing with the script is to put it into ~/bin and run it from there.  So, something like:

```

mkdir -p ~/bin
cp wait-for-panel.sh ~/bin
chmod +x ~/bin/wait-for-panel.sh

```

Then, change the command you are currently using in Sessions to:

```

/home/your_username/bin/wait-for-panel.sh efax-gtk -rs

```

Also, you may have to adjust the final sleep to a value larger than 1 second if gnome-panel starts up slowly on your machine.

---

### Post by dryder on 2008-04-23
I put 
wait-for-panel.sh
in /home/David/bin as suggested and did chmod +x

I tried changing sessions to:
/home/David/bin/wait-for-panel.sh /usr/bin/efax-gtk -rs

and nothing happened. Changed  the argument to efax-gtk -rs and agan nothing happened.
wait-for-panel.sh is:> #!/bin/bash

while ! pgrep gnome-panel > /dev/null ; do
    sleep 1
done

sleep 1

exec $@

I tried sleep 2 which gave it ample time but still nothing.

Checked the script and I own it and it is exceutable. Any suggestions please?

Many thanks,
David

---

### Post by sdennie on 2008-04-23
If you remove the -s part, and use wait-for-panel.sh does the application launch?

---

### Post by dryder on 2008-04-23
No, unfortunately not.

---

### Post by sdennie on 2008-04-23
Ok.  You could try two things.  1) See if you can run the exact thing you put in Sessions from the commandline.  2) Post the output of:

```

ps aux | grep panel

```

---

### Post by dryder on 2008-04-23
> david@ubuntu-server:~$ ps aux | grep panel
david     6785  0.3  0.9  62848 19604 ?        S    14:45   0:01 gnome-panel --sm-client-id default1
david     6895  0.1  1.2  80020 25024 ?        Sl   14:46   0:00 mono /usr/lib/tomboy/Tomboy.exe --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=24
david     7673  0.0  0.0   2896   776 pts/0    S+   14:53   0:00 grep panel
david@ubuntu-server:~$ 


If I open the script using terminal it executes the gui but also the command line version of the program.

But - if I put> /home/David/bin/wait-for-panel.sh efax-gtk -r 
in terminal I get:
> david@ubuntu-server:~$ /home/David/bin/wait-for-panel.sh efax-gtk -r
bash: /home/David/bin/wait-for-panel.sh: No such file or directory
david@ubuntu-server:~$ 

/home/David/bin/wait-for-panel.sh definitely does exist.

---

### Post by dryder on 2008-04-23
I put the script in /usr/bin and it executes from there ok.

But it seems to distinguish from a 'system tray' and 'panel' - I thought they were the sane in Ubuntu. It doesn't like panel.

David

---

### Post by dryder on 2008-04-23
vor,

Solved it - by waiting 10 seconds - it then defaults to panel.

Many thanks - your help is greatly appreciated.

David

---

