---
title: "Ubuntu Software Center crash: authentication error?"
date: 2012-12-22
forum: General Help
---

### Post by 3mp4th on 2012-12-22
Hi there. I'm working on my mother's netbook, which is running Xubuntu 12.10. I installed it just fine, and it's been working great. Then today, I came into work and she said that she was running into two issues, very suddenly. The two issues...

1. Upon login, she was getting a popup asking for a keyring password, which hadn't happened before. She tried to put in her login password, which is the only password she knew for this computer, and it said that it was incorrect.

2. Whilst trying to install Adobe Flash in the Ubuntu Software Center, she found that she could not install ANYTHING using the Software Center. I can use Terminal, which I used to install Flash for her, but she still would like for her Software Center, since she doesn't understand Terminal, and doesn't feel comfortable working in it.

The first issue was solved with another work-around. While I'd initially thought that the issues were related, even with the former fixed, the latter remains. I mention the former only in case it IS related and I just am not aware of it. I fixed it by deleting the default keyring and recreating it with the correct password, using Seahorse.

Now, as for what is happening with the Software Center... when I click "Install" on any program, I get this error:

"Authentication Error
Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.43'}): org.debian.apt.install-or-remove-packages"

I'm not adept enough with Ubuntu to understand what this means. I've tried everything I've found online, clearing the installer with the Terminal, restarting, everything I could think of. Nothing helps.

Additionally, the keyring popup is still happening... but at least now I can put in the password and it logs in.

Anyone have any ideas? Thanks in advance.

---

