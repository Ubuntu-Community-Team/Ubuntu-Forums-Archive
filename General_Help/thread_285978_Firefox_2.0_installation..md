---
title: "Firefox 2.0 installation."
date: 2006-10-27
forum: General Help
---

### Post by Gomek on 2006-10-27
I've searched for various ways to install Firefox 2.0 in Dapper, and so far I've seen that I should either upgrade to Edgy Eft or use a script to install the new version in a folder in /opt.

Well, I don't want to upgrade to Edgy, and I want to avoid installing the program into /opt.

Would it be safe for me to simply download the [firefox deb]("http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0+0dfsg-0ubuntu3_i386.deb") from the repositories and install it from that?

---

### Post by beerfan on 2006-10-27
> **Gomek said:**
> I've searched for various ways to install Firefox 2.0 in Dapper, and so far I've seen that I should either upgrade to Edgy Eft or use a script to install the new version in a folder in /opt.

Well, I don't want to upgrade to Edgy, and I want to avoid installing the program into /opt.

Would it be safe for me to simply download the [firefox deb]("http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0+0dfsg-0ubuntu3_i386.deb") from the repositories and install it from that?

The absolute safest (in my opinion, others may well disagree) way to install Firefox 2.0 in Dapper is to download the [Firefox binary](http://download.mozilla.org/?product=firefox-2.0&os=linux&lang=en-US) and extract it into your home directory (e.g. ~/bin/firefox). Then you just create a launcher for ~/bin/firefox/firefox and update the menu if you want. Running Firefox from your home directory means that you'll be able to get Firefox updates without having to run it as root and it also means that it won't conflict with the Ubuntu firefox which a lot of stuff depends on.

There are other ways that are equally viable but this is the method I'm promoting today. The best part is, if you want to switch back to Ubuntu Firefox uninstalling is as simple as rm ~/bin/firefox.

---

### Post by Gomek on 2006-10-27
To me, that falls in same category as installing it into /opt.  Thanks for your advice, but my original question remains.

---

### Post by elettronicha on 2006-10-27
> **Gomek said:**
> Would it be safe for me to simply download the [firefox deb]("http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0+0dfsg-0ubuntu3_i386.deb") from the repositories and install it from that?

You can try or, if you want, go [here]("http://getswiftfox.com/debian.htm") and download swiftfox 2.0, i.e. firefox 2.0 compiled for specific architectures, choose yours.

---

### Post by skymt on 2006-10-27
There are lots of things in Ubuntu that depend on a specific version of Firefox, for Gecko. If you install 2.0 and remove 1.5, Things Will Break unless you recompile any programs that use Gecko. That's a lot of work, so just install into /opt or ~.

---

### Post by aysiu on 2006-10-27
You want to install in Dapper the Edgy .deb of Firefox?

You're much safer using the script, honestly.

---

### Post by Gomek on 2006-10-27
Yeah, I figured that other things relied on firefox, which is why I came here to ask my question before I did anything stupid.  Just didn't know if the programs that rely on the 1.5 would be happy with 2.0 from Edgy.

As for installing into /opt or ~ or /usr/local or whatever else, I try to keep my package managagement to apt-get as much as possible.  A new version of Firefox isn't worth breaking that rule to me.

---

