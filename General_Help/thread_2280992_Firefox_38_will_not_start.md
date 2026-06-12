---
title: "Firefox 38 will not start"
date: 2015-06-03
forum: General Help
---

### Post by x1a4 on 2015-06-03
I upgraded Firefox to version 38.0.5 and it will not start.  The error is

```

1433352464222	addons.xpi	WARN	Error loading bootstrap.js for {1280606b-2510-4fe0-97ef-9b5a22eafe30}: TypeError: redeclaration of let win (resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/ula/.mozilla/firefox/lfosqfb7.default/extensions/%7B1280606b-2510-4fe0-97ef-9b5a22eafe30%7D.xpi!/bootstrap.js:278:6) JS Stack trace: @XPIProvider.jsm:4348:1 < XPI_loadBootstrapScope@XPIProvider.jsm:4348:7 < XPI_callBootstrapMethod@XPIProvider.jsm:4423:1 < addMetadata@XPIProvider.jsm:3343:1 < XPI_processFileChanges@XPIProvider.jsm:3452:23 < XPI_checkForChanges@XPIProvider.jsm:3613:34 < XPI_startup@XPIProvider.jsm:2097:25 < callProvider@AddonManager.jsm:208:12 < _startProvider@AddonManager.jsm:669:5 < AMI_startup@AddonManager.jsm:840:9 < AMP_startup@AddonManager.jsm:2471:5 < AMC_observe@addonManager.js:55:7
1433352464224	addons.xpi	WARN	Add-on {1280606b-2510-4fe0-97ef-9b5a22eafe30} is missing bootstrap method install
firefox: symbol lookup error: /usr/local/firefox-38.0.5/libxul.so: undefined symbol: gtk_widget_set_can_focus

```

Please help.  Thank you kindly.

---

### Post by NoWayWin8 on 2015-06-03
Start Firefox in Safe Mode. ```
$ firefox --safe-mode
``` Open Add-on manager with **CTRL+SHIFT+A**.  Under 'Appearance' set it to the **Default** theme. Also check your add-ons for compatibility with FF 38.0.5

---

### Post by x1a4 on 2015-06-04
Thank you for your reply.  Can't start in Safe Mode.

The error is: 

```

firefox: symbol lookup error: /usr/local/firefox-38.0.5/libxul.so: undefined symbol: gtk_widget_set_can_focus

```

---

### Post by cogset on 2015-06-04
Not to be pedantic, but it should be:
```
$ firefox -safe-mode
``` not ```
$ firefox --safe-mode
```

---

### Post by ajgreeny on 2015-06-04
You should try renaming the hidden .mozilla in your home as .mozillabak as it is possibly your profile at fault.

---

### Post by sandyd on 2015-06-04
> **x1a4 said:**
> I upgraded Firefox to version 38.0.5 and it will not start.  The error is

```

1433352464222	addons.xpi	WARN	Error loading bootstrap.js for {1280606b-2510-4fe0-97ef-9b5a22eafe30}: TypeError: redeclaration of let win (resource://gre/modules/addons/XPIProvider.jsm -> jar:file:///home/ula/.mozilla/firefox/lfosqfb7.default/extensions/%7B1280606b-2510-4fe0-97ef-9b5a22eafe30%7D.xpi!/bootstrap.js:278:6) JS Stack trace: @XPIProvider.jsm:4348:1 < XPI_loadBootstrapScope@XPIProvider.jsm:4348:7 < XPI_callBootstrapMethod@XPIProvider.jsm:4423:1 < addMetadata@XPIProvider.jsm:3343:1 < XPI_processFileChanges@XPIProvider.jsm:3452:23 < XPI_checkForChanges@XPIProvider.jsm:3613:34 < XPI_startup@XPIProvider.jsm:2097:25 < callProvider@AddonManager.jsm:208:12 < _startProvider@AddonManager.jsm:669:5 < AMI_startup@AddonManager.jsm:840:9 < AMP_startup@AddonManager.jsm:2471:5 < AMC_observe@addonManager.js:55:7
1433352464224	addons.xpi	WARN	Add-on {1280606b-2510-4fe0-97ef-9b5a22eafe30} is missing bootstrap method install
firefox: symbol lookup error: /usr/local/firefox-38.0.5/libxul.so: undefined symbol: gtk_widget_set_can_focus

```

Please help.  Thank you kindly.
What version of Ubuntu is this?

You will see this error on older (unsupported) versions of Ubuntu due to too-old libraries.

---

