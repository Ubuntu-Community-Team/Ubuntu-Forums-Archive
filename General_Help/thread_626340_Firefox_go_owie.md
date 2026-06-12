---
title: "Firefox go owie"
date: 2007-11-29
forum: General Help
---

### Post by Drake2k on 2007-11-29
Today there was a new patch available.  I'm excited to even be able to do them now that my tzdata stuff is fixed.  *cheer for ubuntuforums.org*

after the patch my firefox is acting funny.  When I come to the ububntu forums and click on reply, quote, or anything of the sort, it just shuts down.  SPLAT!  No warning or anything.  I litterally had to load up IE just to come here and post this.  *cry*

Any ideas or suggestions?


I r noob

---

### Post by mpierce on 2007-11-29
What did you apply the patch to?

Why don't you try uninstalling firefox and reinstalling, i.e.,
   dpkg -r firefox (this will keep old config files) or 
  dpkg -P firefox (this will delete old config files)

Make a copy of your bookmarks in your home folder before doing anything. They will be somewhere in ~/.mozilla/

Also note which plugins you are using so you can quickly restore them.

Hope this helps...

---

### Post by Drake2k on 2007-11-29
> **mpierce said:**
> What did you apply the patch to?

Why don't you try uninstalling firefox and reinstalling, i.e.,
   dpkg -r firefox (this will keep old config files) or 
  dpkg -P firefox (this will delete old config files)

Make a copy of your bookmarks in your home folder before doing anything. They will be somewhere in ~/.mozilla/

Also note which plugins you are using so you can quickly restore them.

Hope this helps...


I really don't know what the update was.  It came in my update manager for ubuntu.  It did however make me restart firefox so I'm assuming it was a firefox update.  When I try the command above I get the following:

  ```
dpkg: dependency problems prevent removal of firefox:
 firefox-themes-ubuntu depends on firefox (>= 1.9).
 firefox-gnome-support depends on firefox (= 2.0.0.10+1nobinonly-0ubuntu1).
 yelp depends on firefox (>= 1.5).
 ubufox depends on firefox.
dpkg: error processing firefox (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 firefox

```

I can use IE or Kazahakase just fine.  The latter of which I'm using to reply to you.  I do have google toolbar and ubuntu 0.4~beta 'ubuntu firefox extension'  installed.

I tried to disable the extentions addon but it still crashed when trying to quote you.  I then tried disabling the google toolbar and had the same results.

Then I tried to uninstall the google toolbar (the other addon didn't have the option to uninstall, only disable) it still crashed.

it still go owie.

---

### Post by mysticrider92 on 2007-11-29
I would just try sudo apt-get remove --purge firefox (or apt-get remove firefox if you still want the config files). This will ask you if you want to remove those dependancies, then you can just reinstall them later.

---

### Post by Drake2k on 2007-11-29
well, I managed to uninstall everything using the synaptic package manager.  Then reinstalled everything....  no luck.

any other ideas?  Could there be an error log somewhere to check maybe?

---

### Post by Drake2k on 2007-12-05
There was an update for firefox today along with some other misc updates. Unfortunatly it still didn't fix the problem.

Is no one else having this same problem??

---

### Post by Drake2k on 2007-12-05
Quick reply test.

---

### Post by Drake2k on 2007-12-05
well, I can use the quick reply here on the forums but not the Quote.  I can use certain sites and some I can't.  This is frustrating.  /pout   I just don't know how to even troubleshoot it.

---

### Post by Anduu on 2007-12-05
Great...here I am sitting here with the update manager icon bugging me in the corner of the screen.

The release notes say the Firefox update is to fix some stability issues...nmaybe I'll wait a bit.

Can anyone else confirm this bug?

---

### Post by Drake2k on 2007-12-06
> **Anduu said:**
> Great...here I am sitting here with the update manager icon bugging me in the corner of the screen.

The release notes say the Firefox update is to fix some stability issues...nmaybe I'll wait a bit.

Can anyone else confirm this bug?


Ok...guess what...this 'quote' I'm doing is with firefox...however

I went to firefox' website and downloaded the version they have there. I unzipped it in my /drake  folder and did this

cd firefox
./firefox

it's a completely different copy of firefox but this one works....now what do I do?

---

