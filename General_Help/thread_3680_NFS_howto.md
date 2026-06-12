---
title: "NFS howto?"
date: 2004-11-08
forum: General Help
---

### Post by TravisNewman on 2004-11-08
I tried this one: [http://www.ibiblio.org/mdw/HOWTO/NFS-HOWTO/](http://www.ibiblio.org/mdw/HOWTO/NFS-HOWTO/)
But whenever I try to mount the drives it says connection refused. I know I'm using the right IP addresses. In our apartment there are 3 ubuntu machines, mine is the only one on Hoary, the others are Warty 386 and Warty ppc. No windows machines or apple machines, so no need for samba/appletalk. Is there any straightforward howto on how to get NFS to work? Thanks :)

---

### Post by az on 2004-11-08
There is a faq about this:
[http://www.ubuntulinux.org/support/documentation/faq/nfs-server](http://www.ubuntulinux.org/support/documentation/faq/nfs-server)

---

### Post by TravisNewman on 2004-11-08
[QUOTE=azz]There is a faq about this:
[http://www.ubuntulinux.org/support/documentation/faq/nfs-server](http://www.ubuntulinux.org/support/documentation/faq/nfs-server)[/QUOTE]
 EXACTLY what I needed. Thanks a lot :)

---

### Post by trash on 2005-02-09
Hey panickedthumb, what was it that you did to get it working??

I've done all of the variations, crashed a few times, tried in /mnt and home directory with varying degrees of success but nothing stable or automatic(mount at boot)... what do your working files look like?

thanks

---

### Post by TravisNewman on 2005-02-09
Well, I basically did exactly what the link provided said.
My fstab entry looks like:
192.168.1.102:/share    /univac         nfs     rw              0       0
192.168.1.102 is the ip of the server
/univac is the shared folder.

---

### Post by trash on 2005-02-09
hmmmm...

my fstab
/192.168.0.20:/home/kenji/g3stuff /home/kenji/g4space nfs rw 0 0

I am now getting permission denied...

hosts:
portmap: 192.168.0.1

exports:
/home/kenji/g3stuff 192.168.0.1(rw,async)

kinda looks like it should work but it don't:(

---

### Post by trash on 2005-02-10
anybody got any ideas?
mount: 192.168.0.20:home/kenji/g3stuff failed, reason given by server: Permission denied

I can ping both machines(server and client)
booting the client machine, there is a message in boot saying can't get address for 192.168.0.20 (server), but ....

$ rpcinfo -p 192.168.0.20 (on both machines gives me...)
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32771  nlockmgr
    100021    3   udp  32771  nlockmgr
    100021    4   udp  32771  nlockmgr
    100021    1   tcp  35899  nlockmgr
    100021    3   tcp  35899  nlockmgr
    100021    4   tcp  35899  nlockmgr
    100005    1   udp    825  mountd
    100005    1   tcp    828  mountd
    100005    2   udp    825  mountd
    100005    2   tcp    828  mountd
    100005    3   udp    825  mountd
    100005    3   tcp    828  mountd

I have thought firewall but i use firestarter on my client machine and as far as I understand it leaves the internal network alone aside for masq... just incase though I have the client as a trusted IP, but still no luck.

---

### Post by trash on 2005-02-19
finally with a little bit of tweaking i am able to mount the share but now as soon as i try to open a file, it freezes up to the point where i no longer can even access my home directory on the client machine. can anybody tell me what i'm missing here, it all looks so simple in all the howto's, but i still see a lot of people with troubles regarding nfs.. thanks for any help:)

---

### Post by trash on 2005-02-21
ok finally figured out the silly problem, after trying many howto's and fixes on this forum, it turned out to be a 'fix' that didn't work that i forgot to undo ](*,) 

the 'fix' that didn't, was in the fstab which read:
/192.168.0.20:......
and i also tried another fix that didn't, which read:
//192.168.0.20:......

what does work perfectly(for me) is:
192.168.0.20:/home/g3 /mnt/g4space nfs rw,hard,intr 0 0

*EDIT*

AUGH! after copying a couple of files to the mounted file everything froze up again!!
on shutdown i get NFS and RCP errors 101...
on boot i get 'warning NFS mount version older than kernel'... so forget the 'fix' :(

---

