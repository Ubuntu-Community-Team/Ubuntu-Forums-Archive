---
title: "flashplugin installer unavailable for Ubuntu 20.10"
date: 2020-10-23
forum: General Help
---

### Post by Herber on 2020-10-23
I cannot use flash in firefox or chromium because there is no flashplugin installer  for Ubuntu 20.10.  I know flashplayer is an unsecure add-on, but it is the only way to watch my SLINGPLAYER in linux.  Is there any  solution other than going back to 20.04?

---

### Post by Dennis N on 2020-10-23
Enable "Canonical Partners" repository in **Software and Updates > Other Software **and you can install **adobe-flashplugin** which is the same.

---

### Post by Impavidus on 2020-10-23
Note that in just two months Adobe will finally pull the plug on Flash. Hope you've got an alternative by then. There are very few sites still requiring Flash. I haven't seen one in years.

---

### Post by QIII on 2020-10-23
If you use a Windows machine running Flash, you get a dialog pop-up indicating that it is headed for the scrap heap and asking if you want to uninstall it.

You may want to contact whoever it is you are getting the content from and ask them whether they are going to provide it.

---

### Post by scorp123 on 2020-10-24
> **Herber said:**
>  Is there any  solution other than going back to 20.04?

Yes. Do not use Flash anything. That's dead technology and "end of life" anyway. It will stop working after December 31, 2020 and there will be no further updates ever. Adobe themselves will try and block it from running after that date.

[https://www.adobe.com/products/flashplayer/end-of-life.html]("https://www.adobe.com/products/flashplayer/end-of-life.html")

> " ... Adobe will be removing Flash Player download pages from its site and Flash-based content will be blocked from running in Adobe Flash Player after the EOL Date. ..." 

---

### Post by walts48 on 2020-10-24
> **Herber said:**
> I cannot use flash in firefox or chromium because there is no flashplugin installer  for Ubuntu 20.10.  I know flashplayer is an unsecure add-on, but it is the only way to watch my SLINGPLAYER in linux.  Is there any  solution other than going back to 20.04?

Ask the developers of SLINGPLAYER to update the application to use more secure modern technology. :?:

---

### Post by Herber on 2020-11-09
Thanks to all who replied.  I have found a solution.  The submitted answers don't work because apparently there is no File "adobe-flashplugin" for ubuntu 20.10 available through the software center. 

The file must be downloaded from the site "https://www.ubuntuupdates.org/package/canonical_partner/groovy/partner/base/adobe-flashplugin".  After downloading the file has to be moved out of the "downloads" folder as it cannot be installed from the "downloads" folder.  I moved to the "documents" folder and then double-click the file to launch the software center and install.

---

### Post by TheFu on 2020-11-09
> **walts48 said:**
> Ask the developers of SLINGPLAYER to update the application to use more secure modern technology. :?:

Sllngbox has announced they aren't doing any more development on their platform and will disable all their services in 2 yrs. No clue how this relates to slingplayer.

---

