---
title: "[Cloud LTS12.04] Apache Tomcat in Ubuntu cloud server doesn't start (thank)!"
date: 2014-10-28
forum: General Help
---

### Post by archimede2 on 2014-10-28
Hi all,
i have a remote cloud server based on Ubuntu LTS 12.04; i've installed Tomcat, and i want open port 80. Due this reason, i've tried to install ipconfig but i've read the follow message:

```

root@ar:~# sudo apt-get install ipconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ipconfig

```

And if i try to use iptables, i read the follow message.

```

iptables v1.4.12: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

```

I'm desperate... Can anyone help me? Very thanks!

EDIT: Please go to the last message, i've written the output of catalina.sh, i think is useful to understand the problem.

---

### Post by Alireza_Zamani on 2014-10-28
if you install and activate Apache http server , port 80 in opened,
for view active services :
> service --status-all

and for opened ports :
> nmap 127.0.0.1

---

### Post by archimede2 on 2014-10-28
Thank you! But Apache Tomcat doesn't work, in the fact:

1) If i start it, seem fine:

```

[FONT=Menlo]Using CATALINA_BASE:   /home/apache-tomcat-8.0.14[/FONT]
[FONT=Menlo]Using CATALINA_HOME:   /home/apache-tomcat-8.0.14[/FONT]
[FONT=Menlo]Using CATALINA_TMPDIR: /home/apache-tomcat-8.0.14/temp[/FONT]
[FONT=Menlo]Using JRE_HOME:        /usr/lib/jvm/java-8-oracle[/FONT]
[FONT=Menlo]Using CLASSPATH:       /home/apache-tomcat-8.0.14/bin/bootstrap.jar:/home/apache-tomcat-8.0.14/bin/tomcat-juli.jar[/FONT]
[FONT=Menlo]Tomcat started.
[/FONT]
```[FONT=Menlo]

2) But if i try to access via browser with [http://](http://)[ip]:8080, i read a "unable to connect on server" message.

3) And if i try to stop it, i read the error message:

[/FONT]```

[FONT=Menlo]Using CATALINA_BASE:   /home/apache-tomcat-8.0.14[/FONT]
[FONT=Menlo]Using CATALINA_HOME:   /home/apache-tomcat-8.0.14[/FONT]
[FONT=Menlo]Using CATALINA_TMPDIR: /home/apache-tomcat-8.0.14/temp[/FONT]
[FONT=Menlo]Using JRE_HOME:        /usr/lib/jvm/java-8-oracle[/FONT]
[FONT=Menlo]Using CLASSPATH:       /home/apache-tomcat-8.0.14/bin/bootstrap.jar:/home/apache-tomcat-8.0.14/bin/tomcat-juli.jar[/FONT]
[FONT=Menlo]Oct 28, 2014 2:38:48 PM org.apache.catalina.startup.Catalina stopServer[/FONT]
[FONT=Menlo]SEVERE: Could not contact localhost:8005. Tomcat may not be running.[/FONT]
[FONT=Menlo]Oct 28, 2014 2:38:48 PM org.apache.catalina.startup.Catalina stopServer[/FONT]
[FONT=Menlo]SEVERE: Catalina.stop: [/FONT]
[FONT=Menlo]java.net.ConnectException: Connection refused[/FONT]
[FONT=Menlo]    at java.net.PlainSocketImpl.socketConnect(Native Method)[/FONT]
[FONT=Menlo]    at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:345)[/FONT]
[FONT=Menlo]    at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:206)[/FONT]
[FONT=Menlo]    at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:188)[/FONT]
[FONT=Menlo]    at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:392)[/FONT]
[FONT=Menlo]    at java.net.Socket.connect(Socket.java:589)[/FONT]
[FONT=Menlo]    at java.net.Socket.connect(Socket.java:538)[/FONT]
[FONT=Menlo]    at java.net.Socket.<init>(Socket.java:434)[/FONT]
[FONT=Menlo]    at java.net.Socket.<init>(Socket.java:211)[/FONT]
[FONT=Menlo]    at org.apache.catalina.startup.Catalina.stopServer(Catalina.java:450)[/FONT]
[FONT=Menlo]    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)[/FONT]
[FONT=Menlo]    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)[/FONT]
[FONT=Menlo]    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)[/FONT]
[FONT=Menlo]    at java.lang.reflect.Method.invoke(Method.java:483)[/FONT]
[FONT=Menlo]    at org.apache.catalina.startup.Bootstrap.stopServer(Bootstrap.java:400)[/FONT]
[FONT=Menlo]    at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:487)[/FONT]

```

