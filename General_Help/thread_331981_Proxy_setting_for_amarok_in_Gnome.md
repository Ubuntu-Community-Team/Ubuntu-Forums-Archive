---
title: "Proxy setting for amarok in Gnome"
date: 2007-01-05
forum: General Help
---

### Post by tarun86 on 2007-01-05
Hi I have been using Linux for quite a while and liked KDE as environment. I recently switched to Gnome and I kina of liked it. But the problem is that I can figure out from where Amarok takes the proxy settings from. In KDE it is Konqueror but in Gnome I couldnt find any place in Nautilus to put the proxy settings. So please can anyone guide me to solve ths tiny problem.  

thanks :)

---

### Post by tarun86 on 2007-01-05
well seems like this is a big problem ....I myself couldnt find anything on net...I cant live without amarok on Linux so plz any Gnome user here help me !!

---

### Post by Lord Illidan on 2007-01-05
> **tarun86 said:**
> Hi I have been using Linux for quite a while and liked KDE as environment. I recently switched to Gnome and I kina of liked it. But the problem is that I can figure out from where Amarok takes the proxy settings from. In KDE it is Konqueror but in Gnome I couldnt find any place in Nautilus to put the proxy settings. So please can anyone guide me to solve ths tiny problem.  

thanks :)

Can you explain more what you need with proxy settings and Amarok?

P.S, you can run Konqueror in Gnome, u know..unless you didn't delete KDE from your system.

---

### Post by tarun86 on 2007-01-09
got it !!
just set the proxies in the file** kioslave**  !! you dont need to install the KDE or Konqueror for this !!

---

### Post by tarun86 on 2007-01-09
> **Lord Illidan said:**
> Can you explain more what you need with proxy settings and Amarok?

P.S, you can run Konqueror in Gnome, u know..unless you didn't delete KDE from your system.

By proxy settings I meant where does the Wiki and the Lyrics tab takes their proxy from as behind a proxy server. In KDE we set those in Konqueror and it works fine for amarok too but in Gnome I didnt wanted to install KDE components that installs the KDE desktop!! So didnt wanted to go for Konqueror ;)

---

### Post by jornero on 2007-01-17
Hi

I had the same problem and my solution was the following:

1) Clean all proxy settings in amarok's configuration page
2) Edit ~/.kde/share/config/kioslaverc and add the following section and settings

> [Proxy Settings][$i]
ProxyType=1
httpProxy=http://username:password@proxyserver:port/
httpsProxy=http://username:password@proxyserver:port/
ftpProxy=http://username:password@proxyserver:port/

3) Save the file and restart amarok!

---

### Post by hearty on 2007-10-16
It reported this!
Lyrics could not be retrieved because the server was not reachable.

---

### Post by franganghi on 2008-05-09
> **jornero said:**
> Hi

I had the same problem and my solution was the following:

1) Clean all proxy settings in amarok's configuration page
2) Edit ~/.kde/share/config/kioslaverc and add the following section and settings



3) Save the file and restart amarok!

It worked for me.

Thanks

---

### Post by Adam Jones on 2008-06-23
> **jornero said:**
> Hi

I had the same problem and my solution was the following:

1) Clean all proxy settings in amarok's configuration page
2) Edit ~/.kde/share/config/kioslaverc and add the following section and settings



3) Save the file and restart amarok!

Thanks ! This worked for me.

---

