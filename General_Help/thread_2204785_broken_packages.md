---
title: "broken packages"
date: 2014-02-10
forum: General Help
---

### Post by Jumbo95 on 2014-02-10
Trying to install kali-Linux tools in Ubuntu 13.10. I have got them as far as showing on left hand side of synaptic but when
I try to install [metasploit 2 & armitage on the right I get a broken package message. Any suggestions please

---

### Post by Bashing-om on 2014-02-10
kenw1931; Hi !

Let us have a closer look at what the package manager says:
Post back the output - between code tags - of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Additional advise pending !

[INDENT]the checks and balances
[INDENT][INDENT]to keep everybody happy
[/INDENT][/INDENT][/INDENT]

---

### Post by Jumbo95 on 2014-02-12
Hi Bashing-OM Thanks for your reply. Sorry about the delay I don't seem to be around at thhe same time as you
however let's cut to the chase. I initially started out with ubuntu v 12. 04 but ran into problems with the apps
fading out as I tried to pen them in Terminal, so I switched to v 13.10 and that was worse and crashed. I have
been trying to follow " Exploiterz" as a guide and have used both program numerical refs and distros. I have
now gone back to ubuntu 12.04.3 and have tried debian and other PPI's but all I get now as I try to install via
synaptic is a message saying please fix broken packages. This may be just a hiccup but I have tried to get around it by various commands and also using aptitude commands, no success and at times couldn't even
load  the ppi sources. Nothing special comes up on update or upgrade. Is wagungs contaminated? it has every
appearance of it. Suggestions please.

---

### Post by Bucky Ball on 2014-02-12
Best to run these three commands:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

... and post back and and all errors.

---

### Post by Jumbo95 on 2014-02-12
Hi Bucky Ball, if you read my recent reply you will see I've been around the houses on this one, the basics
which you suggest were the first things I tried

---

### Post by Bashing-om on 2014-02-12
kenw1931; Hey ;

We still have nothing concrete to look at:
What results form terminal commands:
```

sudo apt-get -f install
sudo dpkg --configure -a

```
[INDENT]show a target
[INDENT][INDENT]and we will shoot
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-02-12
I've read 'em. Have you done those three in a row? The 'dist-upgrade' one is what I'm after, but should be done after the other two. Just checkin'. ;)

Ninja-ed by bashing om: If there was a problem with one of the commands I gave would have asked you to try the commands, or one of them, bashing is suggesting.

---

### Post by Jumbo95 on 2014-02-13
Sorry to bucky-ball andbashing-om the error messages are now so various that I'm going to jack. Last one said 
couldn't read line 57 of sources list previous ones were fix broken packages, failure to install all packages fromPPA's
errors on synaptic de da de da.Regards using "sudo apt-get -f install"response was 0 updated.0newly installed 0 removed, response to "sudo dpkg --configure -a"was- no such command

---

### Post by Frogs Hair on 2014-02-13
Post the output of sudo apt-get update in code tags using the # symbol on the reply box tools .

---

### Post by ibjsb4 on 2014-02-13
Also please post the output of:

```
cat -n /etc/apt/sources.list
```

---

### Post by Bucky Ball on 2014-02-13
> couldn't read line 57 of sources list previous ones were fix broken packages, failure to install all packages fromPPA's

Whatever PPA(s) that's talking about is possibly your problem and either needs to be disabled or the line fixed. Run whatever command produced it and see if it identifies a PPA name.

---

