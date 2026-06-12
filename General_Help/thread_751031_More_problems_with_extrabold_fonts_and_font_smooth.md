---
title: "More problems with extrabold fonts and font smoothing"
date: 2008-04-10
forum: General Help
---

### Post by huahe on 2008-04-10
Hello!

We are thinking in migrate all the office PCs to Ubuntu, but before we need that the fonts looks and spacing looks the same under Ubuntu.

If I enable the "Full" font smoothing, the width of each letter is perfect. But the anti-alias looks bad, I prefer the "Slight" font-smoothing. The problem is that bold fonts looks extra bold, and the letter spacing is narrower than Windows.

I saw some fixes, but there is no effect when I paste it in my .fonts.conf

This is the fix I am using:

   <match target="font">
      <test name="weight" compare="more"><const>medium</const></test>
      <edit name="autohint" mode="assign"><bool>false</bool></edit>
      <edit name="hinting" mode="assign"><bool>false</bool></edit>
      <edit name="hintstyle" mode="assign"><const>hintnone</const></edit>
   </match>

After every change, I restart the session with no luck.

I am using Ubuntu 7.10, with libfreetype6 2-3-5-lubuntu4

Check this image to see the problem:

[IMG]http://img142.imageshack.us/img142/4881/boldfontsproblemsubuntunt2.png[/IMG]

Thanks in advance.

---

