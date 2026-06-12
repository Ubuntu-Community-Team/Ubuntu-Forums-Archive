---
title: "No sound on Firefox and Chrome"
date: 2020-11-02
forum: General Help
---

### Post by satimis on 2020-11-02
Hi all,

Ubuntu 20.04 Desktop

After running update and upgrade there is no sound on browsers.  But there is sound on playing .mp4 file.

pavucontrol is running.  Please advise where to check?  Thanks

Regards

---

### Post by yapidumoac on 2020-11-02
Play a video in Chromium. Open pavucontrol, select "Playback", select &#8220;Show Applications&#8221;. Click on the little speaker icon next to the flickering audio graph.

---

### Post by satimis on 2020-11-03
> **yapidumoac said:**
> Play a video in Chromium. Open pavucontrol, select "Playback", select “Show Applications”. Click on the little speaker icon next to the flickering audio graph.
Hi,

Thanks for your advice.

Before posting I have been fiddling around for solution, including working around on sound setting, starting pavucontrol, etc. without result.  All browsers have no sound but .mp4 and .mp3 files work without problem.

Finally I ran following command on Terminal```

$ sudo rm ~/.config/pulse/*

```

Rebooted PC.  Then sound on browser comes back.

I can't explain why?  The problem was caused by running```

$ sudo apt update & sudo apt upgrade

```

Regards

---

