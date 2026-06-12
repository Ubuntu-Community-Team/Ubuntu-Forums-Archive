---
title: "Seeking some advice on Bind9 configuration."
date: 2013-06-13
forum: General Help
---

### Post by bagelthesmartypants on 2013-06-13
Hello, I just joined the forums but have been using ubuntu for years. I was wondering if anyone was able to help me with a simple question I had regarding a bind9 master / slave configuration.

It's a similar setup to such as this;

[http://aesptux.com/2011/11/08/configuring-bind9-master-slave-on-ubuntu/](http://aesptux.com/2011/11/08/configuring-bind9-master-slave-on-ubuntu/)

I had no problem setting it up, and for all intents and purposes it works. I can ping / nslookup / reverse lookup the hosts on my small lan. I had one question regarding the slave device's zone files, should these files ( for instance, /etc/bind/zones/test1.db") be transferred to the slave? If I shut down the master, the slave still works as the primary, and the hosts can still do the same dns requests without error. However these files are not there, I'm wondering if this is some how saved in memory? I assumed they would be transferred over and stay in /etc/bind/zones/test1.db etc etc, but nothing is there. I changed up the slave configuration a few times, specifying the same file names, and then different names; and neither seemed to matter. Which is why I perhaps thought it might be saved in memory now. Anyways I can provide the actual configuration file examples and such, just thought this might be an easy answer for someone.

Much thanks ubuntu community,

Kody Abney.


(P.S. both are running 12.04 precise 64bit, with no apparent trouble.)

---

### Post by SeijiSensei on 2013-06-13
The slave server should definitely be creating copies of the primary's zones.  Try changing the serial number of one of the zones on the primary and restarting bind. What do you seen in /var/log/syslog on both machines?  

Do you have the secondary's IP in an allow-transfer{} directive on the primary?  Does your firewall allow TCP connections to the primary's port 53 from the secondary?  Just allowing UDP is not enough.  That will respond to queries but not permit transfers which use TCP.

---

### Post by bagelthesmartypants on 2013-06-17
Thank you for the reply Seiji. There is no firewall restrictions at all between these two servers. As their on our local lan behind our firewall, and if someone got to them we'd have much bigger issues then the dns server. Anyways here's a quick overview of my config;

master - 10.3.23.74;

configs;

named.conf haven't edited on either, as not needed.

named.conf.options of master;
"

       forwarders {
         66.209.64.20;
         66.209.64.21;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        allow-query { any; };
        allow-recursion { trusted; };
        allow-query-cache { trusted; };
        allow-query-on { any; };
        allow-transfer { 10.3.23.74; };
};

named.conf.local;
"zone "vegasint" IN {
        type slave;
        file "/etc/bind/slave/vegasint.db";
        masters { 10.3.23.74; };
        allow-notify { 10.3.23.74; };
};

zone "23.3.10.in-addr.arpa" IN {
        type slave;
        file "/etc/bind/slave/23.3.10.in-addr.arpa.db";
        masters { 10.3.23.74; };
        allow-notify { 10.3.23.74; };
};

acl "trusted" {
    10.0.0.0/8;
    localhost;
    127.0.0.1;
    localnets;
};"

here's the slaves config;

"zone "vegasint" IN {
        type slave;
        file "/etc/bind/slave/vegasint.db";
        masters { 10.3.23.74; };
        allow-notify { 10.3.23.74; };
};

zone "23.3.10.in-addr.arpa" IN {
        type slave;
        file "/etc/bind/slave/23.3.10.in-addr.arpa.db";
        masters { 10.3.23.74; };
        allow-notify { 10.3.23.74; };
};

acl "trusted" {
    10.0.0.0/8;
    localhost;
    127.0.0.1;
    localnets;
};"

and the named.conf.options are identical; minus the differentiating ip addresses.

