---
title: "Enabling the universe repository??"
date: 2007-01-02
forum: General Help
---

### Post by motermouth on 2007-01-02
I'm trying to make it so that I can read and write on my windows partition from ubuntu. I was given a link that is showing me how to do it and it says to Enable the universe repository...I don't know what that means and I'm currently now hooked up to the internet on that computer so If I need to download a repository I have to do it on this one and then transfer it. Do I need to download a universe package first or does it come with edgy...and how do I enable it if I already have it?

---

### Post by bodhi.zazen on 2007-01-02
[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

### Post by taurus on 2007-01-02
You need to edit /etc/apt/sources.list and remove the # sign in front of all the lines that contain universe or multiverse at the end or near the end (with deb at the beginning).

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and then update your list with

```

sudo aptitude update
sudo aptitude upgrade
```

---

