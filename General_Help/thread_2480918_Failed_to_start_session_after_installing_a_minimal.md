---
title: "Failed to start session after installing a minimal set of LXQt packages"
date: 2022-11-14
forum: General Help
---

### Post by tessawong on 2022-11-14
A few weeks ago I installed Lubuntu 22.10 Kinetic Kudu and found that there were far too many software that I do not need at all such as the following:

a. pulseaudio, alsa audio
b. games
c. LibreOffice
d. GNOME - any package that has the word gnome as part of the name
e. Synaptic
f. video player such as VLC player

Debian offers a ["network install" or "netinst" CD]("https://www.debian.org/CD/netinst/"); however as Ubuntu does not offer one, I downloaded [Ubuntu Server 22.10]("https://releases.ubuntu.com/22.10/ubuntu-22.10-live-server-amd64.iso") and post-installation, at the console *tty1*, I installed the following packages:

```
sudo apt install lxqt-core lightdm gparted openvpn resolvconf libdbus-glib-1-2 bind9-dnsutils numlockx
```

I rebooted my computer and was presented with a graphical login screen.

I input my password and the error message appeared:

```
Failed to start session
```

**Questions**:

1. Why does the distro fail to start a session? Is it because I did not install Xorg server? If yes, what are the names of the packages that pertain to Xorg server that I must install? All the while I was under the impression that Ubuntu Server would automatically install an Xorg server.

2.  What is the name of the package that will install wireless and wired functionality? I wish to avoid using the package called NetworkManager. Is there an alternative to it?

---

### Post by ActionParsnip on 2022-11-14
When you installed lightdm, were you asked to select the display manager?

---

### Post by tessawong on 2022-11-14
> **ActionParsnip said:**
> When you installed lightdm, were you asked to select the display manager?

No. But there was a graphical login screen where I could see my username displayed and an empty box for me to input my password.

That graphical login was *the* display manager, yes?

---

