---
title: "Controls on Mplayer Mozilla plug in???"
date: 2005-07-25
forum: General Help
---

### Post by ixus_123 on 2005-07-25
I just tried PClinux & used the Mplayer / mozilla firefox plugin on that to view some movie trailers on the Apple site.  The plugin on that system hada  handy scroll bar on the bottom with controls so I could watch the clip again, fullscreen it, puase, skip forwards backweards etc.

How do I get this in ubuntu?

---

### Post by damonw5 on 2005-07-25
[QUOTE=ixus_123]I just tried PClinux & used the Mplayer / mozilla firefox plugin on that to view some movie trailers on the Apple site.  The plugin on that system hada  handy scroll bar on the bottom with controls so I could watch the clip again, fullscreen it, puase, skip forwards backweards etc.

How do I get this in ubuntu?[/QUOTE]
 Enable all the repositories (if you haven't already):
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
Install codecs (if you haven't already):
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

Then in Synaptic install package "mozilla-mplayer" and any required dependencies. Restart Firefox and it should work! If it doesn't, post here.

---

### Post by ixus_123 on 2005-07-25
it doesn't work.  It will play video fine but I can't pause it / full screen it / re view it like I can when I apt-get it in other distros.

It's a pain becuase I usually make tea or do something else while a trailer loads, then come back & watch it but in this case it auto starts & there are no controls to watch it again short of refreshing the screen

---

### Post by claydoh on 2005-07-25
I believe you will need a newe version of the mplayer plugin, as the one in the repositories is a little dated. There is a [HOW-TO here]("http://ubuntuforums.org/showthread.php?t=44560") on how to install the latest version.

---

