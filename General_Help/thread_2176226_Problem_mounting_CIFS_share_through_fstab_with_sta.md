---
title: "Problem mounting CIFS share through fstab with static IP, works great with DHCP."
date: 2013-09-23
forum: General Help
---

### Post by Philippe_Lang on 2013-09-23
Hi,

I have a very strange problem here, with Ubuntu 12.04.3. This VM was installed in order to reproduce a bug we have on our productive servers after migrating them to a recent Ubuntu version.

The setup on these machines is the following: apache has config files and root directories which are stored on a distance CIFS share. This CIFS share is mounted on the server through fstab, like this:

```
//10.2.0.254/srv    /srv/    cifs    sec=ntlmv2,_netdev,nobrl,user=smb_data,credentials=/etc/samba/credential,uid=www-data,gid=www-data 0 0
```

When configuring the server with DHCP, everything is fine. The machines boots, and apache is started automatically. This works, but boot.log file is not 100% clean, as you can see:

```
root@test:~# more /var/log/boot.log 
fsck from util-linux 2.20.1
/dev/sda1: clean, 82695/491520 files, 433746/1965824 blocks
 * Starting Userspace bootsplash                                                             [ OK ]
 * Starting Send an event to indicate plymouth is up                                         [ OK ]
 * Stopping Userspace bootsplash                                                             [ OK ]
 * Stopping Send an event to indicate plymouth is up                                         [ OK ]
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /srv [378] terminated with status 32
 * Starting Uncomplicated firewall                                                           [ OK ]
 * Starting configure network device security                                                [ OK ]
 * Starting configure network device security                                                [ OK ]
 * Starting Mount network filesystems                                                        [ OK ]
 * Starting Failsafe Boot Delay                                                              [ OK ]
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /srv [543] terminated with status 32
 * Stopping Mount network filesystems                                                        [ OK ]
 * Starting configure network device                                                         [ OK ]
 * Starting Bridge socket events into upstart                                                [ OK ]
 * Stopping cold plug devices                                                                [ OK ]
 * Stopping log initial device creation                                                      [ OK ]
 * Starting configure network device security                                                [ OK ]
 * Starting configure virtual network devices                                                [ OK ]
 * Stopping configure virtual network devices                                                [ OK ]
 * Stopping OpenSSH server                                                                   [ OK ]
 * Starting OpenSSH server                                                                   [ OK ]
 * Starting Mount network filesystems                                                        [ OK ]
 * Stopping Mount network filesystems                                                        [ OK ]
 * Stopping Failsafe Boot Delay                                                              [ OK ]
 * Starting System V initialisation compatibility                                            [ OK ]
 * Starting configure network device                                                         [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                                                [ OK ] 
 * Stopping System V initialisation compatibility                                            [ OK ]
 * Starting System V runlevel compatibility                                                  [ OK ]
 * Starting automatic crash report generation                                                [ OK ]
 * Starting CPU interrupts balancing daemon                                                  [ OK ]
 * Starting ACPI daemon                                                                      [ OK ]
 * Starting save kernel messages                                                             [ OK ]
 * Starting regular background program processing daemon                                     [ OK ]
 * Starting deferred execution scheduler                                                     [ OK ]
 * Starting crash report submission daemon                                                   [ OK ]
 * Stopping Mount filesystems on boot                                                        [ OK ]
 * Stopping save kernel messages                                                             [ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 * Starting web server apache2                                                               [ OK ] 
 * Stopping System V runlevel compatibility                                                  [ OK ]

```

The machine is apparently trying twice to mount the CIFS share when the network is not ready:

```
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /srv [543] terminated with status 32

```

Maybe that's normal, I don't know. At least it works.

Now of course, our servers are not configured with DHCP. They have static IPs. And if I configure the machine that way, apache does not start anymore. Here the new boot.log file.

```
root@test:/var/log# more boot.log 
fsck from util-linux 2.20.1
/dev/sda1: clean, 82696/491520 files, 433768/1965824 blocks
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /srv [391] terminated with status 32
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                                                [ OK ] 
apache2: Syntax error on line 239 of /etc/apache2/apache2.conf: Could not open configuration file /srv/collab-config/test-stack/: No such file or directory
Action 'start' failed.
The Apache error log may have more information.
 * Starting web server apache2                                                               [fail] 

```

What's more, I can read on the console:

```
mountall: Disconnected from Plymouth
```

I have tested two different machines, with and without LVM, just in case it could have had an effect, since we have added LVM when doing the migrations from our old VMs. But it has absolutely no effect.

But that's not finished! With both DHCP and a static IP, the mount is up and running when I log into the machine:

```
root@test:/var/log# df -T
Filesystem       Type     1K-blocks     Used Available Use% Mounted on
/dev/sda1        ext4       7739864  1611720   5734980  22% /
udev             devtmpfs    242192        4    242188   1% /dev
tmpfs            tmpfs       100616      244    100372   1% /run
none             tmpfs         5120        0      5120   0% /run/lock
none             tmpfs       251536        0    251536   0% /run/shm
//10.2.0.254/srv cifs     103211296 95841256   2127212  98% /srv

```

With a static IP, I simply have to /etc/init.d/apache2 start, and everything works.

Any idea what is happening here?

---

### Post by Philippe_Lang on 2013-09-24
Hi again everyone. Just a quick reply to say that this strange bug was caused by our virtualization infrastructure, Proxmox 2.3. I have made some tests with the latest version of Proxmox (3.1), and the bug has disappeared completely.

---

