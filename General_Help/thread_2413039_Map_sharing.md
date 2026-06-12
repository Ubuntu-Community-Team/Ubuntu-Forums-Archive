---
title: "Map sharing"
date: 2019-02-20
forum: General Help
---

### Post by pacanda on 2019-02-20
I have a problem with sharing maps in my homenetwork, with 3 pc’s, all running under  Ubuntu OS’s, but first some info:
 PC-A runs Ubuntu 18.04.2 LTS
 PC-B runs Ubuntu 16.04 LTS
 PC-C runs Xbuntu 18.04.2 LTS
 Filesystem is of type ext4 on all Pc’s
 Pinging from each of these pc’s to eachother give positive results with no errors; so they see eachother over my home network, where PC-A has a  lan cable connection to my router and PC-B and PC-C are connected via wife.
 All three Pc’s also have full access to the internet, are logged in under the same username and password.
 Samba is installed on all three Pc’s and the same samba-users and passwords are added.
 All Pc’s are identified in their respective hosts files with their static ip-adresses.
 Searching my homenetwork shows Pc-A and Pc-C, but not Pc-B
 
 Now here is my problem
 Pc-A has full acces to shared maps on Pc-C, but neither Pc-B, nor Pc-C can access Pc-A
 - Trying to get access to Pc-a results in a repetitive ask for the password; no access is granted
 - Trying to make shared maps/files on Pc-A gives the following error message:
 'net usershare' error 255: net usershare add: cannot convert name "Everyone" to a SID. {Access Denied} A process has requested access to an object but has not been granted those access rights..
 
 I’m quite familiar with Ubuntu, I know how to use the CLI as well as the GUI to access and edit systemfiles using sudo to give me root rights. But sofar I have not been able to solve this problem.
 But hopefully, there is some magician in our community who finds the ‘magic words’ and is able show me the relevant cli codes.

---

### Post by TheFu on 2019-02-20
For linux/Unix to Unix network file sharing on a secure LAN, using NFS is the "native" method.  If you use NFS, then all the native file permissions on local and remote storage are honored and work the same, as expected.  NFS is faster too, BTW.  NFS is really easy provided that a few assumptions are true.  The "How To" for setting up NFS covers lots and lots of situations that don't generally matter.

Plus, NFS is server-to-server, not user-to-server.

It isn't clear when you say they can ping each other.  Can they ping by name because you've setup DNS or hosts tables or are you using avahi hope-n-pray methods?

I cannot help with Samba, though I use it as a convenience for 1 Win7 box.

---

### Post by Morbius1 on 2019-02-20
> Searching my homenetwork shows Pc-A and Pc-C, but not Pc-B
Ubuntu automatically registeres its samba server to the rest of the network using mDNS ( Avahi ) in Ubuntu 18.xx. In Ubuntu 16 you need to force it. So on the Ubuntu 16 machine:

Create a file at: [B]/etc/avahi/services/samba.service
[/B]
And add this to it:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
It should be automatic at this point but just in case restart avahi:
```
sudo service avahi-daemon restart
```
> 'net usershare' error 255: net usershare add: cannot convert name  "Everyone" to a SID. {Access Denied} A process has requested access to  an object but has not been granted those access rights.
That's a new one to me - at least all in one error message. More information is required.

Posing the output of the following commands from PC-A would be helpful:
```
testparm -s
```
```
net usershare info --long
```
```
ls -al /var/lib/samba/usershares
```

---

### Post by pacanda on 2019-02-21
hi MORBIUS1,
thanks for your reply;
 these are the results of your code suggestions witch i ran on Pc-A; BASIS is the Pc-A's name.
I also made the advised samba service file on Pc-A. Searching my network now shows BASIS, but opening BASIS shows an empty map.

net usershare info --long gave no output at all

```
george@BASIS:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    usershare allow guests = Yes
    wins support = Yes
    idmap config * : backend = tdb
    comment = home directory george
    create mask = 0775
    directory mask = 0775
    path = /home/george/
    printable = Yes
    read only = No
    valid users = george
george@BASIS:~$ 

george@BASIS:~$ ls -al /var/lib/samba/usershares
totaal 8
drwxrwx--T 2 root sambashare 4096 feb 19 18:37 .
drwxr-xr-x 5 root root       4096 feb 21 10:33 ..
george@BASIS:~$ 
```

