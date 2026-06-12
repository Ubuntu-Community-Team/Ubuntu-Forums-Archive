---
title: "SNMP Related Questions"
date: 2015-05-12
forum: General Help
---

### Post by mrJTparadise on 2015-05-12
Hi everyone,

I am new to SNMP - very new.  I've been reading up on it since late yesterday and a majority of my day today.

I am interested in creating an SNMP implementation on my Ubuntu 14.04 system.  

In short, I have scripts that output information and I want to be able to give the clients the ability to view this output.

I have an existing implementation on a similiar device, but I am very new to SNMP and have been reading up on the source files.  I have a custom MIB and smnp.conf/snmpd.conf files.  I also have some C source code along with a Makefile which tells me how they built their implementation.

I have some questions : 

1.  Net-SNMP is not part of the Ubuntu repository and needs to be downloaded from a third-party.  With this said, assuming I got that part correct, what is the different between Net-SNMP and snmp/d?

2.  I've been searching for terms like "SNMP tutorial for developers", etc. and I cannot seem to find a decent tutorial out there.  A majority of the tutorials go over what is a MIB, what is GET/GETNEXT/SET/etc.  Is there a good tutorial out on the web that google is hiding from me?

3.  How would I go about testing my existing implementation?

4.  What is the difference between an agent, daemon, client, server?  A lot of tutorials don't clarify what is what and all this tells me is that all these words are used interchangeably:confused:.

[I]I've been starting to read : 

[https://help.ubuntu.com/community/SNMPAgent](https://help.ubuntu.com/community/SNMPAgent)
[http://www.net-snmp.org/wiki/index.php/TUT:Writing_a_MIB_Module](http://www.net-snmp.org/wiki/index.php/TUT:Writing_a_MIB_Module)
[http://www.net-snmp.org/wiki/index.php/Tutorials](http://www.net-snmp.org/wiki/index.php/Tutorials)[/I]

---

### Post by The Cog on 2015-05-12
1:
Net-SNMP is in the repositories. It seems it be broken bwetween packages **snmp** (manager) and **snmpd** (agent). 

2: 
I don't know any good ones. I just googled for "how to script net-snmp agent" and got a useful looking set of links (net-snmp.org took the top 3 results). 
[http://www.net-snmp.org/wiki/index.php/Tut:Extending_snmpd_using_shell_scripts](http://www.net-snmp.org/wiki/index.php/Tut:Extending_snmpd_using_shell_scripts) was top.

3: 
I would use the snmp utilities **snmpget** and **snmpwalk** from the snmp package. The above howto shows some basic usage.
Use wireshark to capture and decode the packets - that's an education in itself.

4:
The **agent** is the daemon (service) that runs on the managed device (server, router, coffee-machine etc) that responds to requests from the **manager**. 
It may also occasionally send traps (alerts) to the manager, e.g. "Coffee powder level getting low".

I would think that **client** means the manager program, the one that queries the agent to get status information, such as sending "GET ifOperStatus.1" to get the status of interface 1 ([http://www.alvestrand.no/objectid/1.3.6.1.2.1.2.2.1.8.html](http://www.alvestrand.no/objectid/1.3.6.1.2.1.2.2.1.8.html)).
The word client suggests a handraulically operated program by a user to me, rather than an autonomous management program that periodically checks the status of things (and sends emails and raises fault tickets if it finds things that are not right). 
A number of automated management programs work by launching the command-line client utilities periodically and parsing their output.

If you use the Ubuntu snmp and snmpd, you will also want to use package **snmp-mibs-downloader** which downloads loads of mib files, allowing use of names (like ifOperStatus rather than 1.3.6.1.2.1.2.2.1.8). These are free to download but not free to redistribute so can't be included in the Ubuntu reporitories. Hence a downloaded utility instead. This package also allows wireshark to decode the well known OIDs into names.

```
sudo apt-get install snmp snmpd snmp-mibs-downloader
``` is a good start.

---

### Post by mrJTparadise on 2015-05-13
Hey Cog,

Thanks for your input and clarification.  

By now I have some experience using SNMP and modifiying an exising configuration/implementation to match my needs.

In my snmpd.conf file I have a *dlmod nameOfMod *statement that adds a module when snmpd starts.  This module is a few small .c/.h files along with the MIB.  In short without having to understand all of the code, the exisitng configuration and implementation is setup so the manager/user can query the agent/server to basically execute scripts for the manger and return the output to the manager.  All I did was compile the previous implementation and change the name of the script to be called to the one on my machine (This is inside an OID_CASE function of a .c file) .

Now if I, for example, am running this command (it's been tailored to protect myself) to experiment usage :

```
snmpwalk -v 2c -c communityName 10.20.30.40 1.3.6.1.4.1.12345.1.1
```

I get errors on the output whereas if I run the script from the agent machine everything is fine.

An example of an error is : ```
/usr/local/xxx/yyy/zzz: line 543: printf: ERROR: invalid number
``` - looks like a bash error?

Without having to put forth too much effort of sharing code, etc, are there any tips or clues on to what this is happening?

---

### Post by The Cog on 2015-05-13
The error seems to be coming from your compiled code. I can think of two reasons this might happen:

The arguments to the script are different when launching it from the snmpd process. Try logging all the arguments to a file so you can check for differences.

The environment finds itself in a different environment when launched by snmpd. Check for file permissions (I forget which user snmpd runs as but ps will tell you). Check for dependencies on environment variables like the path and the working directory. Full path names to all executables and data files might help.

---

### Post by mrJTparadise on 2015-05-13
How do I enable logging?  I use ```
service snmpd start
``` to start the agent.  

I checked 
```
ps aux
snmp     13028  0.1  0.4  50376  3988 ?        S    15:57   0:10 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux mteTrigger mteTriggerConf -p /var/run/snmpd.pid

``` 

and snmpd is running as user snmp.  This seems fine as snmpd is running as user snmp on the working machine.

---

### Post by mrJTparadise on 2015-05-13
I've managed to just invoke snmpd -Lo for logging.

Here is my output when running the associated snmpwalk command from above

Connection from UDP: [10.20.30.40]:52755->[10.20.30.41]:161
Connection from UDP: [10.20.30.40]:52755->[10.20.30.41]:161
Connection from UDP: [10.20.30.40]:52755->[10.20.30.41]:161
Error: read from file descriptor timed out after 122 bytes

---

### Post by mrJTparadise on 2015-05-13
UPDATE: Odd that if I start snmpd simply by typing snmpd at the prompt

```
# service snmpd start
``` 
The above command causes the error output

```
# snmpd 
```
The above command produces expected output with no errors.

Why is this?

---

### Post by The Cog on 2015-05-13
I don't know. But you could try running this command by hand (as root) - it's what the service runs:
```
/usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -g snmp -I -smux mteTrigger mteTriggerConf -p /var/run/snmpd.pid
```
Notice it tells snmpd to change user to snmp (after it opens port 161 which is a privileged port). Does user snmp have the access rights to all the files needed?

---

### Post by mrJTparadise on 2015-05-14
Doing a 

```
chmod o+rwx *.*
```

Fixed the problem, thanks!

Now, what would be the proper way to do it since giving the entire group 'other' permission can be dangerous?

*EDIT : The correct way to do is it to edit /etc/default/snmpd and change the -u and -g arguments to root or whichever user has rights to the files associated with snmp.*

---

