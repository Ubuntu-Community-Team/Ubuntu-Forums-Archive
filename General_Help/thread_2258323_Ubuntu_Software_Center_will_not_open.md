---
title: "Ubuntu Software Center will not open"
date: 2014-12-26
forum: General Help
---

### Post by sillyboy on 2014-12-26
Ubuntu 12.04
Gnome 2

I just tried to open the Ubuntu Software Center.  It starts to open then just quits without any error messages or anything.  I ran "sudo apt-get update", and "sudo apt-get upgrade" in the Terminal and received no errors. 

Synaptic Package Manager acts the same way when trying to open... 

What can or should I do next?

Thanks

Sb

---

### Post by schragge on 2014-12-26
Try to open it from terminal in debug mode:
```
software-center --debug
```
This way you won't miss error messages if anything goes wrong.

---

### Post by sillyboy on 2014-12-26
> **schragge said:**
> Try to open it from terminal in debug mode:
```
software-center --debug
```
This way you won't miss error messages if anything goes wrong.

Thanks for the quick help....Before I do that I ran "alacarte" in the terminal and received this error>>>

-------------------------------
in terminal:  alacarte   ---- results:

-Name:~$ alacarte 
Fontconfig error: "/home/ralph/.config/font-manager/local.conf", line 1: XML declaration not well-formed 

----------------------------

Should I proceed with the debug code or wait for yor reply to this message?

thanks

---

### Post by schragge on 2014-12-26
Proceed anyway. You also can try to open /home/ralph/.config/font-manager/local.conf in any editor to see what formatting issues it has, but I'd be very surprised if any errors in there were affecting Software Center in some way.

---

### Post by sillyboy on 2014-12-27
> **schragge said:**
> Proceed anyway. You also can try to open /home/ralph/.config/font-manager/local.conf in any editor to see what formatting issues it has, but I'd be very surprised if any errors in there were affecting Software Center in some way.

Entered: software-center --debug, below are the results.  I can't make heads or tails of it.  Thanks

