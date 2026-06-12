---
title: "Dash returns no applications"
date: 2014-05-27
forum: General Help
---

### Post by Onesimus on 2014-05-27
When I use the Dash to search for installed applications so that I might use them, the Dash returns no results !

I have seen this on two of my machines both running Ubuntu 14.04.

Any ideas ?

---

### Post by grumblebum2 on 2014-05-27
Does it work in the guest account?
Have you uninstalled anything?

---

### Post by philinux on 2014-05-27
Try this
sudo apt-get install --reinstall unity-lens-applications unity-lens-files

then do

setsid unity

---

### Post by Onesimus on 2014-05-27
It worked in the guest account.

I logged in using Gnome fallback session so I could see my installed applications (discovered loads I'd forgotten about !) then started up Ubuntu Tweak Tool, and reset the settings to default under the search tab, then logged out.  Logged back in with Unity session, and all seems fine.

So, solved.

---

### Post by roland_1953 on 2014-08-19
Hi, there!

I have exactly the same problem, but none of the fixes above have worked for me.

When I open the dash there are no local applications listed??? 

And, yes, when I log into a guest session the apps all appear in the dash.

Regards,
Roger

---

### Post by rahul_bhise on 2015-04-16
I have exactly the same problem, but none of the fixes above have worked for me.

When I open the dash there are no local applications listed???

And, yes, when I log into a guest session the apps all appear in the dash.

---

### Post by oldos2er on 2015-04-17
It would be best to start a new thread if you need further help.

---

