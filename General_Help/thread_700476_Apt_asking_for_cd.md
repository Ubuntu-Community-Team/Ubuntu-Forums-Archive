---
title: "Apt asking for cd"
date: 2008-02-18
forum: General Help
---

### Post by ketzerei on 2008-02-18
I have a rather... interesting problem. I was trying to install the build-essential package, and now apt and adept are broken. When I try to install something, it keeps giving me this strange error. Here are some screenshots:

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/error3.jpg[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/error2.jpg[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/error1.jpg[/IMG]

It keeps asking for my Kubuntu CD, and I have it, but it says something like "media change" or something and wont accept my cd...

---

### Post by Subliminal Aura on 2008-02-18
Comment out this line from 

/etc/apt/sources.list

# deb cdrom:

---

### Post by SpaceTeddy on 2008-02-18
this should help.. remove the cd source from your sources
[http://ubuntuforums.org/showthread.php?t=700045]("http://ubuntuforums.org/showthread.php?t=700045")

different description, same problem :)

---

### Post by ketzerei on 2008-02-18
Thanks, it works. :D

---

