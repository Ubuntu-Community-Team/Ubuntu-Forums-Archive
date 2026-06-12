---
title: "Install webapp after missing initial popup"
date: 2012-11-06
forum: General Help
---

### Post by shafin on 2012-11-06
I missed the initial pop-up at firefox when I went to google reader. Now how do I install the webapp manually?

Also, how do I uninstall individual webapps?

---

### Post by uclugLee on 2012-11-07
Installing Web Apps Integration
To install this feature in Ubuntu, launch a terminal and run the following commands:

sudo add-apt-repository ppa:webapps/preview
sudo apt-get update
sudo apt-get install unity-webapps-preview

---

### Post by shafin on 2012-11-08
Thanks for the reply, but I have the integration already. 
The problem is, once integration is enabled, after I go to a website that has this capability, a dialogue box comes up and asks if I want to install the app for that site. Once I miss that popup, there is apparently no way to enable integration for that particular site. I was asking if there is any way.

---

### Post by DarkAmbient on 2012-11-08
I can't be 100% accurate about this, what I know is that by using Ubuntu Tweak -> cleaner and cleaning up my computers application-cache, I managed to remove all my web-apps. Chromium started to ask me again if I wanted to install web-apps after that.

---

### Post by diesch on 2012-11-08
Get the list of missed webapps using
```
gsettings get com.canonical.unity.webapps dontask-domains
```Remove to domains you want to be asked again and set the new list using

```
gsettings set com.canonical.unity.webapps dontask-domains "LIST"
```where LIST is the new list, e.g.
```
['tumblr.com', 'facebook.com', 'twitter.com']
```

If you prefer a GUI have a look at [Unsettings]("http://www.florian-diesch.de/software/unsettings/") (in the "Web apps" tab).

---

### Post by shafin on 2012-12-03
Thanks a lot

---

