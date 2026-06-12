---
title: "Kernel problem Linux 4.x"
date: 2015-05-07
forum: General Help
---

### Post by drfox on 2015-05-07
Not sure where to report this. I am running Xubuntu Vivid on a Dell XPS 13 (2015) model 9343
Using kernel 3.19, I get wireless but no sound. (This has been previously reported)
However, on Ubuntu kernel 4.0 through 4.1.0-999 mainline daily 2015-05-06, I get sound but no wifi.
Please feel free to move this post to the correct forum, and any help would be appreciated.
Thanks.

---

### Post by mattharris4 on 2015-05-07
I don't know why you would have wifi on an older kernel and not the new one unless you have a really old computer and support for your wifi card was dropped from the new kernel (assuming you are correct in your computer being a 2015 model that definitely is not the case but others may use this thread for assistance so I need to note that possibility).  If that is the case you need to find some way to reinstall the old kernel.  The sound problem should be easy to correct.

As for sound, likely alsamixer installed muted.  Assuming you can reinstall the old kernel, here is the link to the instructions to rectify that (refer to section two):  [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/) .

Here it is without wading through that link:

1.  Open a terminal (CTRL-ALT-T)
2.  Type "alsamixer" without quotes into the terminal
3.  Select sound card using F6, you can also select recording controls with F5 if that is a concern
4.  There is probably an MM under the bar graphs for "Master:, "Headphon" and "Speaker"  If it says "OO" this is not the issue.
5.  Move to "Master" with the left and right arrow keys
6.  Unmute with the M key
7.  Increase volume to about 80 with the up and down arrows
8.  Use right arrow to move to "Headphon"
9.  Repeat steps 6-8
10. Use right arrow to move to "Speaker"
11. Repeat steps 6-8
12. Press ESC on your keyboard
13. Close terminal
14. Play music or video with sound to make sure problem is rectified.
15. If that doesn't rectify problem or you find in step 4 that this isn't the issue, read link in post for other possible solutions.

---

