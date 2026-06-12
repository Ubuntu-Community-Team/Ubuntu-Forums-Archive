---
title: "bind9 configuration"
date: 2015-03-06
forum: General Help
---

### Post by banyezdemah on 2015-03-06
Hi

Dear friends,
I want to setup a DNS server with a special goal.
I know how to install bind9
The purpose is that I don't want to forward DNS requests to some other DNS servers such as 8.8.8.8 or 8.8.4.4
I want to send the DNS requests directly to the root DNS servers.
I don't know how to configure my DNS server on ubuntu for this purpose.

I will appreciate if you can help me.

Regards :)

---

### Post by nerdtron on 2015-03-06
If you want to use the root dns servers, you can just set your dns entries to the ones listed on [https://www.iana.org/domains/root/servers](https://www.iana.org/domains/root/servers)

---

### Post by banyezdemah on 2015-03-19
I think the link is the list of the root dns servers.
But my problem is that I want to configure my dns server that he ask the requests from root dns servers and dows not forward requests to another servers.
I do not know how should I configure my dns server to do that.

---

### Post by nerdtron on 2015-03-19
Then you should declare forwarders on your bind config that you really want to send the query on the root servers.

fowarders option is the IP address  used in case that a local DNS server do not know the answer to a name resolution query. 

```
 forwarders {
              x.x.x.x;
              x.x.x.x;
         };

```

where x.x.x.x is the IP address of the DNS server you want your queries to be forwarded.

---

### Post by banyezdemah on 2015-03-19
My configuration is here :






acl "trusted" {
       localhost;
       0.0.0.0/0;
};





acl "bogusips" {
        0.0.0.0/8;
        1.0.0.0/8;
        2.0.0.0/8;
        192.0.2.0/24;
        224.0.0.0/3;
        169.254.0.0/16;
};















options {
        directory "/etc/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
#217.218.127.127;
#217.218.155.155;
#8.8.8.8;
#8.8.4.4;
#156.154.70.1;
#156.154.71.1;
#208.67.222.222;
#4.2.2.1;
#4.2.2.2;
198.41.0.4;
192.228.79.201;
192.33.4.12;
199.7.91.13;
192.203.230.10;
192.5.5.241;
192.112.36.4;
128.63.2.53;
192.36.148.17;
192.58.128.30;
193.0.14.129;
199.7.83.42;
202.12.27.33;
        };














recursion yes;
#allow-recursion { "any"; };

allow-recursion { trusted; };




 blackhole { bogusips; };







        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        #listen-on-v6 { any; };
};






but is does not work !!!

---

### Post by nerdtron on 2015-03-19
>  but is does not work !!! 

What is not working? How do you know it not working? What error is present? What does the bind log say?

---

### Post by banyezdemah on 2015-03-19
I check with nslookup and web browsing.
When I set my primary dns server to it, no web site will be open.

---

### Post by SeijiSensei on 2015-03-19
If you want to use the root name servers, you shouldn't have any forwarders.  Without them BIND should query the root servers directly.

---

