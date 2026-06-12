---
title: "citri x access gateway - net6vpn"
date: 2007-05-23
forum: General Help
---

### Post by raves71 on 2007-05-23
Hi Guys,

 I'm trying to install the net6vpn but am having a few problems, when I run the install I get the following output

 ```
Do you agree to the above license terms? [yes or no]
y

This software requires iptables to be installed.  Is it installed? [yes or no]
y

What is the location of your linux kernel source? [/usr/src/linux]


Determining distribution... detected Linux--unknown.
Unpacking (17754+1110399+23=1128176)...
1110422
Checksumming...
0
0
Extracting...
Installing...
install: cannot stat `/tmp/.net6/net6vpnd': No such file or directory
install: cannot stat `/tmp/.net6/net6vpnd..init': No such file or directory
install: cannot stat `/tmp/.net6/net6vpn': No such file or directory
Installing ip_queue kernel module...
gcc: /tmp/.net6/ip_queue.c: No such file or directory
gcc: no input files
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/fs/nls/nls_cp949.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/fs/nls/nls_cp950.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/fs/ocfs2/cluster/ocfs2_nodemanager.ko is not an elf object
WARNING: Module /lib/modules/2.6.20-15-generic/kernel/fs/xfs/xfs.ko is not an elf object
Adding net6vpnd to default runlevel...
Starting daemon
./citrixvpn-linux-2.4-i386.sh: 416: /etc/init.d/net6vpnd: not found
Cleaning up...
Done.

```

 Anyone done this before of have any idea what's going on?

 I'm not sure when where the kernal is in ubuntu, I've tried a few guesses with no joy.

 Many thanks in advance!

---

### Post by Metacarpal on 2007-05-23
Which version of Ubuntu are you using?  If it's available in your repos, try installing vpnc.  Works wonders.  If you're running Feisty, install network-manager-vpnc as well, which is a handy plugin letting you manage your vpn connections through the NM applet in your top panel.

---

### Post by raves71 on 2007-11-29
just an update, no disrespect to Ubuntu,  I found it to be really good but the one thing I couldnt make it do was run the VPN client and unfotunatley that was a deal breaker

 I've tried vista and fedora since... Vista, I had to remove becaus eI just couldnt take it but Fedora 8 has put a tick in every box and the Citrix VPN client works!

 I am however running ubuntu 7.10 on my home PC :)

---

### Post by izaq on 2007-12-10
I have no problem to install Citrix in Ubuntu 7.10 ; but it dosen't work !

this what i do to install net6vpn

sudo ./citrixvpn-linux-2.4-i386.sh

than evry thing is fine 

i run "net6vpnd" than "net6vpn" to login net6vpn --login

username :

password:

but citrix is not working when I enter to website 


can some body help me

---

