---
title: "Remotely running X-windows"
date: 2006-11-04
forum: General Help
---

### Post by wonk-o-matic on 2006-11-04
I have two dapper kubuntu boxes in different rooms, and I'm trying to run X-windows apps from one box while running the display on the other.  I do it between Solaris and XP all the time, but obviously need a better grip on how this works to get it going between these two kubuntu boxes.  

After the many non-solutions that I googled, here's the attempt that I really thought should work, but didn't. 

konsole
xhost + <other_box_IP>
add "6000 <other_box_IP>" to hosts.allow
ssh -l <username> -X <other_box_IP>
(X forwarding is turned on in the other box's sshd_config.)
DISPLAY=<IP>:0.0
(also tried <IP>:0)
xcalc

I get: 
Error: Can't open display: 192.168.1.2:0.0
or
Error: Can't open display: 192.168.1.2:0
Any ideas?  

Thanks in advance, 
Dan

---

### Post by amohanty on 2006-11-04
If this is on an internal network and you have firewall, just turn on XDMCP on the host and do a
X :1 -query <ip>

Unless of course you only want to use an SSH based solution.

HTH
AM

---

### Post by wonk-o-matic on 2006-11-04
Thanks, I'll give that a try.  

BTW, no sooner did I post that question than I realized that xhost and iptables aren't operative, because I'm tunneling through ssh.  

- Dan

---

### Post by CatKiller on 2006-11-04
> **wonk-o-matic said:**
> I have two dapper kubuntu boxes in different rooms, and I'm trying to run X-windows apps from one box while running the display on the other.

```
shh -X user@hostname
```

---

### Post by BalasariusX on 2006-12-19
This is such a common problem for all Linux distros.  Why?  It works fine on my PC with eXceed.

Telnet or SSH to the remote host, export your DISPLAY variable, and launch your app.  Yay, done.

Why doesn't this work on Linux???

I've googled this problem, and nothing seems to work.  There are many threads like one, and none of them seem to fix the problem because the OP never returns and says, "Thanks guys!"

I've tried it all.

SSH -X ...
SSH -Y ...
xhost +

Nothing seems to work.  It's like there something not listening on my local linux box.  I'm using a default install of Edgy Eft.  Nothing fancy.  I just want remote X apps to run.

xhost +
ssh -X root@malak
export DISPLAY=<current PC>:0
xterm

Warning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s

Any help would be greatly appreciated...

---

### Post by Zwack on 2007-01-04
> **BalasariusX said:**
> This is such a common problem for all Linux distros.  Why?  It works fine on my PC with eXceed.

Telnet or SSH to the remote host, export your DISPLAY variable, and launch your app.  Yay, done.

Why doesn't this work on Linux???



Xauthority!

Assuming that you have the X server accepting remote connections...
To check go to System->Adminstration->Login Window.  Select the Security tab and uncheck the "Deny TCP Connections to X Server" option.

Now on your linux box type xauth

You will then get a line saying "Using authority file..." and an xauth> prompt.

At the prompt type list.

You will get a list of "server MIT-MAGIC-COOKIE-1 key"

Look for one that has the display you want to use (you may want to add it)
I have one that has hostname\unix:0 and I don't use that (it's local) instead I use <IP>:0

Then on the remote host I type xauth
and at the prompt
add <xserver> MIT-MAGIC-COOKIE-1 <key>
then
exit.

Then it just works...
You only need to do this once... and I don't need to do it on AIX servers, only HP-UX and Linux boxes...

I hope that this helps,

Z.

---

### Post by BalasariusX on 2007-01-08
Thank you for your reply... still no-joy.

How can I tell if my Xserver is accepting connections?   Sigh.

Local box (Republic)

duncan@Republic:/$ xauth
Using authority file /home/duncan/.Xauthority
xauth> list
Republic/unix:0  MIT-MAGIC-COOKIE-1  14d24cc712f643fcaffef7d4d58abea9
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  14d24cc712f643fcaffef7d4d58abea9

Remote Linux box (Malak):

[root@malak ~]# xauth
Using authority file /root/.Xauthority
xauth> list
131.101.148.18:1  MIT-MAGIC-COOKIE-1  3001e9b318d5dff3bb189cb922862a5b
131.101.148.18:2  MIT-MAGIC-COOKIE-1  2457264118faf9c689094c7798388f63
malak:0  MIT-MAGIC-COOKIE-1  342b3d7d4e015fc1e855d16f1a54a760
republic.ltd.amphenol-tcs.com:0  MIT-MAGIC-COOKIE-1  14d24cc712f643fcaffef7d4d58abea9
malak.ltd.amphenol-tcs.com/unix:10  MIT-MAGIC-COOKIE-1  f940bc1260bf3cc3ae4aa4816d5f252e

I've SSH'd with -X and same error:

xterm Xt error: Can't open display: %s

Then I figured I needed to add malak to republic, so:

xauth> list
Republic/unix:0  MIT-MAGIC-COOKIE-1  14d24cc712f643fcaffef7d4d58abea9
localhost.localdomain/unix:0  MIT-MAGIC-COOKIE-1  14d24cc712f643fcaffef7d4d58abea9
malak.ltd.amphenol-tcs.com:0  MIT-MAGIC-COOKIE-1  342b3d7d4e015fc1e855d16f1a54a760

Still no joy.  :( 

Thanks in advance.

---

