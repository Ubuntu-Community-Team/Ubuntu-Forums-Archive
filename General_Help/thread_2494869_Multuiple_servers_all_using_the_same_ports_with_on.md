---
title: "Multuiple servers all using the same ports with one extrnal IP address?"
date: 2024-01-29
forum: General Help
---

### Post by josephchrzempiec on 2024-01-29
Hello, I was curious Is it possible to have multiple ubuntu servers with the same ports for http and ftp on a single external static ip address?

I know hosting companies do that. Yet unsure how. If someone can please point me in the tight direction to understand this and how I might get started. Please help me with this problem? Thank you

Joseph

---

### Post by SeijiSensei on 2024-01-29
You want a "reverse proxy" configuration. Here's one example using Apache as the gateway.

[https://iws.io/archive/multiple-web-servers-over-a-single-ip-using-apache-as-a-reverse-proxy](https://iws.io/archive/multiple-web-servers-over-a-single-ip-using-apache-as-a-reverse-proxy)

There's a lot of documentation about this approach out on the web.

---

### Post by josephchrzempiec on 2024-01-29
I will take a look at this. thank you.

Edit: This is what I was looking for thank you. I also looked up [SIZE=1][COLOR=var(--tw-prose-headings)][FONT=ui-sans-serif]Multiple Web Servers over a Single IP, Using Apache as a Reverse Proxy on google and found a lot of video [/FONT][/COLOR][/SIZE]tutorials that can help me out. Thank you once again.


> **SeijiSensei said:**
> [https://iws.io/archive/multiple-web-servers-over-a-single-ip-using-apache-as-a-reverse-proxy](https://iws.io/archive/multiple-web-servers-over-a-single-ip-using-apache-as-a-reverse-proxy)

---

### Post by josephchrzempiec on 2024-01-29
I will take a look at this. thank you.

Edit: Yes thank you this is what I was looking for I found some online video tutorials to help me. I do better with videos helping then text it gets very confusing for me. Once again thank you.


> **SeijiSensei said:**
> [https://iws.io/archive/multiple-web-servers-over-a-single-ip-using-apache-as-a-reverse-proxy](https://iws.io/archive/multiple-web-servers-over-a-single-ip-using-apache-as-a-reverse-proxy)

---

