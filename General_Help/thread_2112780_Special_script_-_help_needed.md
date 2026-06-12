---
title: "Special script - help needed"
date: 2013-02-05
forum: General Help
---

### Post by castalla on 2013-02-05
I'm using the following script to start and stop a process when a bluetooth connection is detected.  At the moment I run the script from the terminal.

I'd like to run the script when the PC boots as a background (?) routine.  Could someone advise the best way to do this?  

Also, if anyone has any suggestions to improve the script, I'd welcome any comments.

```
#!/bin/bash
 pid=0
 address="00:15:71:14:E6:22"
 squeezelite_started=false
 while (sleep 1)
 do
 if [[ $squeezelite_started == false ]] ; then
 connected=$(hcitool con) > /dev/null
 if [[ $connected =~ .*${address}.* ]] ; then
sleep 10
 squeezelite -m ab:cd:ef:12:34:56 -n Test -o TEST -r 44100&
 echo $! > /tmp/TEST_squeezelite.pid
 squeezelite_started=true
 echo $address connected started Squeezelite
 fi
 fi

 if [[ $squeezelite_started == true ]] ; then
 connected=$(hcitool con) > /dev/null
 if [[ ! $connected =~ .*${address}.* ]] ; then
 pid=$(cat /tmp/TEST_squeezelite.pid)
sleep 5
 kill -9 $pid
 rm /tmp/TEST_squeezelite.pid
 squeezelite_started=false
 echo $address disconnected stopped Squeezelite
 fi
 fi
 done 
```

---

### Post by omeomi on 2013-02-05
You can just add it as a session startup script (System settings > Startup Applications, if I remember correctly)

---

### Post by castalla on 2013-02-05
I meant how do I add it to startup files , eg. rc.local, etc.

---

### Post by omeomi on 2013-02-05
Ah, just open rc.local
```
 sudo gedit /etc/rc.local
```
and then add the complete path to your script as a line there.

Make sure you make your script executable
```
chmod u+x /path/to/file/script.sh
```

---

### Post by castalla on 2013-02-05
Thanks ... will there be issues with the echo statements?  When I run at the command line, the echo lines appear in the terminal .... 

I suppose I can simply try it and see what happens?

---

### Post by castalla on 2013-02-05
I tried it ... doesn't seem to work.

When I do from the terminal ./TEST then TEST appears as a running process in 'top'

Nothing in top when run from rc.local

---

