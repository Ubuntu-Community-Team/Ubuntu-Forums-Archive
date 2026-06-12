---
title: "pianobar Network Error: TLS Handshake Failed"
date: 2012-10-26
forum: General Help
---

### Post by sarloth on 2012-10-26
Hey Everyone,

I am getting the following when trying to use pianobar to listen to pandora with Ubuntu 12.10. I receive this error with my e-mail, shown differently here for privacy.

```
sarloth@behemoth:~$ pianobar
Welcome to pianobar (2011.12.11)! Press ? for a list of commands.
[?] Email: somemail@test.com
[?] Password: 
(i) Login... Network error: TLS handshake failed.

```

Has anyone been able to use it?

Thanks in advance!

---

### Post by sarloth on 2012-10-27
Shamelessly bumping back to the first page :/

---

### Post by jnaranjo on 2012-11-23
I've got the same error.
I installed pianobar successfully on Linux Mint 13 Maya, but it should work just like on ubuntu.
I ran "sudo apt-get install pianobar"

I get the same error after trying to login:
(i) Login... Network error: TLS handshake failed.

---

### Post by Ryupower on 2013-02-13
Try This, change the configuration of pianobar to:
tls_fingerprint = 2D0AFDAFA16F4B5C0A43F3CB1D4752F9535507C0


here's my source: [https://github.com/PromyLOPh/pianobar/issues/328](https://github.com/PromyLOPh/pianobar/issues/328)

---

### Post by Orbital_sFear on 2013-02-18
Wanted to add a note because I had a few extra steps, since I didn't have a valid config file yet.

Here is what I did:
cd
mkdir .config/pianobar
echo "tls_fingerprint = 2D0AFDAFA16F4B5C0A43F3CB1D4752F9535507C0" > .config/pianobar/config

pianobar

---

### Post by jtsberg on 2013-05-17
Hi all,

I'm having the same trouble with TLS handshakes... I'm using the current fingerprint:
tls_fingerprint = 2D0AFDAFA16F4B5C0A43F3CB1D4752F9535507C0
inside my .config/pianobar/config file, but to no avail.

I'm on Ubuntu 12.04.2 LTS (codename: precise)... I don't think it should matter, but my DE is LXDE.

Any ideas?

PS. This is the readout that I get when attempting to use Pianobar:

> jim@jim-X101:~/Desktop$ pianobarWARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-Awi4OJ/pkcs11: No such file or directory
Welcome to pianobar (2011.12.11)! Press ? for a list of commands.
(i) Login... Network error: TLS handshake failed.
jim@jim-X101:~/Desktop$

---

### Post by azeam on 2013-08-02
> **jtsberg said:**
> Hi all,

I'm having the same trouble with TLS handshakes... I'm using the current fingerprint:
tls_fingerprint = 2D0AFDAFA16F4B5C0A43F3CB1D4752F9535507C0
inside my .config/pianobar/config file, but to no avail.

I'm on Ubuntu 12.04.2 LTS (codename: precise)... I don't think it should matter, but my DE is LXDE.

Any ideas?

PS. This is the readout that I get when attempting to use Pianobar:

Update to a more recent version of pianobar. If you are using Pandora One you'll need a different TLS fingerprint as well, see [http://raspberrypiserver.no-ip.org/pianobar_pandora_remote_control.html#pandoraone](http://raspberrypiserver.no-ip.org/pianobar_pandora_remote_control.html#pandoraone)

---

