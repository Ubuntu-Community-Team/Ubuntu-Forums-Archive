---
title: "Updates: System says it doesn't have enough disc space?"
date: 2017-02-28
forum: General Help
---

### Post by isolated-thinker on 2017-02-28
Greetings!

I ran into this issue once before, but I have been unable to find the forum post with the answer... and the search feature here turned up nothing of familiarity or use.

Basically, it has been a while since I turned on my laptop which is running 16.04 LTS and I wanted to run the updater (as one should if it has been a while).
And I got this...

[IMG]https://uncommongeek.files.wordpress.com/2017/02/diskspace.png[/IMG]

My laptop has a 300Gb hard drive which isn't even 25% full. I remember that one of the fixes for this was to delete previous kernel versions (which the OS keeps for one reason or another), but I can't remember what the terminal command is.

I tried running that sudo apt-get clean, but it came back saying it was an unknown program.

So I turn to you, the community, to once again help me try to remember how to fix this issue.

Thank you!

---

### Post by wyliecoyoteuk on 2017-02-28
Try sudo apt autoremove --purge

or read this:
[http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)

---

### Post by Bashing-om on 2017-02-28
A Bump

+1 to wyliecoyoteuk ... and
see if we can get the response to post update .

Nope, still with the forum glitching .

[INDENT][INDENT]just pass'n by
[/INDENT][/INDENT]

---

### Post by isolated-thinker on 2017-02-28
> **wyliecoyoteuk said:**
> Try sudo apt autoremove --purge

or read this:
[http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/)

That did the trick! Thank you!

---

