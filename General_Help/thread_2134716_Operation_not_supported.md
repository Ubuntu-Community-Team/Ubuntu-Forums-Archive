---
title: "Operation not supported"
date: 2013-04-12
forum: General Help
---

### Post by Silvernail on 2013-04-12
If this needs to be moved, please do.

I'm confuised. If these were to be updates for the software I have installed om my computer, why were there failures and 'Operation not supported' messages?

> 
dave@Dafydd:~$ sudo software-center
[sudo] password for dave: 
2013-04-11 22:29:01,261 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-04-11 22:29:01,439 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-04-11 22:29:06,207 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-04-11 22:29:07,155 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-04-11 22:29:07,160 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-04-11 22:29:28,216 - softwarecenter.db.update - INFO - skipping region restricted app: 'Comentarios Web' (not whitelisted)
2013-04-11 22:29:31,595 - softwarecenter.db.update - INFO - skipping region restricted app: 'Bulleti d'esquerra de Calonge i Sant Antoni ' (not whitelisted)
2013-04-11 22:29:32,773 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-04-11 22:29:36,835 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2013-04-11 22:29:36,836 - softwarecenter.db.database - INFO - reopen() database
2013-04-11 22:29:36,837 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-04-11 22:29:45,139 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-04-11 22:30:56,524 - softwarecenter.backend.login_sso - INFO - _on_authorization_denied: Ubuntu Software Center
2013-04-11 22:31:06,139 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-04-11 22:33:09,165 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-04-11 22:33:23,139 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
dave@Dafydd:~$ 


---

### Post by deadflowr on 2013-04-12
Is there any need to run software-center as root?

Try running it without sudo and see what happens.

---

### Post by Silvernail on 2013-04-12
> **deadflowr said:**
> Is there any need to run software-center as root?
Out of habit mostly. For the first 20 years of my computer life I did not have a graphic interface, and it is almost natural for me to drop to a terminal and type what I want to do. And I get to see what errors occur.

> Try running it without sudo and see what happens.
When I do, I get to the part to click on 'install' and nothing happens. This condition started when I could no longer logon as root.
I also must run 'update-mangar' with 'sudo'. Both conditions are the same whether I type from a terminal or click on the drop down menu.

Dave

---

### Post by steeldriver on 2013-04-12
In general you should run any graphical apps that require elevated permissions with **gk**sudo not plain sudo - else they tend to inherit a messed up environment

---

### Post by Silvernail on 2013-04-12
Ah ha! Thanks

---

### Post by Silvernail on 2013-04-12
Where is the solved button?

---

