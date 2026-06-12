---
title: "get realplayer working in bbc site"
date: 2006-10-30
forum: General Help
---

### Post by fsman on 2006-10-30
I've found a fix to the problem of the BBC website not playing real media files in edgy.

the problem is that the totem-mozilla plugin is trying to play realmedia files - so the bbc site doesn't like it as its looking for realplayer.

If you goto firefox and then about:plugins you see that real files are associated with the totem complex plugin - even through the real plugins are in the firefox directory.

to make firefox use realplayer you need to get rid of libtotem-complex-plugin.so and libtotem-complex-plugin.spt from /usr/lib/firefox/plugins

e.g. cd /usr/lib/firefox/plugins
sudo mv libtotem-complex* ~/

now bbc site uses realplayer and all is well.

Caution - I don't know what these libtotem-complex plugins do (other than realmedia) so this is really a hack at the moment.

---

### Post by fsman on 2006-10-30
looks like a bug in totem-mozilla package

see
[https://launchpad.net/distros/ubuntu/+source/totem/+bug/66902](https://launchpad.net/distros/ubuntu/+source/totem/+bug/66902)
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/60377](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/60377)

---

### Post by jordilin on 2006-10-30
> **fsman said:**
> I've found a fix to the problem of the BBC website not playing real media files in edgy.

the problem is that the totem-mozilla plugin is trying to play realmedia files - so the bbc site doesn't like it as its looking for realplayer.

If you goto firefox and then about:plugins you see that real files are associated with the totem complex plugin - even through the real plugins are in the firefox directory.

to make firefox use realplayer you need to get rid of libtotem-complex-plugin.so and libtotem-complex-plugin.spt from /usr/lib/firefox/plugins

e.g. cd /usr/lib/firefox/plugins
sudo mv libtotem-complex* ~/

now bbc site uses realplayer and all is well.

Caution - I don't know what these libtotem-complex plugins do (other than realmedia) so this is really a hack at the moment.
Yes, you are right. You can remove the libtotem-complex-plugin.* files as they are only soft links that point to other files.
The best way to play real audio streams is using the real player plugin and  not totem, but as real player is not in the distro by default they have to put some media player to deal with them.

---

### Post by Mark76 on 2006-10-30
I've been having problems with RP/RM opening in multiple windows whenever I try to view anything on the BBC site in Opera.

I wonder if the two problems are related?

---

### Post by jordilin on 2006-10-30
> **Mark76 said:**
> I've been having problems with RP/RM opening in multiple windows whenever I try to view anything on the BBC site in Opera.

I wonder if the two problems are related?

You should have realplayer for linux installed and have the proper realplayer  plugins installed for Opera. I don't know how Opera manages plugins but probably is something related.

---

