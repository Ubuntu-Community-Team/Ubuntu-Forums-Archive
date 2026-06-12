---
title: "Trying to install Kaffeine"
date: 2006-07-31
forum: General Help
---

### Post by geovino on 2006-07-31
I was trying to install Kaffeine and I got these error messages:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine-xine_0.7.1-1.3ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine-xine_0.7.1-1.3ubuntu10_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine_0.7.1-1.3ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kaffeine/kaffeine_0.7.1-1.3ubuntu10_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


Do I have to wait until later on to try again or is there something I can configure to get it to install. Any clues? I'm using ver. 6.06. Thanks

---

### Post by xXx 0wn3d xXx on 2006-07-31
You need a new sources.list. Look [ here. ](http://www.psychocats.net/ubuntu/sources.php) I can download the file so the repositories are not down.

---

### Post by Jucato on 2006-07-31
I'm presuming you are using Ubuntu? Because Kubuntu has Kaffeine installed by default.

Are you trying to download the packages separately? Kaffeine is available in the main Ubuntu repositories so it's just as easy as

```
sudo aptitude update
sudo aptitude install kaffeine kaffeine-xine
```

If you are using Ubuntu, is there any reason that the default movie player (Totem) doesn't work for you?

---

### Post by geovino on 2006-07-31
I have Totem, but I got some error messages and I thought I would try something else. What do I have to do to get Totem to work properly?

---

### Post by Jucato on 2006-07-31
That depends. What were you trying to play, and what error message did you receive?

---

### Post by geovino on 2006-08-01
I got it working, I don't think I got the Win32 Codecs but Kaffeine is working. Why are these important files for Video playing left out of the initial Ubuntu install? These should all be included because most preople will want to play dvds. These are the things that need to be added in new versions.

---

### Post by Jucato on 2006-08-01
It's because of Ubuntu's philosophy, it's commitment to Free and Open Source Software. This means that it doesn't include anything non-free "out of the box" (on default installation).

Btw, you might also need to install a package called *libxine-extracodecs* from the multiverse repository (deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse) for MP3 playback and some other non-free multimedia codecs.

---

