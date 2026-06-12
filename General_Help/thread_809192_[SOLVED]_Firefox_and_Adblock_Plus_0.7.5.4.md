---
title: "[SOLVED] Firefox and Adblock Plus 0.7.5.4"
date: 2008-05-27
forum: General Help
---

### Post by TWO on 2008-05-27
Hello

I'm having a problem getting Adblock plus to install, or any Firefox add-on for that matter. I am using Firefox 2.

When I select the link to start the download, it goes through the usual motion of displaying the progress bar, but on completion I am presented with the following error message:
> 
Firefox could not install the file at [https://addons.mozilla.org/en-US/firefox/downloads/file/26635/adblock_plus-0.7.5.4-fx+tb+sm.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/26635/adblock_plus-0.7.5.4-fx+tb+sm.xpi)				
because: Unexpected installation error
Review the Error Console log for more details
-203

line: 3938


I then get the following in the Error Console:

> installLocation has no properties
file:///usr/lib/firefox/components/nsExtensionManager.js

> uncaught exception: [Exception...";[JavaScript Error: "installLocation has no properties" {file:///usr/lib/firefox/components/nsExtensionManager.js" line: 3938}]' when calling method: [nsIExtensionManager::uninstallItem]" nsresult: "0x80570021 (NS_ERROR_XPC_JAVASCRIPT_ERROR_WITH_DETAILS)" location: "JS frame :: chrome://mozapps/content/extensions/extensions.js :: anonymous :: line 1696" data:yes]



> installLocation has no properties
///usr/lib/firefox/components/nsExtensionManager.js

None of that means anything to me! The problem doesn't seem to occur under Firefox 3, but I am reluctant to upgrade as of yet since when I did use Firefox 3, it decided to close itself down a few times without reason, so I figure that I'm quite happy to wait a little longer.

I have never experienced this problem of being unable to install add-ons though in Firefox 2. 

Line 3938 is this:
```
var installLocation = this.getInstallLocation(item.id);
```

(That doesn't mean anything to me either!)

Any help would be greatly appeaciated!

Thanks

TWO

---

### Post by prince_niceguy on 2008-05-27
am not sure... but check the repos.. they have adblock for firefox 2.

---

### Post by y-lee on 2008-05-27
Open nautilus and click View and Show Hidden Folders

Now assuming you have only one Firefox profile navigate to 

```
/home/username/.mozilla/firefox/xxx.default
```

Where *username* is your ubuntu username and *xxx* is some random looking string of characters, look for the file *extensions.rdf* and Delete (or better, rename/backup) it. Firefox should recreate it when it is next started. :)

Hope this works for you.

---

### Post by ErroneousBosch on 2008-05-29
Worked great for me!

---

### Post by TWO on 2008-06-01
> **y-lee said:**
> Open nautilus and click View and Show Hidden Folders

Now assuming you have only one Firefox profile navigate to 

```
/home/username/.mozilla/firefox/xxx.default
```

Where *username* is your ubuntu username and *xxx* is some random looking string of characters, look for the file *extensions.rdf* and Delete (or better, rename/backup) it. Firefox should recreate it when it is next started. :)

Hope this works for you.

Thanks very much! That worked like a charm!

How did you know that that would be the problem??

Thanks

TWO
:)

---

### Post by y-lee on 2008-06-01
> **TWO said:**
> Thanks very much! That worked like a charm!

How did you know that that would be the problem??

Thanks

TWO
:)

I ran Firefox as root one time and somehow messed up my addons :confused: , and had to fix it. So I kinda saw this problem before :)

---

### Post by TWO on 2008-06-01
> **y-lee said:**
> I ran Firefox as root one time and somehow messed up my addons :confused: , and had to fix it. So I kinda saw this problem before :)

That's kind of crazy! But at least you found the solution!

Thanks once again!

TWO

---

