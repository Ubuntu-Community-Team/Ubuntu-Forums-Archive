---
title: "mpd failed to bind to '6600'"
date: 2012-10-30
forum: General Help
---

### Post by Controll on 2012-10-30
Every time I try to run mpd via terminal, I always get: mpd failed to bind to '6600'

I've only been able to find solutions using Archlinux.

Please help a newbie out? Thanks.

---

### Post by papibe on 2012-10-30
Hi Controll.

I have up and running mpd on a old laptop running Lubuntu 12.04.

Could you post the result of this command?
```
grep -i bind /etc/mpd.conf
```
Regards.

---

### Post by mali2297 on 2012-10-30
Any solutions for Arch Linux are likely to be applicable also for (x)ubuntu. Have you tried them?

Check if there are any duplicate lines in /etc/hosts. (From [here]("http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot#Address_already_in_use").)

---

### Post by Controll on 2012-10-30
> **papibe said:**
> Hi Controll.

I have up and running mpd on a old laptop running Lubuntu 12.04.

Could you post the result of this command?
```
grep -i bind /etc/mpd.conf
```Regards.

```
bind_to_address        "localhost"
#bind_to_address        "/var/run/mpd/socket"
```

---

### Post by papibe on 2012-10-30
Thanks.

Right now, your mpd works only from the machine in which is running (bind to localhost).

In my experience, listing all the bindings could be a very exhausting task. Instead, if you comment all binding lines, mpd will bind to all of them, thus working both locally and from your LAN clients:
```
**[COLOR="Red"]#[/COLOR]**bind_to_address        "localhost"
```
Let us know how it goes.
Regards.

---

### Post by Controll on 2012-10-31
> **papibe said:**
> Thanks.

Right now, your mpd works only from the machine in which is running (bind to localhost).

In my experience, listing all the bindings could be a very exhausting task. Instead, if you comment all binding lines, mpd will bind to all of them, thus working both locally and from your LAN clients:
```
**[COLOR=Red]#[/COLOR]**bind_to_address        "localhost"
```Let us know how it goes.
Regards.

I'm pretty new so I'm not exactly sure what you wanted me to do here... I just tried typing the code you gave me into the terminal :p but nothing happened.

---

### Post by papibe on 2012-10-31
You need to edit the file and change a line:

Open the file:
```
gksudo gedit /etc/mpd.conf
```
Then look for this line:
```
bind_to_address        "localhost"
```
Comment the line: add a '#' character at the beginning. It should look like this:
```
#bind_to_address        "localhost"
```
Save the file and exit the editor.

Go to the command line and restart mpd:
```
sudo service mpd restart
```
Let us know how it goes.
Regards.

---

### Post by Controll on 2012-10-31
> **papibe said:**
> You need to edit the file and change a line:

Open the file:
```
gksudo gedit /etc/mpd.conf
```Then look for this line:
```
bind_to_address        "localhost"
```Comment the line: add a '#' character at the beginning. It should look like this:
```
#bind_to_address        "localhost"
```Save the file and exit the editor.

Go to the command line and restart mpd:
```
sudo service mpd restart
```Let us know how it goes.
Regards.

Thanks. Alright I went through and edited the .conf by putting the # before bind_to_address, restarting mpd, then tried running mpd and got the same error as before: mpd failed to bind to '6600'

---

### Post by papibe on 2012-10-31
Could you paste from the terminal both the command and the complete error message?
Regards.

EDIT: btw, under what user are you running mpd? It is much easier to run it as 'you'.

---

### Post by Controll on 2012-10-31
> **papibe said:**
> Could you paste from the terminal both the command and the complete error message?
Regards.

EDIT: btw, under what user are you running mpd? It is much easier to run it as 'you'.

```
controll@Controll:~$ mpd
Failed to bind to '[::]:6600': Address already in use
controll@Controll:~$
```

I am running it under "me," yes.

---

### Post by papibe on 2012-10-31
Could you check that there's no other mpd process running?
```
ps aux | grep mpd
```
If so, kill them all:
```
killall mpd
```
Also, if you set the user on the /etc/mpd.conf file:
```
user                            "youruser"
```
and then start the process as a service:
```
sudo service mpd start
```
or restart it as service:
```
sudo service mpd restart
```
That would take care of several instances.

Let us know how it goes.
Regards.

---

