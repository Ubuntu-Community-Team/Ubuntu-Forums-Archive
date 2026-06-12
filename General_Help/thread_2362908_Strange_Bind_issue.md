---
title: "Strange Bind issue"
date: 2017-06-03
forum: General Help
---

### Post by Andrew_Welham on 2017-06-03
I had quote a complex bind 9 config with different views for different IP ranges. The dns server topically forwarded the requests on to external dns servers either my isp or OpenDNS (based on client IP), and filtered out some ad based domains.
I have had issues with BBC i player on a Samsung TV and also firmware updates. On the DNS server all the IPs appear to get resolved to a real and correct IP. If i set the Samsung TV to manual DNS of 8.8.8.8 then its works fine.
To try to find the issue i started again with a very simple DNS file
options {
        directory "/var/cache/bind";
        pid-file "/var/cache/bind/named.pid";
        listen-on { DNS Server IP; };
        forwarders {8.8.8.8; 8.8.4.4; };
        forward only;
        allow-recursion { any; };
        allow-query { any; };
        allow-query-cache { any; };
        };


Still the same issue, and i cant find any sign of errors even with debug level 3 & 4


Any ideas

---

