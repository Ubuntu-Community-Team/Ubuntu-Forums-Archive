---
title: "Nicotine sharing"
date: 2006-12-25
forum: General Help
---

### Post by vierdreieins on 2006-12-25
I've opened the ports, but I can't seem to get my own folder to share and I feel like I'm missing something here. Whenever I try to browse my own files, I get "/" instead of the folder I chose. On my buddy list, it says that my speed is 0 even though it says I have files available.

Also, there are two ports listed in the settings. Should I only open the first, both, or 2234-2239?

---

### Post by OffHand on 2006-12-25
> **vierdreieins said:**
> I've opened the ports, but I can't seem to get my own folder to share and I feel like I'm missing something here. Whenever I try to browse my own files, I get "/" instead of the folder I chose. On my buddy list, it says that my speed is 0 even though it says I have files available.

Also, there are two ports listed in the settings. Should I only open the first, both, or 2234-2239?

Which version of Nicotine are you running? I can really recommend using Nicotine+ from svn.

[http://www.nicotine-plus.org/wiki/NicotineFromSubversion](http://www.nicotine-plus.org/wiki/NicotineFromSubversion)

You will automatically join the nicotine room once you log in. Usually people can help you there. Only opening one port should be enough.

---

### Post by vierdreieins on 2006-12-26
> **OffHand said:**
> Which version of Nicotine are you running? I can really recommend using Nicotine+ from svn.

[http://www.nicotine-plus.org/wiki/NicotineFromSubversion](http://www.nicotine-plus.org/wiki/NicotineFromSubversion)

You will automatically join the nicotine room once you log in. Usually people can help you there. Only opening one port should be enough.

It's 1.2.4 from the Edgy repos. I didn't bother with anything else because I still don't know how to install things manually.

---

### Post by zanglang on 2006-12-26
Hmm... That seems to be the default behaviour of Nicotine? If you expand the / list furthermore you'll see it only shares the subfolder that you've selected anyway.

---

### Post by spockrock on 2006-12-26
```
sudo su -c 'echo "deb http://www.nicotine-plus.org/ubuntu edgy main" >> /etc/apt/sources.list'
sudo aptitude update
sudo aptitude install nicotine
```

that will add and update to the latest version


enjoy.

---

### Post by OffHand on 2006-12-26
> **vierdreieins said:**
> It's 1.2.4 from the Edgy repos. I didn't bother with anything else because I still don't know how to install things manually.

It's very easy to install it from svn as you can see on the page I linked. If you want a deb you can use the method of the post above this one. 1.2.4 is kinda old... the svn version is already working on 1.2.7.

The Nicotine+ guide comes in handy too: [http://nicotine-plus.sourceforge.net/NicotinePlusGuide/TableOfContent.htm](http://nicotine-plus.sourceforge.net/NicotinePlusGuide/TableOfContent.htm)

To install subversion```
sudo apt-get install subversion
```

---

### Post by vierdreieins on 2007-01-13
I've downloaded nicotine+ from Subversion, but it isn't in Applications and can only be run from the terminal. Is there a way to get an icon somewhere?

---

