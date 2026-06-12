---
title: "Xubuntu 16.04, can't change default browser in Terminal"
date: 2016-05-19
forum: General Help
---

### Post by donsy on 2016-05-19
I have my default browser set as chromium-browser in **Preferred Applications **and also in 
```
sudo update-alternatives --config x-www-browser
sudo update-alternatives --config gnome-www-browser
```
But when I try to open a link that appears in Terminal (xfce4-terminal) it opens in Firefox. Where can I change the xfce4-terminal browser setting?

---

### Post by vasa1 on 2016-05-19
```
update-alternatives --get-selections | grep -i browser
gnome-www-browser              auto     /usr/bin/google-chrome-stable
infobrowser                    auto     /usr/bin/info
www-browser                    auto     /usr/bin/w3m
x-www-browser                  auto     /usr/bin/google-chrome-stable

```
Could you try setting *www-browser* as well?

---

### Post by donsy on 2016-05-19
```
update-alternatives --get-selections | grep -i browser
gnome-www-browser              auto     /usr/bin/chromium-browser
infobrowser                    auto     /usr/bin/info
x-www-browser                  auto     /usr/bin/chromium-browser



```

---

### Post by slickymaster on 2016-05-19
Can you please post back the output of```
cat /usr/share/applications/defaults.list | grep html
```and```
cat /usr/share/applications/defaults.list | grep http
```

---

### Post by vasa1 on 2016-05-19
And I don't know if these bug reports help:
[https://bugzilla.redhat.com/show_bug.cgi?id=1001082](https://bugzilla.redhat.com/show_bug.cgi?id=1001082)
[https://bugzilla.xfce.org/show_bug.cgi?id=10314](https://bugzilla.xfce.org/show_bug.cgi?id=10314)

---

### Post by donsy on 2016-05-19
```
cat /usr/share/applications/defaults.list | grep html
application/xhtml+xml=firefox.desktop
text/html=firefox.desktop



```
Can I simply change it to  text/html=chromium-browser.desktop?

---

### Post by slickymaster on 2016-05-19
> **donsy said:**
> ```
cat /usr/share/applications/defaults.list | grep html
application/xhtml+xml=firefox.desktop
text/html=firefox.desktop



```
Can I simply change it to  text/html=chromium-browser.desktop?

And also on from these ones```
~$ cat /usr/share/applications/defaults.list | grep http
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
```

---

### Post by donsy on 2016-05-19
Changed all from firefox.desktop to chromium-browser.desktop and it still doesn't work.

---

### Post by slickymaster on 2016-05-19
> **donsy said:**
> Changed all from firefox.desktop to chromium-browser.desktop and it still doesn't work.

What about in```
/usr/share/xubuntu/applications/defaults.list
```

---

### Post by donsy on 2016-05-19
Made the following changes in  **~/.local/share/applications/mimeapps.list** under the  **[Default Applications]** heading and it appears to be working OK now.

```
x-scheme-handler/http=chromium-browser.desktop
x-scheme-handler/https=chromium-browser.desktop
x-scheme-handler/ftp=chromium-browser.desktop
x-scheme-handler/chrome=chromium-browser.desktop

```

---

