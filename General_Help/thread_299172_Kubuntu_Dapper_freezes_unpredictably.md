---
title: "Kubuntu Dapper freezes unpredictably"
date: 2006-11-13
forum: General Help
---

### Post by AusIV4 on 2006-11-13
Recently I've reinstalled my Ubuntu system. I tried Edgy for a while and it rendered my system unbootable on several different installs, so I'm not willing to upgrade - I'd rather stick with my current problems.

Before I tried upgrading to Edgy, my system ran Dapper and was incredibly stable. Now I have virtually the same setup, and it will freeze for no apparent reason. I can move the mouse, and if it's on, amarok will continue to play, but ctrl-alt-backspace does nothing, it requires a reboot. On the system, I run a samba server, a combination frontend/backend mythtv server, synergy (client), and often have Amarok playing something. Additionally, my home directory sits on a Logical Volume that combines two raid volumes.

The only apparent differences between this and my previous setup are that I run Amarok much more frequently, I installed MythTV from a third party repository instead of source (the repository claims it's a backport of the Edgy version), I've upgraded Firefox to version 2.0 and Flash to Beta 9. The crashes frequently occur when Firefox (and consequently flash) are not running, so I doubt those are related. I did rebuild my raid volumes during the downtime, but I don't think my problem is related to that.

Really, I'm quite baffled about what could be causing my problems. I've looked at /var/log/syslog, but I haven't seen anything that looks like it would cause a crash. Does anyone have any suggestions on how to start troubleshooting?
[EDIT]
I think the culprit may have been synergy. It turns out that when I added the auto-start command to the KDE startup files, I starting one as root (for login), then not killing that session before starting another as the user. The second instance of synergy would create several errors a second because it couldn't connect to its host, and I'm thinking that may have caused a memory leak or something. I've corrected the issue so that the root instance gets killed before starting the user instance, and it's run longer than I would have expected it to otherwise. This is also inconsistent with my previous setup (when things were stable), as I believe I had the configuration files correct at that time.

---

