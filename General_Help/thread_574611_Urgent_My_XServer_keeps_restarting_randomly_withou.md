---
title: "Urgent: My XServer keeps restarting randomly without reason."
date: 2007-10-13
forum: General Help
---

### Post by applegrew on 2007-10-13
Of late my Xserver suddenly restarts without any reason. Such thing never happened before. I have absolutely no clue except for a error message (shown in red) in the system log shown below.
```
10/09/2007 11:05:24 AM	applegrew	none	last message repeated 7 times
10/09/2007 11:05:08 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/09/2007 11:05:07 AM	applegrew	gconfd (root-8430)	starting (version 2.18.0.1), pid 8430 user 'root'
10/09/2007 11:05:07 AM	applegrew	gconfd (root-8430)	Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
10/09/2007 11:05:07 AM	applegrew	gconfd (root-8430)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
10/09/2007 11:05:07 AM	applegrew	gconfd (root-8430)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
10/09/2007 11:05:07 AM	applegrew	gconfd (root-8430)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
10/09/2007 11:05:07 AM	applegrew	gconfd (root-8430)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
10/09/2007 11:05:02 AM	applegrew	gconfd (apple-8427)	starting (version 2.18.0.1), pid 8427 user 'apple'
10/09/2007 11:05:02 AM	applegrew	gconfd (apple-8427)	Resolved address "xml:readwrite:/home/apple/.gconf" to a writable configuration source at position 1
10/09/2007 11:05:02 AM	applegrew	gconfd (apple-8427)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
10/09/2007 11:05:02 AM	applegrew	gconfd (apple-8427)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
10/09/2007 11:05:02 AM	applegrew	gconfd (apple-8427)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
10/09/2007 11:05:02 AM	applegrew	gconfd (apple-8427)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
10/09/2007 11:05:01 AM	applegrew	/USR/SBIN/CRON[8422]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 11:04:15 AM	applegrew	none	last message repeated 3 times
10/09/2007 11:04:15 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/09/2007 11:00:01 AM	applegrew	/USR/SBIN/CRON[8290]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 11:00:01 AM	applegrew	/USR/SBIN/CRON[8288]	(root) CMD (sv_aliases --cron)
10/09/2007 11:00:01 AM	applegrew	/USR/SBIN/CRON[8286]	(root) CMD (sv_mailman --cron >> /var/log/sv_database2system.log)
10/09/2007 11:00:01 AM	applegrew	/USR/SBIN/CRON[8284]	(root) CMD (   sv_spamcheck_monitor)
10/09/2007 11:00:01 AM	applegrew	/USR/SBIN/CRON[8282]	(root) CMD (   sv_cleaner --cron)
10/09/2007 10:55:01 AM	applegrew	/USR/SBIN/CRON[8260]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:54:01 AM	applegrew	/USR/SBIN/CRON[8255]	(root) CMD (   sv_spamcheck_monitor)
10/09/2007 10:50:01 AM	applegrew	/USR/SBIN/CRON[8239]	(root) CMD (   sv_cleaner --cron)
10/09/2007 10:50:01 AM	applegrew	/USR/SBIN/CRON[8238]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:50:01 AM	applegrew	/USR/SBIN/CRON[8237]	(root) CMD (sv_aliases --cron)
10/09/2007 10:45:01 AM	applegrew	/USR/SBIN/CRON[8195]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:45:01 AM	applegrew	/USR/SBIN/CRON[8192]	(root) CMD (   sv_spamcheck_monitor)
10/09/2007 10:44:44 AM	applegrew	gconfd (root-7649)	GConf server is not in use, shutting down.
10/09/2007 10:44:44 AM	applegrew	gconfd (root-7649)	Exiting
10/09/2007 10:44:38 AM	applegrew	NetworkManager	<WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 
10/09/2007 10:44:38 AM	applegrew	NetworkManager	<information>^IUpdating allowed wireless network lists. 
10/09/2007 10:44:37 AM	applegrew	hcid[5841]	Default passkey agent (:1.24, /org/bluez/passkey_agent_8174) registered
10/09/2007 10:44:33 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/09/2007 10:44:32 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
[COLOR="Red"]10/09/2007 10:44:26 AM	applegrew	kdm_greet[7942]	Internal error: memory corruption detected
10/09/2007 10:44:21 AM	applegrew	kdm_greet[7942]	Can't open default user face
10/09/2007 10:44:17 AM	applegrew	kdm[5969]	X server for display :0 terminated unexpectedly[/COLOR]
10/09/2007 10:44:17 AM	applegrew	gconfd (apple-7646)	Received signal 15, shutting down cleanly
10/09/2007 10:44:17 AM	applegrew	gconfd (apple-7646)	Exiting
10/09/2007 10:40:01 AM	applegrew	/USR/SBIN/CRON[7918]	(root) CMD (sv_aliases --cron)
10/09/2007 10:40:01 AM	applegrew	/USR/SBIN/CRON[7916]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:39:22 AM	applegrew	none	last message repeated 10 times
10/09/2007 10:39:15 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/09/2007 10:39:14 AM	applegrew	gconfd (root-7649)	starting (version 2.18.0.1), pid 7649 user 'root'
10/09/2007 10:39:14 AM	applegrew	gconfd (root-7649)	Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
10/09/2007 10:39:14 AM	applegrew	gconfd (root-7649)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
10/09/2007 10:39:14 AM	applegrew	gconfd (root-7649)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
10/09/2007 10:39:14 AM	applegrew	gconfd (root-7649)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
10/09/2007 10:39:14 AM	applegrew	gconfd (root-7649)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
10/09/2007 10:39:07 AM	applegrew	gconfd (apple-7646)	starting (version 2.18.0.1), pid 7646 user 'apple'
10/09/2007 10:39:07 AM	applegrew	gconfd (apple-7646)	Resolved address "xml:readwrite:/home/apple/.gconf" to a writable configuration source at position 1
10/09/2007 10:39:07 AM	applegrew	gconfd (apple-7646)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
10/09/2007 10:39:07 AM	applegrew	gconfd (apple-7646)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
10/09/2007 10:39:07 AM	applegrew	gconfd (apple-7646)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
10/09/2007 10:39:07 AM	applegrew	gconfd (apple-7646)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
10/09/2007 10:37:26 AM	applegrew	NetworkManager	<WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 
10/09/2007 10:37:26 AM	applegrew	NetworkManager	<information>^IUpdating allowed wireless network lists. 
10/09/2007 10:37:26 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/09/2007 10:37:25 AM	applegrew	hcid[5841]	Default passkey agent (:1.17, /org/bluez/passkey_agent_7608) registered
10/09/2007 10:37:22 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
[COLOR="Red"]10/09/2007 10:37:03 AM	applegrew	kdm_greet[7395]	Internal error: memory corruption detected[/COLOR]
10/09/2007 10:37:01 AM	applegrew	gconfd (root-6256)	GConf server is not in use, shutting down.
10/09/2007 10:37:01 AM	applegrew	gconfd (root-6256)	Exiting
[COLOR="Red"]10/09/2007 10:36:57 AM	applegrew	kdm_greet[7395]	Can't open default user face[/COLOR]
10/09/2007 10:36:50 AM	applegrew	gconfd (apple-6253)	Received signal 15, shutting down cleanly
10/09/2007 10:36:50 AM	applegrew	gconfd (apple-6253)	Exiting
[COLOR="Red"]10/09/2007 10:36:49 AM	applegrew	kdm[5969]	X server for display :0 terminated unexpectedly[/COLOR]
10/09/2007 10:36:01 AM	applegrew	/USR/SBIN/CRON[7373]	(root) CMD (   sv_spamcheck_monitor)
10/09/2007 10:35:01 AM	applegrew	/USR/SBIN/CRON[7366]	(root) CMD (   sv_spamcheck_scholar 2> /dev/null > /dev/null)
10/09/2007 10:35:01 AM	applegrew	/USR/SBIN/CRON[7365]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:30:01 AM	applegrew	/USR/SBIN/CRON[7345]	(root) CMD (sv_mailman --cron >> /var/log/sv_database2system.log)
10/09/2007 10:30:01 AM	applegrew	/USR/SBIN/CRON[7340]	(root) CMD (sv_aliases --cron)
10/09/2007 10:30:01 AM	applegrew	/USR/SBIN/CRON[7337]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:30:01 AM	applegrew	/USR/SBIN/CRON[7335]	(root) CMD (   sv_groups  --cron && sv_users --cron )
10/09/2007 10:27:01 AM	applegrew	/USR/SBIN/CRON[7301]	(root) CMD (   sv_spamcheck_monitor)
10/09/2007 10:26:56 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/09/2007 10:25:02 AM	applegrew	/USR/SBIN/CRON[7284]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:25:02 AM	applegrew	/USR/SBIN/CRON[7283]	(root) CMD (   sv_cleaner --cron)
10/09/2007 10:20:01 AM	applegrew	/USR/SBIN/CRON[7265]	(root) CMD (sv_aliases --cron)
10/09/2007 10:20:01 AM	applegrew	/USR/SBIN/CRON[7263]	(root) CMD (   sv_spamcheck_peon)
10/09/2007 10:18:04 AM	applegrew	syslogd 1.4.1#20ubuntu4	restart.
10/09/2007 10:18:04 AM	applegrew	anacron[5883]	Normal exit (1 job run)
10/09/2007 10:18:04 AM	applegrew	anacron[5883]	Job `cron.daily' terminated (mailing output)

