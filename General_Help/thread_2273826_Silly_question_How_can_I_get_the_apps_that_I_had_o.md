---
title: "Silly question: How can I get the apps that I had on Ubuntu when I'm using Kubuntu?"
date: 2015-04-15
forum: General Help
---

### Post by pinenutsofdoom on 2015-04-15
I'm trying to get VLC and Thunderbird but I'm on a Kubuntu machine. I was hoping to have access to that store page I had on Ubuntu but I can't seem to find it and the one on Ubuntu doesn't have a very large selection or the specific programs I wanted. How can I get back to that Canonical store page?

---

### Post by QIII on 2015-04-15
Hello!

```
sudo apt-get install vlc thunderbird
```

will get you the first two, although I don't remember having to install Thunderbird as I think it comes with Kubuntu by default.

I'm not sure what dependencies you will draw in to Kubuntu or if it will even work with KDE, but you can try

```
sudo apt-get install software-center
```

to get the Software Center.

---

### Post by pinenutsofdoom on 2015-04-15
Thanks for the reply. None of them worked. They each say "E: Package 'xxxxxxxxx" has no installation candidate".

---

### Post by QIII on 2015-04-15
What release of Kubuntu are you running?

---

### Post by pinenutsofdoom on 2015-04-15
The 32-bit version of Kubuntu 14.04.2.

---

### Post by QIII on 2015-04-15
I installed vlc an (apparently, since it turns out it is not present by default) Thunderbird on my 64 bit Trusty.  I just checked and the Software Center is available, but there are a lot of dependencies.

Which repos to do you have enabled?


(Edit:  I just checked to be sure.  All three packages are available for 32 bit)

---

### Post by PhilGil on 2015-04-16
Try the following command before running the commands in [**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")'s post:

```
sudo apt-get update
```

If you get any error messages in the output post them here.

---

### Post by monkeybrain20122 on 2015-04-16
You don't need the software centre. Kubuntu comes with muon which is a gui package manager  (very  similar to synaptic to those who know). You can search, install and update software with it easily.

---

