---
title: "How do I uninstall this?"
date: 2014-06-11
forum: General Help
---

### Post by GrampysGun on 2014-06-11
Sorry for the newb question. But how do I uninstall whatever it is I installed using the following code:
```

 sudo add-apt-repository -y ppa:chris-lea/node.js
 sudo apt-get update
 sudo apt-get install nodejs wget vlc
 sudo npm install -g peerflix
 wget [http://pinguyos.com/files/Torrent-Video-Player](http://pinguyos.com/files/Torrent-Video-Player)
 chmod +x Torrent-Video-Player
 sudo mv Torrent-Video-Player /usr/bin

```
(I got it [here.]("http://news.softpedia.com/news/How-to-Stream-Torrent-Video-Files-Directly-with-VLC-432664.shtml"))

I'm running lubuntu 14.04.

Also, can anyone help me understand, line by line but real simple-like, what generally this code means? What did I install? 

And where can I learn more about this sort of thing?

Thanks!

---

### Post by lukeiamyourfather on 2014-06-11
Use the man command to look at manuals for different software, for example man apt-get or man chmod. Understand everything before executing random commands from the internet, especially when they involve sudo.

```

sudo add-apt-repository -y ppa:chris-lea/node.js

```

The sudo means do something as the root user. The add-apt-repository command is used to add new software repositories, in this case a PPA which is a software repository not officially associated with Ubuntu, but rather an individual (or organization).

```

sudo apt-get update

```

This tells the system to look for an updated list of software packages available from the software repositories (including the just added PPA).

```

sudo apt-get install nodejs wget vlc

```

Install the listed packages, I presume nodejs is from the PPA.

```

sudo npm install -g peerflix

```

Not sure what npm is but it probably has a man page.

```

wget http://pinguyos.com/files/Torrent-Video-Player

```

This downloads the listed file, wget is a command line download utility.

```

chmod +x Torrent-Video-Player

```

The chmod command changes file and directory permissions, the +x means to allow execution of the file.

```

sudo mv Torrent-Video-Player /usr/bin

```

This moves the file to /usr/bin which is typically a place where software is installed when it doesn't come from a repository.

---

### Post by GrampysGun on 2014-06-11
By the way, I downloaded this to be able to watch torrents as I download them. I obviously should not be trying to do stuff like that right now!

> **lukeiamyourfather said:**
> Use the man command to look at manuals for different software, for example man apt-get or man chmod. Understand everything before executing random commands from the internet, especially when they involve sudo.

Will do from now on, thank you for the recommendation.

> **lukeiamyourfather said:**
> 
```

sudo npm install -g peerflix

```

Not sure what npm is but it probably has a man page.


I ran man npm but there was nothing there. Is that where you thought the uninstallation info might have been? I don't know where to look. Any advice? 

Thanks.

---

### Post by GrampysGun on 2014-06-11
Posting question to PinguyOS forum, where the code and application originated from.

---

