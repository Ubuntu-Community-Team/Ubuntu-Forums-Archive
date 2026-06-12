---
title: "VNC (or other remote access) for multiple users"
date: 2022-02-23
forum: General Help
---

### Post by rkorson on 2022-02-23
[SIZE=3][FONT=arial]Dear Friends,

Thank you in advance for your help. I am setting up my HTPC with [/FONT][/SIZE][FONT=arial][SIZE=3][COLOR=#111111]Ubuntu 20.04.3 LTS. I would like to be able to log-in to the desktop environment with different users at the same time. For example I would like to be able to leave one user logged in running Kodi and be able to log-in with another user without disrupting the first... in essence terminal services on a very limited scale.  This will let me use the computer while letting my family still enjoy the HTPC, my box is more then capable of this but I don't know how on Ubuntu. I have done this on CentOS but looking around on the web has lead me to a lot of our of date tutorials.   

What would be the cleanest way to accomplish this?  Thanks!  [/COLOR][/SIZE][/FONT]

---

### Post by ActionParsnip on 2022-02-23
What do you want to do on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by rkorson on 2022-02-23
I was thinking a whole desktop session, file browser, media players, and web.  While I think I need the whole DE you make a fair point.  What do you have in mind?

---

### Post by ActionParsnip on 2022-02-23
> **rkorson said:**
> I was thinking a whole desktop session, file browser, media players, and web.  While I think I need the whole DE you make a fair point.  What do you have in mind?

What OS is the client system running please? You can manage files remotely like a file share. You can mount SFTP using any Linux based OS and even MacOS. If it's Windows then Samba can even be setup to accommodate the shortcomings of the Windows file manager.

Media players is a bit vague. If you want to play the remote music of of the remote system then VLC has a great Web interface and you can evn control it using your phone. If you use Spotify then you can use another Spotify instance logged into the same account to remotely control Spotify on another system.

If you setup an SSH tunnel to the remote system, you can set a proxy in the browser to use the tunnel and your traffic will flow down the tunnel and appear to be coming from the remote system. Dead easy stuff

---

### Post by rkorson on 2022-02-24
Thanks! My client would be MacOS for the most part. I would like the full interface so that I can manage add and manage media with makeMKV for by KODI on the other user.  Thanks!

---

### Post by ActionParsnip on 2022-02-24
MacOS can mount SFTP and you can move files and update files as you need.

---

### Post by ActionParsnip on 2022-02-24
If you connect with
```

ssh -X username@server

```
You can run makemkv in the terminal and it will run on the server but be visible as an app on the Mac desktop.

There is also makemkv which can run on MacOS so you can mount the remote file system and manipulate the files over the network
[https://www.makemkv.com/download/](https://www.makemkv.com/download/)

---

