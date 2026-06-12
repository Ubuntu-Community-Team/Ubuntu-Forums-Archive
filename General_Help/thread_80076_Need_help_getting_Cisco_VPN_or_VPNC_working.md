---
title: "Need help getting Cisco VPN or VPNC working"
date: 2005-10-21
forum: General Help
---

### Post by aclonedsheep on 2005-10-21
Hi,

I have essentially exhausted every resource before posting.  I have seen a few other threads on similiar topics; where university students try to get their cisco clinet working and have trouble, but my problems are slightly different.

The installation completes and tells me to run the script to initialize it.

I get this error:
```
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Unknown symbol in module
Failed (insmod)

```

When I go back and look at the installation I see the following warnings:

```
make -C /usr/src/linux-headers-2.6.12-9-386/ SUBDIRS=/home/ben/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/ben/Desktop/vpnclient/.libdriver.so.cmd for /home/ben/Desktop/vpnclient/libdriver.so
*** Warning: "CNI_DNEListBindings" [/home/ben/Desktop/vpnclient/cisco_ipsec.ko] undefined!
*** Warning: "CniGetBindingByIndex" [/home/ben/Desktop/vpnclient/cisco_ipsec.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
Copying module to directory "/lib/modules/2.6.12-9-386/CiscoVPN".
Already have group 'bin'

```

I also installed vpnc hoping the open-source software would work but have not been able to connect...

So I can take either approach...get the cisco client working or properly configure vpnc (I have my pcf file and also data from the network admin)
From his email:
> 1.      Policy: Cisco VPN Concentrator 3000
2.      Gateway Address: [server]
3.      Use Perfect Forward Secrecy: checked
4.      Group Name: [use your imagination]
5.      Group Password: [obviously censored]
6.      Username: zoo account
7.      IKE Crypto Suite:
  a.      Group: GRP2_DH-1024
  b.      Cipher: 3DES_CBC
  c.      Hash: MD5
8.      IPSec Suite: ESPIP_3DES_MD5-96
9.      Query DNS/WINS: checked

pcf file:

```
[main]
Description=Secure connection to internet
Host=[censored]
AuthType=1
GroupName=[censored]
GroupPwd=
enc_GroupPwd=[censored]
EnableISPConnect=0
ISPConnectType=1
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
DHGroup=2
ForceKeepAlives=0
PeerTimeout=90
EnableLocalLAN=0
VerifyCertDN=

```

If anyone could help me with either method so I can get connected to the wireless network...I would greatly appreciate it!  If you want to help me with both, for the sake of learning, that would be cool too ;) 

Ben

---

### Post by shenki on 2005-10-21
Hello,

after struggling to get the cisco vpn client working under hoary for a few weeks, I found vpnc a saviour - both easy to configure, and easier to run.

I assume you have already 'sudo apt-get install vpnc resolvconf'

Now you want to create a file, with <name of connection profile> being something easy to remember, and short to type out

```
/etc/vpnc/<name of connection profile>.pcf
```

then, enter the following details into that file

```

IPSec gateway <ip of server>
IPSec ID <group name>
IPSec secret <group password>
Xauth username <username>
```

save the file, and then after ensuring you have enabled your wireless connection and have an IP, at a prompt type

```
sudo vpnc-connect <name of connection profile>
```

It will then prompt for your user password, enter that in, and you should be good to go.

---

### Post by hajk on 2005-10-21
....vpnc-connect?

Where, pray, might one find such a file in Breezy?

Unfortunately, /usr/sbin/vpnc-connect is missing from the Breezy vpnc package.
You might try the command "sudo vpnc" in a terminal, you will then be asked for the 
four lines of information in the previous post, in addition to being asked for the password.

BTW, I've only been able to make the connection with no proxy server for my web browser,
and with the firewall (Firestarter) stopped. This last bit must mean that I've got to open
another port for incoming traffic, since I don't restrict outgoing traffic.

---

### Post by PaulBillett on 2005-10-21
[QUOTE=hajk]....vpnc-connect?

Where, pray, might one find such a file in Breezy?[/QUOTE]

I also had a problem when this command didn't work... so I tried using just "sudo vpnc configfilename" and bingo... 

vpnc-connect must be from an older version.

---