```

---

### Post by PmDematagoda on 2007-10-13
Try and do a memory test and see if you get any errors.

---

### Post by applegrew on 2007-10-13
you mean to say to test the ram? OK I will but currently I am downloading something so I will have to wait. In the mean time please suggest other possible test or solutions. Furthremore, I am not having any problem else where like Mysql databse is not getting corrupted.

---

### Post by PmDematagoda on 2007-10-13
You can also try:-

1) Open up your CPU

Take the memory modules out, clean the gold contacts with a soft, clean and dry cloth, do not damage the contacts, and clean the slots out by using some dry air to get any dirt out and check to see if it occurs again.

2) Or, a less reliable method:-

Let your BIOS do a quick-memory check on startup


But all in all, I think the best method for you would be to first test the RAM using the Memory Test.

---

### Post by applegrew on 2007-10-13
ok I will do that as opening by comp is not possible; I have a laptop and I have never opened it before. BTW I m too "an experimenter, give me the most stable OS out there and I can make it unstable in a few hours." ;)

---

### Post by applegrew on 2007-10-13
ok I will do that as opening by comp is not possible; I have a laptop and I have never opened it before. BTW I m too "an experimenter, give me the most stable OS out there and I can make it unstable in a few hours." ;)

---

### Post by applegrew on 2007-10-17
Bump.

I opened and cleaned my RAM (it wasn't dirty though). I also checked my memory using the Memtest at th boot; well actually after running for around 6 hrs and seeing no errors when it showed no signs of finishing, I terminated it.

What's more my Xserver just now restarted again. dunno whay. help........

---

### Post by applegrew on 2007-10-17
and hey BTW the system log again.
```
10/18/2007 02:40:01 AM	applegrew	/USR/SBIN/CRON[6724]	(root) CMD (sv_aliases --cron)
10/18/2007 02:40:01 AM	applegrew	/USR/SBIN/CRON[6722]	(root) CMD (   sv_spamcheck_peon)
10/18/2007 02:36:01 AM	applegrew	/USR/SBIN/CRON[6668]	(root) CMD (   sv_spamcheck_monitor)
10/18/2007 02:35:01 AM	applegrew	/USR/SBIN/CRON[6626]	(root) CMD (   sv_spamcheck_peon)
10/18/2007 02:32:43 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/18/2007 02:32:23 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/18/2007 02:32:23 AM	applegrew	gconfd (apple-6536)	starting (version 2.18.0.1), pid 6536 user 'apple'
10/18/2007 02:32:23 AM	applegrew	gconfd (apple-6536)	Resolved address "xml:readwrite:/home/apple/.gconf" to a writable configuration source at position 1
10/18/2007 02:32:23 AM	applegrew	gconfd (apple-6536)	Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
10/18/2007 02:32:23 AM	applegrew	gconfd (apple-6536)	Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
10/18/2007 02:32:23 AM	applegrew	gconfd (apple-6536)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
10/18/2007 02:32:23 AM	applegrew	gconfd (apple-6536)	Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
10/18/2007 02:32:14 AM	applegrew	gconfd (apple-5918)	GConf server is not in use, shutting down.
10/18/2007 02:32:14 AM	applegrew	gconfd (apple-5918)	Exiting
10/18/2007 02:32:07 AM	applegrew	NetworkManager	<WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - org.freedesktop.NetworkManagerInfo.NoNetworks. 
10/18/2007 02:32:07 AM	applegrew	NetworkManager	<information>^IUpdating allowed wireless network lists. 
10/18/2007 02:32:06 AM	applegrew	hcid[5416]	Default passkey agent (:1.17, /org/bluez/passkey_agent_6508) registered
10/18/2007 02:32:01 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
10/18/2007 02:31:59 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 
[B][COLOR="Red"]10/18/2007 02:31:54 AM	applegrew	kdm_greet[6253]	Internal error: memory corruption detected
10/18/2007 02:31:50 AM	applegrew	kdm_greet[6253]	Can't open default user face
10/18/2007 02:31:46 AM	applegrew	kdm[5596]	X server for display :0 terminated unexpectedly[/COLOR][/B]

