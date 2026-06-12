---
title: "Firefox Crashing"
date: 2015-08-08
forum: General Help
---

### Post by jim_deadlock on 2015-08-08
I have a laptop running 14.04 (fully updated) with 2 user accounts on it. One user runs Firefox 39.0 perfectly, no problems. The other crashes Firefox whenever I try to click a link to a file eg. a .deb, or try to load certain web pages (presumably due to embedded media or something).

I tried to fix this by replacing the entire ~/.mozilla/firefox directory on the problematic user account with a copy of the good one. Still no joy though. I've checked Preferences > Applications and it all looks fine but FF still crashes.

---

### Post by Vladlenin5000 on 2015-08-08
Have you tried to simply delete the profile instead of copying one into another? The folder will be recreated.

---

### Post by jim_deadlock on 2015-08-08
Yes I did also try that, got a fresh vanilla profile but still with the crashes.

When I double-click a .deb file in file manager it opens fine in Software Centre so it doesn't appear to be a general MIME issue.

---

### Post by monkeybrain20122 on 2015-08-08
Start Firefox in the terminal and click one of those links then see if you get any error message when it crashes.

---

### Post by don62 on 2015-08-13
I am running 14.04, & since doing software updates yesterday, am experiencing constany crashes or freezing in Firefox.
Have started Firefox in Terminal & get the following message.

(process:2385): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

(firefox:2385): Gtk-WARNING **: Unable to locate theme engine in module_path: "hcengine",

Means nothing to me, so any help will be greatly appreciated.

---

### Post by jim_deadlock on 2015-08-16
I finally fixed this by deleting ~/.config

There's tons of stuff in there so I have no idea which subdirectory was causing the problem, you can probably narrow it down with trial and error but I'm not bothered as long as my Firefox is working.

---