I will follow your instructions this afternoon also on the 16.04 Pc and let you now the results.
Hope you can further advise me. For now many thanks.

---

### Post by Morbius1 on 2019-02-21
> I also made the advised samba service file on Pc-A. Searching my network now shows BASIS, but opening BASIS shows an empty map.
At least avahi is working. 

Me thinks the reason you see no shares under BASIS is because Samba thinks you have no shares defined. There is a share definition in smb.conf but it's not correctly segmented from the [global] section. 

You are missing a [section] marker letting samba know that what follows is a share definition. If I copy a section of the testparm output it should look something like this:

> wins support = Yes
idmap config * : backend = tdb
[COLOR=#0000cd]**[george]**[/COLOR]
comment = home directory george
create mask = 0775
directory mask = 0775
path = /home/george/
printable = Yes
read only = No
valid users = george

[COLOR=#0000cd]**Note**: testparm is an interpreter of smb.conf. When you go into smb.conf itself it will not look exactly like what testparm shows but what's important here is that **[george]** needs to be placed above the start of your share definition.


[/COLOR]Make the insertion in smb.conf, save the file, then restart smbd:
```
sudo service smbd restart
```

---

### Post by pacanda on 2019-02-22
Hi Morbius1,
Following your suggestions also for the 16.04 Pc, a networksearch now shows FAMHP SMB , where FAMHP is the name of the 16.04 Pc. However, trying to 'open' FAMHP results in a message that the requested connection is refused and the list of shared maps cannot be delivered.
The funny thing is that from both BASIS and FAMHP the third Pc-C (named JFHTOSXP, running under Xbuntu 18.04.2 LTS) is fully accessible, which is a good and expected result.
However, the other way around, connecting to PC-A (BASIS) from any other Pc in my network, shows  an empty map on smb://basis.local/

The other remaining problem is that trying to share maps or files on BASIS still results in the afore mentioned error message:
'net usershare' error 255: net usershare add: cannot convert name "Everyone" to a SID. {Access Denied} A process has requested access to an object but has not been granted those access rights..

The net usershare info --long command gives no output, so I looked into the usershares directory which gives the following results:

george@BASIS:/var/lib/samba/usershares$ ls -al
totaal 8
drwxrwx--T 2 root sambashare 4096 feb 19 18:37 .
drwxr-xr-x 5 root root       4096 feb 22 09:33 ..
george@BASIS:/var/lib/samba/usershares$

Whereas invoking the  net usershare info --long command on the 16.04 Pc shows a list with all shared maps and files on that Pc.

So what to do now?
Kind regards from George, a 72-year dutch guy who really wants to tackle this strange behavior!

---

### Post by Morbius1 on 2019-02-22
> The other remaining problem is that trying to share maps or files on BASIS still results in the afore mentioned error message:
'net usershare' error 255: net usershare add: cannot convert name  "Everyone" to a SID. {Access Denied} A process has requested access to  an object but has not been granted those access rights..
That problem will go away when you add [george] to your /etc/samba/smb.conf file. Both access to the share and your inability to use usershare are related..

Why not post the entire contents of the file:
```
cat /etc/samba/smb.conf
```

---

### Post by pacanda on 2019-02-22
well, following your suggestion to add [george] to my smb.conf file finaly solved the problem completely, hurrah!!!
For what its worth: this is the outcome of running testparm: if you would have any comments on that, its really appreciated.
Anyway, I'm very, very greatfull for your help and especiasily for your persistence to keep helping. Thank you very much again,
George

# Global parameters
[global]
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    usershare allow guests = Yes
    wins support = Yes
    idmap config * : backend = tdb


[homes]
    comment = Printer Drivers
    create mask = 0775
    directory mask = 0775
    path = /var/lib/samba/printers
    printable = Yes
    valid users = george


[home]
    comment = home directory george
    path = /home/george
    read only = No
    valid users = george


[george]
    comment = home directory george
    create mask = 0775
    directory mask = 0775
    path = /home/george
    read only = No
    valid users = george

---

