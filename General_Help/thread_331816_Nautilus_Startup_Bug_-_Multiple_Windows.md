---
title: "Nautilus Startup Bug - Multiple Windows"
date: 2007-01-05
forum: General Help
---

### Post by cmcginty on 2007-01-05
I recently experienced some very strange behavior in Nautilus.

1) From 'Computer' desktop icon. Double click launches Nautilus. None of the following problems listed below are reproducible.

2) From terminal, running 'nautilus' or 'nautilus --no-desktop' brings up 5 or 6 Nautilus windows instead of just one? Also, some times its just 2 windows, and sometimes only 1. At the time I have background tasks (mencoder, launched with 'nice' command) running taking up 100% cpu. Will test later when CPU usage goes down.

3) From terminal, running 'nautilus' or 'nautilus --no-desktop' defaults browser to list view. However, I can not add more columns using "View -> Visible Columns". When going into menu, clicking 'show' / 'hide' has no effect. I was able to reproduce this many times, but currently can't reproduce. Will keep testing this one.

4) Similar to 3, but at some attempts, when I was able to add 'type' column to my view. If I browsed to a new directory, the 'type' column would disappear, and then same symptoms as 3.

Any ideas on how to debug or workaround these errors if I see them again?

- Casey

---

