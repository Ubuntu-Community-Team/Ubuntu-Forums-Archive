---
title: "Thunderbird does not open link in Browser"
date: 2008-06-16
forum: General Help
---

### Post by jbaerbock on 2008-06-16
Ok so I just got 64-bit Kubuntu up and running swimmingly. Only problem is when I click a link in thunderbird (it should open in Konqueror) nothing happens. I changed default app web browser to Konq and yet nothing. Any ideas? Yes I tried restarting.

---

### Post by iaculallad on 2008-06-16
Open Thunderbird and navigate to Edit->Preferences, "Advanced"->"General". click on "Config Editor" and check for the **network.protocol-handler.app.http** key (create the key if it does not exist), place the full path of your browser application:

ie: For Ubuntu Gutsy's Firefox path -  **/usr/bin/firefox**

---

### Post by p_quarles on 2008-06-16
Thunderbird isn't aware of your KDE settings at all, so this is normal. It does, however, allow you to specify the network protocol handler application for http. Putting konqueror in this field will cause it to send http links to this application.

It's been a while since I've used Thunderbird, but the basic procedure is to open up the advanced configuration tool (which looks like Firefox's "about:config" page), and search for http. The value for this field should be the application you want to use.

---

### Post by Bubba64 on 2008-06-16
> **jbaerbock said:**
> Ok so I just got 64-bit Kubuntu up and running swimmingly. Only problem is when I click a link in thunderbird (it should open in Konqueror) nothing happens. I changed default app web browser to Konq and yet nothing. Any ideas? Yes I tried restarting.

Second post on this link fixed this same problem for me.
[http://ubuntuforums.org/showthread.php?t=798848](http://ubuntuforums.org/showthread.php?t=798848)

---

### Post by jbaerbock on 2008-06-16
Ditto, created the string and did /usr/bin/konqueror and bingo it works. Thanks guys.

---

