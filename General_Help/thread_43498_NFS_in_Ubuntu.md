---
title: "NFS in Ubuntu"
date: 2005-06-22
forum: General Help
---

### Post by iveqy on 2005-06-22
Hi, I’m having a problem with my nfs sever/client.

This command:
root@Arwen:~ # mount 192.168.0.107:/home /mnt/misc/

Gives this error:
’mount: 192.168.0.107:/home failed, reason given by server: Access Denied


My client is: Linux Arwen 2.6.8.1-3-386 #1 Thu Nov 18 11:47:33 UTC
2004 i686 GNU/Linux

With package: Debian/Ubuntu 1.0.6-3 common and kernel server

My server is: Linux TheServer 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC
2005 i686 GNU/Linux

With package: Debian/Ubuntu 1.0.6-3 common and kernel server
Export file:
# /etc/exports: the access control list for filesystems which may be exported
# to NFS clients. See exports(5).
/home 192.168.0.105(rw)

hosts.allow:
# /etc/hosts.allow: list of hosts that are allowed to access the system.
# See the manual pages hosts_access(5), hosts_options(5)
# and /usr/doc/netbase/portmapper.txt.gz
#
# Example: ALL: LOCAL @some_netgroup
# ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you’re going to protect the portmapper use the name ”portmap” for the
# daemon name. Remember that you can only use the keyword ”ALL” and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#
portmap: 192.168.0.105
lockd: 192.168.0.105
rquotad: 192.168.0.105
mountd: 192.168.0.105
statd: 192.168.0.105

hosts.deny:
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
# See the manual pages hosts_access(5), hosts_options(5)
# and /usr/doc/netbase/portmapper.txt.gz
#

# Example: ALL: some.host.name, .some.domain
# ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you’re going to protect the portmapper use the name ”portmap” for the
# daemon name. Remember that you can only use the keyword ”ALL” and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don’t
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL

From the server:
root@TheServer:/etc # rpcinfo -p
program vers proto port
100000 2 tcp 111 portmapper
100000 2 udp 111 portmapper
100003 2 udp 2049 nfs
100003 3 udp 2049 nfs
100003 4 udp 2049 nfs
100003 2 tcp 2049 nfs
100003 3 tcp 2049 nfs
100003 4 tcp 2049 nfs
100021 1 udp 32768 nlockmgr
100021 3 udp 32768 nlockmgr
100021 4 udp 32768 nlockmgr
100021 1 tcp 32768 nlockmgr
100021 3 tcp 32768 nlockmgr
100021 4 tcp 32768 nlockmgr
100005 1 udp 678 mountd
100005 1 tcp 681 mountd
100005 2 udp 678 mountd
100005 2 tcp 681 mountd
100005 3 udp 678 mountd
100005 3 tcp 681 mountd
100024 1 udp 752 status
100024 1 tcp 755 status
root@TheServer:/etc #


From the client:
root@Arwen:~ # rpcinfo -p
program vers proto port
100000 2 tcp 111 portmapper
100000 2 udp 111 portmapper
391002 2 tcp 1004 sgi_fam
100024 1 udp 811 status
100024 1 tcp 814 status
root@Arwen:~ #


hoproot@Arwen:~ # rpcinfo -p
program vers proto port
100000 2 tcp 111 portmapper
100000 2 udp 111 portmapper
391002 2 tcp 1004 sgi_fam
100024 1 udp 811 status
100024 1 tcp 814 status
root@Arwen:~ #


Hope someone, please, can help me...

Regards
iveqy

---

### Post by nocturn on 2005-06-22
I have NFS working on my machines.
Check out this howto: [https://wiki.ubuntu.com/SettingUpNFSHowTo](https://wiki.ubuntu.com/SettingUpNFSHowTo)

You could try to open the server to all (just for testing).

---

### Post by Angel on 2005-07-01
[FONT=Times New Roman][SIZE=2][COLOR=blue]Hello
I'm new in the forums and especialy ubuntu. I would like to say hi and i hope you take me as member.

I set up ubuntu and i had lots of hard times to install the updates and to make life easy for me. I wanted to do kickstart in ubuntu and set it up. Testing were made using vmware tools and another script to create vmnet0.
I used kickstart alot in RedHat and i want to try it in ubuntu because not many ppl used it and they are using fai in ubuntu.  ;-) 
Kickstart is one of the automated installation tool made by RedHat. 

Ok, going to the subject, i have created kickstart file ks.cfg, exports(nfs), dhcpd.conf server, and setup the dns /etc/hosts
in the vmware using the cdrom, i write **ks=nfs:server: path_of_ks,cfg ** where i want to install the ubuntu, it works fine until it comes to the nfs configuration part and it says error and it install it like there is no nfs. I tryed to make the /etc/hosts.allow and i wrote this: 
portmap: 148.197.30.0/255.255.255.0 #the ip address of vmnet0 i dont know if it write or wront?!?!?!?

I'm really stuck ](*,)  and i dont know what to do if anyone have any suggestions please i could use some help or ideas. :| 

Thank you
[/COLOR]
[COLOR=DarkRed]Angel[/COLOR][/SIZE][/FONT]

---

