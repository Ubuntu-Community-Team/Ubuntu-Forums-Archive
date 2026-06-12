---
title: "Autorun programs after bootup."
date: 2006-10-14
forum: General Help
---

### Post by SteffJay on 2006-10-14
I would like to know, how i can set two programs to autorun after the pc boots up. The first program is DC++ (client) and the other is OpenDChub (server). The system i have (after update) is Ubuntu 6.06, Kernel 2.6.15-27-386. Any help will be greatly appreciated. Thanks in advance. ;)

---

### Post by evilghost on 2006-10-14
I usually add them to /etc/init.d/bootmisc.sh

---

### Post by SteffJay on 2006-10-15
Thanks for the reply **evilghost**. I found where you suggested but i have not a clue how to alter or add the code in the **/etc/init.d/bootmisc.sh** file, plus anywhere else it needs to be added. A little more help here would be appreciated ....  ;)

---

### Post by Kateikyoushi on 2006-10-15
Try to add them in System >> Preferences >> Sessions, startup programs tab.

---

### Post by SteffJay on 2006-10-15
Hello **Kateikyoushi**. Thanks for your reply. I have tried that in many variations but the only way i can get these to work is to start them from the root terminal. Do you have any more suggestions ?

---

### Post by Kateikyoushi on 2006-10-15
Then try to edit the bootmisc.sh as evilghost wrote.

[Like he recommends in this post.]("http://www.ubuntuforums.org/showpost.php?p=1207235&postcount=5")

Make a backup first.
```
sudo cp /etc/init.d/bootmisc.sh /etc/init.d/bootmisc.sh_old
```

Then edit.
```
sudo nano /etc/init.d/bootmisc.sh
```

---

### Post by SteffJay on 2006-10-15
My God !!!!!   what the hell is all this ???? This means totaly zero to me.....  Bit like Russian...  (and no, i cannot speak that either) !!!  ](*,)

---

### Post by pecata on 2006-10-15
You should read this.
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

---

### Post by Kateikyoushi on 2006-10-15
The first command I wrote creates a backup of your bootmisc.sh file, just in case. Copy the commands to a terminal.

```
sudo cp /etc/init.d/bootmisc.sh /etc/init.d/bootmisc.sh_old
```

Then we edit it.

```
sudo nano /etc/init.d/bootmisc.sh
```

Before the last line which looks like a ":exit 0" or an ":" add the commands which start those applications.
Then press CTRL+x to quit and Y to save it.

To test it copy this to a terminal.

```
sudo /etc/init.d/bootmisc.sh
```

Then your applications should start.

I tested it right now on my machine.

---

### Post by SteffJay on 2006-10-15
To be honest **Kateikyoushi**, I do not know what the commands are and where to put them.......  :(

---

### Post by evilghost on 2006-10-15
Open up a 'Terminal'

Type:  "sudo gedit /etc/init.d/bootmisc.sh &" and hit enter.

This will open the Gnome Editor, from there you can add the commands you want to run in startup.

You'll want to add your commands above the "}" bracket, below is a snippet my bootmisc.sh on a fileserver/sound-server.  As you can see I'm running redir and compress.sh.  AFAIK you can also add them right above the ": exit 0" but I prefer to add them inside the "start" function.

Add the commands you wish and save the changes.  I hope this helped.

```

        #
        #       Remove ".clean" files.
        #
        rm -f /tmp/.clean

        #NCF, start ECASound
        /compress.sh &

        #Redir for VNC
        /usr/bin/redir --lport=57604 --cport=5900 --caddr=127.0.0.1 &
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

: exit 0

```

---

### Post by SteffJay on 2006-10-16
Ok..  I have tried various methods of this for the two programs but they will still not autorun. The two programs are....  Valknut and Verlihub. If you know how to input these into the bootmisc.sh, i would really appreciate it. ;) Verlihub is located in /usr/local/bin/verlihub and Valknut is located in /usr/bin/valknut. The first one can only be invoked by root but the second can be invoked by me. I hope this helps.

*************************
Update
*************************

I have managed to autoboot Valknut by adding into the **system/prefs/sessions** and that is working ok now. Now just the verlihub to do !!

---

### Post by SteffJay on 2006-10-20
Ok..  problem solved. Bearing in mind that i am running Ubuntu 6.06 Dapper/Drake kernel 2.6.15-27-386  This has a lot to do with my problem. But here is the solution:......

First, create a document using **gedit** called "**runhub**". Then copy/paste this into it:

 [b]#!/bin/bash

echo " starting hub..."

ulimit -n 200 && /usr/local/bin/vh_runhub


echo " hub..is up & running"[/b]



Then save that into **/etc/init.d** as **runhub**.

Open a shell and type: **chmod +x** to the **runhub** file.

Then in the shell, type: **update-rc.d runhub defaults 90**

Then reboot the pc. It will then autostart Verlihub.  :KS

I hope this helps.

---

