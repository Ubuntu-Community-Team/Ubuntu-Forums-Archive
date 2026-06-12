---
title: "What installed this software?"
date: 2015-09-22
forum: General Help
---

### Post by scottbomb on 2015-09-22
Today, apt-get upgrade said it wanted to get the latest "chromium-codecs-ffmpeg-extra". I do have ffmpeg installed but I never installed Google Chrome or Chromium. Alarmed at all this Google garbage I don't want on my machine, I did a "sudo apt-get remove --purge chrome*" and ALL KINDS of chromium packages are installed. Is there a way to find out what package installed all of this?

---

### Post by kostkon on 2015-09-22
Probably one of the (l)(x)(k)ubuntu-restricted-extras packages. But it only installs chromium-codecs-ffmpeg-extra.

What does your dpkg.log say about that, how many chromium packages did it actually remove?

---

### Post by nknwn on 2015-09-23
"Chromium is the open-source project that forms the basis for Google  Chrome. Because it&#8217;s completely open source, Chromium is available in  many Linux distributions&#8217; software repositories for easier installation."
[http://www.howtogeek.com/202825/what%E2%80%99s-the-difference-between-chromium-and-chrome/?PageSpeed=noscript](http://www.howtogeek.com/202825/what%E2%80%99s-the-difference-between-chromium-and-chrome/?PageSpeed=noscript)

---

### Post by Bucky Ball on 2015-09-23
> **nknwn said:**
> "Chromium is the open-source project that forms the basis for Google  Chrome. Because it&#8217;s completely open source, Chromium is available in  many Linux distributions&#8217; software repositories for easier installation."
[http://www.howtogeek.com/202825/what%E2%80%99s-the-difference-between-chromium-and-chrome/?PageSpeed=noscript](http://www.howtogeek.com/202825/what%E2%80%99s-the-difference-between-chromium-and-chrome/?PageSpeed=noscript)

Don't see how this has to do with the OP's query. They are not asking what is the difference between them, nor do they have Chrome or Chromium installed. OP is asking why they are getting software updates related to Chromium when it's not installed. :-k ;)

---

### Post by monkeybrain20122 on 2015-09-23
The package is part of ubuntu-restricted-extras.

---

### Post by Bucky Ball on 2015-09-23
> **monkeybrain20122 said:**
> The package is part of ubuntu-restricted-extras.

That would explain it. Presuming you are talking about:

chromium-codecs-ffmpeg-extra

If OP hasn't got chromium installed it may be as easy as simply uninstalling that. Is it required by anything else?

---

### Post by buzzingrobot on 2015-09-23
```
apt-cache rdepends  chromium-codecs-ffmpeg-extra
``` displays:

> Reverse Depends:
  chromium-codecs-ffmpeg-extra:i386
  chromium-codecs-ffmpeg:i386
  chromium-codecs-ffmpeg:i386
  ubuntu-restricted-addons
  kubuntu-restricted-addons
  chromium-codecs-ffmpeg-extra-dbg
  chromium-codecs-ffmpeg
  chromium-codecs-ffmpeg
 |chromium-browser


so it shows up when we add a restricted addons/extras meta-package, which are really convenient collections of several packages made so users don't need to identify and chase down specific codecs and such.  We can look at [http://packages.ubuntu.com](http://packages.ubuntu.com) and see the individual components and install only what we wish, if we've decided that's important.

---

### Post by scottbomb on 2015-09-23
So it IS the extras package. Thanks guys! I ran grep chrom dpkg.log | less  (and again on dkpg.log.1) and saw a lot of references to chromium-codecs-ffmpeg-extra:amd64 but nothing else. I wish I had copied what I saw the other day but all seems to be well now. I went ahead and re-installed it.

---

