---
title: "Ubuntu 12.04/Problems updating (failed to fetch error)"
date: 2014-04-22
forum: General Help
---

### Post by ktpinnock on 2014-04-22
Hey.

I'm trying to update via the command sudo apt-get update and run in to these two errors:

W: Failed to fetch [http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/zeitgeist/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

Clicking on those urls indicate that the page no longer exists or has moved. I've done a few searches indicating that I may be able to get rid of the error by unticking the ppas in the software sources, but I'm afraid that these ppas maybe important. I'm a noob so i pretty much have no idea what i'm talking about so any help or clarification would be great!

---

### Post by monkeybrain20122 on 2014-04-22
That ppa is not available for 12.04 (strangely it is only for 11.10, 13.04 and 13.10 [https://launchpad.net/~zeitgeist/+archive/ppa](https://launchpad.net/~zeitgeist/+archive/ppa), see the "published in" drop down)  You should just remove the ppa from your source. If you have synaptic then just go to System > Repositories > Other Software right click the entry and choose remove.

Or you can use the terminal
```
sudo add-apt repository --remove ppa:zeitgeist/ppa
```

---

### Post by whitesmith on 2014-04-22
+1 previous answer.

---

### Post by ktpinnock on 2014-04-22
Ahh thanks for the quick response. Weird it's not supported by 12.04. Do you know exactly what it does? It must be important for something for it to be in all the other distros...I guess I can assume that it will have no effect if I remove it?

---

### Post by monkeybrain20122 on 2014-04-22
It doesn't do anything since you have not installed anything from it (it is not availiable for 12.04)

---

