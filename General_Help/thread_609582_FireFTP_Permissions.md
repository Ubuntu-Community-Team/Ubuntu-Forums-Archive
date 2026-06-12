---
title: "FireFTP Permissions"
date: 2007-11-11
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-11-11
This handy extension seems to have a problem

In using fireftp, in trying to browse local files, in my home directory, I cannot open any sub-folders, Fireftp gives me a permission denied dialog. I can upload whole directories but not get at the individual files inside. I can browse the file structure fine from Firefox, so this is an extension specific issue. Any one found a fix?

Here is the debug info

```


In popup

You do not have the appropriate permissions or directory does not exist.
Error message= gAlertWindow.add is not a function URL= chrome://fireftp/content/js/etc/log.js Line Number= 23

In lower pane

FireFTP 0.97.1 'Cowboy Dan', created by Mime &#268;uvalo
Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsILocalFile.isDirectory]" nsresult: "0x80004005 (NS_ERROR_FAILURE)" location: "JS frame :: chrome://fireftp/content/js/local/localDirTree.js :: anonymous :: line 109" data: no]
You do not have the appropriate permissions or directory does not exist.
Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsILocalFile.isDirectory]" nsresult: "0x80004005 (NS_ERROR_FAILURE)" location: "JS frame :: chrome://fireftp/content/js/local/localDirTree.js :: anonymous :: line 109" data: no]
You do not have the appropriate permissions or directory does not exist.
Error message= gAlertWindow.add is not a function URL= chrome://fireftp/content/js/etc/log.js Line Number= 23
```

---

### Post by Jose Catre-Vandis on 2007-11-11
Well after a couple of reboots, it seems to have sorted itself out.We shall see...

---

### Post by imbjr on 2007-11-11
I used to get that problem too - I just ended up installed one of the ubuntu-recommended FTP clients.

---

### Post by Jose Catre-Vandis on 2007-11-12
Developer Mime Cuvalo says this is a bug he is working on

---

