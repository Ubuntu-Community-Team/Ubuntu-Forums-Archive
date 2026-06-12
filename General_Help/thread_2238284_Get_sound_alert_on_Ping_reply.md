---
title: "Get sound alert on Ping reply"
date: 2014-08-07
forum: General Help
---

### Post by linuxyogi on 2014-08-07
Hi,

My incoming connection type is CAT5 and although rarely but sometimes I loose connectivity with my ISP.

The IP that I need to ping is 172.16.0.1.

Is there a way to get sound out of the main speakers (I am not asking about motherboard's speaker) once a reply is received ? 

As soon as I lose connectivity I call my ISP and start the ping but it becomes very difficult to just keep looking at the terminal.

---

### Post by vasa1 on 2014-08-07
I use this (as an example):```
alias pg='ping -c3 www.google.com && for i in {1..5}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done'

```

Right now I'm seeing this:```
[11:59 AM] ~ $ ping -c3 172.16.0.1 && for i in {1..5}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.

--- 172.16.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

[12:00 PM] ~ $ 

```

---

### Post by linuxyogi on 2014-08-07
@[**[COLOR=#000000]vasa1[/COLOR]**]("http://ubuntuforums.org/member.php?u=449866")

Its working. I am hearing sound too but what does those mean ? Also, why is it only pinging 5 times and not continuously ? 


```

$ ping -c3 172.16.0.1 && for i in {1..5}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
64 bytes from 172.16.0.1: icmp_seq=1 ttl=63 time=2.82 ms
64 bytes from 172.16.0.1: icmp_seq=2 ttl=63 time=1.75 ms
64 bytes from 172.16.0.1: icmp_seq=3 ttl=63 time=4.67 ms

--- 172.16.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.753/3.083/4.675/1.207 ms
[COLOR=#ff0000]mplayer: could not connect to socket
mplayer: No such file or directory
mplayer: could not connect to socket
mplayer: No such file or directory
mplayer: could not connect to socket[/COLOR]
```

---

### Post by linuxyogi on 2014-08-07
Changed {1..5} to {1..100} so it will ping for 100 times now unless I do ctrl+z. 

Added the line in .bashrc

```
siti='ping -c3 172.16.0.1 && for i in {1..100}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done'
```


```
$ siti
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
64 bytes from 172.16.0.1: icmp_seq=1 ttl=63 time=1.52 ms
64 bytes from 172.16.0.1: icmp_seq=2 ttl=63 time=1.66 ms
64 bytes from 172.16.0.1: icmp_seq=3 ttl=63 time=1.37 ms

--- 172.16.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.377/1.520/1.661/0.124 ms
mplayer: could not connect to socket
mplayer: No such file or directory
mplayer: could not connect to socket
mplayer: No such file or directory
mplayer: could not connect to socket
mplayer: No such file or directory
mplayer: could not connect to socket
mplayer: No such file or directory
mplayer: could not connect to socket
mplayer: No such file or directory
^Z
[4]+  Stopped                 mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga


```


Thanks a lot.

---

### Post by linuxyogi on 2014-08-07
@[**[COLOR=#000000]vasa1[/COLOR]**]("http://ubuntuforums.org/member.php?u=449866")

I just faced a disconnection but the command didn't work. When I did 

```
$ ping -c3 172.16.0.1 && for i in {1..5}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done

``` 

the command just finished. I  mean the ping process did not continue. Now that the connection is back again the command is working again but I need it when  there is no connectivity.

---

### Post by vasa1 on 2014-08-07
> **linuxyogi said:**
> ...
```
$ ping -c3 172.16.0.1 && for i in {1..5}; do mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga ; done

``` 

the command just finished. I  mean the ping process did not continue. Now that the connection is back again the command is working again but I need it when  there is no connectivity.

Sorry about that. It was mainly to show how to link a sound to a command. That code will play the sound if **ping -c3** gives a success exit code. I don't know how to apply it in your case.

---

### Post by sotiris2 on 2014-08-07
I made some adjustments to the script. The previous one would stop if ping failed which is bad since you want it to run through failing and audibly notify you when it finally succeeds.  Some info before the script. 

I made it run 100 times which you can change in the second line. 
It also pings one packet then checks if it was successful and beeps or not. You can change this in line 4 by changing ping -c1 to ping -cX where X is a number. Note that if you change that to 10, if packet 2 succeeds, you will have to wait for packets 3-10 to be done before you will get a sound. Also partial success will also beep I believe. 

Finally I apparently don't have mplayer installed so I can't check if it will play a sound but I copied the command from the script which you said made a sound so it should be ok, otherwise reply and we 'll fix it.

```
#!/bin/bash
for i in {1..100}
do
    ping -c1 172.16.0.1
    if [ $? -eq 0 ]
    then
        #echo success
         mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga
    fi
done 
```


EDIT: Forgot to say. Copy that to a textfile, and make it executable, don't try just pasting into a terminal.

---

### Post by linuxyogi on 2014-08-07
[QUOTE=sotiris2;13092510]I made some adjustments to the script. The previous one would stop if ping failed which is bad since you want it to run through failing and audibly notify you when it finally succeeds.  Some info before the script. 

I made it run 100 times which you can change in the second line. 
It also pings one packet then checks if it was successful and beeps or not. You can change this in line 4 by changing ping -c1 to ping -cX where X is a number. Note that if you change that to 10, if packet 2 succeeds, you will have to wait for packets 3-10 to be done before you will get a sound. Also partial success will also beep I believe. 

Finally I apparently don't have mplayer installed so I can't check if it will play a sound but I copied the command from the script which you said made a sound so it should be ok, otherwise reply and we 'll fix it.

```
$ cat ping
#!/bin/bashfor i in {1..100}
do
    ping -c1 172.16.0.1
    if [ $? -eq 0 ]
    then
        #echo success
         mplayer -really-quiet /usr/share/sounds/freedesktop/stereo/complete.oga
    fi
done
$ ./ping
bash: ./ping: /bin/bashfor: bad interpreter: No such file or directory



```

---

### Post by sotiris2 on 2014-08-07
Omg , stupid formatting mistake. Fixed it above.

---

### Post by linuxyogi on 2014-08-07
> **sotiris2 said:**
> Omg , stupid formatting mistake. Fixed it above.

Its working. I tested by manually  disconnecting the WAN cable and starting the script and then I reconnected the cable again and it worked.

What a relief ! :guitar:

Thanks  !

---

