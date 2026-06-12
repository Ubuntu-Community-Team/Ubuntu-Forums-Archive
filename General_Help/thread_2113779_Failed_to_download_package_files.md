---
title: "Failed to download package files?"
date: 2013-02-08
forum: General Help
---

### Post by oxf on 2013-02-08
Simple to resolve problem I hope.

I'm trying to add Chromium using the Software Centre. I get the error message
"Failed to download package files....check your internet connection"

Details reveal:
"Failed to fetch: [http://security.ubuntu.com/ubuntu/pool/universe/c/chromium](http://security.ubuntu.com/ubuntu/pool/universe/c/chromium)....... etc

I have and I am connected! I have also checked that the Universe repository is enabled.

Please tell me whats going on?


Also is anyone else having issues with Firefox being slow and unresponsive after running updates in Precise 12.04?  I never had this before but sometimes now its terrible, thats why I going to try Chromium!

Thanks..

---

### Post by slickymaster on 2013-02-08
That's odd.

Bellow are the Chromium Packages in "precise":

[chromium-browser]("http://packages.ubuntu.com/precise/chromium-browser") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]
[chromium-browser-dbg]("http://packages.ubuntu.com/precise/chromium-browser-dbg") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]
[chromium-browser-inspector]("http://packages.ubuntu.com/precise/chromium-browser-inspector")
[chromium-browser-l10n]("http://packages.ubuntu.com/precise/chromium-browser-l10n") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]
[chromium-bsu]("http://packages.ubuntu.com/precise/chromium-bsu") (0.9.15-1) [universe]
[chromium-bsu-data]("http://packages.ubuntu.com/precise/chromium-bsu-data") (0.9.15-1) [universe]
[chromium-codecs-ffmpeg]("http://packages.ubuntu.com/precise/chromium-codecs-ffmpeg") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]
[chromium-codecs-ffmpeg-dbg]("http://packages.ubuntu.com/precise/chromium-codecs-ffmpeg-dbg") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]
[chromium-codecs-ffmpeg-extra]("http://packages.ubuntu.com/precise/chromium-codecs-ffmpeg-extra") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]
[chromium-codecs-ffmpeg-extra-dbg]("http://packages.ubuntu.com/precise/chromium-codecs-ffmpeg-extra-dbg") (24.0.1312.56-0ubuntu0.12.04.1) [universe] [security]

---

### Post by ajgreeny on 2013-02-08
I am certainly having major problems with FF 18 on my main desktop computer, so have downgraded FF and re-installed FF 17, which is much better.  The biggest problem I face is terrible jerkyness and loss of scrolling, to such an extent that it makes FF 18 unusable.

I assume this is a hardware issue as it is not a problem on my laptop or netbook.  My problem desktop has a sempron 2400+, ATI 9200SE, and 2GB ram; what hardware are you using?

No problems here with chromium; I simply prefer firefox.

---

### Post by Zteam on 2013-02-08
Run this from a terminal
```
sudo apt-get clean
sudo apt-get update
```

And then try again.

Also if you selected a custom server in Software-center please change it back.

---

### Post by oxf on 2013-02-08
> **Zteam said:**
> Run this from a terminal
```
sudo apt-get clean
sudo apt-get update
```And then try again.

Also if you selected a custom server in Software-center please change it back.

Thanks that solved it. I knew it was something simple!

@ajgreeny

I am also have Firefox 18 installed. My problems are much like yours with the ridiculously slow scrolling, slow response to menus etc etc. Like you on one PC  it works fine but on the other, my Acer Aspire One netbook it's unusable all of  a sudden.  N2600 proc, 2GB ram, not sure what graphics other than it's integrated. 

I purchased this little netbook back in October, installed Precise 12.04 on it and took of on a long trip with it. It worked like a charm including Firefox running smoothly. I got back to the UK at new years and decided to do the updates after which Firefox went to hell!

I looked in Synaptic and only see Firefox 18 listed. How do I revert back to 17?

Caitlin

---

