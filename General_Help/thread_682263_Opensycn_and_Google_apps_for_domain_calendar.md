---
title: "Opensycn and Google apps for domain calendar"
date: 2008-01-29
forum: General Help
---

### Post by frediE on 2008-01-29
Anyone get Opensync Google Calendar plugin (libopensync-plugin-google-calendar) to work with Google Apps for Domain (GAFD)?

I got syncing with my Nokia working perfectly with a generic Google calendar, but the Google Domain seems to be missing the private url address?  or at least not liking the /private/full


i used this write-up to get syncing working with with a regular google calendar. 
[http://anojrs.blogspot.com/2008/01/ubuntu-gutsy-synchronizing-google.html](http://anojrs.blogspot.com/2008/01/ubuntu-gutsy-synchronizing-google.html)

i have shard google calendars before and the gafd seems to be missing the private address stuff.

ohhh i am sooo close...  any suggestions?

---

### Post by frediE on 2008-01-30
No i am not answering myself but i got the Private Address's showing up in Google Apps for Domain.  It is up to the administrator to enable the ability for users to share outside of the directory.

Set user ability needs to be...
Share all information, and outsiders can change calendars - Users can share their calendar information with people outside your domain. This includes guest list, location, and description. Private Addresses are displayed.

Details found here...
[http://www.google.com/support/a/bin/answer.py?answer=60765&useful=1&show_useful=1&comment=en%20:%20how%20to%20get%20%22Private%20Addresses%20are%20displayed.%22&#helpful](http://www.google.com/support/a/bin/answer.py?answer=60765&useful=1&show_useful=1&comment=en%20:%20how%20to%20get%20%22Private%20Addresses%20are%20displayed.%22&#helpful)


(talking to myself)this did not solve the multisync issue but i seems like it is getting me closer.(/end talking to my self).

---

### Post by CosminGC on 2008-02-01
Could you please point me to a guide to sync a nokia to evolution? if not with google calendar would be fine thank you.

---

### Post by frediE on 2008-02-04
Of course, Glad to help.

This post should get you going in the correct direction.
[http://ubuntuforums.org/showthread.php?t=260676](http://ubuntuforums.org/showthread.php?t=260676)

Just follow the directions and install the libopensync-plugins that you want to sync with.

---

### Post by frediE on 2008-02-07
I think I have tried every combo in the opensync google-calendar configuration and I am not having any luck.

This is the default....
```
<config>
	<url>http://www.google.com/calendar/feeds/USER@gmail.com/private/full</url>
	<username>USER@gmail.com</username>
	<password>PASSWORD</password>
</config>
```


I would expect this to work with google apps for domain.... But it doesn't
```
<config>
	<url>http://www.google.com/calendar/feeds/USER@DOMAINl.com/private/full</url>
	<username>USER@DOMAIN.com</username>
	<password>PASSWORD</password>
</config>
```

---

