---
title: "Firefox 1.5 RC 1 Released!"
date: 2005-11-02
forum: General Help
---

### Post by bierpullen on 2005-11-02
Mozilla has released the official version of the newest firefox.
[http://www.mozilla.org/products/firefox/](http://www.mozilla.org/products/firefox/)


[http://www.antarctica-rbak.nl/ubuntu/](http://www.antarctica-rbak.nl/ubuntu/)

---

### Post by Manny C on 2005-11-02
You'll be waiting a while until this hits the repos. ;)

---

### Post by 23meg on 2005-11-02
I had installed 1.5B2 with the instructions [here]("http://wiki.ubuntu.com/FirefoxNewVersion") and upgraded today with Firefox's internal updater without problems.

---

### Post by jrib on 2005-11-02
[QUOTE=23meg]I had installed 1.5B2 with the instructions [here]("http://wiki.ubuntu.com/FirefoxNewVersion") and upgraded today with Firefox's internal updater without problems.[/QUOTE]

In case anyone else can't figure out why the "Check for updates..." option in the help menu is greyed out: If you followed the [wiki]("http://wiki.ubuntu.com/FirefoxNewVersion") beta instructions, firefox won't have write permissions to the install directory.  So you have to run "$sudo firefox" and the option to update will then be available.  Just update and then restart firefox as a normal user.  Personally, I'll be waiting a couple of days for some of my extensions to update first.

---

### Post by ep_ on 2005-11-02
[QUOTE=_jason]In case anyone else can't figure out why the "Check for updates..." option in the help menu is greyed out: If you followed the [wiki]("http://wiki.ubuntu.com/FirefoxNewVersion") beta instructions, firefox won't have write permissions to the install directory.  So you have to run "$sudo firefox" and the option to update will then be available.  Just update and then restart firefox as a normal user.  Personally, I'll be waiting a couple of days for some of my extensions to update first.[/QUOTE]

Thanks Jason, I too followed those WIKI instructions on installing Firefox 1.5 beta and I was wondering why "Check for updates..." was disabled! I'll do this but it seems like sudo firefox  might be a security issue?

---

### Post by nrgtek on 2005-11-02
will fasterfox still be compatible when upgrading?

---

### Post by 23meg on 2005-11-02
No, fasterfox hasn't got a compatibility update yet. But its tweaks stay in effect after upgrading so if you have it installed already you'll still have a fast firefox; you just won't be able to readjust settings.

---

### Post by jrib on 2005-11-02
[QUOTE=ep_]Thanks Jason, I too followed those WIKI instructions on installing Firefox 1.5 beta and I was wondering why "Check for updates..." was disabled! I'll do this but it seems like sudo firefox  might be a security issue?[/QUOTE]
Maybe a more secure way would be to change ownership of the directory?   I'll just trust mozilla and do sudo though.  You are trusting mozilla just like you trust a package upgrade from a repo and run sudo apt-get (I think?).

---

### Post by domino on 2005-11-03
I'm confused about this statement, "For some reason, the mozilla.org build of Firefox is significantly faster than the default Ubuntu one". What does it really mean? Faster application loading or faster website rendering and page loading? If it's the later, there is a plugin named "fasterfox" that will actually do the same thing and tweak Firefox.

If you are experiencing the slow application loading, then you might have too much plugins loaded. At one time,I have had 30 plugins enabled and configured. It took Firefox 6 seconds to actually load the about:blank page. I trimmed it down to 14 plugins and the application loaded almost instantly.

So, what actually does "faster" mean?

---

### Post by realwhz on 2005-11-04
Hi,

Does the official build of firefox 1.5 use the GTK2 open file dialog, just as the build shipped by Ubuntu?

---

