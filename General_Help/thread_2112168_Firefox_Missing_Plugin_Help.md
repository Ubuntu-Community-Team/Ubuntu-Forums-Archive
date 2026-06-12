---
title: "Firefox Missing Plugin Help"
date: 2013-02-04
forum: General Help
---

### Post by Shadius on 2013-02-04
Hey all,

I"m using Firefox on Ubuntu 12.04 and up until now I've been able to view PDF files within the browser. Now it tells me that I'm missing the plugin. I don't know which plugin it is. I have the add-on PDF Viewer 0.7.1 that allowed me to view PDF files within Firefox. I would just like to view PDF files within the Firefox browser again instead of downloading the file everytime since I have to use my school's Blackboard system to access the files. Please help.

---

### Post by schragge on 2013-02-04
What does 'ls /usr/lib/mozilla/plugins' show on your system?
Just guessing, do you have 'ia32-libs-xulrunner' installed? (Don't know if it is needed for PDF Viewer to work on a 64-bit system, but maybe).

Does you browser pass all the tests on [http://mozilla.github.com/pdf.js/features](http://mozilla.github.com/pdf.js/features)?

There is a [similar question](https://github.com/mozilla/pdf.js/issues/2333) on the upstream issue tracker for PDF Viewer. A developer says there it's fixed in a nightly build.

---

### Post by Shadius on 2013-02-05
> **schragge said:**
> What does 'ls /usr/lib/mozilla/plugins' show on your system?
Just guessing, do you have 'ia32-libs-xulrunner' installed? (Don't know if it is needed for PDF Viewer to work on a 64-bit system, but maybe).

Does you browser pass all the tests on [http://mozilla.github.com/pdf.js/features](http://mozilla.github.com/pdf.js/features)?

There is a [similar question](https://github.com/mozilla/pdf.js/issues/2333) on the upstream issue tracker for PDF Viewer. A developer says there it's fixed in a nightly build.

Here's my output for *ls /usr/lib/mozilla/plugins*..

```
shadius@shadius-phantom:~$ ls /usr/lib/mozilla/plugins
flashplugin-alternative.so             libtotem-gmp-plugin.so
libjavaplugin.so                       libtotem-mully-plugin.so
librhythmbox-itms-detection-plugin.so  libtotem-narrowspace-plugin.so
libtotem-cone-plugin.so
shadius@shadius-phantom:~$ 

```

It did pass all the tests. As for the *ia32-libs-xulrunner*, I don't know if I have that installed. How can I check?

---

### Post by schragge on 2013-02-05
> **Shadius said:**
> As for the *ia32-libs-xulrunner*, I don't know if I have that installed. How can I check?Sorry, I've just checked: there's no such package in Ubuntu, so you definitely don't need it.

I should explain what I was looking for. The [add-on page for PDF View](https://addons.mozilla.org/en-US/firefox/addon/pdfjs) states that
> Note: The Adobe Acrobat plugin may conflict with this viewer and should be disabled.If you once installed Adobe Reader plugin, I'd 
[list=1]
[*]open the address *about:plugins* in Firefox and check that the plugin is not present or disabled there.
[*]check for any traces of it left on system, i.e. look for file *nppdf.so*:```
find / -name nppdf.so
``` The usual locations to look for installed plugins are *~/.mozilla/plugins*, */usr/lib/firefox-addons/plugins* and */usr/lib/mozilla/plugins*, but the list is not exhaustive. [This page](http://kb.mozillazine.org/Determining_plugin_directory_on_Linux), albeit quite old and obsolete, gives the idea.
[/list]

Does your browser expose this behaviour on any PDF files or only on some? Maybe only on PDFs from some websites?

Does the [live demo](http://mozilla.github.com/pdf.js/web/viewer.html) work for you?

---

### Post by Impavidus on 2013-02-05
Pdfjs has been integrated in firefox now, but apparently isn't stable enough yet to be enabled by default. You can enable it by going to about:config (type in the address bar). Search for pdfjs.disabled and set to false (right click->toggle).

---

### Post by andrew.46 on 2013-02-20
Newest version of Firefox has now enabled this by default I believe....

---

### Post by Impavidus on 2013-02-21
Yes, now it is. That's firefox 19, installed yesterday.

---

