---
title: "What is the current version of Flatpak for Ubuntu 22.04LTS?"
date: 2023-02-15
forum: General Help
---

### Post by SpaceManJack on 2023-02-15
When I enter the command ```
flatpak --version
```  I get "Flatpak 1.12.7" is this the current version of Flatpak?

I just did a clean install of Ubuntu 22.04 and I'm trying to install TOR using the Flatpak method, I'm going off of this website [https://itsfoss.com/install-tar-browser-linux/](https://itsfoss.com/install-tar-browser-linux/)

Thanks.

---

### Post by monkeybrain20122 on 2023-02-15
Yes, 1.12.7 is the version I have.
 

BTW why make life unnecessarily complicated? You can just download Tor from [https://www.torproject.org/download/](https://www.torproject.org/download/)

Click to start.

---

### Post by SpaceManJack on 2023-02-17
> **monkeybrain20122 said:**
> Yes, 1.12.7 is the version I have.
 

BTW why make life unnecessarily complicated? You can just download Tor from [https://www.torproject.org/download/](https://www.torproject.org/download/)

Click to start.

Actually I couldn't download TOR from Flatpak. There's been a problem with the TOR launcher since last year, here check this out, this is how I got TOR to work, go here and read my edit that says I finally got TOR to work. I'm being serious there's been a widespread problem with the TOR launcher for months now. Thankfully someone on Reddit helped me.
[https://askubuntu.com/questions/1444750/im-having-trouble-installing-tor-browser-bundle-on-ubuntu-22-04-please-help](https://askubuntu.com/questions/1444750/im-having-trouble-installing-tor-browser-bundle-on-ubuntu-22-04-please-help)

---

### Post by #&amp;thj^% on 2023-02-17
Actually it's not complicated at all, but sorry to hear about your woe's
```
flatpak list | grep torbrowser && flatpak remotes && flatpak list --columns=application,origin
Tor Browser Launcher	com.github.micahflee.torbrowser-launcher	0.3.6	stable	system
Name    Options
flathub system
Application ID                                            Origin
com.github.micahflee.torbrowser-launcher                  flathub
org.freedesktop.Platform.GL.default                       flathub
org.freedesktop.Platform.GL.default                       flathub
org.freedesktop.Platform.GL.nvidia-525-89-02              flathub
org.freedesktop.Platform.openh264                         flathub
org.kde.Platform                                          flathub



```
I've not seen a 'Faltpak request for help' from you, if there is link it here.

---

### Post by SpaceManJack on 2023-02-20
> **1fallen said:**
> Actually it's not complicated at all, but sorry to hear about your woe's
```
flatpak list | grep torbrowser && flatpak remotes && flatpak list --columns=application,origin
Tor Browser Launcher    com.github.micahflee.torbrowser-launcher    0.3.6    stable    system
Name    Options
flathub system
Application ID                                            Origin
com.github.micahflee.torbrowser-launcher                  flathub
org.freedesktop.Platform.GL.default                       flathub
org.freedesktop.Platform.GL.default                       flathub
org.freedesktop.Platform.GL.nvidia-525-89-02              flathub
org.freedesktop.Platform.openh264                         flathub
org.kde.Platform                                          flathub



```
I've not seen a 'Faltpak request for help' from you, if there is link it here.

Am i supposed to copy and paste all of that code into the terminal? 

Please go here and read this, [https://askubuntu.com/questions/1444750/im-having-trouble-installing-tor-browser-bundle-on-ubuntu-22-04-please-help](https://askubuntu.com/questions/1444750/im-having-trouble-installing-tor-browser-bundle-on-ubuntu-22-04-please-help) read the whole thing now because you'll see how I figured out how to finally successfully install TOR. I was having trouble trying to install  TOR back in December of 2022, and it would seem they still haven't fixed the TOR launcher. There is a widespread problem with the TOR launcher. If you just google "Ubuntu TOR 404 error" you'll see what I'm talking about. For instance if I install the TOR launcher from the Ubuntu Software store it will not work at all it'll give me a "download error: 404", the TOR launcher is broken.

---

### Post by #&amp;thj^% on 2023-02-20
Your not supposed to anything...I have no problems with torbrowser as shown in my post.
From Debain unstable to Bullseye to Ubuntu no problems.
I'm not inspired to jump through hoops or chase links to help you, I'm not being snarky here.
Your after a system wide Tor, and I'm not a fan of that, I just run torbrowser and I'm happy.
> A Tor system that makes all connections go through tor. It has a very strict firewall that does not allow other connections to go out.

The problem with a &#8216;whole OS solution&#8217; is that some programs may not respect the setting and skip tor.

For apt, please read Can I use APT over Tor? | Tor Project | Support 3 and there are also repositories that have onion addresses, like Debian.

You can also use torsocks to run programs from the terminal, although they could potentially leak your IP, for example in metadata, even when transmitted through tor.
You have Tor going now so I'll leave it at that.
If I need privacy and or proxy services I use a very strict VPN
Tor project itself gives directions on how to do what are known as "transparent proxies," though they highly discourage the practice due to packet leaks. 
It sounds like you need to file a bug against TorBrowser Launcher.
I Still have no problems with Ubuntu Lunar.....
EDIT: I would be more than happy to try and help you here in UF if your still in need, but you will have to create a Help Request in the forums.
```
apt policy torbrowser-launcher
torbrowser-launcher:
  Installed: (none)
  Candidate: 0.3.6-2
  Version table:
     0.3.6-2 500
        500 https://deb.debian.org/debian unstable/contrib amd64 Packages


```
```
flatpak list | grep torbrowser-launcher
Tor Browser Launcher	com.github.micahflee.torbrowser-launcher	0.3.6	stable	system

```

---

### Post by monkeybrain20122 on 2023-02-22
BTW you can also open an instance of Tor in the[ brave-browser]("https://brave.com/"), use the Tor tab.

---

