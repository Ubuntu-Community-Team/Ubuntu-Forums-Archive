---
title: "Unable to start Gnome or Cinnamon from GDM - 15.04"
date: 2015-04-30
forum: General Help
---

### Post by badrx1011 on 2015-04-30
It all started when I upgraded to 15.04.  Everything seemed fine.  Got the name Gnome 3.16 running.  Everything seems great.  Until my roommate asked where the Plex went?  I look, and sure enough, the server is not working.  Turns out that in 15.04 there was a switch to systemd vs upstart?  Something like this.  So I get on the Plex forum and look for a solution.  The solution requires me to add .service file somewhere and what not.  So I do so but it doesn't want to work.... turns out I need to purge my old plex server installation.  So I do that using dpkg --purge and during the uninstall I get this message:

> [h=1][SIZE=2]Start: Unable To Connect To Upstart: Failed To Connect To Socket /Com/Ubuntu/Upstart: Connection Refused[/SIZE][/h]

So I google it and I find someone who fixes the problem with this code:

```
[COLOR=#000000][FONT=Menlo]sudo dpkg-divert --local --rename --add /sbin/initctl[/FONT][/COLOR]
```

And then I'm to follow that with this code:

```
[COLOR=#000000][FONT=Menlo]ln -s /bin/true /sbin/initctl[/FONT][/COLOR]
```

Sweet, it works.  I no longer get that "Unable to connect to Upstart" message.  I launch the Plex server, presto --everythings cherry.  Reboot time.

Booya!  PROBLEM ... Gnome blanks out and stalls.  Cinnamon fallsback to some archaic version.  I'm stuck, don't know what to do now.  I go back to the blog I got the code from and post my results.  Still waiting on someone to respond.  I thought I would post something on here in case someone knows of anything and would lend some help?

Someone posted on his blog with this response:

> [COLOR=#3F4549][FONT=Helvetica Neue]don't you  guys forget to relink /sbin/initctl to /sbin/initctl.distrib or the distro don't boot afterwards.[/FONT][/COLOR]

I don't really know what that means but I take a stab at it because, again -no responses, and do this:

```
ls -s /sbin/initctl.distrib /sbin/initctl 
```

I get an error, /sbin/initctl already exists.  Ok... So why don't I delete or remove /sbin/initctl??  then re link to the iinitctl.distrib??? BRB kids.  This just might work.

---

### Post by ajgreeny on 2015-04-30
It seems to me that upgrading from 14.10 to 15.04 has caused many more problems than is usually the case simply because of this move to systemd instead of upstart.

If you want to return to always starting with upstart instead of systemd you may have to boot to the upstart version in grub.cfg.  I have not really tried any of this for any length of time yet but it may be that grub-customiser can change your boot options and let you boot to the upstart entry in the grub menu as default, or you can edit /etc/default/grub to boot to the appropriate entry in grub.cfg, whichever one that is, and I do not have 15.04 running properly yet to check it.

---

### Post by badrx1011 on 2015-04-30
> **ajgreeny said:**
> It seems to me that upgrading from 14.10 to 15.04 has caused many more problems than is usually the case simply because of this move to systemd instead of upstart.

If you want to return to always starting with upstart instead of systemd you may have to boot to the upstart version in grub.cfg.  I have not really tried any of this for any length of time yet but it may be that grub-customiser can change your boot options and let you boot to the upstart entry in the grub menu as default, or you can edit /etc/default/grub to boot to the appropriate entry in grub.cfg, whichever one that is, and I do not have 15.04 running properly yet to check it.

Ok, thanks for your reply.  I will look into changing the grub.cfg because, funny you should bring up grub, I can't get an option to boot into "recovery" or other kernels like I use to.  Also, to report on my progress:  It didn't work.  Now instead of a blank screen, I get thrown back into GDM --which is better I guess.

---

### Post by badrx1011 on 2015-04-30
> **ajgreeny said:**
> It seems to me that upgrading from 14.10 to 15.04 has caused many more problems than is usually the case simply because of this move to systemd instead of upstart.

If you want to return to always starting with upstart instead of systemd you may have to boot to the upstart version in grub.cfg.  I have not really tried any of this for any length of time yet but it may be that grub-customiser can change your boot options and let you boot to the upstart entry in the grub menu as default, or you can edit /etc/default/grub to boot to the appropriate entry in grub.cfg, whichever one that is, and I do not have 15.04 running properly yet to check it.

Well, that's odd... I'm getting that I no longer have 'grub' installed from console: "The program 'grap' is currently not installed."  But 'update-grub' still works. ... ???

---

