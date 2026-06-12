---
title: "Will getting 18.04.1 change my desktop from Unity to Gnome?"
date: 2018-04-19
forum: General Help
---

### Post by pretty_whistle on 2018-04-19
Unity is no longer included with Ubuntu so does this mean upgrading to 18.04.1 will change Unity to Gnome?

---

### Post by mc4man on 2018-04-19
Not really, may depend on what you're upgrading from on how & what happens. The upgrade will add gnome-shell if not already installed, won't remove unity if installed.

---

### Post by pretty_whistle on 2018-04-19
I am upgrading from 16.04.4 with Unity desktop.

---

### Post by mc4man on 2018-04-19
Assuming you upgrade with ubuntu-desktop package installed in 18.04 that'll pull in gnome-shell, ect. ( recommended to kept installed for the upgrade..
The ubuntu-session package will upgrade to one that runs a gnome-shell session.
Unity will upgrade to the latest 18.04 version (yes people, unity has been updated numerous times in 18.04), whether that upgrade pulls in the new unity-session package I don't know as it's only a recommend of unity.
You currently are using lightdm so that will get updated &  remain but  gdm3 will get installed, which will become the default dm I've no idea. 

Assuming you want to keep unity & assuming the release upgrade goes well then after the upgrade you could install this new meta package if unity session feels incomplete or there is no unity option at the login screen.
ubuntu-unity-desktop

---

### Post by pretty_whistle on 2018-04-19
Ok. Now all I have to do is to decide if I'm going to keep Unity or try Xcfe.

Thanks.

I'll mark this solved.

---