[FONT=Menlo]4) And if i try the nmap command, i read: [/FONT][FONT=Menlo]-bash: nmap: command not found.[/FONT][FONT=Menlo]
[/FONT]
5) And with service status all, i read

```

[FONT=Menlo] [ - ]  bootlogd[/FONT]
[FONT=Menlo] [ ? ]  console-setup[/FONT]
[FONT=Menlo] [ ? ]  cron[/FONT]
[FONT=Menlo] [ ? ]  dbus[/FONT]
[FONT=Menlo] [ ? ]  dmesg[/FONT]
[FONT=Menlo] [ ? ]  hostname[/FONT]
[FONT=Menlo] [ ? ]  hwclock[/FONT]
[FONT=Menlo] [ ? ]  hwclock-save[/FONT]
[FONT=Menlo] [ ? ]  killprocs[/FONT]
[FONT=Menlo] [ ? ]  module-init-tools[/FONT]
[FONT=Menlo] [ ? ]  network-interface[/FONT]
[FONT=Menlo] [ ? ]  network-interface-container[/FONT]
[FONT=Menlo] [ ? ]  network-interface-security[/FONT]
[FONT=Menlo] [ ? ]  networking[/FONT]
[FONT=Menlo] [ ? ]  ondemand[/FONT]
[FONT=Menlo] [ ? ]  plymouth[/FONT]
[FONT=Menlo] [ ? ]  plymouth-log[/FONT]
[FONT=Menlo] [ ? ]  plymouth-splash[/FONT]
[FONT=Menlo] [ ? ]  plymouth-stop[/FONT]
[FONT=Menlo] [ ? ]  plymouth-upstart-bridge[/FONT]
[FONT=Menlo] [ ? ]  procps[/FONT]
[FONT=Menlo] [ ? ]  rc.local[/FONT]
[FONT=Menlo] [ ? ]  resolvconf[/FONT]
[FONT=Menlo] [ ? ]  rsyslog[/FONT]
[FONT=Menlo] [ ? ]  sendsigs[/FONT]
[FONT=Menlo] [ ? ]  setvtrgb[/FONT]
[FONT=Menlo] [ + ]  ssh[/FONT]
[FONT=Menlo] [ - ]  stop-bootlogd[/FONT]
[FONT=Menlo] [ - ]  stop-bootlogd-single[/FONT]
[FONT=Menlo] [ ? ]  sudo[/FONT]
[FONT=Menlo] [ - ]  tomcat7[/FONT]
[FONT=Menlo] [ ? ]  udev[/FONT]
[FONT=Menlo] [ ? ]  udev-fallback-graphics[/FONT]
[FONT=Menlo] [ ? ]  udev-finish[/FONT]
[FONT=Menlo] [ ? ]  udevmonitor[/FONT]
[FONT=Menlo] [ ? ]  udevtrigger[/FONT]
[FONT=Menlo] [ ? ]  umountfs[/FONT]
[FONT=Menlo] [ ? ]  umountnfs.sh[/FONT]
[FONT=Menlo] [ ? ]  umountroot[/FONT]
[FONT=Menlo] [ - ]  urandom[/FONT]
[FONT=Menlo] [ ? ]  vrs_firewall[/FONT]
[FONT=Menlo] [ - ]  x11-common
[/FONT]
```

[FONT=Menlo]Thank for the help, i'm grateful![/FONT]

---

### Post by ian-weisser on 2014-10-28
> **archimede2 said:**
> ```
root@ar:~# sudo apt-get install ipconfig
```
You should not be using sudo from a root prompt.
There is no 'ipconfig' package in the 12.04 repositories. Why are you trying to install it? Are you following directions from someplace?

> **archimede2 said:**
> ```
iptables v1.4.12: can't initialize iptables table `filter': **Permission denied (you must be root)**
```
Perhaps you didn't use root or sudo?
What was the iptables command you were trying to do?

When you installed Ubuntu, did you change any of the default firewall settings? Have you changed any since?
If not, then port 80 is already open through your firewall. All the ports are open. The default firewall setting is to accept all packets.


Here's an example: I want to see my firewall rules.
```
me@me:~$ **iptables -L**
modprobe: ERROR: could not insert 'ip_tables': Operation not permitted
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

