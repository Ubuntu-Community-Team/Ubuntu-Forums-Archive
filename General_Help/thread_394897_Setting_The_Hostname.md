---
title: "Setting The Hostname"
date: 2007-03-27
forum: General Help
---

### Post by quicksilver1234 on 2007-03-27
Hi All,
I'm going through a tutorial on setup. most makes sense but what does this do?
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3")
```
Setting The Hostname

echo server1.example.com > /etc/hostname
/bin/hostname -F /etc/hostname
```

What host are they talking about? My primary web site?
What do I gain by having a file named "/etc/quicksilver1234.com"
Or should that be something like the name of the computer, that I call Hal
"/etc/hal"

---

### Post by dfreer on 2007-03-27
You are reading the command wrong. It's ok though, it's a little confusing.

> echo server1.example.com > /etc/hostname
The *echo* command with the *>* redirect will insert text into a file. So in this case they are inserting the line:
```
server1.example.com
```
into the */etc/hostname* file. You will want to replace *server1.example.com* with name of the computer, "Hal", and your domain name, "quicksilver1234.com"

So this would be the EXACT command you would want to run, assuming the above:

```
echo Hal.quicksilver1234.com > /etc/hostname
```

---

### Post by dfreer on 2007-03-27
BTW, make sure to update your /etc/hosts file as well, otherwise when you reboot sudo will give you a nasty error. For more information read this thread:
[http://www.ubuntuforums.org/showthread.php?t=390469](http://www.ubuntuforums.org/showthread.php?t=390469)

---

### Post by quicksilver1234 on 2007-03-27
Thanks!

---

