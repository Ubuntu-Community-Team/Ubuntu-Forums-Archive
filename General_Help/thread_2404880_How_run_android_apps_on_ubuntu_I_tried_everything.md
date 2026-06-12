---
title: "How run android apps on ubuntu? I tried everything"
date: 2018-10-29
forum: General Help
---

### Post by tackskull on 2018-10-29
Hi everybody, I need to run an app called Pleco (is a chinese-english dictionary, veryusefull for study chinese). I tried with anbox but with this program I can only install x86 apps, and Pleco doesn't have this kind of release. Then I tried to use ARChon with goole chrome browser, but once I installed the app on Chrome, it just freeze on launch. Then I read about geenymotion but now is a pay app and I don't want to spend money for this. I tried to run a android iso from virtual box but the result is so bad on my pc, slow and crashy.

So I ask you guys, there is another way to easy install android apps on Ubuntu?

---

### Post by Holger_Gehrke on 2018-10-29
How did you install your android app on anbox ? You need to have the apk-file and use the android debug bridge (adb, it's in the repositories) with 'adb install apk-file'. When I tried anbox I had no trouble running fbreader (which I got from fdroid.org). Normal Android aplications are not written for any specific processor, they run on a virtual machine - either Dalvik (for Android 4.4 or older) or ART (Android RunTime, after Android 4.4). There are apps that use native code, but those are mostly games trying to get the last bit of speed out of the system.

Holger

---

### Post by tackskull on 2018-11-05
Yes, I installed apps with adb, in fact apps are installed but not the one I need, installing this specific one the terminal say something like "format not supported". I was reading on the internet that anbox can only install x86 apps and there isn't a version of Pleco x86 (the app I need). Can you tell me how install any kind of app on anbox?

---

### Post by Holger_Gehrke on 2018-11-05
So I went to pleco.com and they actually offer a download of the free version of their Software on their site. I opened the apk (apk - like jar and a few other formats - is actually a zip-file with some specific content, like a manifest-file) and found that it does contain native code but only for arm. So you'd need some program that not only runs Android but also emulates an arm processor. Good luck finding one that can do this and do it fast enough to get any use out of a program. Just for comparison: desmume (a Nintendo DS emulator) only has to emulate two ARM-Cores at rather low speeds (an ARM9 at 67Mhz and an ARM7 at 33MHz) and often can't match the speed of the original on my 4 core AMD @ 1.6 GHz. Modern smartphones or tablets have more cores at higher speeds, so ...

Holger

---

