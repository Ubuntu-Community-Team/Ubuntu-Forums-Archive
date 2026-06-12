---
title: "Problems with Ubuntu version 21.04"
date: 2021-07-08
forum: General Help
---

### Post by irv on 2021-07-08
I was wondering if others are having this problem. I did an upgrade to 21.04 yesterday and one thing I found was "the drag and drop" on web pages don't work so well. I upload a lot of video and audio files, (podcasts) and I have to sometimes try to drag and drop them a half dozen times before they will upload. It does the same with graphic files as well. Never had this problem with 20.04.
Does anyone know if there is a bug report on this? I didn't want to file one if I am the only one having this problem.
Maybe I should mention I am using Chrome Browser. I haven't tried it in Firefox yet.

---

### Post by dddman on 2021-07-08
Also boot up in your guest account, see if its the same.

---

### Post by irv on 2021-07-09
Found the problem. It was Wayland I had to switch to Xorg. Here is the fix.
> An upgrade from 20.10 to 21.04 indeed automatically has you switch to Wayland. OBS Studio does not (yet) work in Wayland. To switch to X11, log out. Select your username so the password field appears. At that point, you will see a cog wheel in the bottom right of the login screen. It allows you to select "Ubuntu on Xorg". After that, enter your password to log in.



---

