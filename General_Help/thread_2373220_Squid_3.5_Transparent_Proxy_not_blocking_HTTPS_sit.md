---
title: "Squid 3.5 Transparent Proxy not blocking HTTPS sites"
date: 2017-10-04
forum: General Help
---

### Post by vanlite on 2017-10-04
Hi All,

Excuse me if this is a dumb question as I am aware that squid cannot intercept encrypted traffic but I would like to block certain sites i.e. facebook.com & youtube.com but have been unsuccessful in doing so thus far. I am not an expert and can go as far as google and the squid FAQs can take me, have even tried and succeeded in downloading and compiling with ssl bump, installing generated certificates in the browser but still got errors from the browser in terms of it detecting squid as "MITM" attack.

I have scoured google and cannot find anything with regards to my squid version or even in the same year, all tutorials I have followed have been unsuccessful thus far. I would really appreciate if someone could just point me in the right direction in terms of valid ssl \ tls interception for squid 3.5.25 or just some guidance on how to be able to block encrypted traffic running through my transparent proxy at the moment.

Thank you!

---

### Post by SeijiSensei on 2017-10-04
We use iptables to block SSL connections to Facebook at one of my clients. Our iptables firewalling script generates REJECT rules for each Facebook address we found and adds them to the OUTPUT chain.

A more complex solution uses the SSL_bump code in recent Squid versions. This lets the proxy impersonate the remote site and avoid MITM issues. [https://wiki.squid-cache.org/Features/SslBump](https://wiki.squid-cache.org/Features/SslBump) Then the same ACLs would apply to both HTTP and HTTPS traffic.

---

### Post by vanlite on 2017-10-05
Thank you for the reply!

I think IPTABLES  would be the easiest solution in this situation as I have already reverted to squid installed from the repository's seeing as the compiled version with ssl bump gave me such a hard time, I will test it for future implementation though.

Below is what my IPTABLES look like currently for redirecting traffic to squid transparently, could you possibly tell me which changes would do the trick for blocking these sites?

iptables -t nat -A PREROUTING -s 192.168.215.11 -p tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3129
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -t mangle -A PREROUTING -p tcp --dport 3129 -j DROP

...with .11 being my proxy server obviously.

---

### Post by SeijiSensei on 2017-10-05
I wrote a script to generate our iptables rules since there are literally hundreds of them on the server I manage.  For Facebook, I have a file that contains the addresses of the Facebook servers.  Let's call that file /etc/facebook.  It looks like this:
```

31.13.24.0/21
31.13.64.0/19
31.13.64.0/24
31.13.65.0/24
31.13.66.0/24
31.13.68.0/24
31.13.69.0/24
31.13.70.0/24
31.13.71.0/24
31.13.72.0/24
31.13.73.0/24
31.13.74.0/24
31.13.75.0/24
31.13.76.0/24
31.13.77.0/24
31.13.78.0/24
31.13.79.0/24
31.13.80.0/24
31.13.81.0/24
31.13.82.0/24
31.13.83.0/24
31.13.84.0/24
31.13.85.0/24
31.13.86.0/24
31.13.96.0/19
66.220.144.0/21
66.220.152.0/21
69.63.176.0/21
69.63.176.0/24
69.63.184.0/21
69.171.224.0/20
69.171.239.0/24
69.171.240.0/20
69.171.255.0/24
74.119.76.0/22
103.4.96.0/22
173.252.64.0/19
173.252.70.0/24
173.252.96.0/19
204.15.20.0/22

```
I haven't checked lately to see if there are new IP blocks that need to be added to this list.

In the script that generates the rules we have
```

FB=$(cat /etc/facebook)

for h in $FB
do
        /sbin/iptables -A FORWARD -p tcp -d $h --dport 443 -j REJECT
done

```

Put these, and any other REJECT/DENY rules ahead of the ones you have written.

---

### Post by vanlite on 2017-10-06
Works Like a charm! Thank you SeijiSensei! As soon as I have some free time and patience I will definitely test the ssl_bump method you suggested as well but this will work for now!

---

