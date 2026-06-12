---
title: "Disable overlay scrollbars in Xenial"
date: 2016-05-09
forum: General Help
---

### Post by CantankRus on 2016-05-09
How can you disable the disappearing overlay scrollbars completely in Xenial.
I can disable for the user by adding to ~/.profile ....
```
export GTK_OVERLAY_SCROLLING=0
```

The overlays remain when opening an application as root ...eg in synaptic.

---

### Post by vasa1 on 2016-05-09
I hope you don't mind my asking, but do I have to reload or re-*source* ~/.profile after adding the code you mention?

According to [this thread]("http://ubuntuforums.org/showthread.php?t=2306651"), even Synaptic behaves but needs a log out and log in.

Edit: putting that code in ~/.profile fixed it for user apps but SPM still has them :(

According to [https://bbs.archlinux.org/viewtopic.php?pid=1546793#p1546793](https://bbs.archlinux.org/viewtopic.php?pid=1546793#p1546793), appending the code to /etc/environment should work but that seems odd: my /etc/environment looks like this:
```
$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

```

Would it be safe to add the code to the end of */etc/profile*?

---

### Post by CantankRus on 2016-05-09
I tried adding "GTK_OVERLAY_SCROLLING=0" to various files with no luck.

From your suggestion above... appended to /etc/environment and appears to work.
```
[COLOR="#006400"]**glen@Xenial:~$**[/COLOR] **cat /etc/environment**
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
GTK_OVERLAY_SCROLLING=0
```

For others who want to disable the disappearing scrollbars, you can run this command to edit /etc/environment
```
echo "GTK_OVERLAY_SCROLLING=0" | sudo tee -a /etc/environment
```

Thanks.

---

### Post by vasa1 on 2016-05-09
I added the code via *sudo nano*. Then rebooted. Synaptic Package Manager still showed the overlay scrollbars. I then deleted the code I added, saved */etc/environment* and used *echo "GTK_OVERLAY_SCROLLING=0" | sudo tee -a /etc/environment*. I'll report what happens when I restart my laptop tomorrow morning.

It's not that big an issue because I don't use SPM a lot, but still ... :confused:

Edit: it's possible that things don't work for me because I'm running without a desktop environment which means, I think, that there's no "session manager".

---

