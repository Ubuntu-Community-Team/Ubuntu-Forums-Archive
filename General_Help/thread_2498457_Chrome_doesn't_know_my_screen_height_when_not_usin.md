---
title: "Chrome doesn't know my screen height when not using system title bar &amp; borders"
date: 2024-06-14
forum: General Help
---

### Post by Paddy Landau on 2024-06-14
This is a long shot, because it's Chrome rather than Ubuntu. I'm hoping that someone here has a solution.

It's a nuisance rather than a serious problem.

Recently, Chrome has started an odd thing. In my Chrome Settings > Appearance, I have "Use system title bar and borders" turned off.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293870&stc=1[/IMG]
In the past several days (I don't know exactly how long), this has meant that Chrome now thinks that my screen is taller than it really is when using Chrome maximised vertically. Thus, a good inch or so of the bottom of the screen is missing.

For example, when hovering my mouse over a link, I can't see the link at the bottom of the screen. In full-screen videos (e.g. on Reddit), the controls likewise are unavailable.

It works if I don't maximise vertically (but the problem remains when using a full-screen video).

However, when I turn on "Use system title bar and borders", then everything works correctly again.

 I tried running Chrome in safe mode (i.e. with all extensions disabled), and in an incognito window, but neither of those helped.

This affects only Chrome with that setting turned off (it has previously worked perfectly for years). It doesn't affect Chrome with the setting turned on, or Firefox, VLC, or anything else.

Obviously, for now, I have the setting turned on, which has the downside of losing some vertical space.

[LIST]
[*]Ubuntu 22.04, fully updated
[*]Using X11, not Wayland, because of certain requirements
[*]Chrome was installed from the official Google website, fully updated
[/LIST]
Do you have any idea of how to fix this, please? Or, are you aware of a bug report (I've searched but came up empty-handed)?

Thank you

---

### Post by him610 on 2024-06-14
@Paddy
I looked to see how my * "Use system title bar and borders"* is set. 
My  *"Use system title bar and borders"* is set to OFF and has been since I installed it a couple of years ago.

I don't seem to have the issue with missing bottom space; however, I rarely use full screen mode. I always use less than full screen so I can always adjust height and width using a mouse.

My system:
Xubuntu 22.04.4, X11, Chrome Version 125.0.6422.141 (Official Build) (64-bit)

---

### Post by Paddy Landau on 2024-06-15
Thanks for the reply, @him610. Full-screen (other than videos) doesn't have the problem; I should have mentioned that in the original post, sorry. It's only when the Chrome window is vertically maximised.

In Ubuntu's Settings > Keyboard > View and Customise Shortcuts > Windows, there's a command, "Maximise window vertically". It's disabled by default, but I've enabled it, and that's what I use with Chrome.

When that's used, then I have the problem with Chrome.

---

### Post by Paddy Landau on 2024-07-11
Three weeks later, and everything is working again. I suppose that one of the recent updates must have fixed it.

---

