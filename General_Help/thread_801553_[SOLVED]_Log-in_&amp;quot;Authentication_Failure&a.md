---
title: "[SOLVED] Log-in &amp;quot;Authentication Failure&amp;quot; (messed around with gdm)"
date: 2008-05-20
forum: General Help
---

### Post by jakeofspades on 2008-05-20
I inserting @include common-pamkeyring at the end of my /etc/pam.d/gdm file (and deleted ~/.gnome2/keyring/keyring.default  (or something like that) ) in the hope it would get the keyring password manager to automatically load my wifi passwords.

I did this - rebooted to no avail. Then thought it might be a good idea to suffix the same bit of code to the end of /etc/pam.d/gdm-autologin. Tried that - rebooted and was given "Authentication Failed" and the computer stalled.

So I went into recovery and undid my changes - but :(:( it is still doing this!

I can get internet through the recovery console so I tried reinstalling pam-keyring, gdm, ubuntu-desktop.

Also - on a kind of weird note: after the authentication failed screen I now sometimes get a login screen. But unfortunately any login attempt just results in a "Authentication Failed." All similar threads I've read are resolved with just deleting the @include common-pamkeyring. I don't see why I'm different.

Any help would be really useful, I'm in a ball of stress atm lol (which probably doesn't help)

---

### Post by jakeofspades on 2008-05-21
:( sorry for the multiple post. Still unable to find solution - I really don't want to have to re-install ubuntu and lose everything.

1) My gdm and gdm-autologin have both been edited so they're back to normal (ie I removed the @include common-pamkeyring)
2) I deleted /home/.gnome2/keyrings/login.keyring (supposedly harmless because a new one is created but I'm starting to doubt that)
3) I've reinstalled: gdm, ubuntu-desktop, libpam-keyring, libpam0g, libpam-runtime, libpam-modules.
4) I've disabled autologin

It boots up as normal to the login screen, but just says "Authentication Failed" for every login attempt. I can login at a terminal fine however...

---

### Post by jakeofspades on 2008-05-21
*bump* (sorry)

---

### Post by jakeofspades on 2008-05-22
*bump* ... I hope you see this as my level of desperation and not as an indicator of me being really annoying.

---

### Post by danwood76 on 2008-05-22
Is the gdm keymap correct?

what version of ubuntu are you using?

---

### Post by jakeofspades on 2008-05-22
Few! I've just found a bit of a shabby solution (yet nonetheless a solution!)

I installed Ubuntu on a small partition on the same HD. Booted up in it and then copied my /etc/pam.d directory to the original/broken one. I also copied the ~/.gnome2/keyrings/login.keyring file to the original system (as I had deleted that)

It now logs in fine.

On the 'new' Ubuntu installation I created the same users with the same corresponding passwords as that of the original installation.

danwood: What is the gdm keymap sorry?

---

### Post by danwood76 on 2008-05-22
Its just the keymap that gdm uses, but as your problem was specifically with pam I wouldnt worry.

In the future before deleting system files back them up to somewhere so you can restore them easily if something goes wrong, you've obviously had to go to a bit of trouble to restore those files.

---

### Post by jakeofspades on 2008-05-22
Yea fair enough I normally follow that principle.

The keyring.login file that I actually deleted seemed a harmless thing to do because your system just creates a new one when you login and it's the only way to change your keyring password.

However I think the combination of editing the /etc/pam.d/gdm file and deleting that put me in a bit of a pickle.

I think I might keep the other Ubuntu installation lurking around just as a fall back.

---

