---
title: "xorg server crashes when ubuntuguide.org is opened in firefox"
date: 2008-04-25
forum: General Help
---

### Post by kswenson on 2008-04-25
This is bizarre!

I log on to my 8.04 setup and open a firefox window...
  then put ubuntuguide.org into the location bar and press enter.
THE XSERVER CRASHES and I'm kicked back to the gdm login screen!

Does anyone know what is going on here?

---

### Post by shade on 2008-04-25
I don't know what's causing it, but I can confirm that I'm seeing the same behavior on my 8.04 install.  I looked in Xorg's log file but it doesn't seem to have any useful info in it.  Very weird.

---

### Post by Dev'olution on 2008-04-26
i find that without compiz enabled its fine... but with compiz enabled... it crashes :confused:

---

### Post by kswenson on 2008-04-26
I find that it happens even when compiz is off for me.
I too don't have anything in my xorg log file but /var/log/messages give the following message when I open that web page:

Apr 26 13:35:55 reba kernel: [  414.452678] klauncher[14191]: segfault at 00000095 eip b74efee7 esp bff86050 error 4

I'm not sure what the klauncher thing is about considering I'm running gnome?

kms

---

### Post by RawMustard on 2008-04-26
Install NoScript extension in Firefox and the problem will go.  How anyone could surf the web without NoScipt is beyond my comprehension these days, so much crapolla going on in the background it's not funny any more.  Anyway, that site works fine with javascript disabled!

---

### Post by chrisccoulson on 2008-04-26
What's at the end of /var/log/Xorg.0.log.old after the Xserver has restarted and you're logged back in again?

---

### Post by SOULRiDER on 2008-04-26
Im running Debian, Kernel 2.6.24-1-686 no compiz and its not crashing for me.

---

### Post by MrSnazzy on 2008-04-26
This is happening to me too. I'm pretty sure I could go before I started using compiz, but since it crashes me, whether compiz is disabled or not.

(btw, thanks for the NoScript suggestion)

---

### Post by astroboy78 on 2008-04-27
From the tests I did, I think the problem comes from Firefox 3.0b5. Just uninstall 3.05b and reinstall 2.0.0.14, and everything will come back to normal (sort of)... 

FF 3.0 is just not quite stable in my opinion! Just wait for the final release! :(

I know it's not helping the developers to uninstall an application, but don't you find it odd that a site that helps people troubleshooting issues is causing more issues without solving any? :confused:

---

### Post by aznoohwee on 2008-04-29
check out [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222277]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/222277") for a temporary solution.

---

### Post by jaakkop on 2008-05-01
This kept happening for me also. I reinstalled nvidia-glx-new and it works now... and I don't use compiz or any other compositing window manager.
<edit>It seems that I didn't have any GLX enabled. After enabling it again, the X will still crash when entering ubuntuguide.org.</edit>

---

### Post by perspectoff on 2008-05-01
> **RawMustard said:**
> Install NoScript extension in Firefox and the problem will go.  How anyone could surf the web without NoScipt is beyond my comprehension these days, so much crapolla going on in the background it's not funny any more.  Anyway, that site works fine with javascript disabled!

Amen, brother.

AdBlock, too.

---

### Post by kswenson on 2008-06-30
After some number of updates the problem seems to be cleared up now.

---

