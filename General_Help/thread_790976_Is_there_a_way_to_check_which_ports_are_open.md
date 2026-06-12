---
title: "Is there a way to check which ports are open?"
date: 2008-05-11
forum: General Help
---

### Post by patrickaupperle on 2008-05-11
I installed apache2 and then removed it (it would not work for me, and openSSH fits my needs better.), and I want to make sure port 80 or whatever it is, is closed again.

---

### Post by Monicker on 2008-05-11
A port is only open if something is actually listening on it.  If you apache was truly removed then there should be no problem.

You can run the following if you wish:
```

sudo netstat -anltp|grep :80
```


If by some chance apache were still listening you would see something like the following:
```

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     10528/apache2
```

---

### Post by Tatty on 2008-05-11
You could try the Shields Up utility on this site [http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

---

### Post by p_quarles on 2008-05-11
Monicker's trick above will tell you what ports are open on your machine. If you use a router or gateway, chances are that your network is even further locked down. To check, you can run the following commands:
```
sudo apt-get install nmap curl
```
and then:
```
nmap -P0 $(curl www.whatismyip.org
```
The second command may take several minutes to run, but will give you an accurate picture of which (if any) ports are open to the world outside your home network.

---

### Post by patrickaupperle on 2008-05-11
> **Monicker said:**
> A port is only open if something is actually listening on it.  If you apache was truly removed then there should be no problem.

You can run the following if you wish:
```

sudo netstat -anltp|grep :80
```


If by some chance apache were still listening you would see something like the following:
```

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     10528/apache2
```

This is what I get. Is it OK?

```
tcp        0      0 100.100.1.100:4####     90.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     92.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     90.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     91.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     98.100.90.100:80        TIME_WAIT   -               

```

Edit: Yes I modified the numbers up there. Also, #### is a series of numbers.

---

### Post by Monicker on 2008-05-11
Yes, you are fine.  The only thing showing are outbound connections to the web site of these fourms.  Nothing is listening to port 80 on your machine, and there are no established connections to port 80 on your machine.

An external scan, as suggested by Tatty and p_quarles, is still a good thing to do once in a while, just to make sure there are no other exposed services that you might not be aware of.

---

### Post by inportb on 2008-05-11
Oh, that is an excellent idea. Though... I don't think one needs to install curl when wget is already available:

```
nmap -P0 $(wget -q http://www.whatismyip.org -O-)
```

---

### Post by p_quarles on 2008-05-11
> **patrickaupperle said:**
> This is what I get. Is it OK?

```
tcp        0      0 100.100.1.100:4####     90.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     92.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     90.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     91.100.90.100:80        TIME_WAIT   -               
tcp        0      0 100.100.1.100:4####     98.100.90.100:80        TIME_WAIT   -               

```

Edit: Yes I modified the numbers up there. Also, #### is a series of numbers.
That output shows that you are using a web browser to connect to Ubuntu Forums. Those are outbound connections. "Open ports" would be indicated by any connections which showed the computer's address in that fifth column.

---

### Post by patrickaupperle on 2008-05-11
> **Monicker said:**
> Yes, you are fine.  The only thing showing are outbound connections to the web site of these fourms.  Nothing is listening to port 80 on your machine, and there are no established connections to port 80 on your machine.

An external scan, as suggested by Tatty and p_quarles, is still a good thing to do once in a while, just to make sure there are no other exposed services that you might not be aware of.

Thank you. :KS

---

