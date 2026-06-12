---
title: "Sound problem"
date: 2007-10-20
forum: General Help
---

### Post by racarter on 2007-10-20
```
$ lspci | grep 'Audio'
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

The specs for my Toshiba Satellite laptop can be found here: [http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_outFrm.jsp?moid=1598559&rpn=PSAD0U&ct=DS&soid=1642835&BV_SessionID=@@@@0755060582.1192899618@@@@&BV_EngineID=cccdaddmflilhefcgfkceghdgngdgmm.0]("http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_outFrm.jsp?moid=1598559&rpn=PSAD0U&ct=DS&soid=1642835&BV_SessionID=@@@@0755060582.1192899618@@@@&BV_EngineID=cccdaddmflilhefcgfkceghdgngdgmm.0")

I just installed Ubuntu 7.10 on my laptop. I asked and was told on the #ubuntu irc channel that support for my soundcard should be distributed by default with Ubuntu 7.10. However, sound is disabled and if I try to adjust the volume i receive this message:

```

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

I was receiving a different message earlier but then I tried to install everything gstreamer I could find. Either way I am still not receiving sound from my laptop. What can I do to fix this?

---

