---
title: "delaying startup program"
date: 2008-02-08
forum: General Help
---

### Post by Cew27 on 2008-02-08
hi i have figured out the poblem for my startup program woes i think 
i need to delay a command by 10 seconds how can i do this ? at the moment i have 
sleep 10s sudo /usr/sbin/g15stats
is this right ?

---

### Post by aashay on 2008-02-08
should be
sleep 10 && sudo ...
My personal experience is (with cairo-clock) that the application fails to start. In that case make a small shell script and add this single line to it. Have the script execute at start (as opposed to the "sleep 10 ... "command)

---

### Post by Cew27 on 2008-02-08
thanks for that, how do i script on linux?

---

### Post by aashay on 2008-02-08
for the script related to the above problem, simply add the single line to any textfile. Make it executable (not sure if required) by sudo chmod +x filemane .Add the path of the script file to the startup programs list

---

### Post by nilarimogard on 2008-02-08
Here is what the file should look like (let's name it g15stats-starup.sh):
#!/bin/bash
sleep 10 && sudo /usr/sbin/g15stats

Then run in a terminal window: chmod +x g15stats-starup.sh
After that just add it to startup programs.

---

### Post by Cew27 on 2008-02-08
that didnt work either :(

---

### Post by nilarimogard on 2008-02-08
You must have done something wrong, because that can't not work.
Make sure you entered the whole location of 'g15stats-starup.sh' in startup. Also try running the 'sudo /usr/sbin/g15stats' command without the 'sudo'. You could also try putting a ';' after the command or a '&", like this:

sleep 10 && /usr/sbin/g15stats ;
or:
sleep 10 && /usr/sbin/g15stats &

---

### Post by Cew27 on 2008-02-08
worked thanks

---

### Post by aashay on 2008-02-09
Just curious.. what does the last & do? I remember I had it in my startup script to separate 2 lines. But I have no idea what it does

---

