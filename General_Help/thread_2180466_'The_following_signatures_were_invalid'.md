---
title: "'The following signatures were invalid'"
date: 2013-10-13
forum: General Help
---

### Post by craig_cheek on 2013-10-13
I keep getting the message about untrusted packages when using the ubuntu software centre.
When I run the command sudo apt*get update I get the following.


Reading package lists... Done
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key

any ideas what I can do to fix this please.

regards

Craig

---

### Post by ibjsb4 on 2013-10-13
[Open a termina]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal")l and enter (one line at a time):

```
sudo apt-get clean
sudo cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

Found that [here]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9").

And welcome to the forums :)

---

