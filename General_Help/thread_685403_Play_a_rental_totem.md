---
title: "Play a rental totem"
date: 2008-02-02
forum: General Help
---

### Post by matty13 on 2008-02-02
Ok im trying to play a rental movie i got from lovefilm today using totem player but it won't play it says i need codec's but im not 100% sure which codecs i may need.

Can someone point me in the right direction for the correct codec's.

Thanks!
Matt.

---

### Post by BennBuntu on 2008-02-02
If you haven't already try

```
sudo apt-get install ubuntu-restricted-extras

```

if that doesn't sort it, try medibuntu. [http://www.medibuntu.org/]("http://www.medibuntu.org/")

just click repository howto and follow those.

If you have trouble with other videos, install VLC (in synaptic), handles pretty well everything you can throw at it.

---

### Post by matty13 on 2008-02-02
> **BennBuntu said:**
> If you haven't already try

```
sudo apt-get install ubuntu-restricted-extras

```

if that doesn't sort it, try medibuntu. [http://www.medibuntu.org/]("http://www.medibuntu.org/")

just click repository howto and follow those.

If you have trouble with other videos, install VLC (in synaptic), handles pretty well everything you can throw at it.

Whats the restricted extras do? more explanation before i go and install that.

---

### Post by BennBuntu on 2008-02-02
Does sound a bit ominous ;-)
Description from synaptic
> Commonly used restricted packages
This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio files),
and DVD playback.

Please note that packages from multiverse are restricted by copyright
or legal issues in some countries. See
[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)
for more information.

I think it lists them by name before you type y to install.

---

### Post by zvacet on 2008-02-02
Restricred extras will install Java,Flash,plugins...for you.

```
gsudo gedit /etc/apt/sources.list
```

add this line

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Save and close.

In programs<accesssories>terminal

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

```
sudo apt-get update
```

Go to the synaptic and in search box type w32(or 64 if you use 64bit version)codecs and when you find then mark for installation and install.

---

