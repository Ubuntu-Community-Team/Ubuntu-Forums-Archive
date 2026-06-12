---
title: "What OS is my machine reporting to servers?"
date: 2008-01-08
forum: General Help
---

### Post by knutschr on 2008-01-08
When I visit a site the server can recieve a message of what OS I am using, I understand.
Some use that to make statistics of % using different OS.

When Linux machines are asked, is it a particular file where it fetches the information?
Is it a bad idea to change this if one do not agree with what is presented?

---

### Post by rune0077 on 2008-01-08
I'm not sure about this one, but I think it's your browser that provides this information. Basically I think it's a matter of detecting whether you're using the Windows, Linux or Mac version of Firefox (or whatever browser you're using).

---

### Post by Jussi Kukkonen on 2008-01-08
[http://www.useragentstring.com/](http://www.useragentstring.com/)

---

### Post by astoltz on 2008-01-08
It is indeed the browser.  The string that the browser sends is called the "user-agent" and for a default firefox install on my machine its:  ```
User-Agent: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11
```I'm sure there are many ways to modify this - there is a firefox plugin called user-agent switcher.

---

### Post by knutschr on 2008-01-08
It must be more than that, as one can see in 'Page Hit Ranking' list at [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by p_quarles on 2008-01-08
> **knutschr said:**
> It must be more than that, as one can see in 'Page Hit Ranking' list at [http://distrowatch.com/](http://distrowatch.com/)
That just lists the number of hits that each distro's page gets per day.

---

### Post by Nesman on 2008-01-09
If you would like to change how servers see you in Firefox, you can try the user agent switcher plugin: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

In Opera: Tools -> Quick Preferences -> Network -> Identify as...

Konqueror has a similar option as well.

---

