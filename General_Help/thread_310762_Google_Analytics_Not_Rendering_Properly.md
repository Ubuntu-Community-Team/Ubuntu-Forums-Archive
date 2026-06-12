---
title: "Google Analytics Not Rendering Properly?"
date: 2006-12-01
forum: General Help
---

### Post by leftcase on 2006-12-01
Has anyone else had a problem viewing Google Analytics pages using Firefox 2.0 on Ubuntu-Edgy?

When I try and view my stats, text is missing from all of the flash graphs, charts etc. Could it be I'm missing a font or is it something more sinister!

---

### Post by reclusivemonkey on 2006-12-03
> **leftcase said:**
> Has anyone else had a problem viewing Google Analytics pages using Firefox 2.0 on Ubuntu-Edgy?

When I try and view my stats, text is missing from all of the flash graphs, charts etc. Could it be I'm missing a font or is it something more sinister!

Works fine for me with

```

File name: libflashplayer.so
Shockwave Flash 9.0 d78

```

---

### Post by leftcase on 2006-12-13
Hmmm - I'm using Shockwave Flash 7.0 r68, perhaps I should update !

BTW nice desktop :mrgreen:

---

### Post by reclusivemonkey on 2006-12-13
> **leftcase said:**
> Hmmm - I'm using Shockwave Flash 7.0 r68, perhaps I should update !


I think the latest version of the Flash 9 beta is pretty stable... I don't seem to have had any problems with it.

> **leftcase said:**
> BTW nice desktop :mrgreen:

Thanks :-)

---

### Post by mickbw on 2006-12-13
I have Flash 9 and it still doesn't display correctly.  At least I am pretty sure I do because I don't know how to check the version on my Ubuntu install.

---

### Post by reclusivemonkey on 2006-12-13
> **mickbw said:**
> I have Flash 9 and it still doesn't display correctly.  At least I am pretty sure I do because I don't know how to check the version on my Ubuntu install.

```

about:plugins

```

In the address bar.

---

### Post by leftcase on 2006-12-13
Hey there. I've updated to flash 9 and it now shows properly. I think this issue may be related to missing fonts.

Try a sudo apt-get install flashplugin-nonfree to get the missing font....
Then update to flash 9. I did this by:
```

sudo wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_112006.tar.gz
sudo tar -xvf FP9_plugin_beta_112006.tar.gz
sudo mv /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.7
sudo cp flash-player-plugin-9.0.21.78/libflashplayer.so /usr/lib/firefox/plugins
sudo chmod +x /usr/lib/firefox/plugins/libflashplayer.so

```

Restart Firefox

Now, although typing about:plugins into the browser shows the plugin as flash 7 still, right clicking on a flash component of a webpage shows flash player 9

Woohooo!

---

