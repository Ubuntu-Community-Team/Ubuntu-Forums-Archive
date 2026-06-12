---
title: "How do I create my own custom distro?"
date: 2006-09-13
forum: General Help
---

### Post by erwinquita on 2006-09-13
I was wondering how do you go about creating a custom ubuntu distro? ex fluxbuntu or icebuntu. I wan't to create a disto of my own. can you give me info or links. Any help would be appreciated.

Thanks!

---

### Post by BoHu on 2006-09-13
I am interested in this too. Would like to make a really stripped down distro based on Xubuntu to run on hand-me-down Win95/98 computers. Something like a newer version of Beatrix.

---

### Post by Christopher Cook on 2006-09-13
It takes a LOT of programming. However, people do not just put "making a distro" on the web. I myself have looked, but eventualy gave up.

---

### Post by Christopher Cook on 2006-09-13
Also, just tinker with the ubuntu code, to get started

---

### Post by 3rdalbum on 2006-09-13
Reconstructor will help you there.

[http://reconstructor.aperantis.com/]("http://reconstructor.aperantis.com/")

Find all the Gnome stuff, and type every one of those packages into the "Custom Remove" field. Find the metapackage for the Fluxbox or IceWM or whatever that you want to install, and put its name into the Custom Install field.

Reconstructor will download the new packages from the web and put them into your ISO. Awesome program. Use the new beta version, it's a little easier to use. And don't forget to read the manual - good tips in it.

---

### Post by bionnaki on 2006-09-13
no need to create your own distro. just use gentoo or linux-from-scratch. or even archlinux.

---

### Post by Crayoneater on 2006-09-13
i'm not sure if this is what you are looking for but you could try UCK (ubuntu customization kit)...it lets you take an ubuntu cd and add/remove programs and do some other stuff too....

---

### Post by erwinquita on 2006-09-13
I'm interested on how did ubuntulight really striped the application and customize it to fit light apps packages. Not just forking the application you wan't to the existing ISO ubuntu installer and not using UCK tools or reconstructor.

Is this the right path to go?
[http://www.tldp.net/HOWTO/Debian-Binary-Package-Building-HOWTO/index.html]("http://www.tldp.net/HOWTO/Debian-Binary-Package-Building-HOWTO/index.html")

---

