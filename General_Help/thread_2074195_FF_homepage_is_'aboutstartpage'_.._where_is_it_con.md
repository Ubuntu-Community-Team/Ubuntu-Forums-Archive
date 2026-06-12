---
title: "FF homepage is 'about:startpage' .. where is it configured to use Google?"
date: 2012-10-21
forum: General Help
---

### Post by emonti on 2012-10-21
This is a browser-related question.

In Firefox 16(on Ubuntu 12.04 LTS), the homepage is by default set to 'about:startpage'.

I know I can change the setting to any web page I prefer but I was wondering where Google is configured as the search engine for the 'about:startpage' property.

I had a scratch around in about:config but could not see where it is defined/configured.

---

### Post by Cheesemill on 2012-10-21
Firefox Preferences > General > Home Page

Edit - Ignore this, I didn't read your thread properly.

---

### Post by vasa1 on 2012-10-21
> **emonti said:**
> ...
I had a scratch around in about:config but could not see where it is defined/configured.
If you type "google" in the search bar present near the top of the about:config page, you'll see entries related to Google.

---

### Post by howefield on 2012-10-21
Don't think this is a Firefox option, but more to do with Ubuntu branding, the "Ubuntu Firefox Modifications" addon.

---

### Post by vasa1 on 2012-10-21
> **howefield said:**
> Don't think this is a Firefox option, but more to do with Ubuntu branding, the "Ubuntu Firefox Modifications" addon.
But vanilla Firefox (installed direct from Mozilla and not from the USC or any ppa) also has google.com as the default engine on the page accessed by typing **about:home**.

---

### Post by howefield on 2012-10-21
I get about:startpage going to [http://start.ubuntu.com/12.10/Google/?sourceid=hp](http://start.ubuntu.com/12.10/Google/?sourceid=hp) with Ubuntu Firefox Modifications enabled.
 
Disabling Ubuntu Firefox Modifications gets the plain vanilla Firefox branding, which also goes to google but obviously not via ubuntu.com.

---

### Post by vasa1 on 2012-10-21
> **howefield said:**
> I get about:startpage going to [http://start.ubuntu.com/12.10/Google/?sourceid=hp](http://start.ubuntu.com/12.10/Google/?sourceid=hp) with Ubuntu Firefox Modifications enabled.
 
Disabling Ubuntu Firefox Modifications gets the plain vanilla Firefox branding, which also goes to google but obviously not via ubuntu.com.
Oops! My bad. OP wants to know about about:startpage and I'm going on about about:home :(
(The vanilla Firefox doesn't even recognize about:startpage as a valid url.)

---

