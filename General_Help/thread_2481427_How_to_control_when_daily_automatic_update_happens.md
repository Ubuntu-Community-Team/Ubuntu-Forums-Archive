---
title: "How to control when daily automatic update happens?"
date: 2022-11-29
forum: General Help
---

### Post by grant-b-edwards on 2022-11-29
How do you control when the automatic daily update happens on Ubuntu Server 22.04?

One of my servers does not have internet access during certain days/hours. When the daily update attempts to run without internet access it hangs forever. It will not finish/fail (even when internet access resumes). Every time this happens, I have to manually kill it. I'd like to keep automatic daily updates enabled, but I need to block it from running during certain periods. I found a thread elsewhere that suggested setting up a chron job that uses gsettings commands to enable/disable automatic updates, but the gsetting schemas mentioned in that thread done't seem to exist in server 22.04, and I can't find anything relevant in the existing schemas.

How to I block automatic updates from happening during certain time periods?

---

### Post by ian-weisser on 2022-11-29
Asked multiple places: [https://askubuntu.com/questions/1443080/how-to-control-when-daily-automatic-update-happens](https://askubuntu.com/questions/1443080/how-to-control-when-daily-automatic-update-happens)

---

