---
title: "How to get hardware acceleration with Ubuntu 21.10?"
date: 2022-02-16
forum: General Help
---

### Post by username2758 on 2022-02-16
Hi,

I have hardware acceleration enabled using Chromium with VAAPI (Video Acceleration API) on Ubuntu 20.04.3, but for some reason I can't get VAAPI support using Chromium on Ubuntu 21.10.

Are there any other browsers that has hardware acceleration available for Ubuntu 21.10?

Thanks!

---

### Post by MAFoElffen on 2022-02-16
So with 20.04, you had  patched version of chromium and installed the VA-API driver for your video card...

You know that none of the browser that support that,have video acceleration tuned on by default right? So if you upgraded to 21.10, your also have a newer version of Chromium, where that option would need to be configured and turned on...

Is your version of chromium in 21.10 at or newer than Chromium 91? 
[https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html)

---

### Post by username2758 on 2022-02-17
> **MAFoElffen said:**
> Is your version of chromium in 21.10 at or newer than Chromium 91? 
[https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html)

Yes it is version 98.0.4758.80 (Official Build) snap (64-bit).

I don't know I haven't yet read your suggested article, but on Ubuntu 20.04 I was following a guide using the following commands to install Chromium with VAAPI enabled:
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
sudo apt update ; sudo apt install chromium-browser chromium-codecs-ffmpeg
```

This method works great on Ubuntu 20.04, but it doesn't work on 21.10. I can't even install it because of a problem with the PPA.

---

### Post by ajgreeny on 2022-02-17
That ppa you used in 20.04 [noparse]ppa:xalt7x/chromium-deb-vaapi[/noparse] is now abandoned by xalt7 so will not be any use to you either in older 20.04 installations or in 21.10.

I never bother with hardware acceleration for my browsers, but I do use another one of the two possibilities:-
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-dev)
for the dev version, or
[https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta)
for the beta version.

Currently the dev versions which I normally use are not working as they should, but the beta versions are fine so stick with that for now and check frequently with the dev version to see when it's been fixed.
The ppa tells you how to enable HA, but as I said, I don't use that in my browsers.

---

### Post by username2758 on 2022-02-18
Okay I need extra help with this one please?

I followed the instructions from [https://www.linuxuprising.com/2018/0...celerated.html]("https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html") but apparently it has installed the dev version instead of the beta version of Chromium, making hardware acceleration unavailable to me (see attached screenshots). I wonder if it has something to do with the version of Ubuntu and PPA?

I really need hardware acceleration on this laptop otherwise battery drains too fast let alone the noise from the CPU fans.

---

### Post by username2758 on 2022-02-20
Up. Anyone?

I managed to install the beta version of Brave browser because I wasn't able to do that with Chromium, but I can't get hardware acceleration with Brave either.

---

### Post by Yellow Pasque on 2022-02-21
> Yes it is version 98.0.4758.80 (Official Build) **snap** (64-bit).

You probably need to get rid of the snap version. IIRC, VA-API wasn't available with the snap version. I don't know if that's still the case with 21.10, but I wouldn't doubt it.

---

### Post by username2758 on 2022-02-21
> **Yellow Pasque said:**
> You probably need to get rid of the snap version. IIRC, VA-API wasn't available with the snap version. I don't know if that's still the case with 21.10, but I wouldn't doubt it.

I don't know. I'm following all the right steps to install the beta version of Chromium and I'm still getting the dev version instead.

Do you know how to install Chromium 95? Other Linux users have been reporting that hardware acceleration might work with Chromium 95.

---

### Post by Yellow Pasque on 2022-02-21
> **username2758 said:**
> I don't know. I'm following all the right steps to install the beta version of Chromium and I'm still getting the dev version instead.

Do you know how to install Chromium 95? Other Linux users have been reporting that hardware acceleration might work with Chromium 95.

No. I'm sorry. I don't know too much about Chromium. I'm a Debian/Firefox user. And I wouldn't recommend running old versions of chromium because of security issues.

---

### Post by uninvolved on 2022-02-21
Hardware Acceleration with Chromium-based browsers doesn't work. Google has no plans to make it work. Why it is there and why it is enabled by default is left to an exercise for the reader.

[https://www.omgubuntu.co.uk/2018/10/hardware-acceleration-chrome-linux](https://www.omgubuntu.co.uk/2018/10/hardware-acceleration-chrome-linux)

In fact, leaving it enabled in Chrome/Chromium/Cromium-based browsers (such as Brave, Opera, or Vivaldi) can lead to serious bugs in your system, up to and including cause the computer to completely freeze.

One of my most popular AU answers is on this very subject. Disable HA in any Chrome/Chromium-based browser and mysterious bugs will often disappear. The easiest way to tell which is which is that those bugs only appear while the browser is open.

Not too long ago, this resolved similar complaints - but with Firefox. I am not all that experienced with Firefox these days, so I can't explain anything more than 'it just worked'.

---

