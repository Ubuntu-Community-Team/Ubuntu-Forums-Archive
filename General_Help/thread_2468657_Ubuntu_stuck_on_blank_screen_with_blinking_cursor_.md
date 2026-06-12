---
title: "Ubuntu stuck on blank screen with blinking cursor on boot"
date: 2021-11-06
forum: General Help
---

### Post by wyoumans on 2021-11-06
I asked for help on Ask Ubuntu but haven't gotten any useful information, so I thought I'd try here before I give up and reinstall. Ask Ubuntu post: [https://askubuntu.com/questions/1373627/ubuntu-stuck-on-blank-screen-with-blinking-cursor](https://askubuntu.com/questions/1373627/ubuntu-stuck-on-blank-screen-with-blinking-cursor)


I am running Windows 10, Ubuntu 20.04.2 dual boot on a Lenovo Thinkpad. The setup has been working fine for me for 6+ months.

[B]The problem:
[/B]
The laptop was on with the lid closed and the charging cable got disconnected, and it died. Now when I turn it on it loads grub but if I try to boot Ubuntu it goes to a black screen showing a blinking cursor. I can still boot the Windows partition without a problem.

**What I've tried:**

Apparently a common cause for this is an update/install gone wrong. From grub I can boot Ubuntu in recovery mode where I ran the `dpkg` tool to repair any potentially broken packages but that turned up nothing, and with the lid closed long before it powered off there shouldn't have been any chance of something critical being interrupted.

A couple other common causes are lack of space (my Ubuntu partition has >80% free) and Nvidia graphics driver issues (I use intel integrated graphics).

I tried running `fsck` from a live cd which found no issues, even with the `-f` (force) option, so it doesn't appear to be a filesystem corruption.

I also tried using the boot repair tool ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) which reinstalled grub, but the problem persists and the pastebin log from the tool doesn't seem to indicate any problems.

Before I cave and reinstall, does anyone have an idea what the issue could be?

---

