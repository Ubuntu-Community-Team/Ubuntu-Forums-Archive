---
title: "Evolution issue with one email account"
date: 2016-01-23
forum: General Help
---

### Post by mikeebean on 2016-01-23
I'm trying to use Evolution 3.16.0 (in Ubuntu GNOME 15.04) to access two Outlook.com email addresses. One account works flawlessly. The other will only load a portion of my emails and errors out. I tried running Evolution from the command line and in debug mode, but can't sort out the problem. I'm hoping someone here can shed some light on the issue? The errors from the logfile are:

*on startup:*
(evolution:8197): camel-WARNING **: Failed to initialize NSS SQL database in sql:/etc/pki/nssdb: NSS error -8126

*on access of troublesome inbox:*
(evolution:8197): GLib-GObject-CRITICAL **: g_closure_unref: assertion 'closure->ref_count > 0' failed

*while (I think) retrieving mail in troublesome account:*
(evolution:8197): camel-imapx-CRITICAL **: imapx_untagged_fetch: assertion 'found' failed
[imapx:A] Data read failed with error 'unexpected server response:'
[imapx:A] I/O: ''
[imapx:A] Ignoring timeout error, nothing was waiting (original error: Socket I/O timed out)

These all seem very generic, but I don't know what they might mean. Any help would be appreciated!
(Thanks to [Eduardo López]("http://askubuntu.com/users/465763/eduardo-l%c3%b3pez") at AskUbuntu for the terminal/debugging instructions.)

---

