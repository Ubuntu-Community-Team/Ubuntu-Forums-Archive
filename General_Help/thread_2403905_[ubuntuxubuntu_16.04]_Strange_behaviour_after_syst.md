---
title: "[ubuntu/xubuntu 16.04] Strange behaviour after systemctl hibernate."
date: 2018-10-17
forum: General Help
---

### Post by kujaw2 on 2018-10-17
Linux 4.4.0-137-generic
Laptop: Dell Latitude E6540

I've just managed to get my laptop hibernate via systemctl hibernate, and then resume. This SO answer helped me to set it up: [https://askubuntu.com/a/849167/424528](https://askubuntu.com/a/849167/424528)
Unfortunately, after resuming, the application sort of freeze, I can move their windows but I cannot click anything there. The Whisker menu doesn't react, when I click Ctrl+Alt+F5 I get blank screen, and when I try to go back to the normal desktop via Ctrl+A+F7 the blank screen persisted.
Here are two journalctl logs, first from the hibernation moment, second one from the resume moment.
systemctl hibernate - [https://pastebin.com/xsQGS442](https://pastebin.com/xsQGS442)
resume from power button - [https://pastebin.com/SiEazMYp](https://pastebin.com/SiEazMYp)

---

