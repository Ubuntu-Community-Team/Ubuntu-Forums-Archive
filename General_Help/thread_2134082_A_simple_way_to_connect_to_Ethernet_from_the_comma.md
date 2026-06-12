---
title: "A simple way to connect to Ethernet from the command line?"
date: 2013-04-10
forum: General Help
---

### Post by dancapp on 2013-04-10
Hi everyone. I’ve dug myself into a bit of a hole and I’d really appreciate some help. I’m running Ubuntu with KDE, 64 bit and would describe myself as beginner-intermediate. Here’s what happened:
 
For no reason at all a load of applications uninstalled themselves. After some research I found out I needed to install a specific component of the ‘Policykit’ package (which as it turns out, I probably already had). Installing this then created a situation where I had to choose which user (my own name duplicated twice) must give permissions to update etc. This was a small problem that I could have lived with but I stupidly tried to fix it by uninstalling Policykit. Little did I know that this would make my OS unbootable.
 
So now when I boot I get a message saying I can’t log in (sorry I don’t know the exact message as I’m away from the computer right now). But the long and the short of it is that I need to repair from BASH and here’s where I’m having problems.
 
When I try to ‘apt-get install update’ or ‘install policykit’ from the command line it ‘fails’ to retrieve the package. I’m fairly sure this is because I’m not connected to the Internet – would this be right?
 
So…
 
Can someone talk me through connecting to my Ethernet from the command line? I’m hoping I don’t need to create/edit config files because this will take me to the limits of my understanding. But I can do that if need be. I basically just need a temporary fix in order to briefly connect to the Internet, install policykit and be able to boot into my nice comfortable KDE environment so that I can do everything with GUIs rather than commands.
 
Thanks in advance.

---

