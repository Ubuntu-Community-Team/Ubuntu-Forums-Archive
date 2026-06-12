---
title: "Vidalia Can't Start Or Connect To Tor"
date: 2015-06-22
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-06-22
Hello,

I want to run a Tor relay, so I installed Vidalia from Synaptic Package Manager, since it is no longer included in the Tor Browser Bundle.

Vidalia can neither start Tor, nor connect to the running Tor process from the Tor Browser Bundle.

Any help appreciated.

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-06-22
Not uncommon. I gave up on vadalia.
[B][SelekTOR]("http://www.dazzleships.net/?page_id=71")  is an open source Java-based GUI front-end for the Tor Client which has  a few advantages over Vidalia (the official Tor GUI), such as:

see here [http://www.webupd8.org/2014/09/selektor-tor-gui-with-country-exit-node.html](http://www.webupd8.org/2014/09/selektor-tor-gui-with-country-exit-node.html)
Cheers
[/B]

---

### Post by oscar-tiderman on 2015-06-23
Have you checked your logs? What are they saying? Most likely you are just missing a folder, I do not remember which one it is I usually have to create, your logs should give you a hint. It is also picky about permissions, too permissive will prevent it from running.

---

### Post by coljohnhannibalsmith on 2015-06-24
> **oscar-tiderman said:**
> Have you checked your logs? What are they saying? Most likely you are just missing a folder, I do not remember which one it is I usually have to create, your logs should give you a hint. It is also picky about permissions, too permissive will prevent it from running.

```
Jun 24 10:02:32.060 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jun 24 10:02:32.068 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Jun 24 10:02:32.068 [Notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
Jun 24 10:02:32.068 [Notice] Opening OR listener on 0.0.0.0:9001
Jun 24 10:02:32.068 [Notice] Opening Directory listener on 0.0.0.0:9030
Jun 24 10:02:32.069 [Notice] Opening Socks listener on 127.0.0.1:9050
Jun 24 10:02:32.069 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 24 10:02:32.069 [Notice] Opening Control listener on 127.0.0.1:9051
Jun 24 10:02:32.069 [Notice] Closing partially-constructed listener OR listener on 0.0.0.0:9001
Jun 24 10:02:32.069 [Notice] Closing partially-constructed listener Directory listener on 0.0.0.0:9030
Jun 24 10:02:32.069 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Jun 24 10:02:32.069 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 24 10:02:32.069 [Error] Reading config failed--see warnings above.
```

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-06-24
> **coljohnhannibalsmith said:**
> ```
Jun 24 10:02:32.060 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Jun 24 10:02:32.068 [Notice] Your ContactInfo config option is not set. Please consider setting it, so we can contact you if your server is misconfigured or something else goes wrong.
Jun 24 10:02:32.068 [Notice] Initialized libevent version 2.0.16-stable using method epoll. Good.
Jun 24 10:02:32.068 [Notice] Opening OR listener on 0.0.0.0:9001
Jun 24 10:02:32.068 [Notice] Opening Directory listener on 0.0.0.0:9030
Jun 24 10:02:32.069 [Notice] Opening Socks listener on 127.0.0.1:9050
Jun 24 10:02:32.069 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 24 10:02:32.069 [Notice] Opening Control listener on 127.0.0.1:9051
Jun 24 10:02:32.069 [Notice] Closing partially-constructed listener OR listener on 0.0.0.0:9001
Jun 24 10:02:32.069 [Notice] Closing partially-constructed listener Directory listener on 0.0.0.0:9030
Jun 24 10:02:32.069 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Jun 24 10:02:32.069 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 24 10:02:32.069 [Error] Reading config failed--see warnings above.
```

Thanks, Hannibal
I really think you would like Selecktor, But different Strokes.
To fix your error run command below and then restart vidalia.
```
sudo killall tor
```
Again restart tor
Just a heads up Vidalia will dropped in 15.10 and Newer [https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/1431917](https://bugs.launchpad.net/ubuntu/+source/vidalia/+bug/1431917)

---

### Post by coljohnhannibalsmith on 2015-06-24
> **runrickus said:**
> Not uncommon. I gave up on vadalia.
[B][SelekTOR]("http://www.dazzleships.net/?page_id=71")  is an open source Java-based GUI front-end for the Tor Client which has  a few advantages over Vidalia (the official Tor GUI), such as:

see here [http://www.webupd8.org/2014/09/selektor-tor-gui-with-country-exit-node.html](http://www.webupd8.org/2014/09/selektor-tor-gui-with-country-exit-node.html)
Cheers
[/B]

selektor: Dependency is not satisfiable: (tor >=0.2.4.20).  I only have Tor 0.2.2.35-1 available in the repository.  I'm running Ubuntu 12.04 Precise Pangolin.

Also, Synaptic Package Manager does not show an option to install OpenJRE 1.7, however it could be listed under another name.

Thanks, Hannibal

---

### Post by QDR06VV9 on 2015-06-24
> **coljohnhannibalsmith said:**
> selektor: Dependency is not satisfiable: (tor >=0.2.4.20).  I only have Tor 0.2.2.35-1 available in the repository.  I'm running Ubuntu 12.04 Precise Pangolin.

Also, Synaptic Package Manager does not show an option to install OpenJRE 1.7, however it could be listed under another name.

Thanks, Hannibal
Try this
```
sudo apt-get install openjdk-7-jdk openjdk-7-doc openjdk-7-jre-lib
```
There also is a PPA for tor [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)
Start where it says You need to add the following entry in /etc/apt/sources.list

---

### Post by coljohnhannibalsmith on 2015-06-24
> **runrickus said:**
> Try this
```
sudo apt-get install openjdk-7-jdk openjdk-7-doc openjdk-7-jre-lib
```
There also is a PPA for tor [https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)
Start where it says You need to add the following entry in /etc/apt/sources.list

I've managed to install OpenJRE 7, and I am now trying to install SelekTor from the .deb file.  The Throbber is running in the background, but the progress bar hangs, and Conky shows no network activity.  BTW, I agree that Selektor is a better app, but I am working to solve both problems, so I can get my Tor relay up.  I followed the original installation instructions you linked to, and updated Tor from the Terminal with apt-get, but Synaptic still shows only the older version.  Also, Selektor is not available from Synaptic, so I must use the .deb or the Tarball.  I'm going to try the Tarball now.

Thanks Hannibal

---

### Post by QDR06VV9 on 2015-06-24
It will take a little  time to load just as vidalia did also.
I have found through the years that the tor software in the normal repos is very often outdated.
Been using their PPA without a hitch for years now.
Let us know how you make out.
Regards

---

### Post by coljohnhannibalsmith on 2015-06-24
> **runrickus said:**
> It will take a little  time to load just as vidalia did also.
I have found through the years that the tor software in the normal repos is very often outdated.
Been using their PPA without a hitch for years now.
Let us know how you make out.
Regards

I've finally managed to get Selektor installed and working, but with Selektor running Ubuntu Forums kicks me out, saying I need administrator approval when I try to post.  Also, Flagfox states that it needs the ability to lookup IP addresses by DNS to work.  Selektor is set to proxy all traffic.  I had to restart Firefox to enabled this mode.  Is there another setting I can use when using Selektor to reenable Flagfox or that I can use when not using Selektor to reenable Flagfox functionality?  BTW, I was able to restore Conky network traffic visibility by changing from wlan0 to eth0.  I am currently running RJ45 from the Satelite modem instead of running from a wireless router.  Apparently Conky needs this feature reset in the .conkyrc file, whenever I change from wireless to hardwire.  I wish I could just press a button for this change.

Thanks, Hannibal

Update: When I closed Selektor Flagfox came back.  Also, Vidalia seems to be running now.

---

### Post by QDR06VV9 on 2015-06-24
Becareful with extensions while you use tor.
> **Why does Flagfox care if I'm using a proxy?**
Flagfox needs [domain name service (DNS)]("http://en.wikipedia.org/wiki/Domain_Name_System") access to lookup the [IP address]("http://en.wikipedia.org/wiki/Ip_address")  of the current site.  Normally, you're already at the site and know its  IP, and thus we can just look in the local DNS cache used by Firefox.   If you're using a SOCKS [proxy]("http://en.wikipedia.org/wiki/Proxy_server")  with remote DNS enabled then this isn't possible, as no DNS lookups  will be in your cache.  Thus, when you're using a proxy configured for  remote DNS Flagfox can't find the IP and doesn't know where you are.
 
just use tor browser, and still have the relay running for tor.
[http://www.webupd8.org/2013/12/tor-browser-bundle-ubuntu-ppa.html](http://www.webupd8.org/2013/12/tor-browser-bundle-ubuntu-ppa.html)
Or simply change firefox to not proxy.( in settings /advanced/network/settings/noproxy
The reason vidalia is working again is because you quit or closed selektor.
The Error in your earlier post
> Jun 24 10:02:32.069 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Tells you tor was already running and the command I gave you eariler
```
sudo killall tor 
```
Fixed that, Just RESTART Vidalia that is the way Vidalia is designed to to work.
Glad you got it sorted.
Regards

---

