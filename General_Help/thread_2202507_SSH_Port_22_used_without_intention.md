---
title: "SSH Port 22 used without intention"
date: 2014-01-29
forum: General Help
---

### Post by ruwan2 on 2014-01-29
Hi,
I run gdb debugger remotely on a host PC (ubuntu 12.04, 32 bit). At first I can connect to the target with its IP address. Now I don't know what reason itself adds a port 22, which gives error to the connection.
Besides the above IDE, I also test with a terminal. It has the same problem. (I do not use port 22, but it adds it)

[COLOR=#000080]robert@Aspire-M5100:~$ ssh root@192.168.0.131
ssh: connect to host 192.168.0.131 port 22: No route to host[/COLOR]

There is an article talking about SSH port 22, but it is difficult to understand it and solve the problem. Hopefully you can help me.

[h=1][COLOR=#4b0082]Why putting SSH on another port than 22 is bad idea
[/COLOR][/h][COLOR=#4b0082]
[https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/](https://www.adayinthelifeof.nl/2012/03/12/why-putting-ssh-on-another-port-than-22-is-bad-idea/)
[/COLOR][COLOR=#4b0082]On to the next reason not to change ports: A lot of applications  actually EXPECT ssh traffic on port 22. Now this might be a debate  wether or not those programs are developed properly, but it&#8217;s a fact.  Even though you can easily change the port in many applications but not  all of them do. Trust me, it WILL be annoying for developers, sysadmins  and users to operate on your SSH-port 52241, especially since they are  using 20 boxes, each with a different SSH port.
[/COLOR]
[COLOR=#4b0082] Another issue: many corporations have incoming and outgoing  firewalls, meaning you cannot goto any site to any random port and  expect it to work. Some secure ports, like port 22 are often exempt from  that, while other ports like port 25 or 110 are blocked.[/COLOR][COLOR=#000080]
[/COLOR]

How can I turn off the port 22?
Thanks,

---

### Post by ian-weisser on 2014-01-29
"Turn off the port 22" could mean a couple different things.

It could mean "I want to uninstall the ssh server on the remote machine". If so, uninstall the openssh-server package.

It could mean "I want to connect to a different port instead". Change the port in the remote machine's /etc/ssh/sshd_config, then restart the ssh server to load the changed config file.

---

### Post by papibe on 2014-01-29
Hi ruwan2.

The error you are getting is not related to the port, but to the IP address. You usually get that error if you made a mistake on the IP address, the server is actually down, or you don't have the proper routes to reach the IP address.

Could you ping the server or mtr the server?
```
ping 192.168.0.131

mtr -nrc 1 192.168.0.131
```
Let us know how it goes.
Regards.

---