### Post by rnerwein on 2013-04-10
hi
as i understand - you have a terminal to type in commands - wright ?
if that's true try on the command line the command: ifconfig
did this command shows you a line like: 
inet Adresse:192.168.2.xxx  Bcast:192.168.2.255  Maske:255.255.255.0
if you see this line - you are conected to the internet.
if not try: ifdow and then ifup
try: ifconfig again. whats the result now.
if you got an IP then you can use: [COLOR=#ff0000]sudo[/COLOR] apt-get what_you_need
much luck
ciao

---

### Post by dancapp on 2013-04-10
Thanks rnerwein - I think that's going to help and I'll try it out this evening when I'm home from work.

Like your signature by the way!

---

### Post by dancapp on 2013-04-10
> **rnerwein said:**
> hi
as i understand - you have a terminal to type in commands - wright ?
if that's true try on the command line the command: ifconfig
did this command shows you a line like: 
inet Adresse:192.168.2.xxx  Bcast:192.168.2.255  Maske:255.255.255.0
if you see this line - you are conected to the internet.
if not try: ifdow and then ifup
try: ifconfig again. whats the result now.
if you got an IP then you can use: [COLOR=#ff0000]sudo[/COLOR] apt-get what_you_need
much luck
ciao

Hey, I tried this with no luck. ifconfig shows this:

[INDENT][B]Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
(... a load of other info - should I post it all?)[/B]
[/INDENT]
 
There is no 'Bcast' address and still no connection. When I type *ifdown -a* and *ifup -a* I get no feedback at all, Any ideas?

---

### Post by dancapp on 2013-04-10
I've now got the 'Bcast' IP address yet when I ping google it says 'unknown host'. Do I need to set up a route host and all that stuff?

---

### Post by matt_symes on 2013-04-10
Hi

Packages don't generally uninstall themselves unless there are dependency issues. That will need some investigation.

Have you looked at reinstalling policy kit from the pool in a Ubuntu CD/USB ?

> Can someone talk me through connecting to my Ethernet from the command line?

Let's get some information first about the state of your system, post the output of these commands in their entirety.

From the terminal: Take and upload photos if you find that easier.

```

cat /sys/class/net/eth0/carrier
ifconfig
service network-manager status
route
```

and then

```

dpkg -l | grep policykit
dpkg -l | grep polkit
```

With this information, we should be able to see where you are. We will not be working blind.

Kind regards

---

### Post by dancapp on 2013-04-10
> **matt_symes said:**
> 
```

cat /sys/class/net/eth0/carrier
ifconfig
service network-manager status
route
```

```

dpkg -l | grep policykit
dpkg -l | grep polkit
```


Many thanks Matt. As follows:

cat /sys/class/net/eth0/carrier
1
ifconfig
eth0     Link encap:Ethernet HWaddr 00:24:8c:91:0c:0e
           inet addr:127.0.0.0 Bcast:127.255.255.255 Mask: 255.0.0.0
           inet6 addr: fe80::224:8cff:fe91:c0e/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX Packets:9 errors:0 dropped:0 overruns:0 carrier:0               
           collisions:0 txqueuelen:1000
           RX bytes:756 (756.0 B) TX bytes:4300 (4.3 KB)
           Interrupt:43 Base address:0xa000

lo        Link encap:Local loopback
           inet addr:127.0.0.1  Mask: 255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX Packets:28 errors:0 dropped:0 overruns:0 frame:0          
           TX Packets:28 errors:0 dropped:0 overruns:0 carrier:0          
           collisions:0 txqueuelen:0
           RX bytes:2184 (2.1 KB) TX bytes:2184 (2.1 KB)

service network-manager status
network-manager start/running

route
Kernel IP routing table
Destination.......        Gateway.......        Genmask        .....Flags......       Metric......      Ref.....         Use........          Iface
default..............               127.0.0.0       ......0.0.0.0            .........UG          .........0              .............0.........           0............              eth0

---

### Post by matt_symes on 2013-04-10
Hi

You have an Ethernet connection to the router so that is good. 

Let's try to get you an IP address.

At the terminal type

```
sudo dhclient eth0
```

Post back on the output and the results of (after the command above)
```

ifconfig
ping -c 2 8.8.8.8
nslookup www.bbc.co.uk
```

If that does not work then type

```
sudo service network-manager stop
```

and repeat the above commands.

EDIT: Also post the output of

```
ls /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy
```

EDIT 2:

You forgot to post the output of these two commands

```
dpkg -l | grep policykit
dpkg -l | grep polkit
```

EDIT 3:

Can you also post the output of

```
grep ".*[0-9] remove" /var/log/dpkg.log
```

Kind regards

---

### Post by dancapp on 2013-04-11
Thanks again Matt. Yes I realised this morning I forgot to post the output of:

[I]dpkg -l | grep policykit
dpkg -l | grep polkit[/I]

Unfortunately I'm at work away from my Ubuntu system so I'll get back to you this evening with the output.

---

### Post by dancapp on 2013-04-11
Hi Matt. After doing the 'dhclient eth0' thing...

ifconfig
eth0        Link encap:Ethernet HWaddr 00:24:8c:91:0c:0e
[INDENT]inet addr:127.0.0.0 Bcast:127.255.255.255 Mask: 255.0.0.0[/INDENT]
            [INDENT]inet6 addr: fe80::224:8cff:fe91:c0e/64 Scope:Link[/INDENT]
            [INDENT]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/INDENT]
            [INDENT]RX Packets:24 errors:0 dropped:0 overruns:0 frame:0               [/INDENT]
[INDENT]TX Packets:40 errors:0 dropped:0 overruns:0 carrier:0
[/INDENT]
            [INDENT]collisions:0 txqueuelen:1000[/INDENT]
            [INDENT]RX bytes:2858 (2,8 KB) TX bytes:8718 (8.7 KB)[/INDENT]
            [INDENT]Interrupt:43 Base address:0xc000[/INDENT]
 
lo               Link encap:Local loopback
           [INDENT]inet addr:127.0.0.1  Mask: 255.0.0.0[/INDENT]
            [INDENT]inet6 addr: ::1/128 Scope:Host[/INDENT]
            [INDENT]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/INDENT]
            [INDENT]RX Packets:0 errors:0 dropped:0 overruns:0 frame:0          [/INDENT]
            [INDENT]TX Packets:0 errors:0 dropped:0 overruns:0 carrier:0          [/INDENT]
            [INDENT]collisions:0 txqueuelen:0[/INDENT]
            [INDENT]RX bytes:0 (0 B) TX bytes:0 (0 KB)

[/INDENT]
ping 2 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=44 time=41.4 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=44 time=36.3 ms

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 36.366/38.899/41.432/2.533 ms


nslookup [www.bbc.co.uk](www.bbc.co.uk)
Server: 192.168.1.254
Address: 192.168.1.254#53

Non-authoritative answer:
[www.bbc.co.uk](www.bbc.co.uk)   canonical name = [www.bbc.net.uk](www.bbc.net.uk)
Name: [www.bbc.net.uk](www.bbc.net.uk)
Address: 212.58.244.70


ls /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy
ls: cannot access /usr/share/polkit-1/actions/org.freedesktop.NetworkManager.policy: No such file or directory


