---
title: "reset user profile ubuntu 16.04"
date: 2016-12-20
forum: General Help
---

### Post by dreamquartz on 2016-12-20
Hi all,

Installed KDE, and almost immediately removed it again from 16.04 LTS.
Result: default font has changed on my account.
Created a new user, and it has default font settings (ubuntu regular 11), so it is definitively user related.
Need to reset the font to "ubuntu regular 11" again.
Cannot find where settings are stored on a user.

Indexed everything via Recoll, but that does not help either to locate the setting.

Can anyone please indicate where to to find it, because I do not want to remove the user (loosing a lot of file permissions) or reinstall ubuntu (overkill) at this point.

Joe

---

### Post by oldos2er on 2016-12-20
Do you have Unity Tweak Tool installed? If so, see [http://www.omgubuntu.co.uk/2016/03/how-to-change-ubuntu-desktop-font](http://www.omgubuntu.co.uk/2016/03/how-to-change-ubuntu-desktop-font)

---

### Post by ajgreeny on 2016-12-20
This may or may not help you, but when I added the KDE system-settings package and used it to configure the two KDE applications I use on my Xubuntu desktop, everything went very strange in terms of font display and rendering.

After some searching I found there was a new file sitting in my home which when removed restored all my fonts to what I had previously set in Xubuntu settings-manager.  I now have this short note saved as a reminder of what to do if this should ever happen again.
> FONT RENDERING CONFIGURATION - KDE
File in ~/.config/fontconfig/fonts.conf can cause rendering to become thin and spidery.  Remove for proper gtk rendering.
See if you now have a file similar to this in your home, and if so, trash it to see if that also restores your settings to what you want.
You may need to logout and in again for the changes to take effect, but I can't remember.

---

