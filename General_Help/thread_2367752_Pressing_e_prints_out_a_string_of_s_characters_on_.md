---
title: "Pressing e prints out a string of s characters on Ubuntu 16.04 terminal"
date: 2017-08-03
forum: General Help
---

### Post by nojandals on 2017-08-03
I've setup an ubuntu 16.04 minimal virtual machine on virtualbox which I've been using for around 2 months now. I logged in today via ssh and found that when I pressed the 'e' key on my keyboard, a continuous input of 's' characters would flood the terminal without end. After cancelling out of this via ctrl+c, I checked my aliases thinking i added something silly but found nothing out of the ordinary. Inputting the uppercase 'E' in the terminal does not trigger this behavior, nor does typing lowercase 'e' in nano or vim. I found that by tab auto-completing commands such as 'docker' is also fine. I cloned the virtual machine and found that the behavior was replicated on the cloned machine. Very strange and frustrating. Any help much appreciated.
 [ATTACH=CONFIG]276240[/ATTACH]

---

### Post by HermanAB on 2017-08-03
Well, this is probably not due to smoking your corn flakes...

I have in the distant past seen bugs like this with both X and with Xorg.  My guess was that something, somewhere, got corrupted by a passing neutron.  I fixed it by redefining the errant key using xev and xmodmap back to itself.  I have no idea whether a similar trick will help you.

---

### Post by steeldriver on 2017-08-03
One possibility might be something in the readline initialization file(s) - either /root/.inputrc (if it only affects root) or /etc/inputrc if it affects accounts globally

If the latter 

```

diff -s /usr/share/readline/inputrc /etc/inputrc

```

might be helpful

---

### Post by nojandals on 2017-08-03
Hello Thanks for your reply. I've not used those before but will have a look.

---

### Post by nojandals on 2017-08-03
Thanks so much for your help this solved my problem. I copied and pasted a command into my inputrc file to make bash case-insensitive which was causing the issue. I had to edit it again from within vim explorer as I could not copy or paste any command with an 'e' in it - also could not tab auto-complete from /etc/inputrc. 
[ATTACH=CONFIG]276247[/ATTACH]

---

