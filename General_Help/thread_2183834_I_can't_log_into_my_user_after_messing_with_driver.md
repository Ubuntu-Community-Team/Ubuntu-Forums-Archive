---
title: "I can't log into my user after messing with drivers."
date: 2013-10-26
forum: General Help
---

### Post by AleveSicofante on 2013-10-26
Thinkpad T400 laptop here, with both Intel and AMD (old) graphics. I normally use Intel graphics only, but I wanted to check the AMD ones too, so switched them in the BIOS, booted again, to see a stretched picture. I though it might get better with fglrx, but I now know those don't have support for the Radeon 3470 in this laptop. So I just removed them, switched back to Intel in the BIOS, reinstalled xorg, etc. following instructions at many places on the internet, "just in case".

Now I can't login to my main user (pablo). It actually logs in but I can't see Unity at all. I must return to the login screen with Ctrl+Alt+Del.

I just created a temporary user on the terminal via Ctrl+Alt+F1 (the one I'm using right now to write this) and have no issues with it, nor with the guest user.

I'm posting here my .xsession-errors file in hopes that some brave soul can catch where the problem is:

EDIT: Removed by author

I know there are a number on uninstallations that left some dirt behind, but those don't seem to be but warning errors.

Thanks in advance for any help.


EDIT: Solution found here: [http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels](http://askubuntu.com/questions/204428/unity-missing-cant-see-top-or-side-panels) Unity wasn't starting. I just went to a terminal via Ctrl+Alt+T, launched ccsm and enabled Unity.

---

### Post by bapoumba on 2013-10-26
Please see here : 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765)
Comment #11 may have a workaround, if the following line is indeed the one to look at
```
compiz (core) - Error: Plugin 'opengl' not loaded.
```

Edit : Oh, I see you fixed it :)

---

### Post by AleveSicofante on 2013-10-26
Thank you for your help anyway. :-)  I searched and searched, tried every solution I found, for many hours. Then I finally decided to ask for help here and right after that I typed the magical search terms and the solution appeared (can't even remember which exact search terms I used). This is some Murphy's Law or something. Happens to me all the time... ;-)

---

### Post by bapoumba on 2013-10-26
> **AleveSicofante said:**
> Thank you for your help anyway. :-)  I searched and searched, tried every solution I found, for many hours. Then I finally decided to ask for help here and right after that I typed the magical search terms and the solution appeared (can't even remember which exact search terms I used). This is some Murphy's Law or something. Happens to me all the time... ;-)
Eheh, happens to everyone all the time !
Once you've worded out and written down your problems, poof, light comes in. Not only with computer issues, btw ;)

---

