---
title: "Report a crash doesn't seem to work"
date: 2021-02-22
forum: General Help
---

### Post by Keith_Helms on 2021-02-22
Sometimes a program will crash and I get a popup window asking whether to report the problem.  I click on "send" and nothing happens.  Today vlc crashed and I looked out in the /var/crash directory and found 

```
-rw-r----- 1 keith    whoopsie 253977705 Feb 22 21:11 _usr_bin_vlc.1000.crash
-rw-rw-r-- 1 keith    whoopsie         0 Feb 22 21:11 _usr_bin_vlc.1000.upload
-rw------- 1 whoopsie whoopsie        37 Feb 22 21:18 _usr_bin_vlc.1000.uploaded
```

The file uploaded contains the text

```
_usr_bin_vlc.1000.uploaded: Permission denied
```

I seem to recall that in previous releases, clicking on send sometimes opened a webpage describing a known problem.  Is there something I need to configure to get this working again?

---

### Post by Keith_Helms on 2021-03-02
Ping

---

### Post by deadflowr on 2021-03-02
Here: [https://help.ubuntu.com/community/ReportingBugs#Reporting_a_crash_when_no_message_shows_up_and_crash_files_created]("https://help.ubuntu.com/community/ReportingBugs#Reporting_a_crash_when_no_message_shows_up_and_crash_files_created")

---

