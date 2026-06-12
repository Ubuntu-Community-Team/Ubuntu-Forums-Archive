---
title: "Multi-user, multi-language SCIM issues"
date: 2007-10-24
forum: General Help
---

### Post by noctis_vulpes on 2007-10-24
First of all, I am on Ubuntu 7.04. Language default is set to Korean, and I have another user created with English setting.  What's really bugging me is that SCIM  won't work properly on the account that's set up to use English . Here's what's happening.

Everything works fine on both accounts if they use the system default - it didn't matter if I had set it to English or Korean. 

However, SCIM doesn't do anything as soon as I set the other account to use English as default. The little keyboard icon doesn't launch on startup, and if I bring it up with scim -d, all it does is display that little icon. Beyond that, it's not doing anything.

I can't have both accounts set to same language, since they're both uncomfortable in the other language, and I can't tell the English menu user to not use SCIM, since he needs it to work.

Is there any way to resolve this issue? I've searched everywhere but I can't even run into someone with the same problem. All I found were tips to use when SCIM doesn't work at al - which is not the case. I even tried them just in case... No dice.

If anyone can help, I'd be most obliged. It's just so annoying to be "almost" done.  I mean, there's some issues with graphics card, but that's totally beyond my ability to fix (or to search for solutions, it seems)  and it's not essential... But this is serious. Thanks in advance for any help that you might be able to offer.

---

### Post by jenhsun on 2007-10-24
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

---

### Post by noctis_vulpes on 2007-10-24
...but this is not a same bug at all. My system/keyboard doesn't freeze, and I'm not on Gutsy.

SCIM just doesn't do anything. Rest of the system is working fine, including keyboard input. It only does this on the English user account side - works fine for Korean user.

For now, I've worked around the situation by setting the default language as English and enabling Korean separately on another account (exact opposite of what I did before). This, for some crazy reason, fixes the SCIM issue on English side but now the Korean side can't use Korean/English toggle key (standard in Korean keyboards/systems).

If anyone can help, I will really appreciate it.

---

### Post by jenhsun on 2007-10-28
About anything related on SCIM, Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)

And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

### Post by jenhsun on 2007-10-31
[http://ubuntuforums.org/showpost.php?p=3676651&postcount=6](http://ubuntuforums.org/showpost.php?p=3676651&postcount=6)

---

