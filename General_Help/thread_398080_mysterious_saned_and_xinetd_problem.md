---
title: "mysterious saned and xinetd problem"
date: 2007-03-31
forum: General Help
---

### Post by sbleono on 2007-03-31
I have the scanner part of my Brother DCP-1000 multifunction working in Ubuntu 6.10. It works fine as sane device "brother:bus1;dev1". However, I can't scan over the network if I'm running saned via xinetd. The error I always get is:

$ scanimage -d "net:violet:brother:bus1;dev1" -T
[sanei_debug] Setting debug level of net to 255.
[net] sane_init: authorize = 0x1c3c, version_code = 0xbffff0dc
[net] sane_init: SANE net backend version 1.0.13 (AF-indep+IPv6) from sane-backends 1.0.18-cvs
[net] sane_init: Client has little endian byte order
[net] sane_init: searching for config file
[net] sane_init: trying to add violet
[net] add_device: adding backend violet
[net] add_device: backend violet added
[net] sane_init: done reading config
[net] sane_init: evaluating environment variable SANE_NET_HOSTS
[net] sane_init: done
[net] sane_open("violet:brother:bus1;dev1")
[net] sane_open: host = violet, device = brother:bus1;dev1
[net] sane_open: device found in list
[net] sane_open: device not connected yet...
[net] connect_dev: trying to connect to violet
[net] connect_dev: [0] connection succeeded (IPv4)
[net] connect_dev: sanei_w_init
[net] connect_dev: net_init (user=leon, local version=1.0.3)
[net] connect_dev: freeing init reply (status=Success, remote version=1.0.3)
[net] connect_dev: done
[net] sane_open: net_open
[net] sane_open: remote open failed
scanimage: open of device net:violet:brother:bus1;dev1 failed: Error during device I/O


This happens both locally and remotely. xinetd is definitely firing saned up, though, because "scanimage -L" from a client machine reports:

device `brother:bus1;dev1' is a Brother DCP-1000 USB scanner
device `net:localhost:brother:bus1;dev1' is a Brother DCP-1000 USB scanner

The strange part (to me) is that if I run "sudo -u saned saned -d", I *can* connect and scan over the net backend, both from the server and from a client. It's hard to tell what's going wrong with the xinetd setup because you can't get debug info out of saned in that mode, AFAIK.

Here's my xinetd.d/sane-port file:

service sane-port
{
socket_type = stream
server = /usr/sbin/saned
protocol = tcp
user = saned
group = saned
wait = no
disable = no
flags = IPV6
}

I've tried without the "flags" line as well, so I'm pretty sure it's not an IPV4 vs IPV6 issue.

The saned user is part of the scanner group.

Can anyone suggest a method for me to get some debugging info from saned, or point out any other configs I should check?

Thanks!

---

### Post by serj_alligator on 2007-04-03
Hello,
I'm currently doing the same thing as you are and I guess we have printers that are really alike.
I have MFC-3420C and jus made it scan from all users all there's left is configure saned.
Anyways I got the answer! =)
Check this post out I applied it and now users can scan as well! =)
[http://ubuntuforums.org/showpost.php?p=1069843&postcount=4]("http://ubuntuforums.org/showpost.php?p=1069843&postcount=4")
Read it carefully and don't forget to change value for product id! =)

Hope it helps!
./5erJ.:D

---

### Post by sbleono on 2007-04-03
Thanks for replying. I actually had already configured the permissions on my USB device. It's just that I'm having trouble scanning over the network for some reason.

I found a workaround, which is to disable the sane-port service in xinetd (so it's not listening anymore on 6566), and to run the following script:

```

#!/bin/bash
while [ true ]; do
        saned -d
done

```

I haven't created a service script for it yet, but I'll do that shortly.

---

### Post by serj_alligator on 2007-04-03
Yeah... we have the same problems... :/
Your script did actually help! It works now,
I guess I will just wait for you to write a service script... =)
It seems to me that the trouble is because our scanning device are found as "brother:bus1;dev1". But I can't figure out how to make it /dev/usbscanner...
In instructions from brother using mknod it seems like it's possible to accomplish that...
The only thing I can't understand is how because all it does pretty much is making new device but it's not pointed anywhere and after simple reboot it's gone. I might be wrong but it seems like the saned doesn't understand anything except for /dev/*lalala*...
But now the script of yours worked and I'm completely confused because it works as "brother:bus1;dev1".
My best understanding is that xinetd handles something wrong...you got any ideas?
Maybe we should submit script to ubuntu wiki and also write a report to brother... =) perhaps they can fix it in next version than...
If you have any luck or need help I can help =) (used to write service scripts for game servers while back =) )

P.S maybe 'nohup' would help i will try to poke around and write script my self.... too ;)

---

### Post by sbleono on 2007-04-10
Serj, here's my init script. It's rough, but it works, and I didn't have any more time to figure out how to make it work right with the start-stop-daemon command. Add it to your rc.d dirs with "update-rc.d saned multiuser"

```

#!/bin/sh
#
# /etc/init.d/saned  --  script to start and stop saned.

test -x /usr/local/bin/runsaned || exit 0

case "$1" in
    start)
        echo -n "Starting scanner server: saned"
        sudo -u saned /usr/local/bin/runsaned &
        echo "."
        ;;
    stop)
        echo -n "Stopping scanner server: saned"
        killall runsaned
        killall saned
        echo "."
        ;;
    reload)
        ;;
    force-reload)
        ;;
    restart)
        $0 stop
        $0 start
        ;;
    *)
        echo "Usage: /etc/init.d/saned {start|stop|reload|force-reload|restart}"
        exit 1
        ;;
esac

exit 0

```

---

### Post by czechmate on 2007-04-12
I had the same problem and accidentally fixed it using info at [http://penguin-breeder.org/sane/saned/](http://penguin-breeder.org/sane/saned/)

If you write a shell script that wraps saned and redirects stderr to /dev/null, and then call that shell script from xinetd, it works great. 

Create a file /usr/sbin/saned.sh like this:
#!/bin/sh
exec /usr/sbin/saned 2> /dev/null

And change the line in /etc/xinetd.d/sane as follows:
        server          = /usr/sbin/saned.sh


There must be some erroneous output from saned that is causing the comms to fail. I hope this works for you too.

---

### Post by YorYor on 2007-05-08
After much mucking around, I have finally fixed my problem.
I have 2 devices, one USB scanner (Canon CanonScan N670U) and a HP AIO (HP LaserJet 3200) connected to my office server.
With the normal installation and configuration, everything seems to work fine, but running "scanimage -L" from client-side only returns the HP3200. I'm guessing because it actually has a device node (/dev/usblp0), whereas the N670U is accessed via libusb (libusb:001:002).

Finally tried the saned -d from commandline, and the client-side works.
Tried to use a script to wrap it via xinetd, but it wouldn't return anything. Telnetting in results in connection closed immediately.
Finally gave up, and use the shell script method to loop it from boot.

All's working fine for me now.
If anyone has any idea how to make Ubuntu (Dapper Server LTS) assign a device node to the USB scanner instead of accessing via libusb only, please share!

---