In the logs i see the following, ( sorry a little long, for some reason this forums won't let me attach at the moment, might be my laptop.)

"Jun 17 10:01:16 vegas-dns2-slave named[344]: starting BIND 9.8.1-P1 -u bind
Jun 17 10:01:16 vegas-dns2-slave named[344]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions -Wl,-z,relro' 'CPPFLAGS=-D_FORTIFY_SOURCE=2'
Jun 17 10:01:16 vegas-dns2-slave named[344]: adjusted limit on open files from 4096 to 1048576
Jun 17 10:01:16 vegas-dns2-slave named[344]: found 1 CPU, using 1 worker thread
Jun 17 10:01:16 vegas-dns2-slave named[344]: using up to 4096 sockets
Jun 17 10:01:16 vegas-dns2-slave named[344]: loading configuration from '/etc/bind/named.conf'
Jun 17 10:01:16 vegas-dns2-slave named[344]: reading built-in trusted keys from file '/etc/bind/bind.keys'
Jun 17 10:01:16 vegas-dns2-slave named[344]: using default UDP/IPv4 port range: [1024, 65535]
Jun 17 10:01:16 vegas-dns2-slave named[344]: using default UDP/IPv6 port range: [1024, 65535]
Jun 17 10:01:16 vegas-dns2-slave named[344]: listening on IPv4 interface lo, 127.0.0.1#53
Jun 17 10:01:16 vegas-dns2-slave named[344]: listening on IPv4 interface eth0, 10.3.23.76#53
Jun 17 10:01:16 vegas-dns2-slave named[344]: generating session key for dynamic DNS
Jun 17 10:01:16 vegas-dns2-slave named[344]: sizing zone task pool based on 7 zones
Jun 17 10:01:16 vegas-dns2-slave named[344]: using built-in root key for view _default
Jun 17 10:01:16 vegas-dns2-slave named[344]: set up managed keys zone for view _default, file 'managed-keys.bind'
Jun 17 10:01:16 vegas-dns2-slave named[344]: Warning: 'empty-zones-enable/disable-empty-zone' not set: disabling RFC 1918 empty zones
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 254.169.IN-ADDR.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 100.51.198.IN-ADDR.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 113.0.203.IN-ADDR.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: D.F.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 8.E.F.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 9.E.F.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: A.E.F.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: B.E.F.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: automatic empty zone: 8.B.D.0.1.0.0.2.IP6.ARPA
Jun 17 10:01:16 vegas-dns2-slave named[344]: command channel listening on 127.0.0.1#953
Jun 17 10:01:16 vegas-dns2-slave named[344]: command channel listening on ::1#953
Jun 17 10:01:16 vegas-dns2-slave named[344]: zone 0.in-addr.arpa/IN: loaded serial 1
Jun 17 10:01:16 vegas-dns2-slave named[344]: zone 127.in-addr.arpa/IN: loaded serial 1
Jun 17 10:01:16 vegas-dns2-slave named[344]: zone 255.in-addr.arpa/IN: loaded serial 1
Jun 17 10:01:16 vegas-dns2-slave named[344]: zone localhost/IN: loaded serial 2
Jun 17 10:01:16 vegas-dns2-slave named[344]: managed-keys-zone ./IN: loaded serial 5
Jun 17 10:01:16 vegas-dns2-slave named[344]: running
Jun 17 10:01:16 vegas-dns2-slave named[344]: zone 23.3.10.in-addr.arpa/IN: Transfer started.
Jun 17 10:01:16 vegas-dns2-slave named[344]: transfer of '23.3.10.in-addr.arpa/IN' from 10.3.23.74#53: connected using 10.3.23.76#50543
Jun 17 10:01:16 vegas-dns2-slave named[344]: zone 23.3.10.in-addr.arpa/IN: transferred serial 2008080901
Jun 17 10:01:16 vegas-dns2-slave named[344]: transfer of '23.3.10.in-addr.arpa/IN' from 10.3.23.74#53: Transfer completed: 1 messages, 6 records, 234 bytes, 0.001 secs (234000 bytes/sec)
Jun 17 10:01:16 vegas-dns2-slave named[344]: dumping master file: /etc/bind/slave/tmp-qfzEWDhXQc: open: permission denied
Jun 17 10:01:16 vegas-dns2-slave kernel: [401341.556802] type=1400 audit(1371488476.955:70): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/slave/tmp-qfzEWDhXQc" pid=345 comm="named" requested_mask="c" denied_mask="c" fsuid=106 ouid=106
Jun 17 10:01:17 vegas-dns2-slave named[344]: zone vegasint/IN: Transfer started.
Jun 17 10:01:17 vegas-dns2-slave named[344]: transfer of 'vegasint/IN' from 10.3.23.74#53: connected using 10.3.23.76#42667
Jun 17 10:01:17 vegas-dns2-slave named[344]: zone vegasint/IN: transferred serial 2008080901
Jun 17 10:01:17 vegas-dns2-slave named[344]: transfer of 'vegasint/IN' from 10.3.23.74#53: Transfer completed: 1 messages, 7 records, 228 bytes, 0.002 secs (114000 bytes/sec)
Jun 17 10:01:17 vegas-dns2-slave named[344]: zone vegasint/IN: sending notifies (serial 2008080901)
Jun 17 10:01:17 vegas-dns2-slave named[344]: dumping master file: /etc/bind/slave/tmp-LFazQo8bKf: open: permission denied
Jun 17 10:01:17 vegas-dns2-slave kernel: [401342.056865] type=1400 audit(1371488477.455:71): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/named" name="/etc/bind/slave/tmp-LFazQo8bKf" pid=345 comm="named" requested_mask="c" denied_mask="c" fsuid=106 ouid=106"

Anyways you can see it all goes well minus, "/etc/bind/slave/tmp-LFazQo8bKf: open: permission denied". I changed it from /etc/bind/zones/* default because I read some where this error was perhaps because of permission issues regarding the daemon. I followed a few different tutorials referencing such an error, but none worked. ( This had me changing permissions on /etc/init.d/apparmor/named and also the named binary, as well as the bind folders. I tried a few things, such as creating the files on the slave, ( thinking it will auto update them, no luck), directly copying the zone files seeing if they update, again no luck. Am I suppose to create these files, or are they 100% supposed to be created automatically? I'll keep tinkering with it, but thanks for the help.

(ps what anime is that character? xD).

Thanks,

Kody Abney.

---

### Post by bagelthesmartypants on 2013-06-17
Argh, It posted my slave config twice, apologies. Here's the master;

"
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

         forwarders {
         66.209.64.20;
         66.209.64.21;
         };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;

    auth-nxdomain no;    # conform to RFC1035
    allow-query { any; };
    allow-recursion { trusted; };
    allow-query-cache { trusted; };
    allow-query-on { any; };"
"
zone    "vegasint" IN {
        type master;
        file "/etc/bind/zones/vegasint.db";
        allow-transfer { 10.3.23.76; };
};

zone "23.3.10.in-addr.arpa" IN {
        type master;
        file "/etc/bind/zones/23.3.10.in-addr.arpa";
        allow-transfer { 10.3.23.76; };
};

acl "trusted" {
    10.0.0.0/8;
    localhost;
    127.0.0.1;
    localnets;
};

"

Thanks.

---