### Post by hajk on 2005-10-21
Allright, for those of you with Firestarter running, this is how you configure vpnc in Breezy (with thanks to the IT folks at Clemson...):

1. Make the <target>.conf file with the four lines as shown by the 
    previous poster, where <target> is the name you give the vpn connection.

2. Edit /etc/firestarter/user-pre after first enabling this file to writable:

    sudo chmod 600 /etc/firestarter/user-pre
    sudo vi /etc/firestarter/user-pre    (... or use sudo gedit)

    Enter the following 6 lines:

    iptables -A INPUT -j ACCEPT -s <vpn gateway> -p esp
    iptables -A INPUT -j ACCEPT -s <vpn-gateway> -p udp -m multiport --sports isakmp,10000
    iptables -A INPUT -j ACCEPT -i tun+
    iptables -A OUTPUT -j ACCEPT -d <vpn-gateway> -p esp
    iptables -A OUTPUT -j ACCEPT -d <vpn-gateway> -p udp -m multiport --dports isakmp,10000
    iptables -A OUTPUT -j ACCEPT -o tun+
 
    where <vpn-gateway> should be replaced with the address in the first
    entry of the above .conf file. Save this file (for the paranoid: chmod 400)
    and

3. sudo /etc/init.d/firestarter restart

4. sudo vpnc <target>.conf   (...as stated by the previous poster)

5. Enjoy your connection

6. sudo vpnc-disconnect

    This command is available in Breezy to shut it down.
 
It works for me.:D

---

### Post by aclonedsheep on 2005-10-25
I get this error:

```
vpnc: binding to port 500: Permission denied

```

I didnt make my own config file but just entered in the info manually after running vpnc

I have the cisco config file pasted in the original post plus the information the IT people gave me here...theres a lot more fields than vpnc is asking me for...is that why I can't connect?  How can I do this?

Thanks

Ben

---

### Post by hajk on 2005-10-25
Yes, VPNC only asks those items: gateway address, group ID, group secret,
user ID and user password. Entering them in a file saves typing, make sure that you leave only a single space between words in <name>.conf

IPSec gateway <address>
IPSec ID <groupID>
IPSec secret <groupSecret>
XAuth username <user ID>
XAuth password <user password>

the first three items you get from the IT department.

Make sure that you run VPNC with root priveleges,

sudo vpnc <name>.conf.

If you run the Firestarter firewall, then add the pre-rules of my previous post.

You don't need the "resolvconf" package to use VPNC, since VPNC will also
temporarily change /etc/resolv.conf to reflect the new nameservers of the connection; afterwards the original /etc/resolv.conf will be restored, you don't need "resolvconf" for that. In fact, I removed "resolvconf" completely (in Synaptic), because it causes you to lose /etc/resolv.conf after a reboot.
I had to manually remove the symlink /etc/resolv.conf --> and then restore it by rewriting it with sudo gedit (you could also use System/Administration/Networking).

Let us know if this solves things.

---

### Post by aclonedsheep on 2005-10-26
Thanks to everyone who helped with this...vpnc is connecting fine, I just wasn't running it with sudo hence the permission denied error :)

Never could get the cisco client running but obviously I don't need to since this works perfect.

Thanks again

---

### Post by charles.regan on 2005-11-30
vpnc: binding to port 500: Address already in use

How can I fix this ? I running as sudo.

---

### Post by eoinmadden on 2006-06-07
[QUOTE=charles.regan]vpnc: binding to port 500: Address already in use

How can I fix this ? I running as sudo.[/QUOTE]
 I get around this by typing:

sudo vpnc --local-port 501

But this is a "work-around", not a "fix".

---

### Post by foxy123 on 2006-07-21
thanks a lot guys for this thread. I managed to connect to my home network via vpnc, but I can only see my own laptop there. On Windows I have "Allow local LAN Access" ticked in Cisco VPN Client. How to do it with vpnc?

---

### Post by drjan on 2006-11-04
sudo vpnc --local-port 501

But this is a "work-around", not a "fix".[/QUOTE]

I had the same problem on Debian Etch:

I you follow the documentation of kvpnc you are temptated to install
racoon

If you like to use vpnc only against a CISCO big mistake.
racoon starts as a daemon and listens on port 500 ....

# ps -ef | grep racoon
# kill PID-of-racoon

and vpnc works as it should .... :)

---

