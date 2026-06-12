---
title: "Katoolin keyserver timed out"
date: 2017-03-13
forum: General Help
---

### Post by totpoter on 2017-03-13
So I'm trying to install katoolin which I have done before without problem, but this time I am unable to connect to the keyserver for some reason. This is what happens when I try to get into the "Add kali linux repositories" section (1).```
Executing: /tmp/apt-key-gpghome.DTfiFtMCkM/gpg.1.sh --keyserver pgp.mit.edu --recv-keys ED444FF07D8D0BF6
gpg: requesting key 7D8D0BF6 from hkp server pgp.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


```

I googled around to try and fix this, and saw that to fix this problem I could replace the keyserver line in the katoolin.py file with a working one so I tried that with the ubuntu keyserver but when I tried to edit it with ```
sudo gedit /home/username/katoolin/katoolin.py
``` and replaced the lines with ```
"apt-key adv --keyserver keyserver.ubuntu.com:80 --recv-keys 7F0CEB10"
``` instead of the pgp.mit.edu one, I am returned by this error ```
** (gedit:8133): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

```

Python is updated and working, so is git and I was logged in as root when doing all of this (and as the regular user aswell). I tried all solutions I could find but none of them are working. The best thing would be if the keyserver error could be fixed without replacing the lines but getting another working keyserver would fix the problem aswell. As said this happens when i enter 1 to add kali repos.

---

