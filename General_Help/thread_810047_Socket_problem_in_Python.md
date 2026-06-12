---
title: "Socket problem in Python"
date: 2008-05-27
forum: General Help
---

### Post by Roberto_Lapuente on 2008-05-27
Python socket problem
Hi, I'm trying to listen a port with python on a debian server. I try the program in ubuntu and it worked but in debian it gives back:
socket.error: (99, 'Cannot assign requested address')
my code is:

```

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.bind((socket.gethostname(), 6002))
sock.listen(5)
```

please help

---

### Post by Monicker on 2008-05-27
No need to repeat the same thing from an earler thread.

[http://ubuntuforums.org/showthread.php?t=809753]("http://ubuntuforums.org/showthread.php?t=809753")

Be patient.  If someone has an answer, they will respond.

---

### Post by superyounan1 on 2008-05-27
could it be you have some process already listening on that port?

```
netstat -lp
```

---

### Post by Roberto_Lapuente on 2008-05-27
Sorry about the two threads but im really in a hurry.
I tried to change the port I tried 25, 6000, 6001, 6666, 8000 and the same error on all of them.

doesn't debian has a firewall or something i have to configure before i can listen to a port?

---

### Post by Monicker on 2008-05-27
> **Roberto_Lapuente said:**
> Sorry about the two threads but im really in a hurry.
I tried to change the port I tried 25, 6000, 6001, 6666, 8000 and the same error on all of them.

doesn't debian has a firewall or something i have to configure before i can listen to a port?

Ubuntu does not block any ports by default.  Even if you had activated some firewall rules, it would not prevent an application from binding to a port, or cause the type of error that you are seeing.

Did you look up the specific error message?

---

### Post by superyounan1 on 2008-05-27
> **Roberto_Lapuente said:**
> Sorry about the two threads but im really in a hurry.
I tried to change the port I tried 25, 6000, 6001, 6666, 8000 and the same error on all of them.

doesn't debian has a firewall or something i have to configure before i can listen to a port?

hmm, i don't know if the firewall would prevent sockets to be opened, i thought it would just keep outside connections from seeing the ports

check iptables or firestart if you have that installed

---

### Post by Roberto_Lapuente on 2008-05-27
> Did you look up the specific error message?

The error says:

  File "<string>", line1, in bind
socket.error: (99, 'Cannot assign requested addres?)

I look up for the error but i didn't find any information

---

### Post by Monicker on 2008-05-27
Really?  I googled and found a number of references to that error message.

You could start here:  [http://mail.python.org/pipermail/python-list/2004-June/268180.html]("http://mail.python.org/pipermail/python-list/2004-June/268180.html")

---

### Post by Roberto_Lapuente on 2008-05-28
I used:
```
ifconfig lo up
```
and now it is openig the port but if I use:
```
host=socket.gethostbyname(socket.gethostname())
print host
```

it prints:
127.0.1.1
and from the modem configuration I know its IP address is
192.168.1.87

---

### Post by Roberto_Lapuente on 2008-05-28
I replaced socket.gethostbyname(socket.gethostname())
with the IP adress i get form my router and it worked so it's the sock.gethostbyname 

does someone knows why it isn't working??

---