10/18/2007 02:30:01 AM	applegrew	/USR/SBIN/CRON[6210]	(root) CMD (   sv_groups  --cron && sv_users --cron )

10/18/2007 02:30:01 AM	applegrew	/USR/SBIN/CRON[6209]	(root) CMD (sv_aliases --cron)

10/18/2007 02:30:01 AM	applegrew	/USR/SBIN/CRON[6207]	(root) CMD (sv_mailman --cron >> /var/log/sv_database2system.log)

10/18/2007 02:30:01 AM	applegrew	/USR/SBIN/CRON[6205]	(root) CMD (   sv_spamcheck_peon)

10/18/2007 02:27:01 AM	applegrew	/USR/SBIN/CRON[6195]	(root) CMD (   sv_spamcheck_monitor)

10/18/2007 02:25:05 AM	applegrew	modprobe	WARNING: Not loading blacklisted module ipv6 

10/18/2007 02:25:01 AM	applegrew	/USR/SBIN/CRON[6169]	(root) CMD (   sv_cleaner --cron)

10/18/2007 02:25:01 AM	applegrew	/USR/SBIN/CRON[6167]	(root) CMD (   sv_spamcheck_peon)

10/18/2007 02:23:48 AM	applegrew	syslogd 1.4.1#20ubuntu4	restart.

10/18/2007 02:23:48 AM	applegrew	anacron[5458]	Normal exit (1 job run)

10/18/2007 02:23:48 AM	applegrew	anacron[5458]	Job `cron.daily' terminated
```

---

