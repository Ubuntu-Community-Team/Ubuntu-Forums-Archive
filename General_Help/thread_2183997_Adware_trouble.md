---
title: "Adware trouble"
date: 2013-10-27
forum: General Help
---

### Post by pbhill on 2013-10-27
Recently I have been having an awful time using Firefox. I am getting pop up ads and redirects. Even after I close the redicted window I'll get music playing in the background. It's making web browsing nearly impossible. I have run ClamAV, and have AdAware installed in Firefox, to no avail. Some of the offending websites seem to be: *superfish.com, fogporoducts.com, and scorecard[I]*[/I] Any help would be appreciated.

---

### Post by philinux on 2013-10-27
I use adblock plus addon. Works a treat.

[https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/)

---

### Post by pbhill on 2013-10-27
> **philinux said:**
> I use adblock plus addon. Works a treat.

[https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/](https://addons.mozilla.org/en-US/firefox/addon/adblock-plus/)

I have adblock installed. It doesn't stop these ads.

---

### Post by Jeremy Reid on 2013-10-27
Do these adverts pop-up no matter what website you are on? Have you tried a clean install of Firefox?

---

### Post by pbhill on 2013-10-27
Seems to be only on websites that have other ads... (most!) Have not reinstalled. Didn't want to lose my bookmarks, etc.

---

### Post by Jeremy Reid on 2013-10-27
What might be an idea is to sync your bookmarks using Firefox Sync and do a clean install after. Are you sure this isn't an adware issue and just a problem with Adblocker not working? What websites do you use where you commonly see this issue?

---

### Post by buzzingrobot on 2013-10-27
You can also write out (export) your bookmarks to a local file and then load them (import) into a new Firefox installation.

Click the "Bookmarks" link on the menu bar.  Then, "Show All Bookmarks".  On the panel that opens, click "Import and Backup". You will see options to export and import your bookmarks.

---

### Post by philinux on 2013-10-27
> **Jeremy Reid said:**
> Do these adverts pop-up no matter what website you are on? Have you tried a clean install of Firefox?

Bookmarks> Show all bookmarks> Backup.
I still think adblock plus is your best bet and maybe noscript.

---

### Post by Johan De Cauwer on 2013-10-27
> **philinux said:**
> 
I still think adblock plus is your best bet and maybe noscript.

I tried [www.superfish.com](www.superfish.com) and it redirects to [http://wwws.superfish.com/](http://wwws.superfish.com/) wwws? Anyhow, no sound or pop-ups but my default browser is chromium. So I tried the site with Firefox (no adblock or noscript) but had the same result on ubuntu 13.10. So I guess the problem is not related to that site and thus probably related to the installaton of the OP. A virus for Ubuntu?

---

### Post by buzzingrobot on 2013-10-27
A virus seems unlikely.  Probably some detritus deposited by a misbehaving site.  Best bet is reinstalling. Firefox after a "sudo apt-get purge firefox".

by keeping system monitor open there's a chance the offending executable (if that's what it is) could be spotted, located, and removed.

---

### Post by coffeecat on 2013-10-27
[noparse]The superfish.com website didn't give me any trouble, but googling for superfish.com came up with this among others:[/noparse]

[http://malwaretips.com/blogs/superfish-window-shopper-adware/](http://malwaretips.com/blogs/superfish-window-shopper-adware/)

@pbhill, does this look familiar?

Also, I can't work out what you mean by "fogporoducts.com, and scorecard".

---

### Post by philinux on 2013-10-27
pbhill,

try clearing the firefox cache. History> clear recent.

---

### Post by oldos2er on 2013-10-27
> **philinux said:**
> Bookmarks> Show all bookmarks> Backup.
I still think adblock plus is your best bet and maybe noscript.

+1 for Noscript. It's worked for me where Adblock plus hasn't.

---

