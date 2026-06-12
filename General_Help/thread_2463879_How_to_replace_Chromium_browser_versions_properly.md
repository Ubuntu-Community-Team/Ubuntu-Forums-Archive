---
title: "How to replace Chromium browser versions properly?"
date: 2021-06-20
forum: General Help
---

### Post by username2758 on 2021-06-20
Hi! Very simple question here!

I've tried installing a version of Chromium that has support for VAAPI on Ubuntu 20.04, but unfortunately it has issues playing videos on some websites.

Here's how I installed the Chromium with VAAPI support:
```
sudo add-apt-repository ppa:xalt7x/chromium-deb-vaapi
```
```
cat <<EOF | sudo tee /etc/apt/preferences.d/pin-xalt7x-chromium-deb-vaapi Package: *
Pin: release o=LP-PPA-xalt7x-chromium-deb-vaapi
Pin-Priority: 1337
EOF
```
```
sudo apt update && sudo apt install chromium-browser chromium-codecs-ffmpeg
```

How do I replace Chromium browser versions properly? Should I just uninstall it and install the other version?

Thanks!

---

### Post by TheFu on 2021-06-21
The default chromium included in Ubuntu recently has been a snap package, so you need to purge that.
Within the APT system, if the PPA is one that you trust, then that should automatically get the PPA version and dependencies required by that version.

You can always see the different installed version by using **snap list** and **dpkg -l**. Just filter on 'chromium' to limit the output.

---

### Post by username2758 on 2021-06-21
You mean I need to manually remove the PPA first? 

What if I install Chromium via snap without removing the already installed Chromium with VAAPI support? Will Ubuntu keep two versions of the same application or that isn't allowed?

I just noticed now that Chromium with VAAPI support playbacks Youtube videos beautifully, significantly reducing CPU workload compared to Mozilla or Chrome on Ubuntu.

It would be interesting if I could keep both!

---

### Post by Frogs Hair on 2021-06-23
The PPA has been abandoned per the link.

 [https://launchpad.net/~xalt7x/+archive/ubuntu/chromium-deb-vaapi](https://launchpad.net/~xalt7x/+archive/ubuntu/chromium-deb-vaapi)

---

### Post by username2758 on 2021-06-27
> **Frogs Hair said:**
> The PPA has been abandoned per the link.

 [https://launchpad.net/~xalt7x/+archive/ubuntu/chromium-deb-vaapi](https://launchpad.net/~xalt7x/+archive/ubuntu/chromium-deb-vaapi)
I didn't know, thanks! I will be replacing this version of Chromium on my machine then.

Do you know of any other browser that has support for hardware acceleration (GPU) in Linux?

---

### Post by monkeybrain20122 on 2021-06-27
> **username2758 said:**
> I didn't know, thanks! I will be replacing this version of Chromium on my machine then.

Do you know of any other browser that has support for hardware acceleration (GPU) in Linux?

It says in the link

> 1) VAAPI (hardware video decoding for Intel/AMD on X11) was the main  reason to maintain it. Since version 88 it should be available for all  Chromium-based browsers. Copy address bellow to your address bar and  check if it's enabled (may work for other Chromium-based browsers (e.g.  Brave, Vivaldi, Opera, Edge))
chrome://flags/#enable-accelerated-video-decode

---

### Post by monkeybrain20122 on 2021-07-05
Actually, don't bother. vaapi doesn't work on Chromium [https://github.com/saiarcot895/chromium-ubuntu-build/issues/116](https://github.com/saiarcot895/chromium-ubuntu-build/issues/116)

But it works on Firefox!

See my last two posts [https://ubuntuforums.org/showthread.php?t=2463888&page=3](https://ubuntuforums.org/showthread.php?t=2463888&page=3)

---

