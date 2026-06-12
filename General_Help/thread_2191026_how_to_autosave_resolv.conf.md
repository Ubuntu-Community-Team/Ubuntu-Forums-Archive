---
title: "how to autosave resolv.conf"
date: 2013-11-30
forum: General Help
---

### Post by jj4 on 2013-11-30
I have changed nameservers in /etc/resolv.conf to opendns servers.
However, everytime I restart the computer, the file is reset to nameserver 127.0.0.1
How can I permanently save the file so that it reads:
nameserver  208.67.222.222
nameserver 208.67.220.220

---

### Post by Iowan on 2013-11-30
Network Manager has an option to set DNS servers. Otherwise, you might need to check the files in */etc/resolvconf/resolv.conf.d*
 On my machine,* /etc/resolvconf/resolv.conf.d/original* has a listing of the files I see in* /etc/resolv.conf*.

---

### Post by steeldriver on 2013-11-30
You're going about things the wrong way

If you are using the desktop version (with the GUI Network Manager / nm-applet) then open up the connection - either from the applet directly, or by running nm-connection-editor in a terminal - and in the 'IPv4 Settings' tab, switch the mode from 'Automatic (DHCP)' to 'Automatic (DHCP) addresses only' and then add the desired name server(s) in the boxes provided.

OTOH if you're running a server edition, edit the appropriate interface stanza in /etc/network/interfaces and add a space-separated list of nameserver values with the key *dns-nameservers* e.g.

```

dns-nameservers  208.67.222.222 208.67.220.220

```

---

### Post by jj4 on 2013-11-30
> **steeldriver said:**
> You're going about things the wrong way

If you are using the desktop version (with the GUI Network Manager / nm-applet) then open up the connection - either from the applet directly, or by running nm-connection-editor in a terminal - and in the 'IPv4 Settings' tab, switch the mode from 'Automatic (DHCP)' to 'Automatic (DHCP) addresses only' and then add the desired name server(s) in the boxes provided.

OTOH if you're running a server edition, edit the appropriate interface stanza in /etc/network/interfaces and add a space-separated list of nameserver values with the key *dns-nameservers* e.g.

```

dns-nameservers  208.67.222.222 208.67.220.220

```

the problem is I'm using raspbmc, which is a version of ubuntu.
There is no file called resolv.conf.d

The /etc/network/interfaces file contains:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



Do I just add nameservers in there?

I cannot do this through network manager gui as it does not show ipv4 or ipv6 options

```

jason@spain /etc/network $ cd /etc/resolvconf/resolv.conf.d
jason@spain /etc/resolvconf/resolv.conf.d $ ls -l
total 4
-rw-r--r-- 1 root root   0 Sep  7  2012 base
-rw-r--r-- 1 root root 151 Sep  7  2012 head
jason@spain /etc/resolvconf/resolv.conf.d $ nano head


```

---

### Post by Iowan on 2013-11-30
Looks like Network Manager is handling eth0...
What options DOES it provide?
(You gonna make me load up **raspbmc** on my Pi? ;) )
Perhaps the [Crystalbuntu/raspbmc]("http://forum.stmlabs.com/") forums could provide more direct answers
[Here]("http://forum.stmlabs.com/archive/index.php?thread-322.html") is one from there that might be useful.
[This]("http://forum.stmlabs.com/archive/index.php?thread-8324.html") is another.

---

### Post by jeanjd63 on 2013-11-30
> **jj4 said:**
> the problem is I'm using raspbmc, which is a version of ubuntu.
There is no file called resolv.conf.d

The /etc/network/interfaces file contains:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



Do I just add nameservers in there?

I cannot do this through network manager gui as it does not show ipv4 or ipv6 options

```

jason@spain /etc/network $ cd /etc/resolvconf/resolv.conf.d
jason@spain /etc/resolvconf/resolv.conf.d $ ls -l
total 4
-rw-r--r-- 1 root root   0 Sep  7  2012 base
-rw-r--r-- 1 root root 151 Sep  7  2012 head
jason@spain /etc/resolvconf/resolv.conf.d $ nano head


```


Hello
You can do :
**sudo  nano  head**
and add yours dns.
you save then you do :
**sudo resolvconf --enable-updates**
and
**sudo resolvconf -u**
then you can do a :
**sudo  cat  /etc/resolv.conf **
for verify

Bye

---

### Post by papibe on 2013-11-30
Hi jj4.

raspbmc has a custom, and limited, version of NetworkManager, that works using the GUI (Programs -> Raspbmc Settings). It does not provide a way to use both DHCP and set a custom DNS.

You may custom your request to the DHCP server so that it supersede the DNS given by the server. Open your /etc/dhcp/dhclient.conf and look for a line that looks like this:
```
#supersede domain-name "fugue.com home.vix.com";
```
Add a line under it with this syntax:
```
supersede domain-name-servers **208.67.222.222**,** 208.67.220.220**;
```
Then restart your machine.

When you are back on the GUI, you can check the changes by going to 'Settings -> System Info -> Network'

Hope it helps. Let us know how it goes.
Regards.

---

