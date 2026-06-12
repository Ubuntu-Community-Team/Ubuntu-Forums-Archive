---
title: "Sost lock-up error?"
date: 2019-05-16
forum: General Help
---

### Post by jet-bundle on 2019-05-16
I have an old Dell Dimension 4600 which was given a new lease of life three years ago with the installation of Lubuntu 16.04. It has been running 18.04 quite happily for nearly a year, but within the past couple of weeks it has failed to boot successfully on four occasions. Failures 1, 2 and 4 left me with a black screen (on failure 4 I noticed occasional coloured dots on the top line of the display before the screen went completely black). Failure 3, though, gave a cyan screen with a message whose top line was something like:
```
[60.052047] watch dog: BUG: soft lock-up - CPU#0 stuck for 22s! [plymouth:369]
```
(I wrote that down by hand, so it might not be exactly right.) After several seconds, the multi-line message scrolled up and a new version appeared below.

The current kernel version is 4.15.0.-50; it was 4.15.0-48 for the first three failures.

I've seen suggestions that this error message can arise when there as a result of hardware issues. There have been no hardware changes recently, though I did fill the empty memory slots when upgrading to 18.04.

Any advice would be appreciated.

---

### Post by jet-bundle on 2019-05-16
Sorry, I checked the text before posting, but not the title. "Soft lockup error?"

---

