---
title: "Installing webapps after denying installation popup"
date: 2014-10-02
forum: General Help
---

### Post by Tornikee on 2014-10-02
I cancelled a webapp installation prompt popup that appears when you visit a webapp-supporting website but later decided to install it. Where should I look for webapps for installation? I found [this]("http://bit.ly/1uF5NME") while looking for Facebook app, but the Software Centre either could not find it in sources.

---

### Post by Tornikee on 2014-10-06
No ideas?

---

### Post by CantankRus on 2014-10-06
Most likely in this section of **dconf-editor** which you may have to install.
Drill down to **com.canonical.unity.webapps** and reset to default the **dontask-domains** key.
I uninstall unity-webapps-common so can't be sure.

You can also check this dconf value via terminal...
```
gsettings get com.canonical.unity.webapps dontask-domains
```

To clear the key so all will ask again you can use...
```
gsettings reset com.canonical.unity.webapps dontask-domains
```

---

### Post by Tornikee on 2014-10-07
Thanks a lot, that worked perfectly.

---

