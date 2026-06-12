---
title: "Is someone using my ports besides me"
date: 2006-10-16
forum: General Help
---

### Post by kent41 on 2006-10-16
In looking at my ports I found something strange.

one port has [B]Internet Printing
[/B]

And another has a programing language on it (Python)

What is going on can someone tell me if I need these or how to get rid of them

```
kent@ubuntu:/$ sudo nmap -sT -O localhost

Starting nmap 3.81 ( http://www.insecure.org/nmap/ ) at 2006-10-16 21:28 CDT
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1661 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
[B]631/tcp   open  ipp
32770/tcp open  sometimes-rpc3[/B]
```

```

kent@ubuntu:/$ cat /etc/services |  grep  631
ipp             631/tcp                         # Internet Printing Protocol
ipp             631/udp
```


```

kent@ubuntu:/$ sudo netstat -anp | grep 631
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     7712/cupsd
tcp        0      0 127.0.0.1:631           127.0.0.1:42543         ESTABLISHED7712/cupsd
tcp        0      0 127.0.0.1:42543         127.0.0.1:631           ESTABLISHED8279/gnome-cups-ico


```
```

kent@ubuntu:/$ sudo lsof -i | grep 32770
python     7802  hplip    4u  IPv4  10796       TCP localhost.localdomain:32770 (LISTEN)

```

```

kent@ubuntu:~$  sudo netstat -anp | grep 32770

tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7636/python

```

---

### Post by ciscosurfer on 2006-10-17
You're fine.  IPP is setup by default.  Port 631 is talking to 42543 on your own system (127.0.0.1 -- your loopback address; this is you, your localhost -- your CUPS daemon and your CUPS process within GNOME are talking to each other). IPP does mean Internet Printing Protocol but that doesn't mean that it's talking on *The Internet (big 'I') -- *without mincing words and getting too semantic, IPP is/can also be used on internets (small 'i') as well.  In this case, IPP is actually being used in this way, as it's being used in this capacity; on your own network (even if you're not connected to other machines).  I hope that makes sense.  I can elaborate further if you need me too ;-)  Bottom line, there's no need to worry ;-)

HPLIP is the HP Linux Printing and Imaging System and uses 'sometimes-rpc3' port 32770 and the script it run/has open is written in python and is running over IPv4 -- Internet Protocol 4.  Port 32770 if registered as Filenet NCH and is sometimes used in conjunction with NFS or NIS.  But here, neither one of those are being used...HPLIP is being used instead.  I can expound on this as well if need be.  But again, the bottom line here too is your fine.  No worries here either.

Everything is copacetic.  You're in good shape!

---

### Post by kent41 on 2006-10-17
> **ciscosurfer said:**
> You're fine.  IPP is setup by default.  Port 631 is talking to 42543 on your own system (127.0.0.1 -- your loopback address; this is you, your localhost -- your CUPS daemon and your CUPS process within GNOME are talking to each other). IPP does mean Internet Printing Protocol but that doesn't mean that it's talking on *The Internet (big 'I') -- *without mincing words and getting too semantic, IPP is/can also be used on internets (small 'i') as well.  In this case, IPP is actually being used in this way, as it's being used in this capacity; on your own network (even if you're not connected to other machines).  I hope that makes sense.  I can elaborate further if you need me too ;-)  Bottom line, there's no need to worry ;-)

HPLIP is the HP Linux Printing and Imaging System and uses 'sometimes-rpc3' port 32770 and the script it run/has open is written in python and is running over IPv4 -- Internet Protocol 4.  Port 32770 if registered as Filenet NCH and is sometimes used in conjunction with NFS or NIS.  But here, neither one of those are being used...HPLIP is being used instead.  I can expound on this as well if need be.  But again, the bottom line here too is your fine.  No worries here either.

Everything is copacetic.  You're in good shape!


Boy thats good news.
Thanks for the reply and have a good day:)

---

### Post by ciscosurfer on 2006-10-17
No problem.  If you have any other questions, just post them in the forums and we'll be happy to give it a go!

---

