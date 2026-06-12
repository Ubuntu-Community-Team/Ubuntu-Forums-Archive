---
title: "apt-get update error"
date: 2008-05-09
forum: General Help
---

### Post by mardawi on 2008-05-09
when running apt-get update in the terminal it fetches the repos alright but at the end it displays:```

Reading package lists... Done
W: GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://jo.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

Can someone please explain to me what the error is and how to fix it.

Thanks!

---

### Post by tamoneya on 2008-05-09
seems like the encryption keys got messed up.  Anyways just solve it by doing as it says:```
sudo apt-get update
```

---

### Post by mardawi on 2008-05-09
i was doing apt-get update when i got the error

---

### Post by tamoneya on 2008-05-09
sorry i missed that part.  What happens with this```
dpkg --configure -a
```

---

### Post by mardawi on 2008-05-09
> **tamoneya said:**
> sorry i missed that part.  What happens with this```
dpkg --configure -a
```

didn't work, still same problem

---

### Post by tamoneya on 2008-05-09
Okay well it seems as if you wont be able to do anything with apt-get until you get a new version of the encryption key.  I have never done this for the ubuntu main repositories but I pulled this command from the cinelerra site.  I think it should work but I would give this thread an hour or so to let other users read it and make sure I haven't made a serious error.

This is the original code
```
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

I think this should work:
```
wget -q http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by mardawi on 2008-05-09
it says:
```
gpg: no valid OpenPGP data found.
```

---

### Post by tamoneya on 2008-05-09
hmm that should definately be the correct data.  Im not really sure why this wasnt correctly recognized.  Looking at the page in opera shows what looks like a key to me.

[http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)

Ive never seen this problem really so you may just have to wait for someone to come along with an answer.  In the mean time I would go into synaptic and try changing my mirror.  That may result in a key change and ubuntu will get it automatically.

---

### Post by tamoneya on 2008-05-09
it seems as if you are not alone in your problems.  This means that it probably is a problem on the server side and therefore it should figure itself out shortly.

[http://ubuntuforums.org/showthread.php?p=4923380](http://ubuntuforums.org/showthread.php?p=4923380)

---

### Post by mardawi on 2008-05-09
Ok.

Thanks a lot for all your help!

---

### Post by letrappe on 2008-05-16
> **tamoneya said:**
>  it should figure itself out shortly.

does Ubuntu fix itself autonomously now?  lol!:lolflag:

---

### Post by walter_j on 2008-12-19
I still get this error after trying to update ubuntu server 8.04. Whats wrong?

---

### Post by walter_j on 2008-12-21
> **walter_j said:**
> I still get this error after trying to update ubuntu server 8.04. Whats wrong?

I found my error. I had the wrong gateway ip in /etc/resolv.conf

no apt-get errors now

walter

---

