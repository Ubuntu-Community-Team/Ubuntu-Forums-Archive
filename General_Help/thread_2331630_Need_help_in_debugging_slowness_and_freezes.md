---
title: "Need help in debugging slowness and freezes"
date: 2016-07-24
forum: General Help
---

### Post by kanishkdudeja on 2016-07-24
I purchased a new PC lately with the following configuration:

Intel core i3 processor with 3.6 ghz
4 gb ram
160 gb hard-disk

I installed Ubuntu 16.04 on it and it seems to be working extremely slow. I was a user of Ubuntu since 10.04 but switched to Elementary OS a couple of months back since I liked it's user interface.

Their latest beta release seems to have lot of bugs so I switched back to Ubuntu.

Here is what I generally keep open:

1) 10 tabs in Chrome
2) Skype 4.3
3) Slack
4) Sublime text
5) Terminator

I thought the ram and processor are good enough to handle this kind of load.

But I get freezes(the mouse doesn't hang, just takes time) while opening any new application. If I click on the dash, it takes 3-4 secs for the dash window to appear.

If I open Firefox for example, even then it seems to freeze and take a little bit of time to stabilize.

Can anyone help me in debugging these issues?

---

### Post by dragonfly41 on 2016-07-24
I would start by launching System Monitor to inspect the resources used by each of your running processes.

Have you tried systematically closing one application at a time to check resources (e.g. Skype 4.3)?

---

### Post by gordintoronto on 2016-07-24
It seems likely that you are running out of RAM, so it's using the SLOW swap. I use conky to monitor my CPU, RAM and disk space usage. Running top in a terminal might give you useful information.

---

### Post by kanishkdudeja on 2016-07-26
Thanks @gordintoronto and @dragonfly41. Looks like the RAM is the issue. Chrome seems to be taking too much memory. Out of 4 GB RAM, 3.8 GB is being used. Looks like I should upgrade to 12GB or 16GB of ram.

---

