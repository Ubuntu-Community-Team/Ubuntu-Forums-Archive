---
title: "End a process I can't see"
date: 2007-04-03
forum: General Help
---

### Post by songamericadj on 2007-04-03
How do I end a process that is not listed in the running processes list? And can I end it in the terminal and if I can what is the code to do so? Thanks in advance!

---

### Post by sisco311 on 2007-04-03
in terminal:
```
killall process_name
```
or
```
sudo killall process_name
```
where process_name is the name of the process
use:
```
ps -aux
```
to list the process
or
```
ps -aux | grep process_name
```
where process_name is the name of the process

---

### Post by garlik42 on 2007-04-03
How are you viewing the processes ? 
Not sure if there is an easier way to do this with ubuntu, but here is how to do it with the command line from most linux systems.

sudo ps x

This will list all running processes on the system

then

sudo kill pid 
where pid is the # you found from the above list, but be careful about what you kill.
If the above kill doesn't work,

sudo kill -9 pid 
might work better.

---

### Post by sisco311 on 2007-04-03
```
kill -15 ps_id
```
where ps_id is the number in second column of the ps  command and -15 is the term signal

---

### Post by songamericadj on 2007-04-03
thank you all soo much for your help! i still couldn't fix my problem. But I will be more specific this time,

I am trying to end the process called "avgupdate." Everytime I used your suggestions, don't get me wrong I appreciate all of your help, they didn't work. Is there any way to end this very annoying process? Thanks again, in advance, for all your help, I greatly appreciate it!

---

### Post by eentonig on 2007-04-03
Can you post the output of

> ps -Al | grep avg

---

### Post by songamericadj on 2007-04-03
Thanks for that! I still can't end the process it doesn't seem to be listed anywhere. Here is exactly what happened:

I was in terminal running "avgupdate -o" and it wasn't responding so I closed the terminal window. Then I went back into terminal, executed "sudo -i," and then tryed to run "avgupdate -o" again, thats when I got the message "avgupdate is already running." I tried all of your suggestions and still got nothing. Maybe this new information will help someone help me. Thanks in advance!

---

### Post by sisco311 on 2007-04-03
```
sudo rm -r /opt/grisoft/avg7/var/run/avgupdate.pid
```

[http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html]("http://www.debianadmin.com/protect-ubuntu-desktop-from-viruses-using-avg-antivirus.html")

---

### Post by songamericadj on 2007-04-03
It worked! Thank you so much!

---

### Post by spankymasterc on 2007-04-03
Make it so complicated...

System > Administrator > System Monitor > Processes and look for it in there gawsh....

---

### Post by IcemanV9 on 2007-04-03
It would be easier if you need ...

To find a process # ...
```
pgrep avgupdate
```

Or, just kill the app without looking up for process # ...
```
pkill avgupdate
```

---