The command failed with a cryptic error because I didn't use sudo (or a root terminal) to authorize a root command.
Let's try it again with sudo:
```
me@me:~$ **sudo iptables -L**
[sudo] password for me: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

This time I succeeded. I can see all the firewall rules. They are really boring, the Ubuntu default is to ACCEPT all packets in both directions on all ports. If I want to run a webserver on Port 80, the firewall is not in the way.

---

### Post by archimede2 on 2014-10-28
> **ian-weisser said:**
> You should not be using sudo from a root prompt.
There is no 'ipconfig' package in the 12.04 repositories. Why are you trying to install it? Are you following directions from someplace?


Perhaps you didn't use root or sudo?
What was the iptables command you were trying to do?

When you installed Ubuntu, did you change any of the default firewall settings? Have you changed any since?
If not, then port 80 is already open through your firewall. All the ports are open. The default firewall setting is to accept all packets.


Here's an example: I want to see my firewall rules.
```
me@me:~$ **iptables -L**
modprobe: ERROR: could not insert 'ip_tables': Operation not permitted
iptables v1.4.21: can't initialize iptables table `filter': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.
```

The command failed with a cryptic error because I didn't use sudo (or a root terminal) to authorize a root command.
Let's try it again with sudo:
```
me@me:~$ **sudo iptables -L**
[sudo] password for me: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

This time I succeeded. I can see all the firewall rules. They are really boring, the Ubuntu default is to ACCEPT all packets in both directions on all ports. If I want to run a webserver on Port 80, the firewall is not in the way.

1) Ok, but why my Tomcat is so strange? If the port is opening, why i don't see via browser, and why i cannot shutdown it?
2) I'm trying to install ipconfig to open a port, but if is not necessary ok.
3) With sudo iptables -l command, i see
```

[FONT=Menlo]iptables v1.4.12: can't initialize iptables table `filter': Permission denied (you must be root)[/FONT]
[FONT=Menlo]Perhaps iptables or your kernel needs to be upgraded.[/FONT]

```
4) And with netstat command i see (i think this is important, i don't see any 80 port) the output:
```

