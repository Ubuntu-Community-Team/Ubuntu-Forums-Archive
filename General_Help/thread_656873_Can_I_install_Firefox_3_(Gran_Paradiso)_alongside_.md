---
title: "Can I install Firefox 3 (Gran Paradiso) alongside firefox 2?"
date: 2008-01-03
forum: General Help
---

### Post by Excalibre on 2008-01-03
I want to check out FF3 but I obviously don't want to switch to it yet; does anyone know how to use it alongside FF2 (and import my FF2 profile, hopefully without screwing it up in the process?) The version in the repositories is old (Alpha 8) and I'd like to try Beta 2, so I guess apt-get isn't an option.

Sorry, I'm sure this is something that would be relatively simple for others but I'm still pretty new at this and don't have all that much idea what I'm doing. Thanks in advance!

---

### Post by PeterJS on 2008-01-03
Found these instructions referenced in another post.
[http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html)
I don't know if it will auto import your settings when if first runs, I know that the version from the Hardy debs does.

---

### Post by ~LoKe on 2008-01-03
> **PeterJS said:**
> Found these instructions referenced in another post.
[http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/installing-firefox-30-beta-1-on-ubuntu-710-gutsy-gibbon.html)
I don't know if it will auto import your settings when if first runs, I know that the version from the Hardy debs does.

It should still use the profile from your .mozilla directory in your /home/username folder.

---

### Post by PeterJS on 2008-01-03
As a humorous aside I just installed firefox in a language I've never heard of. It caught me off gaurd, I've since gone back and gotten the right version, but that was a very what the heck few moments.

---

### Post by ~LoKe on 2008-01-03
> **PeterJS said:**
> As a humorous aside I just installed firefox in a language I've never heard of. It caught me off gaurd, I've since gone back and gotten the right version, but that was a very what the heck few moments.

Which language? I actually installed it on my Windows installation with the Korean language.  :lolflag:

---

### Post by PeterJS on 2008-01-03
Basque, right there at the top of the alphabet, I was too busy looking at the OS column to pay attention to the language rows,

---

### Post by Excalibre on 2008-01-03
> **~LoKe said:**
> It should still use the profile from your .mozilla directory in your /home/username folder.
But it won't screw up my profile, right? I mean, I want my current FF2 profile to stay in the same condition it's in now.

---

### Post by ~LoKe on 2008-01-03
> **Excalibre said:**
> But it won't screw up my profile, right? I mean, I want my current FF2 profile to stay in the same condition it's in now.

Make a backup if you're worried, but no, it shouldn't affect your profile.  At one point I had ff2 and ff3 installed and running, but only for bit.

---

### Post by Excalibre on 2008-01-03
[quote=~LoKe]Make a backup if you're worried, but no, it shouldn't affect your profile. At one point I had ff2 and ff3 installed and running, but only for bit.[/quote]

Unfortunately, it turns out it did. It seems to be pretty minor stuff, but it did indeed screw around with my profile. You'd think that the default behavior would be - for prerelease versions and major milestone releases - for the thing to create a new profile and automatically import key things like bookmarks and stored passwords, instead of requiring users to do it by hand. Especially since apparently it stores bookmarks and history and prefs in a different way - wouldn't they WANT a nice clean profile?

Anyway, I think it killed my cookies but I'm not having any other problems, so it's not a tragedy. But dang, you'd think it could be a little smarter and maybe at very least ASK before it decides to alter an existing profile.

---

### Post by ubu-for on 2008-01-03
> **~LoKe said:**
> It should still use the profile from your .mozilla directory in your /home/username folder.

I would like to install Firefox 3.0 or Iceweasel, too, but without any plugins from Firefox 2.0. Even if I only unpack for example Swiftweasel 3.0b2 and start from it's folder without installation, Swiftweasel uses the same settings and plugins like Firefox 2.0.

Is it possible? Thanks in advance.

---

### Post by ~LoKe on 2008-01-03
> **Excalibre said:**
> Anyway, I think it killed my cookies but I'm not having any other problems, so it's not a tragedy. But dang, you'd think it could be a little smarter and maybe at very least ASK before it decides to alter an existing profile.

It's in development so it's not really supposed to be "user friendly" quite yet.  But cookies...not really a big deal, is it?  It should still have your passwords saved.

---

### Post by Excalibre on 2008-01-03
> **~LoKe said:**
> It's in development so it's not really supposed to be "user friendly" quite yet.  But cookies...not really a big deal, is it?  It should still have your passwords saved.
No, like I said, not a big deal, but it seems like it should be set up for the most common way it'll be used (and if memory serves, major milestone releases of Firefox in the past were badly behaved this way too.) It's just a minor irritation, not a major bug. Whereas the lack of subpixel rendering - man, that's awful. I hope the Ubuntu people figure that one out when they do an official package of the final product.

---

### Post by Excalibre on 2008-01-03
> **ubu-for said:**
> I would like to install Firefox 3.0 or Iceweasel, too, but without any plugins from Firefox 2.0. Even if I only unpack for example Swiftweasel 3.0b2 and start from it's folder without installation, Swiftweasel uses the same settings and plugins like Firefox 2.0.

Is it possible? Thanks in advance.
I'm guessing it's the same as what I just went through. Summarized from here: [http://forums.mozillazine.org/viewtopic.php?t=613873](http://forums.mozillazine.org/viewtopic.php?t=613873)

You need to (preferably before the first time you run a new Firefox):

(a) back up your profile (it's in your ~/.mozilla/firefox directory - just make a copy somewhere.)
(b) exit FF2 and start it up with the profile manager (run the program with the -profilemanager command line option)
(c) make a new profile (call it, say, Swiftweasel30b2 or whatever) but then exit instead of starting Firefox; make sure your 'default profile' is still set to your current profile
(d) change your current FF2 launcher to use the -no-remote option
(e) set up a FF3 launcher with the options '-no-remote -profilemanager *profileName*'

This will let you use them both side-by-side (that's what the -no-remote option is for), and ensure that they're not using the same profile.

---

### Post by ogcub on 2008-01-03
Hi,
I am currently using Hardy, and I can install FF3 directly from Ubuntu repos. However, it might be not available for stable releases, I don't know

---

### Post by ~LoKe on 2008-01-03
> **ogcub said:**
> Hi,
I am currently using Hardy, and I can install FF3 directly from Ubuntu repos. However, it might be not available for stable releases, I don't know

The version in Gutsy repos is Alpha, not Beta.  Unfortunately.

---

### Post by ubu-for on 2008-01-03
> **Excalibre said:**
> (b) exit FF2 and start it up with the profile manager (run the program with the -profilemanager command line option)

You can enter "firefox -p" instead.

> **Excalibre said:**
> This will let you use them both side-by-side (that's what the -no-remote option is for), and ensure that they're not using the same profile.

Thank you very much!

---

