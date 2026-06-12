---
title: "Upgrade to 18.04, Need &quot;print_plugin' module"
date: 2019-12-04
forum: General Help
---

### Post by newbiemike on 2019-12-04
I've used Gourmet Recipe Manager app under Ubuntu 14 and 16 with no problems but upgrading to 18.04 I can no longer email recipes from the app. To do so requires a Printing and PDF Export plugin, but while attempting to activate the plugin I get the following error message:

ImportError: No module named print_plugin

You may need to install additional python packages for this module to work properly. If you have a package management system on your computer, use it to search for a package containing "print_plugin", such as "python-print_plugin" or "print_plugin"

I've tried to search synaptic for the appropriate package to no avail.

Again, this error did not occur with previous versions of Ubuntu.  Help appreciated as always.

Thanks,

Mike

---

### Post by DuckHook on 2019-12-04
Perhaps [this]("https://askubuntu.com/questions/1185579/printing-pdf-export-plugin-for-gourmet-recipe-manager-0-17-4") workaround might work?

---

### Post by newbiemike on 2019-12-04
Thanks, unfortunately that doesn't work, I still get the same error when I try to enable the plugin.

---

### Post by DuckHook on 2019-12-04
Perhaps pay special attention to the workaround in the very last comment/reply. Aside from that, I'm afraid I have no further suggestions. You may wish to add your voice to the launchpad bug report referenced in the link. It may help to fix the problem in a future release.

---

### Post by newbiemike on 2019-12-05
I gave the workaround another try and then played around with the plugins in Gourmet and now it works.

Thanks so much ! :-)

Mike

---

### Post by DuckHook on 2019-12-05
If you would care to detail the steps that you took, then mark this thread "solved", it may help someone else who comes across this thread in the future. It would also be appreciated by the community.

---

### Post by newbiemike on 2019-12-06
The problem was resolved with this workaround:

[https://askubuntu.com/questions/1185579/printing-pdf-export-plugin-for-gourmet-recipe-manager-0-17-4](https://askubuntu.com/questions/1185579/printing-pdf-export-plugin-for-gourmet-recipe-manager-0-17-4)

Then the Printing and PDF Export plugin in Gourmet can be activated successfully.  It is also necessary to active the Send to Email plugin.

---

