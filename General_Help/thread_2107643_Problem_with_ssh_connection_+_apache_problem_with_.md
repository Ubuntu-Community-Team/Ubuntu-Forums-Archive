---
title: "Problem with ssh connection + apache problem with iptables (maybe)"
date: 2013-01-22
forum: General Help
---

### Post by jasinka on 2013-01-22
Hello,

I have kimsufi from OVH, using ubuntu 10.04

Before have installed - 
Chkrootkit
Rkhunter
denyhosts
service nginx
fail2ban
and iptables.

Now my problem is i can't login via ssh. I made resque mode,so i can connect, but can't delete some of iptables config files, becouse i am not root.
[U][COLOR="Silver"]Maybe i don't know how to do "mount", i need help with it.

About mount i have error - 
root@rescue:~# sudo mount -t ext4 /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy

On Winscp i see all normal files, like on ubuntu, so this is mounted? Just, no /var/www/[/COLOR][/U]

It looks working with "e2fsck /dev/md2".

I can't do apt-get. I have error - 
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

Another problem is, i think apache have problem with ngnix, and all my websites don't working...

So, please help me here if you can.
Who can help me here or via skype/talk/messange i can pay in paypal around 10-15 USD.

Thank you in advance for helping.

---

