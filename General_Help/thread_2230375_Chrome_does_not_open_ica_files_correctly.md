---
title: "Chrome does not open ica files correctly"
date: 2014-06-18
forum: General Help
---

### Post by togmolodon66 on 2014-06-18
OS: Ubuntu Trusty 64bit
Browser: Google Chrome Version 35.0.1916.153
Citrix Receiver: Version 13

Citrix receiver (ica files) no longer work i.e., does not open correctly with wfica when using Google Chrome v35 and newer. The same does however work when done using Firefox version 30.

Chrome plugin list does not show the Citrix Receiver plugin. Moreover, the solutions described in the following URL's does not work either:

[http://ubuntuforums.org/showthread.php?t=1645173](http://ubuntuforums.org/showthread.php?t=1645173)
[http://support.citrix.com/article/CTX136578](http://support.citrix.com/article/CTX136578)

Thanks!

---

### Post by togmolodon66 on 2014-06-19
Was able to finally resolve this by repeating the procedures enumerated here [http://ubuntuforums.org/showthread.php?t=1645173](http://ubuntuforums.org/showthread.php?t=1645173), then made some additional changes, and they are as follows:

1. Edit **[COLOR=#000000].local/share/applications/mimeapps.list [/COLOR]**file using your favorite text editor, look for this line --> "application/x-ica=google-chrome.desktop;wine-extension-xbk.desktop;" and delete it, make sure that only the following should pertain to .ica files --> application/x-ica=wfica.desktop

2. Login to your Citrix site, from there click on any of the published application via XenApp, and save te file.

3. Go to the directory where you saved the launch.ica file, then right click, and choose "Always open with Citrix Receiver".

That's all there is to it!

HTH.

---

