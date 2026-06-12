---
title: "Unable to locate theme engine in module_path: &quot;clearlooks&quot;,"
date: 2015-04-29
forum: General Help
---

### Post by Ralph L on 2015-04-29
I have install clearlooks-phenix v5 into xubuntu 14.04 LTS in /usr/share/themes as instructed.  It seems to run mostly ok, although the slider didn't turn blue as advertised and couple other things seemed strange.  However, when I run ```
sudo thunar
``` it gives off a long list of the errors ```
(thunar:2369): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",
```  However, this root based version of thunar seems to run ok.  If I start thunar from the Terminal with just ```
thunar
``` I don't get the errors.  Can anybody tell me what is wrong????

---

### Post by kerry_s on 2015-04-29
if you installed it from the repos, then it should have installed the gtk2-engines so you should have clearlooks theme installed.

you know that's a gtk3 theme in a gtk2 os ?

---

### Post by Ralph L on 2015-04-30
kerry_s
Thank you very much for responding.  No I did not know that xubuntu 14.04 was a gtk2 os.  And it hadn't occurred to me that clearlooks-phenix might be in the xubuntu repositories.  My previous system is ubuntu 12.04, and when I found clearlooks-phenix for that system, it wasn't in repositories.  The clearlooks-phenix web site said to select the version based on the version of libgtk-3-0 in synaptic.  I have libgtk-3-0 3.10.8, which indicates clearlooks phenix v5 for ubuntu, so I installed that in xubuntu.  Anyway, I deleted v5 and installed from the xubuntu repository (v3).  The error message went away and everything seems to be working now.

Edit:  Oh, and I had to install gtk2-engines using synaptic.  I think this was what really solved the problem as this installs the clearlooks engine, which the scripts refer to in many places.  Also, the error message mentioned the clearlooks engine.  In addition, installing gtk2-engines made the slider bar in the application windows turn blue as it was supposed to be all along.  So it may be that I could have continued running clearlooks-phenix v5, but just installing gtk2-engines.  Maybe I'll experiment some time.....

Thank you again for the help

---

