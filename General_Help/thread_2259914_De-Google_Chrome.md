---
title: "De-Google Chrome"
date: 2015-01-07
forum: General Help
---

### Post by DigiAngel on 2015-01-07
So I'm messing around with Chrome on Ubuntu 14.04.  After setting all the settings I can find to not go out to Google (safebrowsing jazz and whatnot), I find that as soon as I fire up Chrome, it goes right to Google https even with starting with just a blank page.  Anyone ever attempt to...take the Google out of Chrome?

---

### Post by ajgreeny on 2015-01-08
If you manage to do that, what does chrome offer that chromium doesn't apart from the pepperflash-plugin installed by default?

I don't use chrome, so I ask this, not because I believe that it will be the same, but because I simply don't know.

---

### Post by DigiAngel on 2015-01-08
In a word, Netflix ;)

---

### Post by DigiAngel on 2015-01-08
This seems to have done the trick:

[https://github.com/gorhill/httpswitchboard/wiki/Privacy-matters:-Hidden-remote-connections](https://github.com/gorhill/httpswitchboard/wiki/Privacy-matters:-Hidden-remote-connections)

start with these flags:
```
--disable-background-networking --disable-component-extensions-with-background-pages
```

no more tcpdump showing connections to clients[*].google.com.  Maybe now I'll actually use this browser.

---

