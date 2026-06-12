---
title: "CLI: Using multiple &quot;grep&quot;s with &quot;tail -F&quot;"
date: 2006-07-21
forum: General Help
---

### Post by ssalman on 2006-07-21
Hi, I’m trying to learn the grep command and use it with tail. I came across a weird situation, and I would like to understand why it’s happening and if there is ways around it. Here is what I’m doing:

I set up a firewall using [this ]("https://help.ubuntu.com/community/IptablesHowTo")iptables howto 

And I would like to monitor the blocked logs, so I’m using 

```
tail /var/log/syslog | grep “iptables denied:” | grep –o “DST=[0-9\.]*[[:space:]]”
``` 
and it works great, but when I want to have a constant feedback using the tail –F command it does not return anything:

```
tail /var/log/syslog –F | grep “iptables denied:” | grep –o “DST=[0-9\.]*[[:space:]]”
``` 
using only one grep filter works, so I'm thinking the tail -F does not work with multiple filters? not really sure where I went wrong.

Thanks.

---

### Post by fabiand on 2006-07-21
Hey,

try to use "tail -f" (small f) instead of a capital F.

---

### Post by ssalman on 2006-07-21
> **fabiand said:**
> Hey,

try to use "tail -f" (small f) instead of a capital F.

Thanks for the reply, but it did not work, same behaviour remains!!:(

---

### Post by IYY on 2006-07-21
> using only one grep filter works, so I'm thinking the tail -F does not work with multiple filters? not really sure where I went wrong.

You're right. -F will make grep continue updating, so it can't work with a pipe, and you'll have to take another route. There was a nice little command to execute a command once every n seconds, but alas I forgot it (maybe someone will remember), so here's a slightly less elegant way you could try instead:

```
while true
do
   tail /var/log/syslog | grep “iptables denied:” | grep –o “DST=[0-9\.]*[[:space:]]”
   sleep 0.5
done
```

---

### Post by steve.horsley on 2006-07-22
The problem is that grep doesn't normally flush its output at the end of every line. You WILL get the stuff eventually, but only when grep accumulates a buffer full. Try using the option  --line-buffered on the middle grep like this:
> tail /var/log/syslog &#8211;F | grep --line-buffered &#8220;iptables denied:&#8221; | grep &#8211;o &#8220;DST=[0-9\.]*[[:space:]]&#8221;

---

### Post by ssalman on 2006-07-25
> **steve.horsley said:**
> The problem is that grep doesn't normally flush its output at the end of every line. You WILL get the stuff eventually, but only when grep accumulates a buffer full. Try using the option  --line-buffered on the middle grep like this:

Thanks steve, you were absolutly right, I needed to add this option to all grep commands in the middle (I had an example with many pipelines) and it worked... Thank you very much.

---

### Post by anguyen on 2006-07-27
Is the command you're thinking of 'watch'?

> **IYY said:**
> You're right. -F will make grep continue updating, so it can't work with a pipe, and you'll have to take another route. There was a nice little command to execute a command once every n seconds, but alas I forgot it (maybe someone will remember), so here's a slightly less elegant way you could try instead:

```
while true
do
   tail /var/log/syslog | grep “iptables denied:” | grep –o “DST=[0-9\.]*[[:space:]]”
   sleep 0.5
done
```

---

