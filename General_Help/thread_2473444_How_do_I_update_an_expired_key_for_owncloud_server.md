---
title: "How do I update an expired key for owncloud server?"
date: 2022-04-04
forum: General Help
---

### Post by scottbomb on 2022-04-04
I'm using Kubuntu 20.04. Running "apt update" on my owncloud server generates this:

Err:6 [http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_20.04](http://download.opensuse.org/repositories/isv:/ownCloud:/server:/10/Ubuntu_20.04)  InRelease
  The following signatures were invalid: EXPKEYSIG 4ABE1AC7557BEFF9 isv:ownCloud OBS Project <isv:ownCloud@build.opensuse.org>

I ran sudo apt-key list | grep "expired: "

and I see this key expired a couple of days ago:

pub   rsa2048 2016-09-25 [SC] [expired: 2022-04-02]

How exactly do I replace it with a new key? Searching online leads me to resolved bugs, posts from 6 years ago, etc.

---

### Post by &amp;KyT$0P# on 2022-04-04
Where did you get that key?  Try re-downloading it from the same URL you originally got it from, in case the repo owner has replaced it with a non-expired key.

---

### Post by #&amp;thj^% on 2022-04-04
I had played with this on 16.04, now I wonder if this still works: and they changed repos. [https://download.opensuse.org/repositories/home:/strycore/Debian_10/](https://download.opensuse.org/repositories/home:/strycore/Debian_10/)
```
wget https://download.opensuse.org/repositories/home:/strycore/Debian_10//Release.key -O - | sudo apt-key add -    
```
and 
```
sudo apt update
```
Crossed fingers
EDIT:>>Yep still works:
```
HTTP request sent, awaiting response... 200 OK
Length: 1101 (1.1K)
Saving to: &#8216;STDOUT&#8217;

-                          0%[                                   ]       0  --.-KB/s               -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.5 (GNU/Linux)

mQENBFRZVvQBCAC6o95XEzZiupu57b6iGh8dR3Zt0itwKxOWlBDwGoibcvsQgC0N
ZqVaHf/9MSC9E7JxJFEDE6Qa2w8+OWFlUsjJsTSFQ7IVyawueP4r4JZ9RMT0O5iG
CNfWSShurZ2LhoMvsne2MZpW46VKAs/TTvoruV1ml12uB7f66vEl2JEPXy91R8YQ
i/LvPQW73nStgaGFZ4gGXBUcSDE9NXJGeb6ag2zfxDJftPOrdXumqUezFYOAH9ae
ToeIyy4v/XL+SlaGct0YstwCB/tmMzMyMufK561J+1b1VX8DVxjIek1a+F5rsk+6
dopMG+Xt9Cm/I4Ien9/8pOOGkB/rqbUy79J3ABEBAAG0PGhvbWU6c3RyeWNvcmUg
T0JTIFByb2plY3QgPGhvbWU6c3RyeWNvcmVAYnVpbGQub3BlbnN1c2Uub3JnPokB
PgQTAQIAKAUCYLp8LQIbAwUJEH/VOQYLCQgHAwIGFQgCCQoLBBYCAwECHgECF4AA
CgkQL38Npf1bZLmRaAgAriB11Iihbix36K6X/ZHoewLNcKJ8c5vpV8Xz1x9rMjer
ZUS0dXfN/yqH0r8aeIhEM5nZpNpuEtFzV6zllb6ALR+9PM/wfYikhdsl2abTkwo9
1Z3Mv+sEqF+R8wURDweB3+NgBEqz5jcpG1zcN5QKiI3djGxYu+fAyUVwlaZLr6yj
ZbQht/0xtKI5jSru0yzEXPQesh/aj3NDhN2Uo6TgeiJ3+q4C3obYLcSScbX5NuSL
XIIZKKA7kF97voQSiY8IntFGlakRYyWEHL/qHJZaDiN14ilzJWyGLo25osGZtUVt
SJaWWHebbpFxUY9GoGde9/15AdsQVcRxA8gDiEDLD4hGBBMRAgAGBQJUWVb0AAoJ
EDswEbdrnWUjt2gAn3cUL8HGu6MltT9u5yvhjbPZH6F1AKCoj1eNGamRYlgE0Jh9
wYDNbncEOg==
=M6jm
-----END PGP PUBLIC KEY BLOCK-----
-                        100%[==================================>]   1.08K  --.-KB/s    in 0s      

2022-04-04 18:58:58 (51.8 MB/s) - written to stdout [1101/1101]


```

---

### Post by scottbomb on 2022-04-04
I don't know from where I originally downloaded it. I tried the wget suggestion and got the same warnings on apt update. One would think they would make this a FAQ or something on their website but I've searched it to no avail.

---

### Post by #&amp;thj^% on 2022-04-04
You will now have to remove all lutris  ppa:lutris-team/lutris from your source list "/etc/apt/sources.list.d/"
after that is done run:
```
sudo apt autoremove
sudo apt clean
sudo apt update
```

then re-add the PPA

---

