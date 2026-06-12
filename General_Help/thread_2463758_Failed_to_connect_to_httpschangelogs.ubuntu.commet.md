---
title: "Failed to connect to https://changelogs.ubuntu.com/meta-release-lts at login"
date: 2021-06-17
forum: General Help
---

### Post by beakersbike on 2021-06-17
How do I get rid of the login message "Failed to connect to https://changelogs.ubuntu.com/meta-release-lts".  I can successfully connect to the URL:

[FONT=courier new]# curl -v [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts)[/FONT]
[FONT=courier new]*   Trying 91.189.91.49:443...[/FONT]
[FONT=courier new]* TCP_NODELAY set[/FONT]
[FONT=courier new]* Connected to changelogs.ubuntu.com (91.189.91.49) port 443 (#0)[/FONT]
[FONT=courier new].[/FONT]
[FONT=courier new]. <snip>[/FONT]
[FONT=courier new].[/FONT]
[FONT=courier new]* Connection state changed (HTTP/2 confirmed)[/FONT]
[FONT=courier new]* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0[/FONT]
[FONT=courier new]* Using Stream ID: 1 (easy handle 0x55f3654a1820)[/FONT]
[FONT=courier new]> GET /meta-release-lts HTTP/2
.
. <snip>
.[/FONT]

I've not noticed any other adverse effects.  I can update and upgrade without issue.  The Ubuntu version is 20.04.2 LTS.

[FONT=courier new]# lsb_release -a[/FONT]
[FONT=courier new]No LSB modules are available.[/FONT]
[FONT=courier new]Distributor ID: Ubuntu[/FONT]
[FONT=courier new]Description:    Ubuntu 20.04.2 LTS[/FONT]
[FONT=courier new]Release:        20.04[/FONT]
[FONT=courier new]Codename:       focal[/FONT]

---

