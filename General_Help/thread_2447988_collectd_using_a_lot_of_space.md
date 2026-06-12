---
title: "collectd using a lot of space"
date: 2020-07-30
forum: General Help
---

### Post by thisfro on 2020-07-30
Hi

I have a Ubuntu server running for some years now.

The directory ```
/var/lib/collectd/rrd/myserver
``` is a whopping 85GB and my disk is 99% full because of this and sometimes services do not work because of this.

Does anyone know how to free some space from there? I couldn't find anything in the collectd wiki or on google...

Thanks for any help!

---

### Post by TheFu on 2020-07-30
Options:
[LIST]
[*]collectd isn't necessary.  Disable it and delete all the files or
[*]figure out how to remove old files  or
[*]figure out how to have the tool only retain XXX MB of data.
[/LIST]

Google found this: [https://collectd.org/wiki/index.php/Troubleshooting#.28Huge.29_Spikes_in_RRD_files_and_graphs](https://collectd.org/wiki/index.php/Troubleshooting#.28Huge.29_Spikes_in_RRD_files_and_graphs) The wiki assumes knowledge that I don't have. Perhaps you do, so that link makes sense?

Usually, rrd is a rotating set of data, so perhaps there are non-rrd files causing the issues?

---

### Post by thisfro on 2020-07-30
Thanks for the link! (how did I not find this... smh)

I think it was installed as a dependency for something I might have installed back in the day and stopped using. So I don't know a lot about it either, but maybe I can figure something out.

---

