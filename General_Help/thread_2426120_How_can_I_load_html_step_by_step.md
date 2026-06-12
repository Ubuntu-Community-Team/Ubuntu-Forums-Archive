---
title: "How can I load html step by step"
date: 2019-09-04
forum: General Help
---

### Post by Kevin McCready on 2019-09-04
I have an html file which displays information I want and then goes off to another website before I can see the information.
How can I load the file step by step or find the information I want?

---

### Post by TheFu on 2019-09-05
3 ideas:
I use **wallabag** to grab it quickly. There's a browser addon that sends the URL to my wallabag server. This is working for me on many sites, but not all.

**Pandoc** might work too. 

Might try disabling javascript. The redirection might be a javascript function, but the main page might only display via javascript, so this is less likely to actually work.

---

### Post by Kevin McCready on 2019-09-05
Thanks. I couldn't get pandoc working properly I don't think. I'm actually trying to find information about a NZ artist called Dennis Wilson. If I click on many of the google results the page quickly displays some information and then goes to another website. So I saved a google link but when I tried to upload it for this post it wouldn't, so I took a screenshot from a text editor (attached).

---

### Post by SeijiSensei on 2019-09-06
Searching Google for "dennis wilson nz" just brings up pages about the now-deceased drummer for the 60's American band, The Beach Boys. And none of the pages I looked at redirected me to another site.

---

### Post by norobro on 2019-09-06
It would help us help you if you provided a link to the site with which you are having problems.

That being said, if you are trying to reach [https://regionbusinessworld.news](https://regionbusinessworld.news) (from your screen cap) it looks like that site has been hacked and is being redirected to "mobilego.io". Turning off javascript in my browser prevents the redirect.

---

### Post by Kevin McCready on 2019-09-07
Thanks for that. Yes it was regionbusinessworld and a whole lot of other links most of which had news in their name which did the identical trick (maybe google has cleaned them away in the last few days). I tried to turn off  java in firefox quantum 69.0 (32-bit) but couldn't manage it.

---

### Post by Holger_Gehrke on 2019-09-07
a) Not Java, JavaScript. The names may be similar, the languages aren't. Java used to be useable in web-pages through applets, but those days are gone and the Java-plugin can't be used in modern browsers any more because the API it used was discarded for security reasons.
b) JavaScript is so important for modern web-pages that the option **not** to use it isn't available in the settings-pages any more. The setting can still be changed through the 'about:config' URL and switching the setting 'javascript.enabled' to 'off'.

Holger

---

### Post by TheFu on 2019-09-07
If you just want the information, you can try google's cache version or the WayBackMachine.  [https://archive.org/web/](https://archive.org/web/)

---

### Post by sdsurfer on 2019-09-09
> I tried to turn off  java in firefox quantum 69.0 (32-bit) but couldn't manage it

- about:config in FireFox URL bar
- Search for javascript (you don't even have to complete the word)
- Double-click the javascript.enabled entry so it is set to false
- Browser restart is not required

Tried to post a screen shot but guess I don't have privileges

Don't forget to turn it back on or many websites will be broken (which they shouldn't be, graceful degradation is not honored these days)

---

