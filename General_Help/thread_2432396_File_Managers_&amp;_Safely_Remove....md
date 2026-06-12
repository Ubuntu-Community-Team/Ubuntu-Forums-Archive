---
title: "File Managers &amp; Safely Remove..."
date: 2019-12-02
forum: General Help
---

### Post by 2CV67 on 2019-12-02
When I use my Ubuntu default File Manager (Files) to unmount an External Hard Drive, I right-click & get an option "Safely Remove Drive" followed by a warning, something like "Do not remove drive - writing to device" followed after several seconds by "Device can be removed".

When I use the PCManFM file manager, I just get "Unmount Volume" and suppose I can remove it immediately...

Is there a good explanation for this difference in behaviour?
Can I really remove the device immediately with no risk, using PCManFM?

Thanks!

---

### Post by #&amp;thj^% on 2019-12-02
Kind of hard question to answer but I'll try,  PCManFM and other similar lightweight file managers (Thunar etc) do not integrate into the OS. They keep to themselves and store their own separate settings and configuration files.
Something like Nautilus or Dolphin. These are much larger file managers which do much more within the OS. 
Personal Note here: **_PCmanfm doesn't handle USB eject notifications well._**
**Nemo **seems the best all around file manager IMHO

---

### Post by 2CV67 on 2019-12-04
Thanks for your response 1fallen.

I tried Nemo in my Ubuntu 18.04LTS partition & liked its features.
In view of your comments on PCManFM/USB I should probably try Nemo in Lubuntu instead of the default PCManFM?

Back in my main Ubuntu 19.04, I disliked the default Files (Nautilus?) for its lack of options:
1. No "Open as Admin"
2. No display of "Path to File"
3. Need 2 clicks to open a new tab.

But after a bit of digging:
1. I got "Open as Admin" by installing "nautilus-admin".
2. I got display of "Path to File" by using dconf editor > org > nautilus > preferences > always-use-location-entry. I really try to avoid using dconf editor (potentially dangerous) but is there another way for this one?
3. I found I could open a new tab with one middle-click.

So I think I can now live with Files.

---

### Post by Dennis N on 2019-12-04
> ..is there another way for this one? 
In Files - you also can do:
Control+L will switch location bar to text mode with (copyable) path of current folder; Or type in a valid path here (has auto completion) and press enter to go there. Esc will return back to the button path.
Control+T will open a new tab in Files (faster than Options Button > New Tab)

Tip:
In Ubuntu, you can use **Removable Drive Menu** extension to eject drives or unmount partitions. Or you can remove USBs from **Places Status Indicator** extension.

---

### Post by 2CV67 on 2019-12-05
Thanks for the useful Keyboard shortcuts, DennisN, which avoid having to use dconf-editor.

I was going to ask you how on earth I was supposed to learn about these shortcuts & I spent a long time browsing before finding they are immediately available at: Files > Menu > Keyboard Shortcuts!    :oops:

So I will mention that for anybody else who needs it...

---

