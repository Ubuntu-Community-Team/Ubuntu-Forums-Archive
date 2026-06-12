---
title: "Repository problems:"
date: 2017-08-05
forum: General Help
---

### Post by Donnut on 2017-08-05
I'm trying to update my Intel HD Graphics card and I keep getting these errors. Any idea on how to fix them?

```
W:GPG error: https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease: The following signatures couldn't be verified because the public key is not available: 
NO_PUBKEY 611B903CAB97EA77, E:The repository 'https://download.01.org/gfx/ubuntu/17.04/main zesty InRelease' is not signed., W:Updating from such a repository 
can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 
'http://ppa.launchpad.net/killhellokitty/themes.ppa/ubuntu zesty Release' does not have a Release file., W:Updating from such a repository can't be done securely, and is 
therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., 
E:The repository 'http://ppa.launchpad.net/tualatrix/next/ubuntu zesty Release' does not have a Release file.  [  ] &#9702;rc/main-window.c/on_transaction_finished: Package 
transaction finished with an error
```

---

### Post by #&amp;thj^% on 2017-08-05
I don't think they have Zesty setup for that.
You may have to change you source to use xenail instead. (This could be risky though)
See this [https://01.org/linuxgraphics/forum/graphics-installer-discussions/new-ubuntu-16.04-packages-use-unknown-key-again](https://01.org/linuxgraphics/forum/graphics-installer-discussions/new-ubuntu-16.04-packages-use-unknown-key-again)
Also same for this one.
```
:The repository 'http://ppa.launchpad.net/tualatrix/next/ubuntu**_ zesty Release' does not have a Release file._**  [  ] &#9702;rc/main-window.c/on_transaction_finished: Package 
transaction finished with an error
```

---

### Post by Frogs Hair on 2017-08-05
The PPA below has not been updated since 14.04.  Ubuntu Tweak is no longer maintained and use at your own risk. You can disable the source from software & updates and continue to use the application or use the Unity Tweak Tool as replacement for many of the same functions.

```
http://ppa.launchpad.net/tualatrix/next/ubuntu zesty Release' does not have a Release file. 
```

---

### Post by Donnut on 2017-08-05
Is there a way to manually install the video drivers? My 3D performance is pretty poor and I don't want to reformat and start over...
```
Updating from such a repository can't be done securely, [B]and is 
therefore disabled by default[/B].,
``` Way to enable it?

---

### Post by #&amp;thj^% on 2017-08-06
The instructions to add the key is on the download page

[https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.5](https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.5)

tell you how to install the GPG key so you can verify the update tool. 

I would just install the Debs but that's just me.;)


   [* amd64.deb]("https://download.01.org/gfx/ubuntu/17.04/main/pool/main/i/intel-graphics-update-tool/intel-graphics-update-tool_2.0.5_amd64.deb")
[   * i386.deb]("https://download.01.org/gfx/ubuntu/17.04/main/pool/main/i/intel-graphics-update-tool/intel-graphics-update-tool_2.0.5_i386.deb")

This version is already in Artful
```
apt policy intel-graphics-update-tool
intel-graphics-update-tool:
  Installed: 2.0.5
  Candidate: 2.0.5
  Version table:
 *** 2.0.5 100
        100 /var/lib/dpkg/status

```

---

### Post by Donnut on 2017-08-06
OK, I feel stupid... First, I installed the key which I would have done before had I scrolled down the page and read, and the repositories were from outdated themes! Disable them, add the key, and presto! It works!!! Thanks for all your help!

---

