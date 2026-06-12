---
title: "Firefox Very Slow After Update"
date: 2022-11-30
forum: General Help
---

### Post by AdamShumpisxXx on 2022-11-30
OS: Ubuntu 22.04.1 LTS x86_64
Kernel: 5.15.0-53-generic
DE: GNOME 42.5
WM: Mutter
CPU: AMD FX-8350 (8) @ 4.000GHz
GPU: AMD ATI Radeon RX 580

Firefox installed through Snap (107.0.1 64-bit). YouTube almost unusable with multiple tabs open. HTOP shows normal usage with plenty of overhead. Firefox will complain about any new tabs for YouTube slowing down the browser. O&#822;t&#822;h&#822;e&#822;r&#822; &#822;w&#822;e&#822;b&#822;s&#822;i&#822;t&#822;e&#822;s&#822; &#822;s&#822;e&#822;e&#822;m&#822;i&#822;n&#822;g&#822;l&#822;y&#822; &#822;d&#822;o&#822;n&#822;'&#822;t&#822; &#822;c&#822;a&#822;u&#822;s&#822;e&#822; &#822;t&#822;h&#822;e&#822; &#822;s&#822;a&#822;m&#822;e&#822; &#822;i&#822;s&#822;s&#822;u&#822;e&#822;. Issue is intermittent. Weird calls for 19-22GBs of virtual memory showing in HTOP even though not even half the RAM is being utilized. 3-ish to 7-ish GBs of RAM being used by Firefox alone. Could be reading HTOP wrong. Screenshot attached. I'll post a video if necessary. Thank you in advance for any help someone may provide!

[https://imgur.com/a/NCiN86V](https://imgur.com/a/NCiN86V)

EDIT: Nevermind, it's not just YouTube. It's every website.

[https://imgur.com/a/E4AY2Ml](https://imgur.com/a/E4AY2Ml)

---

### Post by #&amp;thj^% on 2022-11-30
One sure way to isolate firefox-snap to view the good stuff, is throw this in your URL Bar
```
about:processes
```
Removes all doubts.

---

### Post by AdamShumpisxXx on 2022-11-30
I'll have to run it for longer to get more information but the only odd thing showing so far is the CPU Usage for Data Decoder shoots up to 130% or more sporadically. Not sure if that tells you anything but it is an observation.

---

### Post by #&amp;thj^% on 2022-11-30
Dang that is a lot, can you try to disable hardware acceleration in Firefox.
[list]
    [*]Options/Preferences -> General: Performance
    [*]remove checkmark: [ ] "Use recommended performance settings"
    [*]remove checkmark: [ ] "Use hardware acceleration when available" [/list]
Also if you need to report it use this in the address bar as well: "about:memory"
Here's a screenshot with only 3 tabs but steaming X-mas music on youtube.

---

### Post by AdamShumpisxXx on 2022-11-30
I don't know how that made CPU Usage worse but now that same process is using 450% at times. Doesn't make any sense. The video never skips, stops or buffers as long as I only run one tab. It's the new tabs created that seem to have all the issues with "slowing down Firefox" and running slow / freezing. RAM usage is good with plenty of headroom in all scenarios. Windows 11 partition has no such issue. Dual booting on the same NVMe using UEFI for both, SecureBoot Disabled and TPM Disabled.

As an aside, I really hate all the Snap / Flatpak package manager stuff in Ubuntu these days. Used to just be "apt-get install package" and everything seemed to fit in nicer. All well. Guess I got old!

---

### Post by #&amp;thj^% on 2022-11-30
Well that screenshot I show is a Flatpak Firefox

---

### Post by AdamShumpisxXx on 2022-11-30
Is it newer or older than the version I have?

---

### Post by #&amp;thj^% on 2022-11-30
```
flatpak list | grep firefox
Firefox	org.mozilla.firefox	107.0.1	stable	system

```
The forums are acting wonky today

---

### Post by AdamShumpisxXx on 2022-11-30
I'm glad I'm not the only one noticing. The General Help section wouldn't open for me and I had to go to my profile and click on the link for this thread directly.

Anyway...damn. Looks like it's the same version I got from Snap. Any advantage to remove --purge Firefox from Snap and install it from Flatpak instead?

---

### Post by #&amp;thj^% on 2022-11-30
> **AdamShumpisxXx said:**
> 
Anyway...damn. Looks like it's the same version I got from Snap. Any advantage to remove --purge Firefox from Snap and install it from Flatpak instead?

My view is subjective and since you asked, that's the very first thing I do is to purge snap's and snapd.
In my Two years of this practice I've not seen any ill effects form removing snapd,, but here's a kicker, I don't use Gnome either. ;)

---

### Post by AdamShumpisxXx on 2022-11-30
I caved and ran "remove --purge" on the Firefox Snap and installed the Firefox Flatpak. Seems to run just as well as it used to before all the issues I mentioned in the OP. You mean to tell me I should probably get rid of Snap altogether? After this experience I'm contemplating it. I'd ask you a few questions here but that would make this thread off-topic. I'll mark this thread as Solved now. Thanks!

---

### Post by oldfred on 2022-11-30
I use Kubuntu & first thing I do is remove all snaps. 
When they converted Firefox to snap only, I added the ppa. The ppa also updates my Thunderbird to latest version.

You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)

---

### Post by AdamShumpisxXx on 2022-12-01
OK. You people sold me on getting ridding of my Snap packages and the Snap manager altogether. I have a few questions about it so I'll make another thread. Thanks!

---

