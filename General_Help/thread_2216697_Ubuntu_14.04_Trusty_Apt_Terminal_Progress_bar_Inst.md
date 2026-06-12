---
title: "Ubuntu 14.04 Trusty Apt Terminal Progress bar Install Permission Denied"
date: 2014-04-13
forum: General Help
---

### Post by Redalien0304 on 2014-04-13
Trying Install Ubuntu Trusty Apt Terminal Progess Bar from this Links
[http://www.omgubuntu.co.uk/2014/04/how-to-enable-apt-terminal-progress-bar](http://www.omgubuntu.co.uk/2014/04/how-to-enable-apt-terminal-progress-bar)

i have rtried without sudo & with sudo "sudo echo 'Dpkg::Progress-Fancy "1";' > /etc/apt/apt.conf.d/99progressbar"
I am getting this "bash: /etc/apt/apt.conf.d/99progressbar: Permission denied"
Any help is Appreciated Thanks.

---

### Post by Impavidus on 2014-04-13
Using sudo causes echo to be run with root privileges, but not the output redirect. Try```
echo stuff | sudo tee /etc/path/filename
```

---

### Post by oldos2er on 2014-04-13
You could also run ```
sudo -i

echo 'Dpkg:Progress-Fancy "1";' > /etc/apt/apt.conf.d/99progressbar

exit
```

---

