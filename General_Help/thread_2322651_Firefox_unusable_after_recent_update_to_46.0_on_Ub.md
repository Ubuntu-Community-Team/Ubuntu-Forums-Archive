---
title: "Firefox unusable after recent update to 46.0 on Ubuntu Mate 15.10"
date: 2016-04-29
forum: General Help
---

### Post by alecz20 on 2016-04-29
I am running Ubuntu Mate 15.10 with a GTK2 Human theme that also has some GTK3 components.
Before the upgrade, I was running Firefox 45 without issues.

Firefox updated automatically, and now I have two big issues:

1 - The text in the address bar and the Search bar is white (on white background) which is unreadable unless highlighted
2 - The File Browser for Download looks like a very ugly Gnome3 Nautilus file browser, before it used to be the beautiful Caja File Browser

I know that Firefox 46.0 has security fixes and I would like to keep the most recent version, but what happened to the drastic change in appearance?
Chrome does not have this issue:

Here's how the file browser used to look:
[ATTACH=CONFIG]268714[/ATTACH]
Here's how it looks now:
[ATTACH=CONFIG]268715[/ATTACH]

And the address bar:
[ATTACH=CONFIG]268716[/ATTACH]

- Does anyone know why this happened? I suspect it has to do with GTK3. And how it can be corrected? The Mate Ambiant theme shows the text in the address bar, but there is no text on the tabs now. Plus the theme is too dark for me.
- Should I downgrade Firefox for now?
- Should I upgrade to Ubuntu Mate 16.04?
- Should I downgrade to Ubuntu Mate 14.04?
- any other suggestions? Is there an Ubuntu Mate Human theme (that looks like Ubuntu 10.04, or 9.10) that works with modern Ubuntu Mate versions?

I know I put a lot of questions, and I don't expect all to be answered, but I would appreciate any opinions, answers, and experiences you can share.

---

### Post by mikewhatever on 2016-04-29
Have you tried a GTK3 theme? I think Firefox needs GTK3 since version 46.

---

### Post by Dennis N on 2016-04-29
Here is some user discussion of themes:

[https://www.reddit.com/r/linux/comments/4gjte4/firefox_460_released_with_gtk3_integration/](https://www.reddit.com/r/linux/comments/4gjte4/firefox_460_released_with_gtk3_integration/)

You need to use a compatable theme. I am using Ubuntu MATE 16.04 with Greybird and Firefox 46 (as well as everything else) looks good using that.

---

### Post by vasa1 on 2016-04-29
Don't upgrade/downgrade anything before you try changing themes. Dark themes are often problematic although there are fixes. Make sure the gtk3 theme you choose is compatible with your gtk3 version. You can find out which version of gtk3 is on your system by running *dpkg -l libgtk-3-0*:
```
$ dpkg -l libgtk-3-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-=============================================================================
ii  libgtk-3-0:amd64                     **3.18**.9-1ubuntu3         amd64                   GTK+ graphical user interface library
$ 
```

---

### Post by alecz20 on 2016-05-07
Thanks for the replies.

My libgtk version is:  libgtk-3-0:amd 3.16.7-0ubun amd64
The theme I am using is working fine outside Firefox ([http://gnome-look.org/content/show.php/Human+GTK+3?content=164227](http://gnome-look.org/content/show.php/Human+GTK+3?content=164227))

If I use a different theme, such as the suggested Greybird, I can see the text, but personally, I don't really like the colours (I guess I just got to used to the old Ubuntu Human theme)

Also, how about the download dialog? Any chance to have the one from Caja rather than the one from Nautilus? Or this is how it's going to be because of GTK3?

If anybody has a better working Human-like theme, please post it here, or IM me!

---

### Post by alecz20 on 2016-05-11
A bug report has been opened for the File Dialogue interface:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1576825](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1576825)

---

### Post by vasa1 on 2016-05-11
> **alecz20 said:**
> Thanks for the replies.

My libgtk version is:  libgtk-3-0:amd 3.16.7-0ubun amd64
The theme I am using is working fine outside Firefox ([http://gnome-look.org/content/show.php/Human+GTK+3?content=164227](http://gnome-look.org/content/show.php/Human+GTK+3?content=164227))

If I use a different theme, such as the suggested Greybird, I can see the text, but personally, I don't really like the colours (I guess I just got to used to the old Ubuntu Human theme)

Also, how about the download dialog? Any chance to have the one from Caja rather than the one from Nautilus? Or this is how it's going to be because of GTK3?

If anybody has a better working Human-like theme, please post it here, or IM me!

[LIST]
[*]You got to make sure your gtk 3 theme is compatible with your distro's gtk3 version. An older gtk3 theme won't play nice.
[*]The file browser will now be gtk3-based (like that of Nautilus) and not gtk2-based (like that of Caja).
[*]BTW, please don't ask people to IM you or to PM you. Let's all see what everyone has to say. Thanks! :) 
[/LIST]

---

### Post by alecz20 on 2016-05-11
> **vasa1 said:**
> [LIST]
[*]You got to make sure your gtk 3 theme is compatible with your distro's gtk3 version. An older gtk3 theme won't play nice.
[/LIST]
How can I check if a theme is compatible with my GTK3 version? You can see the theme I am trying to use in my previous post.

> **vasa1 said:**
> [LIST]
[*]The file browser will now be gtk3-based (like that of Nautilus) and not gtk2-based (like that of Caja).
[/LIST]
This sucks. The gtk3-based file browser is buggy (e.g. the sort by filename mixes files and folders) and looks ugly 8-)
I know, I should probably fill a bug, but I really liked the old GTK2-based file browser.

> **vasa1 said:**
> [LIST]
[*]BTW, please don't ask people to IM you or to PM you. Let's all see what everyone has to say. Thanks! :) 
[/LIST]
I asked for PM to prevent necromancy should this thread get old before a solution is found

---

### Post by Dennis N on 2016-05-11
> The gtk3-based file browser is buggy (e.g. **the sort by filename mixes files and folders**) and looks ugly

No, it's not a bug. It's a setting (but not easy to find). Use dconf-editor, and navigate to the setting shown in the attached screenshot. Check the box on the selected line to sort directories first.

---

### Post by alecz20 on 2016-05-15
Thanks Denis. That worked. Also it appears to be the default behavior, not sure why it was unchecked in my case.

On another note, I found that Firefox 46.0 that comes with Ubuntu Mate 16.04 has nice File Dialogue, so I guess that the issue will be resolved when I upgrade to 16.04.1

---

