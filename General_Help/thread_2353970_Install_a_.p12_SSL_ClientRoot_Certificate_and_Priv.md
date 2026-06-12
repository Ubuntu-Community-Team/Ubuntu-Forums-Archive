---
title: "Install a .p12 SSL Client/Root Certificate and Private Key on 16.04?"
date: 2017-02-26
forum: General Help
---

### Post by redpenguinmail on 2017-02-26
I am attempting to watch an HLS Video stream from a server that requires I send a Client Certificate and Private Key.

I have that info in a .p12 file that has the Client and Root Certificate. It also has the encrypted private key.

On Windows I was able to simply import the entire .p12 file and the stream works with Chrome, ffmpeg, and Kodi but not VLC and others.

Anyway I have followed instructions on supposedly converting the Client Certificate to .crt, placing it in /etc/ssl/certs and the key to a .key, placing it into /etc/ssl/private.

I can't get Chrome, Kodi, or ffmpeg to use the SSL info and they just error out.

---

