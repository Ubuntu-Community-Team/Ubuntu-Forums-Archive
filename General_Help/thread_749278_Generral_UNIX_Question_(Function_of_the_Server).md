---
title: "Generral UNIX Question (Function of the Server)?"
date: 2008-04-08
forum: General Help
---

### Post by matey3 on 2008-04-08
Hello All;

Is there any command or series of command that would show me what the main function of a server is?
How can I know if this machine is setup to be a DNS and/or DHCP or any has other functions?
uname -a doesnt give me the info i want.

I thought about using a windoz machine and doing an ipconfig /all to see the addresses of my dns server etc. but I have 20 or more servers here (some run vm some xen etc) and some one decided to setup so many different subnets that dont see each other (for the sake of so-called security which I call paranoia) but any way i inherited a big mess..


thanks for any help.

I am messing with this one dns server which is running OpenBSD (which i hate) lol and I cannot figure out why the clock on it is always ONE HOUR Behind?
it is also a dhcp server and the phone system are connected to it so whjen it has the wrong time everything has the wrong time!

I Use the date command to set up the time but in a few minutes it goes back one hour? I cannot find any commands beside ntpd -n -s -S -file (only switches avail)? and ntpd.conf is setup to get its time from x.pool.ntp.org
plus 5 more server addresses which i tested to make sure they work before i put them in there.
the thing I dislike about BSd 4.0 is that there are no commands like hwclock or ntpdate or anything like that at all? no update either! lol

sorry for long post but i had to explain why since i thought ppl would be wondering...

---

### Post by asbjorne08 on 2008-04-08
to find the services you have on a computer you could of cource nmap it

```
nmap hostname/ip
```

About the clock issue, it sounds like a timezone issue, try to find a bsd command to edit the timezone the computer is in.

-- 
a

---

