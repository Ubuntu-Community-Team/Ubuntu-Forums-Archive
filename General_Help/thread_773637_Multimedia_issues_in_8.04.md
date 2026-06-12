---
title: "Multimedia issues in 8.04"
date: 2008-04-29
forum: General Help
---

### Post by ksauber on 2008-04-29
Just installed Hardy (8.04) and attempted to install multimedia codecs.

The Codecs was the "GStreamer ffmpeg video plugin"

Attempt generated this error:
 
**W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263**

Any ideas what this means? :confused:

---

### Post by FredB on 2008-04-29
Looks like you're using a 3rd party repository without the pgpkey related to it.

Just open Synaptic, Settings / Repository and manage 3rd party repository.

You will not see that error message a long time after that.

---

### Post by jocko on 2008-04-29
> **ksauber said:**
> Just installed Hardy (8.04) and attempted to install multimedia codecs.

The Codecs was the "GStreamer ffmpeg video plugin"

Attempt generated this error:
 
**[COLOR=Red]W:[/COLOR] GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263**

Any ideas what this means? :confused:

It means you haven't told apt to trust one of your third party repos (wine).
This will not prevent you from installing anything, it will just give you the warning (**[COLOR=Red]W:[/COLOR]** ...) you posted above, and if you try to install anything from the wine repo it will ask you if you really want to install from a repo that you haven't told it to trust...

This is how to fix it (if you decide to trust the wine repo, which I guess you do?) (taken from the [Wine HQ]("http://winehq.org/site/download-deb")):

Open up a terminal and paste this command:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by ksauber on 2008-05-01
Thanks for your help! :popcorn:

---