### Post by Controll on 2012-11-01
> **papibe said:**
> Could you check that there's no other mpd process running?
```
ps aux | grep mpd
```If so, kill them all:
```
killall mpd
```Also, if you set the user on the /etc/mpd.conf file:
```
user                            "youruser"
```and then start the process as a service:
```
sudo service mpd start
```or restart it as service:
```
sudo service mpd restart
```That would take care of several instances.

Let us know how it goes.
Regards.

```
controll@Controll:~$ sudo service mpd start
 * Starting Music Player Daemon mpd                                                       listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
daemon: could not create pid file "/var/run/mpd/pid": Permission denied
                                                                                   [fail]
```

This is what I get after doing everything and trying to start mpd.

Now, I changed user in gedit from "mpd" to "controll"

---

### Post by HiImTye on 2012-11-01
if you use a different username, you also have to either change the permissions of the default files, or specify new files for mpd to use. all of the files are listed in the configuration file

---

### Post by Wim Sturkenboom on 2012-11-01
> **Controll said:**
> ```
controll@Controll:~$ mpd
Failed to bind to '[::]:6600': Address already in use
controll@Controll:~$
```
Just to explain why this goes wrong. You already had the service / daemon started (sudo service mpd restart) and you try to start it again.

---

### Post by Controll on 2012-11-01
> **Wim Sturkenboom said:**
> Just to explain why this goes wrong. You already had the service / daemon started (sudo service mpd restart) and you try to start it again.

```
controll@Controll:~$ killall mpd
mpd: no process found
controll@Controll:~$ mpd
listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
db_file setting missing 
```

I've typed killall mpd before mpd and still get the same result.

---

### Post by HiImTye on 2012-11-01
> **Controll said:**
> I've typed killall mpd before mpd and still get the same result.
that doesn't matter, mpd just gets restarted unless you specifically tell it to stop
```
ps -e | grep mpd$
```
will still show mpd running after you kill the process, as it just gets spawned again. to stop it use
```
sudo /etc/init.d/mpd stop
```
or
```
sudo service mpd stop
```

---

### Post by Controll on 2012-11-01
> **HiImTye said:**
> that doesn't matter, mpd just gets restarted unless you specifically tell it to stop
```
ps -e | grep mpd$
```will still show mpd running after you kill the process, as it just gets spawned again. to stop it use
```
sudo /etc/init.d/mpd stop
```or
```
sudo service mpd stop
```

Alright, I stopped it successfully, then put in ```
 sudo service mpd restart 
``` and keep getting the same old error ```
  * Stopping Music Player Daemon mpd                                      [ OK ] 
controll@Controll:~$ gksudo gedit /etc/mpd.conf
controll@Controll:~$ sudo service mpd restart
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
daemon: could not create pid file "/var/run/mpd/pid": Permission denied
                                                                         [fail] 
```

---

### Post by kanikilu on 2012-11-01
Sorry, I don't use or know much about mpd, so this may serve as nothing more than a bump, but the mpd troubleshooting page says to run the following command and check the output (maybe it will be useful to someone else here?):

```
/usr/bin/mpd --stdout --no-daemon --verbose
```

[http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot](http://mpd.wikia.com/wiki/Music_Player_Daemon_HOWTO_Troubleshoot)

---

### Post by LewisTM on 2012-11-01
Since you are running MPD as yourself (controll) you don't have permission to write in /var/run/mpd

You should edit your mpd.conf file and change this line
```
pid_file "/var/run/mpd/pid"
```
to
```
pid_file "/tmp/mpd/pid"
```
Then restart the service.

---

### Post by Controll on 2012-11-01
> **LewisTM said:**
> Since you are running MPD as yourself (controll) you don't have permission to write in /var/run/mpd

You should edit your mpd.conf file and change this line
```
pid_file "/var/run/mpd/pid"
```to
```
pid_file "/tmp/mpd/pid"
```Then restart the service.

I edited the file, restarted, and tried starting mpd, get this still:

```
controll@Controll:~$ sudo service mpd restart
[sudo] password for controll: 
 * Stopping Music Player Daemon mpd                                      [ OK ] 
 * Starting Music Player Daemon mpd                                             listen: bind to '0.0.0.0:6600' failed: Address already in use (continuing anyway, because binding to '[::]:6600' succeeded)
                                                                         [ OK ]
controll@Controll:~$ mpd
Failed to bind to '[::]:6600': Address already in use
controll@Controll:~$
```

---

### Post by papibe on 2012-11-01
Your are ready to rock and roll.

The first command to start the service was successful (the message is just a warning).

The second one it not necessary, as the service is already running, thus the error.

Use your favorite mpd client, and let us know how it goes.
Regards.

---

