---
title: "Auto Start"
date: 2008-04-15
forum: General Help
---

### Post by mattc908 on 2008-04-15
I've been trying to setup team-speak to auto-start whenever the server starts up, I managed to do it this way with a different but similar program. for some reason teamspeak wont do it? Any Idea?

rc.local


```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.



# Start the Vent Server
/bin/sh /home/mattc908/startvent.sh
#Start The Tss2 Server
/bin/sh /home/mattc908/starttss2.sh


exit 0
```

startts2.sh
```
#!/bin/sh

# Start the Tss2 Server
cd /home/mattc908/insight/tss2_1
./teamspeak2-server_startscript start

```

It works with the ventrilo server which is almost identical scripting for the startup.

---

### Post by Diabolis on 2008-04-15
I haven't tried it in a scrip, but issuing "cd" and the trying to execute doesn't seem right to me. You can execute it directly by typing it like this:

./home/mattc908/insight/tss2_1/teamspeak2-server_startscript start

try to execute at a terminal to see if it works.

I have wrote some scripts and I found usefull to put them all in the same folder and then add the folder to my PATH variable. By doing that you don't have to type the path to the scripts every time you want to execute them. If you want to give it a try, edit your .bashrc file. Its a hidden file in your home folder. While at your home folder, type ctrl + h so you can see hidden files.

Here is what I added to mine:
> 
GASTONBIN=/home/gaston/misDocumentos/bin
PATH=$PATH:$GASTONBIN


---

### Post by Diabolis on 2008-04-15
You can put all your scripts in the same folder and then add that folder to your PATH variables, so you don't have to type the path to your scripts every time. Adding a folder to your PATH variable is very easy. Just edit your .bashrc file, which is a hidden file under your home folder. In order to see hidden files, type ctrl +h. Or edit it by typing gedit .bashrc.

I did that to the folder that contains my scripts, this is what I added to the end of it:
```

GASTONBIN=/home/gaston/misDocumentos/bin
PATH=$PATH:$GASTONBIN

```

---

### Post by mattc908 on 2008-04-16
```
mattc908@mattc908:~$ ./home/mattc908/insight/tss2_1/teamspeak2-server_startscript start
-bash: ./home/mattc908/insight/tss2_1/teamspeak2-server_startscript: No such file or directory

```

```

mattc908@mattc908:~$ cd /home/mattc908/insight/tss2_1
mattc908@mattc908:~/insight/tss2_1$ ls
bad_names.txt  Manual       server_linux  teamspeak2-server_startscript
httpdocs       manual.html  server.log    tsserver2.pid
INSTALL        mysql_sql    sqlite.so     whitelist.txt
INSTALL.mysql  README       sqlite_sql
libsqlmy.so    server.dbs   tcpquerydocs
LICENSE        server.ini   teamspeak
mattc908@mattc908:~/insight/tss2_1$ 

```


Any Idea?

---

### Post by Diabolis on 2008-04-16
yeah **teamspeak2-server_startscript** couln't be executed with that command, that is what the error is saying actually.
It depends on the first line of the file. It could be a bash or a shell script.

I don't remember exactly how to execute it, so try this: 

```
sh ./home/mattc908/insight/tss2_1/teamspeak2-server_startscript start
```

or

```
bash ./home/mattc908/insight/tss2_1/teamspeak2-server_startscript start
```

---

