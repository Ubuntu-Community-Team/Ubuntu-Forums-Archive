---
title: "Managing Multiple CRON remotely ??"
date: 2007-12-02
forum: General Help
---

### Post by js.opdebeeck on 2007-12-02
Hello

I know it's not related directly to Ubuntu, but *nix general.

My favorite OS is Ubuntu so I think you can help.

**Do you know a solution to manage multiple CRON events on multiple machines ?**

I've searched  on google and into some forums ... nothing. Only Job Schedulers looks to be a solution. But I only need CRON management .


A tool or a WebTool can do that ?



Thanks


Js

---

### Post by diplo on 2007-12-05
Not sure about Managing Multiple Crons, but you could get one server to send commands to multiple servers via a cron. So only update the one cron, this all depends wether the other units are local and what you want them to do really.

---

### Post by pointone on 2007-12-05
For something really basic and simple, you could just write a shell script that downloads a crontab file from some central server daily and updates the system's crontab file.

For something more advanced and secure, look into Cfengine and Puppet.

---

