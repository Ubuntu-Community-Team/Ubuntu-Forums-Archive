---
title: "Problem wiht firefox"
date: 2006-10-30
forum: General Help
---

### Post by alekz on 2006-10-30
Hi, i on firefox 2.0 now, but since 1.5 i have this problem: When i run firefox it doesn't open my homepage, in prefferences i set that option, i think is a hijacker software, because sometimes it opens [www.s.com](www.s.com) or some other url about hardware and other stuff, i only have this problem on my current user, on root works fine, anyone can help me?

Thanks.

---

### Post by ciscosurfer on 2006-10-30
Open Firefox and enter **about:config** into the URL bar.  Then type in **home** and see what pops up.  If there is a string there that has **s.com** set, *delete it*.  You also set an *override* by *right-clicking new>string* and type in for the name: **startup.homepage_override_url** and then enter in whatever page you like, for example, **ubuntuforums.org** or even **about:blank** to make absolutely certain your start page starts blank.

---

### Post by bruenig on 2006-10-30
> **alekz said:**
> Hi, i on firefox 2.0 now, but since 1.5 i have this problem: When i run firefox it doesn't open my homepage, in prefferences i set that option, i think is a hijacker software, because sometimes it opens [www.s.com](www.s.com) or some other url about hardware and other stuff, i only have this problem on my current user, on root works fine, anyone can help me?

Thanks.

First, I have no explicit idea, so this is just a thought. I poked around about:config and there appear to be four settings for home page.

To get to about:config if you don't know, just enter it into the location (address) bar. Once you get to the about:config page, put "home" into the filter and that should show all of the homepage settings. See if anything looks out of line.

---

### Post by alekz on 2006-10-30
I already checked all the about:config options, but none resolves the problem, any other idea?

Thanks =)

---

### Post by ciscosurfer on 2006-10-30
You can always erase your Firefox directory (backup your bookmarks, etc.), uninstall Firefox, then reinsall it again and see if that helps.  If that doesn't work, you've got other issues that need to be addressed.

---

