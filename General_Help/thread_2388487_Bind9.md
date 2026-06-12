---
title: "Bind9"
date: 2018-04-03
forum: General Help
---

### Post by lrzuniga on 2018-04-03
Hi,

Installed bind9 on ubuntu server 16.04 and it works fine.

Managing it with webmin and it seems pretty straighforward.

The problem is when I add a new record, it is not resolvable until I restart the bind9 service. Once the service is restart, the record resolves immediately.

Not sure if this is the expected behaviour, but I don't think it would be.

Would appreciate any help in where I should be looking.


named.conf.options:
```
options {    directory "/var/cache/bind";


    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113


    // If your ISP provided one or more IP addresses for stable
    // nameservers, you probably want to use them as forwarders.
    // Uncomment the following block, and insert the addresses replacing
    // the all-0's placeholder.


    // forwarders {
    //     0.0.0.0;
    // };


    //========================================================================
    // If BIND logs error messages about the root key being expired,
    // you will need to update your keys.  See https://www.isc.org/bind-keys
    //========================================================================
    dnssec-validation auto;


    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
    forwarders {
        1.1.1.1;
        };
};
```

named.conf.local:
```
//// Do any local configuration here
//


// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";


zone "myplanet-intra.com" {
    type master;
    file "/var/lib/bind/myplanet-intra.com.hosts";
    };
zone "25.168.192.in-addr.arpa" {
    type master;
    file "/var/lib/bind/192.168.25.rev";
    };
```

Any help appreciated!

Luis

---

### Post by #&amp;thj^% on 2018-04-03
I have always found adding new records to bind9 has always required a bind9 restart.
Just makes good sense if you think about it. :)

---

### Post by lrzuniga on 2018-04-03
interesting.

coming from managing our DNS on an apple mac mini, I've not run into doing that before.

good to know!

Thanks 1fallen

Luis

---

### Post by SeijiSensei on 2018-04-03
You can also force bind to reread the zone files by issuing the command

```
sudo killall -HUP named
```

That doesn't restart the server; it just updates the records.

---

### Post by #&amp;thj^% on 2018-04-03
> **SeijiSensei said:**
> You can also force bind to reread the zone files by issuing the command

```
sudo killall -HUP named
```

That doesn't restart the server; it just updates the records.
+1 Very nice SeijiSensei I never even thought of that. :)

---

### Post by lrzuniga on 2018-04-03
mr google is saying the preferred way is ```
rndc reload
```

anyhoo, good to know it doesn't happen automagically like on osx server

thanks all

L.

---

### Post by lrzuniga on 2018-04-03
and then I find this in webmin....
[IMG]https://content.screencast.com/users/luis.z/folders/Snagit/media/c4208560-88db-4f0a-a753-88c3a8570a6d/2018-04-03_14-57-03%20(1).png&quot;><img class=&quot;embeddedObject&quot; src=&quot;https://content.screencast.com/users/luis.z/folders/Snagit/media/c4208560-88db-4f0a-a753-88c3a8570a6d/2018-04-03_14-57-03%20(1).png[/IMG]


:lolflag:

---

### Post by #&amp;thj^% on 2018-04-03
:D Thanks lrzuniga ;)
You will find in your journey with linux>>>so many different ways to do things.
Kind Regards

---

### Post by lrzuniga on 2018-04-03
indeed...and helpful people along the way!

---

