---
title: "Add a permanent route at startup"
date: 2014-08-23
forum: General Help
---

### Post by James Wilde on 2014-08-23
I give up!  Thought I knew linux and Unix but it's all evaporated since I retired.

I would like to add the following route command to my Ubuntu box every time it starts up, since the route command does not allow permanent routing.  If there's another command (other than route) which can do this, please let me know.

I have formed a script with the following line:

route add -net 192.168.1.192 netmask 255.255.255.224 gw 192.168.1.2

The reason is I have a number of machines behind a repeater (IP 192.168.1.2) and if I don't have this route in the routing table, boxes in front of the repeater can't find the ones behind.

Now, I've placed this script in various places, and tested all manner of ways of running it but to no avail.  The file is owned by me (just changed this back to root for one more test), with mod 4775 and in my /etc/sudoers file I've added the line:

ALL ALL=NOPASSWD:/home/james/routes

And wherever I run it from, it won't run unless I run it myself in a terminal window.  I can't get it to run automatically.  I've had the line in /etc/rc.local, in .xinitrc (where I have another simple command to load an Xmodmap file).

Please help so I don't have to run it manually.

TIA

---

### Post by varunendra on 2014-08-25
If you are running it from /etc/rc.local, you shouldn't need to add the "ALL ALL=NOPASSWD..." line in /etc/sudoers file, since the rc.local file itself runs the commands/scripts with root privileges.

Assuming it runs the script even before the network gets ready, thus causing it to not work, how about adding some timeout to the script? E.g. -
```
sleep 20
/sbin/route add -net 192.168.1.192 netmask 255.255.255.224 gw 192.168.1.2
```
..then to let rc.local move forward without waiting for its timeout, change the line in it to -
```
/home/james/routes **[COLOR="#FF0000"]&[/COLOR]**
```
..to send it to background processes while the rc.local script moves on to other tasks/finish point.

I think a better place where the main script can/should be put so that it executes exactly when the interface goes 'up', is **/etc/network/ifup.d**. But I have experimented with the /etc/network/*.d directories only once, and don't remember whether I needed something extra than just putting the scripts there.

---

### Post by SeijiSensei on 2014-08-26
Is the network started at boot, or does it only start after you have logged in?  Ubuntu generally takes the latter approach so the network isn't available when /etc/rc.local is run.  If you [configure the network statically]("https://help.ubuntu.com/14.04/serverguide/network-configuration.html#static-ip-addressing") in /etc/network/interfaces, then it will be up when /etc/rc.local runs so you can add the route there.

---

### Post by btindie on 2014-08-26
Is that on a desktop or server?

If it's a desktop then you can just edit the connection properties and under the 'IPv4 Settings' tab click on 'Routes' and add it in there.

If it's a server and you have the connection defined in /etc/network/interfaces then you can just add the below to the iface section
```

up ip route add 192.168.1.192/27 via 192.168.1.2 dev eth0 proto static
down ip route add 192.168.1.192/27 via 192.168.1.2 dev eth0 proto static

```

---

