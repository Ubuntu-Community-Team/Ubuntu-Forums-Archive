---
title: "install UPS gamatronic smart compact 650 on ubuntu hardy"
date: 2008-05-28
forum: General Help
---

### Post by greyangel on 2008-05-28
hi,
i have a problem installing gamatronic ups in serial port.

i type:
sudo /etc/init.d/nut start
and i get (in console):

Broadcast Message from nut@ubuntu-desktop  (somewhere) at 0:06 ...                                                
Communications with UPS ups1@localhost lost                                    
 Broadcast Message from nut@ubuntu-desktop (somewhere) at 0:06 ...                                                                            
UPS ups1@localhost is unavailable

in log it writes:
May 29 00:06:32 ubuntu-desktop upsd[31969]: Invalid CIDR type block: Must be > 0 && < 32


the only driver that gives some normal output in sudo upsdrvctl start is Megatec
the output:
Network UPS Tools - UPS driver controller 2.2.1-
Network UPS Tools 2.2.1- - Megatec protocol driver 1.5.13 [megatec]
Carlos Rodrigues (c) 2003-2007

Megatec protocol UPS detected [GAMATRONIC SC-SERIES VER2.12NS].

my config files:

/etc/nut/upsd.conf
ACL all 127.0.0.1/80
ACL localhost 127.0.0.1/80
ACCEPT localhost

/etc/nut/upsd.users
[TheUser]
password = ThePassword
allowfrom = localhost
upsmon master

/etc/nut/upsmon.conf
MONITOR ups1@localhost 1 TheUser ThePassword master
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h now"
# NOTIFYCMD /usr/local/ups/bin/notifyme
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
# NOTIFYMSG ONLINE "UPS %s is getting line power"
# NOTIFYMSG ONBATT "Someone pulled the plug on %s"
# NOTIFYFLAG ONLINE SYSLOG
# NOTIFYFLAG ONBATT SYSLOG+WALL+EXEC
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 0

/etc/nut/ups.conf
driver=megatec
port=/dev/ttyS1

thanks,
paul

---

### Post by tk471 on 2008-06-02
> /etc/nut/upsd.conf
ACL all 127.0.0.1/80
ACL localhost 127.0.0.1/80
ACCEPT localhost

It must be your netmask value.  '80' should be '32'.

/etc/nut/upsd.conf
ACL all 127.0.0.1/32
ACL localhost 127.0.0.1/32
ACCEPT localhost

See if that fixes it.

---

### Post by greyangel on 2008-06-02
thanks for reply :)
eventually i read the manual of nut and solved it. the problem  was the bad name of ups in different config files.
here is my current working configuration:
/etc/nut/ups.conf
[[COLOR="Purple"]ups[/COLOR]]
driver=megatec
port=/dev/ttyS1

/etc/nut/upsd.conf
ACL all 0.0.0.0/0
ACL [COLOR="Red"]localhost[/COLOR] 127.0.0.1/0
ACCEPT [COLOR="Red"]localhost[/COLOR]
REJECT all

/etc/nut/upsd.users
[[COLOR="SeaGreen"]my_user_name[/COLOR]]
password = [COLOR="Orange"]my_password[/COLOR]
allowfrom = [COLOR="Red"]localhost[/COLOR]
upsmon master

/etc/nut/upsmon.conf
MONITOR [COLOR="Purple"]ups[/COLOR]@[COLOR="Red"]localhost[/COLOR]:3493 1 [COLOR="SeaGreen"]my_user_name[/COLOR] [COLOR="Orange"]my_password[/COLOR] master
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h now"
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
on %s"
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 0

the number of port (3493) i discovered
after the server started and said "listening to port 3493"

one more thing.. the nut scripts didn't really work to me (and to some other people as i saw in forums):
so i  changed it a bit (not most secure, but working):
starting_ups script:
sudo chmod -R 777 /var/run/nut/
sudo upsdrvctl -u root start
sudo chmod -R 777 /var/run/nut/
sudo start-stop-daemon -S -q -p /var/run/nut/upsd.pid -x /sbin/upsd
sudo start-stop-daemon -S -q -p /var/run/nut/upsmon.pid -x /sbin/upsmon

stopping_ups script:
sudo start-stop-daemon -K -o -q -p /var/run/nut/upsmon.pid -n upsmon
sudo start-stop-daemon -K -o -q -p /var/run/nut/upsd.pid -n upsd
sudo upsdrvctl stop

i put the starting script in System->Preferences->Sessions->startup-programs
and stopping script added to
/etc/gdm/PostSession/Default

and now it works just fine:)
hope this post will help to all who has the the same problem.

---

### Post by tk471 on 2008-06-02
I would recommend changing your permissions back for '/var/run/nut'.  I had found I had no problems after adding user 'nut' to group 'nut' and 'dialout':

$ sudo adduser nut nut
Adding user `nut' to group `nut' ...
Adding user nut to group nut
Done.
$ sudo adduser nut dialout
Adding user `nut' to group `dialout' ...
Adding user nut to group dialout
Done.

Notice the user/groups for /var/run/nut:

$ sudo ls -la /var/run/nut
total 12
drwxrwx---  2 nut  nut     120 2008-06-02 00:38 .
drwxr-xr-x 19 root root    780 2008-06-02 07:57 ..
srw-rw----  1 nut  dialout   0 2008-06-02 00:38 tripplite_usb-ups1
-rw-r--r--  1 nut  dialout   5 2008-06-02 00:38 tripplite_usb-ups1.pid
-rw-r--r--  1 nut  dialout   5 2008-06-02 00:38 upsd.pid
-rw-r--r--  1 root root      5 2008-06-02 00:38 upsmon.pid

Of course, you'll see some slightly different items (since different UPS), but it should be more secure this way.  Just a thought.

---

