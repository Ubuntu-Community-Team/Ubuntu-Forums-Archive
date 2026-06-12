---
title: "Error with Sources.list.d"
date: 2017-11-11
forum: General Help
---

### Post by delta79 on 2017-11-11
Hi there

I've been using Ubuntu for almost a week now, and I'm having several issues installing software, but for now, my main concern is that since I downloaded a .list and a .list.save file, I can't use apt-get commands. Whenever I try to do anything I get an error message telling me that the sources list could not be read. Then I get a message saying that there's an error on the 1st line of the following source: /etc/apt/sources.list.d/sublime-text.list

I checked with gedit and the file has a wrong link, but the thing is that instead of changing the link, I wanted to delete the file and download another program, and I can't because whenever I try to remove the file by using apt-get, I get this same error.

---

### Post by steeldriver on 2017-11-11
Files in /etc/apt/sources.list.d aren't removed using apt-get; they're removed using rm

```

sudo rm /etc/apt/sources.list.d/sublime-text.list

```

---

### Post by delta79 on 2017-11-12
Thanks! It actually worked. All I could find were forums saying that the right command was apt-get remove.

---