```
ralph@ralph-System-Product-Name:~$ software-center --debug
Fontconfig error: "/home/ralph/.config/font-manager/local.conf", line 1: XML declaration not well-formed
2014-12-27 08:46:26,623 - softwarecenter.ui.gtk3.em - DEBUG - EM's: 17 15 21
2014-12-27 08:46:26,733 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-12-27 08:46:26,737 - softwarecenter.performance - DEBUG - opening the pkginfo: 0.00367093086243
2014-12-27 08:46:26,738 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2014-12-27 08:46:26,739 - softwarecenter.performance - DEBUG - opening the xapiandb: 0.0012481212616
2014-12-27 08:46:26,741 - softwarecenter.performance - DEBUG - building the icon cache: 0.00150012969971
2014-12-27 08:46:26,750 - softwarecenter.performance - DEBUG - creating the backend: 0.00903487205505
2014-12-27 08:46:26,750 - softwarecenter.performance - DEBUG - get the app-manager: 4.88758087158e-05
2014-12-27 08:46:26,751 - softwarecenter.ui.gtk3.utils - DEBUG - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2014-12-27 08:46:26,763 - softwarecenter.performance - DEBUG - ViewManager: 0.00984692573547
2014-12-27 08:46:26,875 - softwarecenter.performance - DEBUG - building panes: 0.112093925476
2014-12-27 08:46:27,153 - softwarecenter.backend.reviews.rnr - DEBUG - refresh with days_delta: 1
2014-12-27 08:46:27,153 - softwarecenter.backend.spawn_helper - DEBUG - run_generic_piston_helper()
2014-12-27 08:46:27,157 - softwarecenter.backend.spawn_helper - DEBUG - running: '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 1}']' as pid: '3170'
2014-12-27 08:46:27,158 - softwarecenter.backend.reviews - DEBUG - _retrieve_votes_from_server started
2014-12-27 08:46:27,159 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-12-27 08:46:27,161 - softwarecenter.ui.gtk3.app - DEBUG - query for the update-database exception 'org.freedesktop.DBus.Error.ServiceUnknown: The name com.ubuntu.Softwarecenter was not provided by any .service files' (probably ok)
2014-12-27 08:46:27,161 - softwarecenter.performance - DEBUG - create review loader: 0.285869121552
2014-12-27 08:46:27,162 - softwarecenter.plugin - DEBUG - no dir ''
2014-12-27 08:46:27,162 - softwarecenter.plugin - DEBUG - no dir '/usr/share/software-center/plugins'
2014-12-27 08:46:27,162 - softwarecenter.plugin - DEBUG - no dir '/home/ralph/.local/share/software-center/plugins'
2014-12-27 08:46:27,162 - softwarecenter.plugin - DEBUG - plugins are '[]'
2014-12-27 08:46:27,162 - softwarecenter.performance - DEBUG - create plugin manager: 0.000294923782349
2014-12-27 08:46:27,172 - softwarecenter.performance - DEBUG - create SoftwareCenterApp: 0.466958999634
2014-12-27 08:46:27,304 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2014-12-27 08:46:27,305 - softwarecenter.ui.gtk3.panes.softwarepane - DEBUG - show_appview_spinner
2014-12-27 08:46:27,307 - softwarecenter.ui.gtk3.app - DEBUG - on_menu_file_activate
2014-12-27 08:46:27,314 - softwarecenter.backend.spawn_helper - DEBUG - helper_finished: '3170' '0'
2014-12-27 08:46:27,314 - softwarecenter.backend.spawn_helper - DEBUG - got data for cmd: '['/usr/share/software-center/piston_generic_helper.py', '--datadir', '/usr/share/software-center/', 'RatingsAndReviewsAPI', 'review_stats', '{"days": 1}']'='[<softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xa993c8c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98c4c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98c8c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98cac>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98b8c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98bac>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98bec>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xac98c0c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb52950c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb5294ec>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb5294cc>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb5294ac>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb52944c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb5293ec>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb5293cc>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb52936c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb529b2c>, <softwarecenter.backend.piston.rnrclient_pristine.ReviewsStats object at 0xb529b8c>]'
2014-12-27 08:46:27,316 - softwarecenter.ui.gtk3.app - DEBUG - on_review_stats_loaded: '5462'
2014-12-27 08:46:27,755 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2014-12-27 08:46:27,982 - softwarecenter.ui.gtk3.panes.viewswitcher - DEBUG - on_transactions_changed '{}'
2014-12-27 08:46:27,991 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/ui/gtk3/models/pendingstore.py', 72, '_on_lowlevel_transactions_changed')'
2014-12-27 08:46:27,991 - root - DEBUG - on_transaction_changed  (0)
2014-12-27 08:46:27,997 - softwarecenter.ui.gtk3.panes.viewswitcher - DEBUG - on_transactions_changed '{}'
2014-12-27 08:46:28,001 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/ui/gtk3/models/pendingstore.py', 72, '_on_lowlevel_transactions_changed')'
2014-12-27 08:46:28,001 - root - DEBUG - on_transaction_changed  (0)
Segmentation fault
ralph@ralph-System-Product-Name:~$
```

---

### Post by schragge on 2014-12-27
Well, the output doesn't give me any clues either. Just a *segmentation fault*, without any obvious errors before it. Try to clean the cache, and see if that helps:
```
rm -r ~/.cache/software-center/
```
If it doesn't, remove the cache for APT, too:
```

sudo rm /var/cache/apt/*.bin

```

---

### Post by sillyboy on 2014-12-27
Allright I will try to remove the cache.  Before I do I wanted to tell you about the big red dot on my top panel bar, it has a white line running thru it E to W.  When I click on it there is a message that says "A problem occurred when checking for the updates".

Thanks

---

### Post by sillyboy on 2014-12-27
I tried removing the cache.  USC still will not open.  Below are the results for the second entry.  ??


ralph@ralph-System-Product-Name:~$ rm -r ~/.cache/software-center/



ralph@ralph-System-Product-Name:~$ sudo rm /var/cache/apt/*.bin
[sudo] password for ralph: 
rm: cannot remove `/var/cache/apt/*.bin': No such file or directory
ralph@ralph-System-Product-Name:~$ 

Thank You

---

### Post by sillyboy on 2014-12-28
Solved ;)  From the big red Dot on the top panel I clicked on "Preferences" and this took me to the, USC>Software Sources>Other Software.  I unchecked the entry "Added by Software Center yada, yada...", I then was asked to update, entered password.  When it was done, USC and SPM worked as it should.

Thank for the help everyone

Sb  ):P

---

### Post by schragge on 2014-12-28
Glad you've got it figured out.

---

