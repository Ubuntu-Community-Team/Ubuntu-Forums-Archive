---
title: "automatic update?"
date: 2005-07-18
forum: General Help
---

### Post by The Rev on 2005-07-18
Hi everybody!

New at this forum and would like to ask a question  :razz: 
When I try to automaticaly update Ubuntu 5.04 I read this message:

[http://nl.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:](http://nl.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:) Fout bij het lezen van de server - read (104 Verbinding gesloten door communicatiepartner) [IP: 82.211.81.138 80]

In English it is: ... mistake in reading the server -read (104connection closed bij communicationpartner)

Does anybody know how I can solve this??

Thanks, The Rev

---

### Post by angkor on 2005-07-18
Hmm, that's pretty....duister ;)

Could you post your /etc/apt/sources.list? Maybe there's something funny in there.

---

### Post by The Rev on 2005-07-19
This is what it:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by angkor on 2005-07-19
Nothing wrong with that. You could try opening up (uncommenting) the universe repos, but I connect to the exact same repos as you do.  :neutral: Are you behind a firewall or proxy or something?

---

