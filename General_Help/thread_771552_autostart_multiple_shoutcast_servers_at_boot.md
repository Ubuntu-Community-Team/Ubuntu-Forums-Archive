---
title: "autostart multiple shoutcast servers at boot?"
date: 2008-04-27
forum: General Help
---

### Post by djdrdewey on 2008-04-27
Hello Ubuntu community! My friend and I are working on our server, and need help trying to make 3 shoutcast servers start-up at boot. We are using Ubuntu 8.04 64 bit. We are playing with the following script we found thanks to google: 

```
#!/usr/bin/perl

@a=qx{ps x | grep -i sc_serv};
$b=1;

foreach (@a) {
        if ($_ =~ /grep/) {
        $_ =~ s/.*/blah/g;
        }
        if ($_ =~ /sc_serv/) {$b=0;}
}

if ($b == 1) {
        qx{cd ~/scserv_aa/ ; ./sc_serv &> /dev/null &};
}
```

but we can only get 1 shoutcast server working (on port 8000). We want to have our 2 other server start (on ports 8003 and 8005). We tried using 2 other scripts, but still only one started. Any help is greatly appreciated. Thank you for your time and help!

-Dj. Dr. Dewey

---

### Post by piine on 2009-05-14
Hi, I've had the same problem. The only solution that I have found for the problem is to create a symbolic link from the original file and append the customer or port # to it and create a new conf file with the same appendage.

ex.
```

$ sudo ln -sf /usr/local/bin/shoutcast /usr/local/bin/shoutcast-8003
$ sudo cp /etc/shoutcast.conf /etc/shoutcast-8003.conf
$ sudo shoutcast-8003 /etc/shoutcast-8003.conf

```

---

### Post by piine on 2009-05-14
Also, I created a init.d for each one and added it to the rc.d, that way, you won't need the script. Depending on the placement and permissions of the file, you could write a web interface to control the individual servers.

---

### Post by piine on 2009-05-14
This is a init.d file I've found for multiple server.
Read the note in the file, it explains everythig

[http://www.ecualug.org/files/shoutcast-redhat-initd.txt](http://www.ecualug.org/files/shoutcast-redhat-initd.txt)

---

