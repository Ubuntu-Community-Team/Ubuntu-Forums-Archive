---
title: "Taming Firefox plugins"
date: 2007-04-11
forum: General Help
---

### Post by mssever on 2007-04-11
I often come agross sites that serve media content in RealMedia format using the rtsp: protocol. I have RealPlayer installed, as well as the RealPlayer plugin (technically the Helix plugin).

The problem is that Firefox ALWAYS uses the mplayer plugin to handle files of type audio/x-pn-realaudio, even though mplayer can't handle the rtsp: protocol. Is there a way to configure which plugin Firefox uses for a particular mimetype? Setting network.protocol-handler.app.rtsp in about:config doesn't work in most cases because the links are usually http: links that load a file in the plugin which redirects to a rtsp: location.

This kind of thing was easy in Netscape 4 (which was an otherwise-terrible browser), but there seems to have been a major regression since then. In order to make Firefox use mplayer instead of the brain dead totem, I had to manually rename the plugin files so Firefox couldn't find them. However, I have to have mplayer, because RealPlayer can't handle WMV.

---

### Post by kerry_s on 2007-04-11
-> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by mssever on 2007-04-11
Thanks for the link. The extension works.

<rant>Why does Firefox require a third-party extension to do something so basic? No program should trust third-party code to the point that if a plugin asks for a certain mimetype, Firefox doesn't even make it possible to say No.</rant>

---

