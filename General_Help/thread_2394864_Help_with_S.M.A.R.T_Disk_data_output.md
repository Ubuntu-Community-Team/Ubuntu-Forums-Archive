---
title: "Help with S.M.A.R.T Disk data output"
date: 2018-06-22
forum: General Help
---

### Post by richardv22 on 2018-06-22
Hi guys,

I've noticed "Disk is OK, 1 bad sector detected" in my S.M.A.R.T Data in Disks Utility. I tried to run Self Test, but it right away showed FAILED (Read) error and the "Overall Assessment" showed "SELF-TEST FAILED". SMART Attributes are all OK.

I booted Ubuntu on USB stick and installed GSmartControl and it shows some Read failures (pastebin link is at the bottom of this post). But even after this error, there's "SMART overall-health self-assessment test result: PASSED" in the output. Screenshot of the GUI is in attachment.

Then I ran sudo smartctl -a /dev/sda (which is probably something similar) and it shows some errors but still "SMART overall-health self-assessment test result: PASSED" message.

Should I be worried? Is there way to fix it?

GSmartControl output: [https://pastebin.com/M2QNjqpQ](https://pastebin.com/M2QNjqpQ)

smartctrl -a /dev/sda output: [URL="https://pastebin.com/egcn16wh"]https://pastebin.com/egcn16wh


[/URL]

---

### Post by deadflowr on 2018-06-22
You have one current pending sector count.
[https://kb.acronis.com/content/9133]("https://kb.acronis.com/content/9133")
It's a coin toss as how imminent failure could be.
Could be a small glitch that won't affect anything more than what it has.
Or could be the start of a downward spiral of catastrophe.

I think the normal advice you'd get is backup the data from the disk immediately.
And replace (the disk) it as soon as you can.

It's better to side on the concept it's going to fail soon and do what you can to save what you have,
then to do nothing but hope it does not fail and watch it die, along with all your data.

---

### Post by richardv22 on 2018-06-22
Thank you very much for your answer!

I'll be checking on that pending sector value regularly and act on it accordingly.

---

