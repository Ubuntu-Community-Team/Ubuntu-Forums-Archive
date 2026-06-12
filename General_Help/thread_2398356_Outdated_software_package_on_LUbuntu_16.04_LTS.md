---
title: "Outdated software package on LUbuntu 16.04 LTS"
date: 2018-08-10
forum: General Help
---

### Post by postcd on 2018-08-10
Hello,

the software package "mpv" seems to be outdated per [this issue]("https://github.com/mpv-player/mpv/issues/6065#issuecomment-412195839").
I have same LUbuntu version and exactly same issue as described on the linked page.

In short, mpv developer says i am using 2015 mpv package version, but i think my 16.04 is supported and so it should have newest version right? Please what to try to find where is the problem?

As mentioned in linked page, i am using main, restricted, multiverse, universe. Thank You in advance.

---

### Post by mc4man on 2018-08-10
get here
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)
(- likely will be a slightly newer 16.04 build shortly, development of mpv has slowed to a crawl so not a priority here..

---

### Post by Holger_Gehrke on 2018-08-10
> **postcd said:**
> 
In short, mpv developer says i am using 2015 mpv package version, but i think my 16.04 is supported and so it should have newest version right? Please what to try to find where is the problem?


You seem to be suffering from a misinterpretation of the word 'supported'. At some point during the development of a release of Ubuntu, package version are "frozen" and packages that are part of the release are only changed to fix bugs of very high severity (crashes, high risk of data loss or security related). See this page in the [Ubuntu wiki]("https://wiki.ubuntu.com/StableReleaseUpdates") for the reasoning behind this policy from the point of view of the maintainers. If you want or need newer version of some software software, then PPAs (like the one mc4man gave) are one way to do it; snap packages are another. snap is somewhat new and a lot of stuff is still in flux or not nearly as seamless as it needs to be. PPAs are currently the better alternative, but can turn a release upgrade into an unholy mess ...

Holger

---

### Post by Impavidus on 2018-08-11
As noted above, the software for each Ubuntu release gets frozen, except for serious bugfixes and a few applications like Firefox. If you want something more recent, use snaps, PPAs or a more recent release of Ubuntu. 18.04 has been around for some time and has a more recent version of mpv (0.27 instead of 0.14).

---

### Post by postcd on 2018-09-01
I have found a tutorial that contained following commands i executed:

> sudo add-apt-repository ppa:mc3man/mpv-tests
sudo apt update && sudo apt install mpv

resulting installed package now is: mpv/xenial,now 2:0.28.0+git7~xenial3 i386

But the video with subtitles continue having bad characters. When i open the .srt file, all characters are good and Save As shows Encoding CP1250 and CR+LF (unsure if it means it is current state of the file)

So please where is the problem that MPV do not properly read the .srt file? My Ubuntu locale is Czech... thank you

---

### Post by Impavidus on 2018-09-02
Those 8-bit encodings like CP1250 are really old-fashioned these days. I suggest you try and convert this to UTF-8. Either use the save as-function of your text editor or use the command line tool iconv:```
iconv --output=output.srt --from-code=CP1250 --to-code=UTF-8 input.srt
```

---

### Post by postcd on 2018-09-03
**No, conversion is not a solution for me. **But thanks anyway for the command. It is too often i DL this encoded subtitle files and wanting me to execute such command everytime is a joke.
I need video player to support CP1250. and i think you are wrong, the players should be "backwards compatible" support even old encodings, i do not think it is so huge task for developers to support/autodetect one more subtitle charset. Though i was told i am still one version behind latest release. Unsure if 0.28 and 0.29 makes the difference in CP1250 "support"..?

Actually i think CP1250 is supported, though not autodetected.
Currently i went to Linux main menu, find mpv app, right click, properties and there on other tab is the app path and i can add:
--sub-codepage=windows-1250 
to it, **which makes the CP1250 subtitles working**, but MPV should do the detection automatically.

---

