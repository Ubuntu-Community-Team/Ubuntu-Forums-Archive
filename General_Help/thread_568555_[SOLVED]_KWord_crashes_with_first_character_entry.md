---
title: "[SOLVED] KWord crashes with first character entry"
date: 2007-10-05
forum: General Help
---

### Post by BuilderQ on 2007-10-05
**Edit: I think this was an example of [Bug 125958](http://bugs.kde.org/show_bug.cgi?id=125958). Uninstalling aspell fixed it.**



Having encountered [a problem with inserting images](http://ubuntuforums.org/showthread.php?t=566702) in Abiword, and knowing the slowness of Open Office, I decided to download KWord and try it.

I launched KWord from the terminal, and was pleased to see that it loaded quickly. However, I also saw the first of the error messages I was to receive::
> kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

Next, I inserted one of the images that had been causing problems in Abiword. It worked, but the terminal repeated the last error message 4 times, then added some new errors:
> koffice (lib kofficecore): WARNING: Drawing white rectangle! (KoPicture::draw)
kword: WARNING: KWFrameSet::findAnchor anchor not found (frameset='Picture 1' frameNum=0)
Finally, I pressed the 'j' key, and my little test was over:
> KCrash: Application 'kword' crashing...
KCrash cannot reach kdeinit, launching directly.

The KWord version is 1.6.2. Any thoughts?

---

