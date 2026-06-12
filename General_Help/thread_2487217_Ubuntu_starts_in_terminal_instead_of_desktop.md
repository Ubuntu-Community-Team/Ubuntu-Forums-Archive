---
title: "Ubuntu starts in terminal instead of desktop"
date: 2023-05-27
forum: General Help
---

### Post by luncaaa on 2023-05-27
Hello o/

I turned off the computer about a week ago (and it was working fine) and I turned it on today but, for some reason, I can only see a terminal. I have searched for solutions, tried to update all packages and have run a lot of commands, but nothing worked.

The users and the files seem to be ok (nothing was lost), only the desktop is missing. How can I fix this?

---

### Post by TheFu on 2023-05-27
Check the system logs for errors.  Otherwise you'll be guessing about thousands of possible causes.

Always check the logs first. Always.

---

### Post by luncaaa on 2023-05-27
Which logs should I check? There are a lot of files in /var/log.
I tried checking syslog, but it's too long and it doesn't fix in the screen... How can I fully view it or scroll in the terminal?

---

### Post by Holger_Gehrke on 2023-05-27
Use 'less /var/log/syslog' to view ('q' to quit, 'h' for help). Alternatively you could use 'journalctl' to view the journal. The journal is stored in a binary format but journalctl allows you to view it in a human-readable way (AFAIK it uses less to show that, so the same keys are used). 'journalctl' has a lot of option to control what parts of the journal you want to see. To get a description of any command that gives an overview of the available options, you can use 'man command', for example 'man journalctl'. The journal has quite a few entries that don't go to the syslog, so it might show a problem more clearly than that; or it might hide the 'tree' you're looking for in a 'forest' of irrelevant messages ...

Holger

---

### Post by Rubi1200 on 2023-05-27
I would start by checking the last boot log entries for any clues.

```
sudo journalctl -b
```

---

### Post by TheFu on 2023-05-27
> **luncaaa said:**
> Which logs should I check? There are a lot of files in /var/log.
I tried checking syslog, but it's too long and it doesn't fix in the screen... How can I fully view it or scroll in the terminal?

I like to use **grep**, but there are many different techniques.  You can use any of them.
[https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#1-overview)
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

Or one of the 500 other sources would be fine. Logs in all Linux systems are pretty much the same. Reading them is a basic skill.
There might be some GUI tools as well. I've just never used them.

With the introduction of systemd, we've gained an amazing logging system, called journald too.  The tool to access those "journals" is called **journalctl**. It has too many features to list them all. And since they are all documented already, you can check out that documentation. It if 99.999999% already on your system.  Reading the documentation for each command is a basic skill.  We aren't really supposed to tell you to read the manpages in these forums, but if nobody tells you about them, how will you ever know and be able to help yourself with future issues?  **man journalctl** would be the manpage for seeing system logs on Ubuntu, using that tool.

I still like to use **grep** myself.  It gets to the point and we can search 50-500 logs with a single command when I don't have a clue about what may be causing a problem.  

If I know what the issue is and just need the logs to confirm it, then I'd look in the specific, related, log file.  For example, if I'm having issues with any graphical stuff, then I'd check the X/Windows Server log.  That's in /var/log/Xorg.0.log .  I had an issue with it a few days ago (unlikely you had the same issue) on a server system I'd just installed.  Seems I'd forgotten to install a few initialization settings and programs, so I could only login to a local console or through ssh.

When a previously working GUI stops working, there are lots and lots of things that could happen to break it.  Most are related to software updates, misconfiguration or some hardware error like a disk that is just starting to fail and took a few key files with those failures.  

I've had a GPU start failing, but not completely die too.  Figuring out that one took some time. The logs showed GPU issues, but nothing else.  Eventually, I installed an old GPU and everything was good - no crashes, so that was the fix.  $40 later (it was a long time ago) and I had a new, very cheap, low-end GPU for the system.  If the issue had been a PSU, then other parts would have shown power issues, under voltage, etc.  I've also had a cracked motherboard cause issues.  Fortunately, that was just with the onboard NIC, so data corruption when writing to a server was seen. No other systems writing to that same server were involved.  Using completely different network ports and the corrupted files followed the computer, not the location (ethernet jack).

Anyway, it is unlikely anyone here will see the issue before you do, so you'll need to perform the trouble shooting - simplify and test.  Remove different parts that could be causing the issue, until only 1 part is left and has to be the cause.  For example, have you booted from an Ubuntu installation ISO into Try Ubuntu mode?  If that works, you know it isn't the GPU, motherboard, or anything not used as part of the normal, installed OS, boot.  That generally leaves the HDD, installed software, or configuration.

---