[FONT=Menlo]tcp        0      0 0.0.0.0:22              0.0.0.0:*               [COLOR=#c33720]**LISTEN **[/COLOR]    [/FONT]
[FONT=Menlo]tcp6       0      0 :::22                   :::*                    [COLOR=#c33720][B]LISTEN

```[/B][/COLOR][/FONT]


Very thanks!

---

### Post by archimede2 on 2014-10-28
Up (i'm desperate, thank to all...)

---

### Post by ian-weisser on 2014-10-28
> **archimede2 said:**
> 3) With sudo iptables -l command, i see

If you use your normal login account (not the root account) with sudo commands (like 'sudo iptables -L'), do the commands work?
If not, are you using a user account that has admin permissions? With a cloud instance, I would assume so...but checking helps.

> **archimede2 said:**
> 4) And with netstat command i see
What's the *exact* netstat command you are using? Using the right one is important.

Here's an example:

This is a user netstat command. Note the lack of sudo:
```
me@me:~$ netstat -tlpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:18229           0.0.0.0:*               LISTEN      2431/skype      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -  
```

Now compare it to this root netstat command, using sudo:
```
me@me:~$ sudo netstat -tlpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:18229           0.0.0.0:*               LISTEN      2431/skype      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1205/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      10737/cupsd     
tcp6       0      0 ::1:631                 :::*                    LISTEN      10737/cupsd
```

You can tell from my services (skype, cups, dnsmasq) that mine isn't a cloud instance.

I think your Tomboy isn't opening a port under your username. I don't use Tomboy, so know little about it.
Try a sudo netstat to determine if it's listening on any port at all.

When you post output, be sure to include your original command and *all* output, just like in your first post.

---

### Post by archimede2 on 2014-10-28
> **ian-weisser said:**
> If you use your normal login account (not the root account) with sudo commands (like 'sudo iptables -L'), do the commands work?
If not, are you using a user account that has admin permissions? With a cloud instance, I would assume so...but checking helps.


What's the *exact* netstat command you are using? Using the right one is important.

Here's an example:

This is a user netstat command. Note the lack of sudo:
```
me@me:~$ netstat -tlpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:18229           0.0.0.0:*               LISTEN      2431/skype      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -  
```

Now compare it to this root netstat command, using sudo:
```
me@me:~$ sudo netstat -tlpn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:18229           0.0.0.0:*               LISTEN      2431/skype      
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1205/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      10737/cupsd     
tcp6       0      0 ::1:631                 :::*                    LISTEN      10737/cupsd
```

You can tell from my services (skype, cups, dnsmasq) that mine isn't a cloud instance.

I think your Tomboy isn't opening a port under your username. I don't use Tomboy, so know little about it.
Try a sudo netstat to determine if it's listening on any port at all.

When you post output, be sure to include your original command and *all* output, just like in your first post.


Very thank for your help, i appreciate it... Since 2 days i'm working for this! Now i give you all informations.

1) I've only the root user, normally, in my test cloud server, i make all with it.
2) In my cloud i'm root user (the provider has give me the credentials.
3) The command is [FONT=Menlo]netstat -ntlp | grep LISTEN
4) The output of netstat -ntlp is
```


```[/FONT]```
[FONT=Menlo]Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name[/FONT]
[FONT=Menlo]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      5622/sshd       [/FONT]
[FONT=Menlo]tcp6       0      0 :::22                   :::*                    LISTEN      5622/sshd
[/FONT]
```[FONT=Menlo]
5) The output with sudo is:
[/FONT]```

[FONT=Menlo]Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name[/FONT]
[FONT=Menlo]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      5622/sshd       [/FONT]
[FONT=Menlo]tcp6       0      0 :::22                   :::*                    LISTEN      5622/sshd 
[/FONT]
```[FONT=Menlo]

If you want other infos, i'm here! Thank...
[/FONT]

[FONT=Menlo]
[/FONT]

---

### Post by archimede2 on 2014-10-28
If necessary, i can give you via private message my cloud credentials to help, to understand the problem... At the moment, i haven't any app installed and by me isn't a problem, after the solutions, reset the pwd and choose one other! (thank)

---

### Post by QIII on 2014-10-28
Please do not conduct any support in private.  Doing so will deprive other community members of the benefit of any solution found.

Thanks.

---

### Post by archimede2 on 2014-10-28
No, i don't want deprive any! My intentions are (only if you agree) give credential to an users, so he can best the situation understand, and after post here the ENTIRE solutions!
Do you agree? Thank

---

### Post by archimede2 on 2014-10-28
Another information about the problem: Tomcat was not started!

If i write sudo netstat -an | grep 8080 i see:


```

tcp6       0      0 127.101.13.1:8080       127.101.13.1:53557      TIME_WAIT

```


and if i write sudo ps -ef | grep catalina i see:


```

root     31224 32353  0 May14 pts/37   00:00:00 grep --color=auto catalina

```

And this is the COMPLETE output of ./catalina.sh run:

```

[FONT=Menlo]Using CATALINA_BASE:   /home/apache-tomcat-8.0.14[/FONT]
[FONT=Menlo]Using CATALINA_HOME:   /home/apache-tomcat-8.0.14[/FONT]
[FONT=Menlo]Using CATALINA_TMPDIR: /home/apache-tomcat-8.0.14/temp[/FONT]
[FONT=Menlo]Using JRE_HOME:        /usr/lib/jvm/java-8-oracle[/FONT]
[FONT=Menlo]Using CLASSPATH:       /home/apache-tomcat-8.0.14/bin/bootstrap.jar:/home/apache-tomcat-8.0.14/bin/tomcat-juli.jar[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.308 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log Server version: Apache Tomcat/8.0.14[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log Server built:   Sep 24 2014 09:01:51[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log Server number:  8.0.14.0[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log OS Name:        Linux[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log OS Version:     2.6.32-5-vserver-amd64[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log Architecture:   amd64[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log JVM Version:    1.8.0_25-b17[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.311 INFO [main] org.apache.catalina.startup.VersionLoggerListener.log JVM Vendor:     Oracle Corporation[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.579 INFO [main] org.apache.catalina.core.AprLifecycleListener.init The APR based Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: /usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.830 INFO [main] org.apache.coyote.AbstractProtocol.init Initializing ProtocolHandler ["http-nio-8080"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.848 INFO [main] org.apache.tomcat.util.net.NioSelectorPool.getSharedSelector Using a shared selector for servlet write/read[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.852 INFO [main] org.apache.coyote.AbstractProtocol.init Initializing ProtocolHandler ["ajp-nio-8009"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.854 INFO [main] org.apache.tomcat.util.net.NioSelectorPool.getSharedSelector Using a shared selector for servlet write/read[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.854 INFO [main] org.apache.catalina.startup.Catalina.load Initialization processed in 637 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.883 INFO [main] org.apache.catalina.core.StandardService.startInternal Starting service Catalina[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.883 INFO [main] org.apache.catalina.core.StandardEngine.startInternal Starting Servlet Engine: Apache Tomcat/8.0.14[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:35.900 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory /home/apache-tomcat-8.0.14/webapps/ROOT[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:36.685 INFO [localhost-startStop-1] org.apache.catalina.util.SessionIdGeneratorBase.createSecureRandom Creation of SecureRandom instance for session ID generation using [SHA1PRNG] took [512] milliseconds.[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:36.714 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory /home/apache-tomcat-8.0.14/webapps/ROOT has finished in 814 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:36.715 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory /home/apache-tomcat-8.0.14/webapps/docs[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:36.738 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory /home/apache-tomcat-8.0.14/webapps/docs has finished in 24 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:36.739 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory /home/apache-tomcat-8.0.14/webapps/examples[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.138 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory /home/apache-tomcat-8.0.14/webapps/examples has finished in 399 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.139 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory /home/apache-tomcat-8.0.14/webapps/host-manager[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.168 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory /home/apache-tomcat-8.0.14/webapps/host-manager has finished in 28 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.168 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deploying web application directory /home/apache-tomcat-8.0.14/webapps/manager[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.200 INFO [localhost-startStop-1] org.apache.catalina.startup.HostConfig.deployDirectory Deployment of web application directory /home/apache-tomcat-8.0.14/webapps/manager has finished in 32 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.205 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["http-nio-8080"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.212 INFO [main] org.apache.coyote.AbstractProtocol.start Starting ProtocolHandler ["ajp-nio-8009"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.213 INFO [main] org.apache.catalina.startup.Catalina.start Server startup in 1358 ms[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.215 SEVERE [main] org.apache.catalina.core.StandardServer.await StandardServer.await: create[localhost:8005]: [/FONT]
[FONT=Menlo] java.net.BindException: Cannot assign requested address[/FONT]
[FONT=Menlo]	at java.net.PlainSocketImpl.socketBind(Native Method)[/FONT]
[FONT=Menlo]	at java.net.AbstractPlainSocketImpl.bind(AbstractPlainSocketImpl.java:382)[/FONT]
[FONT=Menlo]	at java.net.ServerSocket.bind(ServerSocket.java:375)[/FONT]
[FONT=Menlo]	at java.net.ServerSocket.<init>(ServerSocket.java:237)[/FONT]
[FONT=Menlo]	at org.apache.catalina.core.StandardServer.await(StandardServer.java:420)[/FONT]
[FONT=Menlo]	at org.apache.catalina.startup.Catalina.await(Catalina.java:713)[/FONT]
[FONT=Menlo]	at org.apache.catalina.startup.Catalina.start(Catalina.java:659)[/FONT]
[FONT=Menlo]	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)[/FONT]
[FONT=Menlo]	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)[/FONT]
[FONT=Menlo]	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)[/FONT]
[FONT=Menlo]	at java.lang.reflect.Method.invoke(Method.java:483)[/FONT]
[FONT=Menlo]	at org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:351)[/FONT]
[FONT=Menlo]	at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:485)[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.216 INFO [main] org.apache.coyote.AbstractProtocol.pause Pausing ProtocolHandler ["http-nio-8080"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.270 INFO [main] org.apache.coyote.AbstractProtocol.pause Pausing ProtocolHandler ["ajp-nio-8009"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.321 INFO [main] org.apache.catalina.core.StandardService.stopInternal Stopping service Catalina[/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.350 INFO [main] org.apache.coyote.AbstractProtocol.stop Stopping ProtocolHandler ["http-nio-8080"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.351 INFO [main] org.apache.coyote.AbstractProtocol.stop Stopping ProtocolHandler ["ajp-nio-8009"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.351 INFO [main] org.apache.coyote.AbstractProtocol.destroy Destroying ProtocolHandler ["http-nio-8080"][/FONT]
[FONT=Menlo]28-Oct-2014 18:59:37.352 INFO [main] org.apache.coyote.AbstractProtocol.destroy Destroying ProtocolHandler ["ajp-nio-8009"]

```[/FONT]

---

### Post by dragonfly41 on 2014-10-28
> 
SEVERE: Could not contact localhost:8005. Tomcat may not be running.


Thought.  Possibly another version of Tomcat already running .. ?

[http://www.coderanch.com/t/611399/Tomcat/Server-Tomcat-Server-localhost-failed](http://www.coderanch.com/t/611399/Tomcat/Server-Tomcat-Server-localhost-failed)

---

### Post by archimede2 on 2014-10-28
No...

---

### Post by yabu2 on 2014-10-31
Have you ever tried "catalina.sh run" so you could knowing whats going on with that

---

