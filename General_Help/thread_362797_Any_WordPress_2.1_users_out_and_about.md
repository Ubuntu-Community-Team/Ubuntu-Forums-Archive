---
title: "Any WordPress 2.1 users out and about?"
date: 2007-02-16
forum: General Help
---

### Post by volfro on 2007-02-16
Hiya!

I recently upgraded my (remote, shared server) installation of WordPress to version 2.1.

Since the upgrade, if I'm using Firefox 2 (both 32- and 64-bit), none of the AJAX works in wp-admin. 

(This includes dynamically adding or deleting categories, for instance, or using the WYSIWYG editor to create HTML hyperlinks within a post.)

Everything works perfectly via IceWeasel, Epiphany, and (gasp!) IE7 on XP Pro. 

I'm running Edgy on AMD64.

I've tried re-uploading (by deleting AND overwriting) the .js files, the .js and .php files, and the entire wp-admin directory, using several different FTP clients.

I've also tried running Firefox in safe mode, disabling plugins etc temporarily to see if that's the problem. It's not. It's also not the Mozilla rendering engine, since IceWeasel and Epiphany both render the wp-admin pages perfectly, ajax and all. And it can't be the server, right? Since it works in other browsers.

Just wondering if this broke for anybody else using Firefox 2 on Edgy.

---

### Post by stupid head on 2007-02-16
Test it out with a new Firefox profile.

---

### Post by volfro on 2007-02-16
I'll try that. 

It should be noted that Ajax works on other sites (i.e. Google Maps). Not sure what the deal is.

---

### Post by Dubbayoo on 2007-02-16
as near as i can tell it works for me

---

### Post by llamakc on 2007-02-16
Works here also: Firefox 2.0.0.1, WordPress  2.0.4-2.

---

### Post by true_friend on 2007-02-16
Try [Swiftfox]("http://getswiftfox.com") the linux build of firfox may it help.

---

### Post by volfro on 2007-02-19
Like I said, it's working fine in other browsers (IceWeasel, Epiphany, etc). Ultimately I was trying to determine if this was a problem for anybody else, and if so, how to fix it.

I'd prefer to keep using my Firefox--it's got all my plugins, bookmarks, etc. It's too time-consuming to have to start a separate browser every time I want to update my site. 

Any other tips?

---

### Post by llamakc on 2007-02-19
Did the offsite upgrade use a manual upgrade or an Ubuntu package? Have you checked the wordpress forums? 

Somebody recommended creating a new profile in Firefox for testing purposes. Have you done that?

---

### Post by volfro on 2007-02-19
I used a manual upgrade, since I'm on Edgyx64 using Firefox 32. Yes, I checked Wordpress forums, but posted here as it seemed to be OS-specific.

Incidentally, I finally figured out how to create a new profile manager (start firefox with the '-ProfileManager' switch in the launcher or via CLI) and created a new one. It worked. So my old profile must have gotten corrupted somehow (it's at least a year old). Had to export everything from my old one and re-import it into the new one but it's still going, so that's a good sign.

Thanks for the suggestions!

---

