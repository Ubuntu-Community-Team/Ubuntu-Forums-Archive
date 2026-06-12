---
title: "web proxy server package disappears"
date: 2024-07-07
forum: General Help
---

### Post by Skaperen on 2024-07-07
years ago i used to run an HTTP proxy server that was simple to configure and lightweight to run.  it was called *polipo*.  it seems to no long be in the repository (its file name is not in the file lists).  does anyone know of something simple i could run in its place?  i have a current need to run several proxy servers all under 24.04.

---

### Post by currentshaft on 2024-07-07
privoxy is powerful and actively maintained

---

### Post by Skaperen on 2024-07-08
> **currentshaft said:**
> privoxy is powerful and actively maintained

what does "powerful" mean for this?  my understanding of "power" is a rate over time of energy transfer.

---

### Post by ActionParsnip on 2024-07-08
openssh-server can be used as a proxy. You'll just need SSH which is in all operating systems, to make an SSH tunnel. You can then point to the client to localhost:portyouchoose and it'll work. Lots of guides online

---

### Post by Skaperen on 2024-07-08
> **ActionParsnip said:**
> openssh-server can be used as a proxy. You'll just need SSH which is in all operating systems, to make an SSH tunnel. You can then point to the client to localhost:portyouchoose and it'll work. Lots of guides online

so SSH has some HTTP support code in it?  how do i turn that on?

---

### Post by currentshaft on 2024-07-08
> **Skaperen said:**
> what does "powerful" mean for this?  my understanding of "power" is a rate over time of energy transfer.

Powerful = capable. It has a lot of filtering options and features to shape HTTP traffic, which I assumed is what you want.

---

### Post by ActionParsnip on 2024-07-12
[https://www.linuxjournal.com/content/use-ssh-create-http-proxy](https://www.linuxjournal.com/content/use-ssh-create-http-proxy)

That's one guide I found online super fast....

---

### Post by TheFu on 2024-07-13
> **Skaperen said:**
> so SSH has some HTTP support code in it?  how do i turn that on?

Outbound proxy or inbound reverse proxy?

ssh can be used as a SOCKS proxy.  It is handy if you want to connect to HTTP/S servers on your LAN through a secure tunnel.  I've posted how I did it in the forums a few times over the decades.  When running it, all my http/s traffic appears to be coming from the ssh server I connect into that I'm using as a SOCKS proxy.  The major web browsers all support SOCKS proxies, BTW.  Some, like Firefox, make us point-n-click to make the settings while others have a few command line options so scripting the startup with a SOCKS proxy setup/configured is easy.

The defacto outbound proxy, typically used for an entire LAN is "**squid**".  I haven't used it in about 20 yrs, but it is still popular and "powerful".

If you are running internal web servers on you LAN and want external people to have access, there are a number of options.  Perhaps you want TLS cert termination to happen on the reverse proxy before normal HTTP traffic is sent to the actual web servers.  There are a number of reverse proxy servers.  nginx, apache, HAProxy, and it seems almost every popular scripting language for a webapp will have 5 created in their specific language too.  When I was doing ruby programming, I used "thin" as the reverse proxy and load balancer.  There are others.  Php, Python, Perl each have some options.  HAProxy is designed for webtraffic, but it can be used for any TCP connections at all, which differentiates is from most other options.  I've used **nginx** and **haproxy** most recently for reverse proxies.  haproxy is about 10x easier to setup compared to nginx, assuming you aren't already familiar with nginx.

So ... what purpose for a "proxy" do you want?

---

### Post by Skaperen on 2024-07-15
> **currentshaft said:**
> Powerful = capable. It has a lot of filtering options and features to shape HTTP traffic, which I assumed is what you want.

no.

i want something that is simple, has basic common options like what port to listen to, is light weight (limits its memory and CPU usage), support HTTPS in some way (probably as a connection relay once it gets the IP address of the named host and extracts the specified port number or uses the default).

i have no interest in some massive program that can do everything imaginable by at least someone.

---

### Post by Skaperen on 2024-07-15
> **TheFu said:**
> Outbound proxy or inbound reverse proxy?
...
So ... what purpose for a "proxy" do you want?

i want to access a couple of web sites via a VPS i lease for cheap.  it will be on a port i will disallow network access to.  i will access it via SSH to the VPS then to the local-only port or localhost IP address.

i'll look around for "socks proxy".  that may be all i need.

---

### Post by currentshaft on 2024-07-16
> **Skaperen said:**
> no.

i want something that is simple, has basic common options like what port to listen to, is light weight (limits its memory and CPU usage), support HTTPS in some way (probably as a connection relay once it gets the IP address of the named host and extracts the specified port number or uses the default).

i have no interest in some massive program that can do everything imaginable by at least someone.

Privoxy does all that and is not "massive" (whatever that is supposed to mean).

If you just want to forward a remote port, use SSH though.

---