dpkg -l | grep policykit
rc policykit-1...........................................0.104-1ubuntu+fixed1..................(I assume you don't need the description)
rc policykit-1-gnome................................0.105-1ubuntu3.1................
ii policykit-1-desktop-privileges.................0.10..................

dpkg -l | grep polkit
rc lib32polkit................................0.96-0~ppa1................
rc lib32polkit-qt................................0.95.1-0~ppa2................
rc libpolkit-agent-1-0................................0.104-1ubuntu1+fixed1................
rc libpolkit-backend-1-0................................0.104-1ubuntu1+fixed1................
rc libpolkit-gobject-1-0................................0.104-1ubuntu1+fixed1................
rc libpolkit-qt-1-0................................0.95.1-1fakesync1...............
rc libpolkit-qt-1-1................................0.103.0-1...............
rc libpolkit-kde-1................................0.99.0-3ubuntu5................

---

### Post by dancapp on 2013-04-11
I've had to take a photo of the output from:

grep ".*[0-9] remove" /var/log/dpkg.log

I've got a nasty feeling about it. This is only the last bit of it. shift+PgUp doesn't even let me get to the top of it. Let me know if you need more:


[IMG]http://i45.tinypic.com/r8azi0.jpg[/IMG]

---

### Post by matt_symes on 2013-04-11
Hi

First.

> eth0 Link encap:Ethernet HWaddr 00:24:8c:91:0c:0e
inet addr:127.0.0.0 Bcast:127.255.255.255 Mask: 255.0.0.0

I'm surprised about your IP address being reported as 127.0.0.0. 

Do you still have network manager running ?

```
service network-manager status
```

Maybe your using IPv6. I don't know much about that so you have pointed out something i must read up on.

Anyway, you have connectivity to the outside world so that is good. 

Can you post the output of

```
route
```

Second.

Wow ! That's a lot of packages removed there ! What on earth happened ?

Before we do anything, can i take a look at you sources please.

From the terminal,

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by dancapp on 2013-04-11
service network-manager status
network-manager start/running


route
Kernel IP routing table
Destination..................Gateway................Genmask.............Flags.............Metric............Ref........Use...........Iface
default.........................BTHomeHub..........0.0.0.0.................UG................0....................0...........0...............eth0
192.168.1.0..................*...........................255.255.255.0......U...................0...................0............0..............eth0


Here's the output of:

grep "^[^#]" /etc/apt/sources.list{,.d/*}

(as much as I can capture)

[IMG]http://i50.tinypic.com/286xwm.jpg[/IMG]

[IMG]http://i50.tinypic.com/i5dw7m.jpg[/IMG]


As for the deletion of packages, I didn't realise I'd done it but I think I know why. Some steps I followed before posting this thread told me that I might not be able to install policykit because I had too many PPAs, so I followed steps to delete all but the essential ones from my 'sources.list' file. I thought it was just delete the sources but perhaps it deleted all of the packages drawn from those sources? If not then I have no idea why.

Thanks again for the help.

---

### Post by matt_symes on 2013-04-11
Hi

You have lost half your packages required for a functioning desktop ! It is possible they have been downgraded but i doubt it.

Amongst other useful packages you have lost udisks, consolekit, policykit, upower and the list goes on and on.

You are mixing PPA's from Lucid and Precise and, i expect, other releases. I think this is why you have the problems you have. It's hard to be 100% sure as i cannot see all the text output from the photo.

But anyway, please don't do this again or you may have the same problems in the future. Use PPAs for the release you are running and don't mix and match from different releases.

Disable all PPAs before dist upgrading and make sure when you re-enable them, they are pointing to the new release (if it's available).

From this point, you have two choices - the easy way and the hard way.

The easy way is to backup your data and reinstall.

The hard way all to remove all the the packages from Lucid and other release that do not match your current release. You can then try to reinstall all the packages for precise. This option should be doable if you so choose but i expect it will not be quick. It will also depend on your technical ability.

What would you like to do ?

Sorry to put it like that. I'm just being honest about what i think is the state of your install. As i said, it would be useful to see all the text from the sources.

Kind regards

---

### Post by dancapp on 2013-04-11
Hi Matt. My bad feeling was correct then.
I think I also have Jaunty on there. The instructions I followed when I did this told me to add old stable Ubuntu PPAs to my sources.list but thinking about it I misinterpreted this and ended up mixingh sources.

I'm happy to reinstall so long as I can back up my documents. It'd be great if I could also backup bookmarks, preferences etc but if not it's not the end of the World. I have an external USB drive, or would I create a partition for the backup files?

---

### Post by matt_symes on 2013-04-11
Hi

I would boot into a LiveCD/USB and copy the entire contents of your home directory to the external USB drive.

After that you can you can copy back your files and bookmarks and saved e-mails (etc) onto your new install.

If you want pointers for that then post back. I can help tomorrow.

Kind regards

---

### Post by dancapp on 2013-04-11
Many thanks for all your help Matt. It really is appreciated (and I hope this thread might help others who end up with similar problems). I'll post back here to confirm the successful reinstall.

---

### Post by dancapp on 2013-04-11
Matt. The only problem I've got now is that viewing from within my live Kubuntu CD, my .mozilla file from my existing Ubuntu install is blank and contains no bookmark info. A quick web search suggests I need to manually export my bookmarks from Firefox, but how can I do that if I can't load my existing Ubuntu GUI?Hope that makes sense.

---

