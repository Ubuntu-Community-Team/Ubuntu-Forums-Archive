---
title: "EasyUbuntu Do not work in 7.10"
date: 2007-10-20
forum: General Help
---

### Post by UK-Wobbie on 2007-10-20
Hey i have Ubuntu 7.10 installed and i have only installed EasyUbuntu.. When i click on the EasyUbuntu starter link it will not open and it's not doing anything :(

Do any one no why?

Thanks :)

---

### Post by r-mo on 2007-10-20
It was written for feisty.  If you're wanting it for media codecs then

```
sudo apt-get install ubuntu-restricted-extras
```

will get you most of what you need. Then for dvd playback and even more codecs :)

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

```

---

### Post by UK-Wobbie on 2007-10-20
> **r-mo said:**
> It was written for feisty.  If you're wanting it for media codecs then

```
sudo apt-get install ubuntu-restricted-extras
```

will get you most of what you need. Then for dvd playback and even more codecs :)

```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
sudo apt-get install libdvdcss2
sudo apt-get install w32codecs

```

Thanks buddied i give it a go :)

---

