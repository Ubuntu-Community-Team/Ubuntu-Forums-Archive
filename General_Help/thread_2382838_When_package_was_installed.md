---
title: "When package was installed"
date: 2018-01-17
forum: General Help
---

### Post by raleigh3 on 2018-01-17
I would like to find out WHEN pm-utils was installed.
  
I looked thru PPM but could not find install date.

---

### Post by DuckHook on 2018-01-17
```
_P=pm-utils && (cat /var/log/dpkg.log{,.1};zcat /var/log/dpkg.log.*.gz) | egrep --text "^[^ ]* [^ ]* (configure|install|remove|status [^ ]*|trigproc|upgrade) $_P[: ]" | sort --reverse | less
```
There is no guarantee this will return any results. It goes through the *dpkg* logs grepping for *pm-utils*, then sorts them in chronological order. Results are displayed using *less*. Problem is, dpkg logs are rotated out after 14 iterations (including the gzipped ones). So, if your install was before the oldest log date, it won't show you a result.

---

### Post by vasa1 on 2018-01-18
> **DuckHook said:**
> ... Problem is, dpkg logs are rotated out after 14 iterations (including the gzipped ones). So, if your install was before the oldest log date, it won't show you a result.
By the way, the *dpkg*-related logrotate file is */etc/logrotate.d/dpkg*. Mine has```
/var/log/dpkg.log {
	monthly
	rotate **60**
	compress
	delaycompress
	missingok
	notifempty
	create 644 root root
}
/var/log/alternatives.log {
	monthly
	rotate **60**
	compress
	delaycompress
	missingok
	notifempty
	create 644 root root
}
```

---

### Post by raleigh3 on 2018-01-18
thanks. It found that package.

---

### Post by vasa1 on 2018-01-19
```
zgrep "status installed package_name" /var/log/dpkg.log*
```will list all the dates, from newest to oldest, on which *package_name* was installed.

As DuckHook pointed out, the results depend on how many logs are present.

---

### Post by raleigh3 on 2018-01-19
Thanks guys for the info.

I had rotate 12 in my dpkg.

---

