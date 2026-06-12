---
title: "New tab homepage ver 0.3 won't install, Firefox 2.0.0.14"
date: 2008-06-01
forum: General Help
---

### Post by randyrick on 2008-06-01
Hello.

I'm not sure what has since changed but for more than a few days now, I'm unable to use New Tab Homepage on my Firefox 2.0.0.14. I tried uninstalling, then re-installing from the Firefox add-ons page but I always get this error message

"New Tab Homepage 0.3 could not be installed because it is not compatible with Firefox 2.0.0.14..."

Which is weird since the section to where you install 0.3 specifically mentions that it's for Firefox 2.0.0.14.

[https://addons.mozilla.org/en-US/firefox/addons/versions/777](https://addons.mozilla.org/en-US/firefox/addons/versions/777)

I'm running Ubuntu 7.10, has anyone else experienced this?

Until it's fixed, I'll just use NewTabURL ([https://addons.mozilla.org/en-US/firefox/addon/2221](https://addons.mozilla.org/en-US/firefox/addon/2221)).

---

### Post by Nepherte on 2008-06-01
Step 1: Download new tab homepage to your disk.

Step 2: Unpack the file to your disk using the default archive manager (file-roller).

Step 3: Open the file 'install.rdf' that was created when unpacking, change the value of maxVersion to 2.0.0.14 and save the file.

Step 4: Repack all the files and folders (including the modified one) to a zip archive. After creating the archive, rename the extension to .xpi

Step 5: Install the new .xpi in firefox and it should work.

---

### Post by randyrick on 2008-06-01
Thanks!

---

