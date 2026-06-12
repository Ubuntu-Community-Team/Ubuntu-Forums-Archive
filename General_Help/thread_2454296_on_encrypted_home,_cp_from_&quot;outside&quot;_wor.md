---
title: "on encrypted home, cp from &quot;outside&quot; works, mv doesn't"
date: 2020-11-26
forum: General Help
---

### Post by enboig on 2020-11-26
I have encrypted my home following [https://tlbdk.github.io/ubuntu/2018/10/22/fscrypt.html](https://tlbdk.github.io/ubuntu/2018/10/22/fscrypt.html)
Everything works ok, except firefox is unable to download files (while chrome does).
When I download a file, it downloads to /tmp, but cannot be moved to ~/Downloads

Opening a console and going to /tmp/mozilla-..../ I can **cp** the file to my home, but **mv** fails (operation not permited)

The files is 660 and the destination folder is 775, so it shouldn't be a permission problem.

Any idea?

Thanks

---

### Post by TheFu on 2020-11-29
Why would a file downloaded by chrome be in a  /tmp/mozilla-... directory?
You've lost me.

Also, using a deprecated encryption method probably has risks.  There are reasons why HOME directory encryption was removed from Ubuntu.  Use whole partition encryption if that is your desire based on LUKS and dm-crypt.

File permissions for move require delete authority on the source and create authority on the target. Those are controlled by the respective directories.

Is the Chrome browser a snap package?  If so, I'd really be surprised if downloads to /tmp/ are allowed at all.  Snaps run in a constrained environment which usually only allows writes to HOME.  You can read more about this at: 
[LIST]
[*][https://snapcraft.io/docs/snap-confinement](https://snapcraft.io/docs/snap-confinement)
[*][https://snapcraft.io/docs/removable-media-interface](https://snapcraft.io/docs/removable-media-interface)
[*][https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)
[*]
[/LIST]

---

