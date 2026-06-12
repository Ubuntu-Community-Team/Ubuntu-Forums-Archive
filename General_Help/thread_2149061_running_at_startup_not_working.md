---
title: "running at startup not working"
date: 2013-05-27
forum: General Help
---

### Post by rebeltaz on 2013-05-27
I am trying to run two commands at startup. One is the program transmission and the other is a script I wrote to monitor and log network connectivity - watch.router

I ran crontab -e and added '@reboot /usr/bin/transmission' to the end of that, saved and exited.

I added '/home/derek/watch.router' as the second to last line of /etc/rc.local (before 'exit 0'), saved and exited.

Then I rebooted. Neither command ran. Can someone tell me what I am doing wrong? Thanks...

---

### Post by ajgreeny on 2013-05-27
Why not just add transmission to your startup-applications list, instructions here:-
[http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login)
and the watch.router script may need the desktop up and running to work properly, hence adding it to rc.local will not work, though not knowing the content of the script, it's impossible to say more, so let's see what the script contains.

---

### Post by rebeltaz on 2013-05-27
> **ajgreeny said:**
> Why not just add transmission to your startup-applications list, instructions here:-
[http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login](http://askubuntu.com/questions/48321/how-do-i-start-applications-automatically-on-login)
and the watch.router script may need the desktop up and running to work properly, hence adding it to rc.local will not work, though not knowing the content of the script, it's impossible to say more, so let's see what the script contains.

I could do that (add transmission to startup app list) but I do like knowing how to do things behind the scenes as it were.

This is the script:

```

#!/bin/bash
while [ 1 ]
tput clear
echo "DSL Modem Sync Monitor"

do
   tput cup 3 1
   ping 68.16.xxx.x -c 1

   if [ $? -eq 0 ]
   then
        tput cup 12 1
        echo "Sync Condition Normal"
        tput el
      sleep 1s
   else
      COUNT=1
      LOOP=0

      while [ $LOOP -le 10 ]
      do
           tput cup 12 1
           echo "Packet Loss $COUNT Out Of 10"
           tput el

         sleep 1s
         tput cup 3 1 
         ping 68.16.xxx.x -c 1

         if [ $? -ne 0 ]
         then         
            let COUNT=COUNT+1
         fi

         let LOOP=LOOP+1
      done
      
      if [ $COUNT -ge "10" ]
      then 
         date >> sync.error
           tput cup 12 1
           echo "Sync Error Ocurred"
           tput el
         sleep 1s
      fi
   fi
done

```

It's not pretty, but it gets the job done - the job being keeping a log of outages for my next call to AT&T.

---

### Post by efflandt on 2013-05-27
I don't know if BellSouth would appreciate you pinging them every second. Doesn't your DSL router/modem have logs (which with some you could relay to Linux syslogd)?

Where do you expect the output from your script to go (not sure if it goes to syslog or if not having anywhere for it to go is the problem)? If you do not know where something is going to go, define where it should go. Perhaps you should append that to a log file instead of trying to output (echo) it to a terminal that does not exist.

The problem running transmission from cron during boot is that it is a gui, which needs a working DISPLAY defined, but X is not running yet during boot, so defining that would not help early in the boot process.

---

### Post by rebeltaz on 2013-05-27
> **efflandt said:**
> I don't know if BellSouth would appreciate you pinging them every second. Doesn't your DSL router/modem have logs (which with some you could relay to Linux syslogd)?

Where do you expect the output from your script to go (not sure if it goes to syslog or if not having anywhere for it to go is the problem)? If you do not know where something is going to go, define where it should go. Perhaps you should append that to a log file instead of trying to output (echo) it to a terminal that does not exist.

The problem running transmission from cron during boot is that it is a gui, which needs a working DISPLAY defined, but X is not running yet during boot, so defining that would not help early in the boot process.

The IP address I am pinging is my own static business account IP. I don't see where BS would care. Besides that, I'm none too happy with them either, so...  

The echo commands are simply for visual indication of the current status. I am appending to the log file "sync.error" on line 40 with 'date >> sync.error'

There are logs on the router ( a Motorola Netopia ) but I don't see anything in those about losing sync.

---

### Post by CaptainMark on 2013-05-28
+1 to efflandt's statement, there are two transmission commands: transmission-gtk or transmission-cli, both will fail in your case, transmission-gtk requires the x server to be running (you have to be logged into a graphical session) and transmission-cli requires an attached tty or there is nowhere to display its output. Also by adding these commands to your crontab and your /etc/rc.local script then you are trying to run transmission and your script as root and not as your user which is a bad idea for security reasons and also impractical,

I would definitely recommend ajgreeny's idea of adding them to your startup applications list, note though if you use the command "transmission-gtk -m" then transmission will start minimised in a non-obtrusive fashion which is probably more ideal.
[COLOR=#000000][/COLOR]

---

### Post by rebeltaz on 2013-05-28
Thanks. I did just add both to the startup list. I appreciate the responses.

---

