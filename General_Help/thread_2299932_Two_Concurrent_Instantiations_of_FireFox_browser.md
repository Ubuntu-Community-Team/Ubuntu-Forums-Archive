---
title: "Two Concurrent Instantiations of FireFox browser"
date: 2015-10-22
forum: General Help
---

### Post by lusbyclark2 on 2015-10-22
I am wondering if it is possible to open two instantiations of the FireFox browser concurrently in Ubuntu Linux.  If it is,  please explain the procedure.  It must be at least somewhat complicated because I have tried the easy way without success.

---

### Post by Dennis N on 2015-10-22
Yes you can, but to get guidance, I suggest you put your question in a support form like General Help.

---

### Post by Bucky Ball on 2015-10-22
*Thread moved to **General Help**.*

And so it was. :) The area you posted in originally is a non-support area. 

Well, I use shortcut keys for everything, Windows key (super)+f for Firefox. If I hit that once it launches FF. If I then hit the combo again, it opens another instance of FF.

When you say you tried it the easy way, what is the easy way? You launch FF then hit the icon again and it doesn't launch another instance of FF?

I don't know if this suggestion is any good to you as don't know why you want to open two instances of FF, but in the top right hand corner of FF, just below the close/minimise buttons and just above the FF menu button, you will see a square with little rectangles inside (see box middle right in attached pic). If you hit that it shows you tab groups. You can arrange your tabs into groups then just switch between the groups. 

:)

---

### Post by deadflowr on 2015-10-22
Do you want two instances of the same installed version, or two different versions running at once?

If two instances of the same version, in Unity all you need to do to start a second instance is to middle-mouse-button click on the firefox icon.

if you mean how to install and run two different version we'd probably need more info on how you want to go about it.

Also, what was the easy way?

---

### Post by vasa1 on 2015-10-22
> **Bucky Ball said:**
> ...
Well, I use shortcut keys for everything, Windows key (super)+f for Firefox. If I hit that once it launches FF. If I then hit the combo again, it opens another instance of FF.

When you say you tried it the easy way, what is the easy way? You launch FF then hit the icon again and it doesn't launch another instance of FF?
...
I've gone the other way ;) I set up Super+F to open Firefox if it isn't running or to give it focus if it is running but is not in focus. (That way, I don't have to Alt-tab through other open applications or use the mouse to click on the Firefox icon in my taskbar.)

I too am curious about the easy way that didn't work and also about why OP wants two separate instances of Firefox.

---

### Post by Dennis N on 2015-10-22
You can use the same Firefox installation with different profiles (different set of bookmarks, passwords, different theme, etc) and select which to use at launch using the profile manager, or you could have two different launchers.

Profiles are covered here:

[https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

You could also have two distinct Firefox installs (perhaps a different version for development testing, for example). If one Firefox is the version from the repository, the other would have to be manually installed from a Firefox tarball in a different location, and then you would need to create a separate profile* and separate launcher for it to reflect the different location. I would install the second one in /opt

*otherwise, it will use the default, which the original Firefox is already using. That is not desirable.

---

### Post by Bucky Ball on 2015-10-22
@lusbyclark2: You seem to have marked this solved but have not shared how you solved it. Could you please share with the community how you resolved your issue, if you did. Thanks. :)

---

