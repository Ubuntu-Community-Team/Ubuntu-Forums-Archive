---
title: "Endless Loop &quot;Trust This Computer&quot; Iphone5S"
date: 2014-01-26
forum: General Help
---

### Post by jp734 on 2014-01-26
When I connect my phone to the computer, it asks me if I want to trust the computer. I tap on "Trust" and nothing happens. It just asks me again and again and again.

I have installed ifuse, libimobiledevice4,libusbmuxd2, usbmuxd.

On my laptop with Puppy Precise 5.6.1, it opens the phone just fine. What's missing on lubuntu 13.10 with 3.11.0-15-generic?

---

### Post by Newbunto on 2014-03-24
It seems that this is an iOS 7 problem, well-motivated but inconsiderately implemented. It only started being a problem for me when I let the iPhone upgrade to iOS 7.1

I found a solution at [http://askubuntu.com/questions/371711/ios-7-locked-bug-via-ubuntu-13-10](http://askubuntu.com/questions/371711/ios-7-locked-bug-via-ubuntu-13-10)

Quoting from that for 13.10

> For 13.10 you can download the .deb package from the launchpad site [here]("https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1207812/+attachment/3941542/+files/libimobiledevice4_1.1.6-git20140105_amd64.deb").

It worked for me. Download that .deb file and then ```
sudo dpkg -i *xxx*.deb
```

"Worked" means that in nautilus I was then again able to navigate to my photos, double click to view and then copy to local disk - because that's all I need to do. YMMV.

---

