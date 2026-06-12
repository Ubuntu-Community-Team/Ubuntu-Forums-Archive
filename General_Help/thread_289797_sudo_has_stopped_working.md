---
title: "sudo has stopped working"
date: 2006-10-31
forum: General Help
---

### Post by timhaughton on 2006-10-31
Hi, I have a remote Edgy server (over 100 miles away) that I communicate with via ssh and I'm having problems. sudo has spontaneously stopped working. Any command I try and sudo fails silently. sudo -i fails silently.

I tried another shell I happened to have open to it on another machine and it gave me a pam authentication message saying conversation error or some such. This was working fine until about 30 minutes ago.

Now, as I said, I'm over 100 miles away, and I can't sudo reboot, so what can I do? Needless to say if I can't rely on a remote server to at least stay in a state where I can administrate it, it has to go.

Any help is appreciated.

Cheers,

Tim

---

### Post by timhaughton on 2006-10-31
Update: I figured out what I did. Instead of adding myself to a new developers group, I actually wiped out all of my other groups (including admin). So no sudoing for me today :(

Tim

---

### Post by zek725 on 2006-11-02
```
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
```

sudo does not work now! I'm in Xubuntu Edgy. I've installed smb4k and with it came Konqueror and other stuff. Help!

PROBLEM SOLVED. > [http://ubuntuforums.org/showpost.php?p=1706595](http://ubuntuforums.org/showpost.php?p=1706595)
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

