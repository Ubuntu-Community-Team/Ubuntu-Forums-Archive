---
title: "crontab kill command"
date: 2015-11-15
forum: General Help
---

### Post by Spency on 2015-11-15
Hi,

I run a server with apt-mirror on it. Currently, I have crontab run apt-mirror, reboot after a certain number of hours and swap out the mirror.list config file and then re-run apt-mirror twice daily. There's a day time mirror.list with a thread rate limit of 10k and a night mirror.list without a thread limit. Since, every time apt-mirror is run it has a different PID I cannot configure crontab to kill a specific PID at 2 different times of the day. Secondly, I have found that running kill on the apt-mirror PID does not shut down the 20 different download threads that it creates. 

Is there a clever way to configure crontab to kill apt-mirror and all of it's download threads without having to reboot the system?

I have viewed this thread: [http://ubuntuforums.org/showthread.php?t=1034335](http://ubuntuforums.org/showthread.php?t=1034335)
And it mentions use of apt-mirror-stop and apt-mirror-start scripts, but does not contain the script contents itself, so I'm not sure how the author accomplished what I'm trying to do myself.

Thanks!

---

### Post by Lars Noodén on 2015-11-15
Which [signal](http://manpages.ubuntu.com/manpages/trusty/en/man7/signal.7.html) are you using to kill it?  Often HUP is used to by daemons as a way to reload the configuration.

---

### Post by Spency on 2015-11-15
[Kill]("http://manpages.ubuntu.com/manpages/trusty/en/man2/kill.2.html")

---

### Post by Lars Noodén on 2015-11-15
If you are using the [kill(1)](http://manpages.ubuntu.com/manpages/trusty/en/man1/kill.1.html) utility, it defaults to the TERM signal.

You can tell it to use a HUP signal:

```

kill --signal HUP *xxxx*

```

You could also use pkill.

---

### Post by Spency on 2015-11-15
So if I understand correctly, sending HUP signal will simply restart a program and have it re-read all it's configuration files in the process - so then, it never loses it's PID, and I can configure crontab to use ```
/usr/bin/kill --signal hup
``` with a static PID. But then if I restarted the computer at any point, it would break that entry in crontab right?[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Lars Noodén on 2015-11-15
Yes.  After the restart it would have a different PID.  But you could use pkill with -x and --signal HUP to find and kill the process. 

I don't know how apt-mirror will behave with HUP signal.  It might reload the configuration or it might just die or it might keep rolling along.  What happens when you try it?

---

### Post by Spency on 2015-11-15
Thank you so much for your help so far.  I used ```
sudo pkill -x -f 'sudo apt-mirror'
``` to shutdown a manual start up of apt-mirror which worked, however the 20 or so wget processes ```
 sudo apt-mirror
``` started remained active. I will have to experiment with shutting down the apt-mirror process when crontab starts it up. Although I worry something is being overlooked.

---

### Post by Lars Noodén on 2015-11-16
What if you try a different signal?

```

sudo pkill -x -f 'sudo apt-mirror' --signal HUP

```

---

### Post by HermanAB on 2015-11-16
Howdy,

I have found that 'pkill' and 'pgrep' are not always available on a machine, but there is also 'pidof' to find a process PID by name, which usually is available.  You can list the various kill signals available with 'kill -l'.

Useful signals to try are: SIGHUP, SIGSTOP, SIGTSTP and SIGCONT.

So you could do something like:
PID=$( pidof -s processname )
kill -SIGHUP $PID

---

### Post by Spency on 2015-11-18
HermanAB. I do not understand your contribution. I ran ```
 $ kill -SIGHUP $$( pidof -s apt-mirror) 
``` but recieved an syntax error messsage. ```
 -bash: syntax error near unexpected token `('
```

Could you please elaborate more?

---

### Post by Lars Noodén on 2015-11-19
It looks to me like it should be this:
```
 kill -SIGHUP $( pidof -s apt-mirror )

```

The $( ... ) alone is [command](http://mywiki.wooledge.org/CommandSubstitution) [substitution](http://wiki.bash-hackers.org/syntax/expansion/cmdsubst).  There the extra dollar sign is a problem and probably a typo.

---

### Post by Spency on 2015-11-19
The issue is that apt-mirror's process name is not just apt-mirror it's /usr/bin/perl /usr/bin/apt-mirror AANND sudo apt-mirror.
It took me a while until I realized the output of pidof apt-mirror is nothing. 

Lars, your solution actually works fine for killing apt-mirror. My next issue was killing all of the wget processes it created, which never got shut down even if you killed apt-mirror. After reading a little about pidof, I adapted Hermans solution.
```
kill $( pidof  wget )
``` 

And whala, bandwidth restored.

---

### Post by Lars Noodén on 2015-11-20
> **Spency said:**
> My next issue was killing all of the wget processes it created, which never got shut down even if you killed apt-mirror. 

Then I would consider it a bug in apt-mirror worth reporting.  

```

ubuntu-bug apt-mirror

```

There needs to be a way to kill apt-mirror and all of its processes with HUP, TERM, STOP or some other kill signal.  If you report it, then apt-mirror can improve.

---

### Post by Spency on 2015-11-20
I chose to create an issue thread at the [apt-mirror github page]("https://github.com/apt-mirror/apt-mirror/issues/54")

I also found out that if you want to kill apt-mirror started by crontab you have to use:
```
pkill -x -f '/bin/sh -c /usr/bin/apt-mirror > /opt/apt-mirror/mirror/archive.ubuntu.com/ubuntu/apt-mirror.log' --signal HUP
```
and from crontab itself:
```
/usr/bin/pkill -x -f '/bin/sh -c /usr/bin/apt-mirror > /opt/apt-mirror/mirror/archive.ubuntu.com/ubuntu/apt-mirror.log' --signal HUP
```

---

