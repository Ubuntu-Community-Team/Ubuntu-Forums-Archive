---
title: "Deleting automatically old logs"
date: 2008-03-30
forum: General Help
---

### Post by miju on 2008-03-30
hi,

I operate a tor/freenet server and I notice that I'm accumulating enormous numbers of logs of various types. All these logs seem to contain a lot traffic data including ip addresses. I am worried because I don't want this to happen. I thought that Tor and Freenet did not keep these logs........how I can prevent the logging ........or at least how can I set the logs to be deleted automatically after 1 or 2 days?:confused:

---

### Post by dcstar on 2008-03-30
> **miju said:**
> hi,

I operate a tor/freenet server and I notice that I'm accumulating enormous numbers of logs of various types. All these logs seem to contain a lot traffic data including ip addresses. I am worried because I don't want this to happen. I thought that Tor and Freenet did not keep these logs........how I can prevent the logging ........or at least how can I set the logs to be deleted automatically after 1 or 2 days?:confused:

```
man logrotate
```

---

### Post by jethro10 on 2008-04-11
Hi,
Im sure the previous answer "MAN LOGROTATE" is useless to you and I hate it when that happens to me.

Your a new user it seems with a basic question. Anyhow. I'm just learing this myself and came upon this thread.

look in /etc/logrotate.d and you may find a script there that rotates your programs logs. If so just edit it and you might see something like

rotate 6 or rotate 52
this is how many old copies it keeps. Just change it down.

EXAMPLE :-
If you go into synaptic package manager and search for tor, for instance, select it then click properties, as long as its installed, then the installed files tab, you can find  /etc/logrotate.d/tor as an entry.

this will be your tor rotate script. brows to the file and double click to view it
In here rotate 5 is set to 5 old days and also says compress, so your old logs will be zipped up (or is it tar'd up?)

To edit the file, from a command prompt type:-
gksudo gedit /etc/logrotate.d/tor



Does this help?
J

---

