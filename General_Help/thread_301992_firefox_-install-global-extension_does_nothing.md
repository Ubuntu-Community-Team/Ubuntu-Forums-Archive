---
title: "firefox -install-global-extension does nothing"
date: 2006-11-17
forum: General Help
---

### Post by piti118 on 2006-11-17
I'm using edgy and firefox2.

According to [http://www.mozilla.org/projects/firefox/extensions/commandlineoptions.html](http://www.mozilla.org/projects/firefox/extensions/commandlineoptions.html) I should be able to issue firefox -install-global-extension /path/to/myextension.xpi and then it will install the extension in the global scope forme.

However, when I execute the command it returns but when I open firefox I can't find the extension. I tried to browse /usr/lib/firefox/extensions nothing gets installed.

I thought it was the permission problem. So, I tried sudo firefox -install-global-extension myextension.xpi or even su root. I tried several extensions too but none of them work.

Am I missing something?

---

### Post by bruenig on 2006-11-18
Not sure about your whole question but I can tell you that the extensions are stored in ~/.mozilla/firefox/********.default/extensions

---

### Post by piti118 on 2006-11-18
Thanks for you reply.

What I meant to do was the create a script that will install an extension to all users(current and ones that will be created in the future). 

Firefox seems to have a thing called global extension which is kind of like the default ubuntu theme for firefox which available to all users.

The documentation on mozilla site tell me that there exists a commandline argument called -install-global-extension which I could use. But, that doesn't seem to do anything.

I also tried

sudo -H firefox -install-global-extension /some/bogus/path

It didn't even complain.

---

### Post by mkoyle on 2007-01-14
I have the same problem; since 'thunderbird -install-global-extension' works fine, I suspect a problem with settings.  I did not have any luck figuring out what it is, though.

Another reference to the same problem can be found at 

[http://forums.mozillazine.org/viewtopic.php?p=2398824](http://forums.mozillazine.org/viewtopic.php?p=2398824)

---

### Post by mkoyle on 2007-01-14
I added an Ubuntu bug inquiry at launchpad.  It is probably a problem in the Debian package itself.  Anyway, that bug report for anyone that wants to check on the resolution is

[https://launchpad.net/ubuntu/+source/firefox/+bug/79352](https://launchpad.net/ubuntu/+source/firefox/+bug/79352)

--Matthew

---

