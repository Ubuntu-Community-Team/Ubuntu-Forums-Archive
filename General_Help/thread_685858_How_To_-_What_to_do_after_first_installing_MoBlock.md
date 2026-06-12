---
title: "How To - What to do after first installing MoBlock"
date: 2008-02-02
forum: General Help
---

### Post by DugieHowsa on 2008-02-02
Like everyone else, I followed the instructions from the MoBlock community page and the main MoBlock thread.

[https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock)
[http://ubuntuforums.org/showthread.php?t=192559](http://ubuntuforums.org/showthread.php?t=192559)

Like many other people, I had issues after install.  By default, it appears that some legitimate traffic is blocked, and what appears to be network problems, is in fact MoBlock working normally.

MoBlock is more or less a host firewall.  In order for it to work properly, there are a few minor changes you may need to make to the MoBlock config.

1)  Open the MoBlock config file:
```

sudo gedit /etc/moblock/moblock.conf
```

2)  Modify the file to allow Outbound Web and DNS:
```

WHITE_TCP_OUT="80 443"
WHITE_UDP_OUT="53"
```

This should take care of web surfing.  Feel free to add ports for other applications if needed.  I found that some web sites are blocked by the default blocklist, so I need to specifically allow these ports.

3)  OPTIONAL:  If you are on a LAN, and not directly connected to your ISP, add the network range of your internal network.  This will allow you to connect to all your local resources, and all other hosts on your local network to connect to you:
```

WHITE_IP_IN="192.168.100.0/24"
WHITE_IP_OUT="192.168.100.0/24"
```

NOTE:  Your IP address range may be different, so run the ifconfig command from the terminal to find out what your directly connected network range is.  Add multiple networks if necessary.

4)  Be sure to restart MoBlock after making any changes:
```

sudo moblock-control restart
```

This is by no means an extensive write up, but I figured it may help those out who are having some difficulty after initially installing MoBlock and are experiencing some network and internet problems.

---

