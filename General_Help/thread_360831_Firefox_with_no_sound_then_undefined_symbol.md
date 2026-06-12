---
title: "Firefox with no sound then undefined symbol"
date: 2007-02-13
forum: General Help
---

### Post by steevc on 2007-02-13
I've had sound working fine with Flash and Realplayer through Firefox on KDE until recently. The last thing I changed was to set the Auto-suspend in KDE to zero as I heard this would reduce the issues with sound clashes between KDE apps and Firefox. I ran Firefox from a Konsole and saw this error when I tried Youtube:

/bin/sh: /usr/bin/esd: not found

Should I have ESD, and if so, where do I get it?

The other problem cropped up today when Firefox would not start at all. It gave this error:

/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libi18n.so: undefined symbol: _ZN19nsACString_intgrnal6AssignEPKc

I couldn't find a mention of this particular message so I re-installed Firefox and it seems to work, apart from the sound thing above. Maybe this remark will help someone else.

---

### Post by jellyfisharepretty on 2007-02-13
Looks like for some reason your flash plugin is trying to use the enlightened sound daemon (esd) for sound.

Personally, I've switched to the adobe linux flash player some time ago, the latest version uses ALSA, which I believe is used by ubuntu by default for sound.  That's been working really well for me.

I don't know about the problem with firefox not starting, but if it starts now, then I suppose it's ok.

---

