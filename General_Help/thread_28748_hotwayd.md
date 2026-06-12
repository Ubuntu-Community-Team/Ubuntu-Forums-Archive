---
title: "hotwayd"
date: 2005-04-21
forum: General Help
---

### Post by sameat on 2005-04-21
Has anybody had any luck getting hotwayd to run?  I have installed it per  the inetd instructions, ([http://hotwayd.sourceforge.net/e107_plugins/custompages/Install_inetd.php](http://hotwayd.sourceforge.net/e107_plugins/custompages/Install_inetd.php))
but it doesn't seem to be working.  When I attempt to telnet, I get:

Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

and after a few seconds: 

Connection closed by foreign host.

Any thoughts?  Thanks!

---

### Post by treris on 2005-05-13
Yeah I have te same problem, at first it worked, but after a reboot I had no luck getting it back to work, maybe the connection to the telnet 127.0.0.1 at port 110 is closing too fast for the e-mail client to connect to hotmail??

---

### Post by hub on 2005-10-02
I have a close problem with hotwayd, the deb has been installed normally, I can launch it normally typing hotwayd:
goldfish@salmon:~$ hotwayd
+OK POP3 hotwayd v0.8 -> The POP3-HTTPMail Gateway. Server on salmon active.

then check with nmap if the port is open:

goldfish@salmon:~$ nmap -v salmon

Starting nmap 3.75 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-10-02 17:54 BST
Initiating Connect() Scan against localhost.localdomain (127.0.0.1) [1663 ports] at 17:54
Discovered open port 631/tcp on 127.0.0.1
Discovered open port 2628/tcp on 127.0.0.1
Discovered open port 139/tcp on 127.0.0.1
Discovered open port 445/tcp on 127.0.0.1
The Connect() Scan took 0.20s to scan 1663 total ports.
Host localhost.localdomain (127.0.0.1) appears to be up ... good.
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1659 ports scanned but not shown below are in state: closed)
PORT     STATE SERVICE
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
2628/tcp open  dict

Nmap run completed -- 1 IP address (1 host up) scanned in 0.368 seconds

no 110 at all.

My /etc/xinetd.conf




defaults
{


}

service hotwayd
{
#only_from=192.168.0.0/24 #for gentoo security?
disable = no
type = unlisted
socket_type = stream
protocol = tcp
wait = no
user = goldfish
groups = yes
server = /usr/bin/hotwayd #must be full path!
#server_args = -p [http://proxy:8080](http://proxy:8080) -u proxy_user -q proxy_password
port = 110
}


includedir /etc/xinetd.d




and the directory include does not have any hotwayd file.


firestarter does not have any rules against the use of a port 110.

treris what does nmap give you?

---

