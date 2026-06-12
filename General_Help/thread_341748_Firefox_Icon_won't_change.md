---
title: "Firefox Icon won't change"
date: 2007-01-19
forum: General Help
---

### Post by Souljah on 2007-01-19
Hi,

I have followed this thread: [http://ubuntuforums.org/showthread.php?t=199193](http://ubuntuforums.org/showthread.php?t=199193). My Firefox has still not changed and I can't seem to locate the .png file to replace that blue earth icon with. The Firefox icon does show on my ubuntu task bar where all the current active programs are. How not at the top where you click on it and it opens up firefox. What others can we change it.

I am using Ubuntu Dapper Drake 6.06. By the way, firefox is all ready updated.

---

### Post by lukew on 2007-01-19
> **Souljah said:**
> Hi,

I have followed this thread: [http://ubuntuforums.org/showthread.php?t=199193](http://ubuntuforums.org/showthread.php?t=199193). My Firefox has still not changed and I can't seem to locate the .png file to replace that blue earth icon with. The Firefox icon does show on my ubuntu task bar where all the current active programs are. How not at the top where you click on it and it opens up firefox. What others can we change it.

I am using Ubuntu Dapper Drake 6.06. By the way, firefox is all ready updated.

You can change the icon of the application launcher via Right clicking on it and selecting properties. There is an option to change the icon.

Luke

---

### Post by Souljah on 2007-01-19
Yes that's right, but where is the original firefox icon. I would like to know that. Haha.

---

### Post by lukew on 2007-01-19
> **Souljah said:**
> Yes that's right, but where is the original firefox icon. I would like to know that. Haha.

Off the top of my head

/usr/share/pixmaps/firefox? 

If no one has replied by the time i get back from work I wil post the exact location.

you can always finf out from synamptec all files which the firefox application installs. You should some a path which will be an icon dir somewhere!!

Or you could always find -name fire*

Luke

---

### Post by Souljah on 2007-01-19
I didn't do it from synaptic because it wasn't updated so I downloaded it myself. It's installed in the /opt/firefox folder.

---

### Post by Souljah on 2007-01-19
I got it to work myself. I applied this command:

```
sudo cp mozicon128.png -t //usr/share/pixmaps
```

and then I changed the icon from the properties screen.

---

