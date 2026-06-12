---
title: "Autologin for uids &lt; 1000?"
date: 2007-03-15
forum: General Help
---

### Post by guice on 2007-03-15
For a little background, I have an OSX system and Ubuntu. I needed to get NFS to work from Ubuntu to OSX. The only way to do this was to make the UIDs match.

OSX starts UIDs at 500. Ubuntu starts them at 1000. I decided to use: 569, just some random number picked. I did successfully change my UID on Ubuntu and OSX, but now I have a small problem.

Ubuntu's autologin function no longer recognizes my login account. Is there anyway to make the autologin see my user account? There has to be something within it telling Ubuntu not to look at UIDs < 1000. Where is that? And where can I set it for 500?

Actually, now that I think about it, my account doesn't show up in the Users admin panel anymore either.

---

### Post by guice on 2007-03-17
Is there no way to make Ubuntu understand traditional user logins being under 1000? There has to be a way. UID 569 or UID 1000 has no relevance as to whether this is an user account or not...

---

