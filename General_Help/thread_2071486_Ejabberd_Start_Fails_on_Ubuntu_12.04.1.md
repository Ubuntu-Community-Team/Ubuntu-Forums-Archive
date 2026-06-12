---
title: "Ejabberd Start Fails on Ubuntu 12.04.1"
date: 2012-10-15
forum: General Help
---

### Post by flamadiddle on 2012-10-15
I am trying to install [FONT="Courier New"]ejabberd 2.1.10-2[/FONT] on my [FONT="Courier New"]Ubuntu 12.04.1[/FONT] server. This is a fresh install, and ejabberd is never successfully installed.

[SIZE="4"]**The Install**[/SIZE]

Every time, apt-get hangs on this:

```
Setting up ejabberd (2.1.10-2ubuntu1) ...
Generating SSL certificate /etc/ejabberd/ejabberd.pem...

Creating config file /etc/ejabberd/ejabberd.cfg with new version
Starting jabber server: ejabberd............................................................ failed.
```

The dots just go until it times out or I 'killall' [FONT="Courier New"]beam[/FONT], [FONT="Courier New"]beam.smp[/FONT], [FONT="Courier New"]epmd[/FONT], and [FONT="Courier New"]ejabberd[/FONT] processes. I've turned off all firewall restrictions.

Here's the output of [FONT="Courier New"]epmd -names[/FONT] while the install is hung:

```
epmd: up and running on port 4369 with data:
name ejabberdctl at port 42108
name ejabberd at port 39621
```

And after it fails:

```
epmd: up and running on port 4369 with data:
name ejabberd at port 39621
```

At the same time (during and after), the output of both [FONT="Courier New"]netstat -atnp | grep 5222[/FONT] and [FONT="Courier New"]netstat -atnp | grep 5280[/FONT] is empty.


[SIZE="4"]**The Crash File**[/SIZE]

A crash dump file is created at [FONT="Courier New"]/var/log/ejabber/erl_crash.dump[/FONT]. The slogan (i.e. reason for the crash) is:

```
Slogan: Kernel pid terminated (application_controller) ({application_start_failure,kernel,{shutdown,{kernel,start,[normal,[]]}}})
```

[SIZE="4"]**It's alive?**[/SIZE]

Whenever I try to relaunch ejabberd with [FONT="Courier New"]service ejabberd start[/FONT], the same thing happens - even if I've killed all processes before doing so.

However, when I killall the processes listed above again, and run [FONT="Courier New"]su - ejabberd -c /usr/sbin/ejabberd[/FONT], this is the output I get:

```
Erlang R14B04 (erts-5.8.5) [source] [64-bit] [rq:1] [async-threads:0] [kernel-poll:false]

Eshell V5.8.5  (abort with ^G)
(ejabberd@ns1)1> 
=INFO REPORT==== 15-Oct-2012::12:26:13 ===
I(<0.478.0>:ejabberd_listener:166) : Reusing listening port for 5222

=INFO REPORT==== 15-Oct-2012::12:26:13 ===
I(<0.479.0>:ejabberd_listener:166) : Reusing listening port for 5269

=INFO REPORT==== 15-Oct-2012::12:26:13 ===
I(<0.480.0>:ejabberd_listener:166) : Reusing listening port for 5280

=INFO REPORT==== 15-Oct-2012::12:26:13 ===
I(<0.40.0>:ejabberd_app:72) : ejabberd 2.1.10 is started in the node ejabberd@ns1
```

Then, the server appears to be running. I get a login prompt when I access [FONT="Courier New"]http://mydomain.com:5280/admin/[/FONT]. Of course I can't login unless I create an account.

At this time, the output of [FONT="Courier New"]netstat -atnp | grep 5222[/FONT] and [FONT="Courier New"]netstat -atnp | grep 5280[/FONT] is as follows:

```
tcp        0      0 0.0.0.0:5222            0.0.0.0:*               LISTEN      19347/beam      
tcp        0      0 0.0.0.0:5280            0.0.0.0:*               LISTEN      19347/beam      
```

[SIZE="4"]**ejabberdctl**[/SIZE]

Even when it appears ejabberd is running, trying to do anything with ejabberdctl fails. For example: trying to register a user:

```
root@ns1:~# ejabberdctl register myusername mydomain.com mypassword
Failed RPC connection to the node ejabberd@ns1: nodedown
```

I have no idea what I'm doing wrong. I've attached a gzipped copy of the erl_crash.dump file in case it's helpful. This happens on two different servers I have with identical software installed (really not much of anything). Please help. Thanks.

---

### Post by OyvindL on 2013-02-22
Did you find any solution on this? Have the same problem and my googling didn't get me any answers ;)
Could possibly Apache do some conflict?

---

### Post by flamadiddle on 2013-02-22
Yes I did. Sorry for not posting my solution here before. I asked the same question on AskUbuntu.com and [found a solution there]("http://askubuntu.com/a/205566/3291"). The problem was that ejabberd couldn't find my host by name (it uses the node name). I just needed to add this line to my /etc/hosts file:

```
123.123.123.123   ns1
```

Since it was trying to connect to the node 'ejabberd@ns1'.

Obviously, 123.123.123.123 is not my actual IP, but you get the idea.

---

