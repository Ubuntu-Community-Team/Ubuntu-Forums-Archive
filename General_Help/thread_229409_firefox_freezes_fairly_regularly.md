---
title: "firefox freezes fairly regularly"
date: 2006-08-04
forum: General Help
---

### Post by OneSeventeen on 2006-08-04
Lately firefox has been freezing on a regular basis on all my ubuntu machines.  Is there a way I can view error codes and stuff like that to track down what is going on?

This especially happens on media-centered sites, such as video.google.com and other sites that use flash for navigation.

about:plugins shows application/x-shockwave-flash and application/futuresplash, and I have the following extensions installed:
[list]
[*]English (GB) Language pack
[*]Permit Cookies
[*]NoScript
[*]Web Developer
[*]Gmail Notifier
[*]Pearl Crescent Page Saver Basic
[*]Tab Mix Plus
[/list]

I know this might better go in the mozillazine forums, but I wanted to check if other ubuntu users were having similar problems first.

---

### Post by Arisna on 2006-08-04
I had a similar problem for a long time, except Firefox (or any Mozilla browser) would crash instead of freezing.  The problem seems to be with SVG content.  This may be a related issue.  Try the following command in a Terminal and see if you are able to use those sites properly for the rest of the session:

```
export XLIB_SKIP_ARGB_VISUALS="1"
```

If that takes care of the problem, you may want to append the above variable assignment (just take off the "export" part) to the file /etc/environment.

---

### Post by lorenco on 2006-08-04
I aslo have some crashes... .this only started a while ago.  (After an upgrade ???)  I will thry the SVG option but think there is a problem with the latest firefox on ubuntu (PS I'm running Kubuntu

---

### Post by OneSeventeen on 2006-08-04
Well, that didn't seem to fix it.

Here's the steps it takes to freeze my browser:
[list=1][*]Go to flash powered website
[*]Click on a link before the flash has loaded
[/list]Done!

Maybe it is just a faulty flash player, or there needs to be an update since all the firefox changes?

---

