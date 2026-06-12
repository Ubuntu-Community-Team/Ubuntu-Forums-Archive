---
title: "Limiting user access"
date: 2007-02-08
forum: General Help
---

### Post by kris kincaid on 2007-02-08
I tried searching for an answer (I know its come up before) but, came up empty. Here goes:

I want to completely limit a users access to the system. I don't want them to be able to view folders outside their /home/*user* folder, or even know there are folders outside their /home folder. Basically, I want the people to be able to surf the net, play games, use Open Office, etc, but not be able to tamper with other folders.

I tried System -- Users and Groups then tweaking, but I can still see system files.

Thanks!

---

### Post by aysiu on 2007-02-08
Try install Kubuntu Edgy. That hides just about everything.

Otherwise, you can try *kiosktool*. I think there's a Gnome equivalent, too... Sabayon?

---

### Post by kevinlyfellow on 2007-02-08
Here's a link that may be useful, I don't think it has everything you need though
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-other-kiosk-configs.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/s1-ddg-lockdown-other-kiosk-configs.html)

browse through that manual and I think you will find lots of nice info

---

### Post by kevinlyfellow on 2007-02-08
What about doing this
```
chmod -R 752 /
```
and then setting up a new user that does not belong to the group 'root'

---

### Post by kris kincaid on 2007-02-08
Thanks for the suggestions.

---

