---
title: "Open new log files..."
date: 2008-06-19
forum: General Help
---

### Post by seeker1458 on 2008-06-19
Hey guys, I have am using VMWare to virtualize a Hardy syslog-ng server.  I have everything set up the way I want it, but do any of you know a way to get new *.log files to open automatically in syslog?  I've got around 20 devices pointing to this box, and I don't want to have to check if a device has sent a message.

---

### Post by HalPomeranz on 2008-06-19
Here's a sample syslog-ng.conf file:

```

options { check_hostname(yes); keep_hostname(yes); chain_hostnames(no); };

source inputs {
        internal();
        unix-stream("/dev/log");
        pipe("/proc/kmsg");
        udp();
        tcp(max_connections(100));
};

destination local {
        file("/var/log-ng/$HOST/$YEAR/$MONTH/$FACILITY.$YEAR$MONTH$DAY"
             owner(root) group(root) perm(0600)
             dir_perm(0700) create_dirs(yes));
};

log { source(inputs); destination(local); };

```

This will cause Syslog-NG to automatically divide out your log messages by hostname, year, month, and Syslog facility in directories under /var/log-ng.  And the create_dirs(yes) option will cause it to create new directories as needed as soon as new hosts start logging to your machine.

---

