---
title: "Error: Opening the cache (E: Type &quot;deb  is not known on line 34...."
date: 2007-05-21
forum: General Help
---

### Post by ntpnick on 2007-05-21
I get this wierd error on Ubuntu Feisty Fawn it says Error: Opening the cache (E: Type "deb  is not known on line 34 in source list /etc/aptsources.list, E:The list of of sources could not be read.)

I am a Linux newbie, and I can make heads or tails of this error, let alone solve it...So if anyone can it help, it would be appriciated.

---

### Post by marianom on 2007-05-21
Maybe the server address in line 34 is down or maybe some malformed information has been  introduced in the file. Anyway, copy here the contents of your /etc/aptsources.list. We'll check it and let you know what to do.

---

### Post by ntpnick on 2007-05-21
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
‚Äúdeb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main‚Äù
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by aysiu on 2007-05-21
Maybe it's this line? ```
&#8218;Äúdeb http://www.getautomatix.com/apt feisty main&#8218;Äù
```

---

### Post by ntpnick on 2007-05-21
> **aysiu said:**
> Maybe it's this line? ```
‚Äúdeb http://www.getautomatix.com/apt feisty main‚Äù
```

Looking back at the output that line is actually  ```
"http://www.getautomatix.com/apt feisty main"
```
I just saved it ina txt file and pulled it up on my other computer and posted since ff hates me on Ubuntu....

---

### Post by marianom on 2007-05-22
IMHO someone should talk with Automatix folks: I've seen some (2 or 3 to be accurate) claims about broken sources.list when their soft is installed.

I see the same line three times:
```
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
```
Maybe you can erase two of them (e.g. the first two), save and retry.

---

### Post by ntpnick on 2007-05-22
> **marianom said:**
> IMHO someone should talk with Automatix folks: I've seen some (2 or 3 to be accurate) claims about broken sources.list when their soft is installed.

I see the same line three times:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
Maybe you can erase two of them (e.g. the first two), save and retry.

Erm how do I do that?

---

### Post by marianom on 2007-05-22
> **ntpnick said:**
> Erm how do I do that?

Open /etc/apt/sources.list with your favorite editor (remember you need to sudo to gain full right with the file *[1]*), navigate to the mentioned lines, delete and save. Always backup first.

For example, from a terminal:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gedit /etc/apt/sources.list
```

When the file is open, page down till the first two automatix lines appear, erase them and save the file.

*[1] To learn more about sudo, read [this]("https://help.ubuntu.com/community/RootSudo").*

---

### Post by aysiu on 2007-05-22
Shouldn't that be ```
*gksudo* gedit /etc/apt/sources.list
```?

---

### Post by marianom on 2007-05-22
Seems so. I wrongfully assume that the use of sudo in the previous line would grant full rights on the file to the user (I'm more a vim guy, just didn't want to confuse our friend with it).
Thanks for mention it.

---

### Post by ntpnick on 2007-05-22
Um I still a bit confused, sorry.

---

### Post by marianom on 2007-05-22
No need to be sorry. 
Just let us know which part you didn't get or exactly where are you facing problems, so we can guide you.

---

### Post by ntpnick on 2007-05-22
Well when aysiu corrected you I sort of got all confused. I'm not all too great with the terminal, could your write it step by step?

---

### Post by marianom on 2007-05-22
Sure.

Open a terminal: Applications -> Accesories -> Terminal.

Use the following commands there:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
gksudo gedit /etc/apt/sources.list

```

Page down until you find the lines you need to erase (these are the original lines as far as I understood)

```
"http://www.getautomatix.com/apt feisty main"
deb http://www.getautomatix.com/apt feisty main
deb http://www.getautomatix.com/apt feisty main

```

Erase the first two, save the file and close it.

Everything should work afterwards.

---

