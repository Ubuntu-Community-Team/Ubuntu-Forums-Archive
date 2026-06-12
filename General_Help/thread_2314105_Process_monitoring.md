---
title: "Process monitoring"
date: 2016-02-18
forum: General Help
---

### Post by neil37 on 2016-02-18
Hi,

I'm looking to try and get a script made that will monitor for a few processes and restart them if they have crashed/ended.

I have been given this script to try for teamspeak server.
> [I]#!/bin/bash
[/I]
*while true; do*

*        if [ "`ps ax | grep -v grep | grep ts3server`" ]; then *
*        echo -e "TS3_Server: $COL_GREEN WORKS! $COL_RESET" *
*        else*
*        echo -e "TS3_Server: $COL_RED ERROR! $COL_RESET"*
*                sleep 5*
*        ./ts3server_startscript.sh start*
*        fi*

*sleep 60*
*done*



My questions are:

1: How do I find the process name running on the system (e.g ts3server as per above) that I'd need to include in a script like the one above?
2: How can I make a script that will do several processes monitors that will restart the script if it crashes?
3: Can I just run the script as a crontab and that will work?

Thanks in advance to anyone who will help me understand this?

P.S I'm running Ubuntu 14.04 and I'm a starter at Ubuntu.

---

### Post by potato5 on 2016-02-20
I can advise monit ([https://mmonit.com/monit/](https://mmonit.com/monit/)), it does what you want (easy and simple).

---

