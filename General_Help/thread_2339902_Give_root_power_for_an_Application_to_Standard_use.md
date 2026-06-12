---
title: "Give root power for an Application to Standard user."
date: 2016-10-13
forum: General Help
---

### Post by spitts1316 on 2016-10-13
I have tried opening an App in both the Standard user Acct and the Administrator but in both it says I need root access.   I thought the Admin user had root access so how do I give both
root access?  The Application is EtherApe.  It also says I don't have permission to capture on this device.  It is a Net10 Hotspot.

---

### Post by &amp;KyT$0P# on 2016-10-13
When opening as the admin user, use [FONT=Courier New]sudo[/FONT] (or [FONT=Courier New]gksu[/FONT] if it's a GUI app).

---

### Post by ian-weisser on 2016-10-13
When I use etherape, I open a teminal: 'gksu etherape'

---

### Post by yetimon_64 on 2016-10-13
> **halogen2 said:**
> When opening as the admin user, use [FONT=Courier New]sudo[/FONT] (or [FONT=Courier New]gksu[/FONT] if it's a GUI app).

gksu may not be installed in later versions of ubuntu, apparently it is obsolete nowadays and has to be installed by the user. You can also use sudo with GUI apps IF you use the  "-H" or "--set-home" switch. From man sudo ...
```
     -H, --set-home
                 Request that the security policy set the HOME environment variable to the home
                 directory specified by the target user's password database entry.  Depending on the
                 policy, this may be the default behavior.

``` This switch will protect the user's permissions and ownerships in their home folder that can otherwise be damaged by straight "sudo" usage.

eg for etherape,
```
sudo -H etherape
```
Which effectively has the same effect as the gksu command ian-weisser posted and can be safely used if gksu is not installed.

Regards, yeti.

---

