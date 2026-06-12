---
title: "help..Synchronizing clock load problem"
date: 2005-09-23
forum: General Help
---

### Post by cigarette_burn on 2005-09-23
I have a problem with my notebook taking to long to load at start up. I found this in the ubuntuguide.org

Q: Synchronizing clock to ntp.ubuntulinux.org... (taking too long to load)

   1. Read General Notes
   2. Read How to temporary skip boot-up services?
   3. Read How to permanently disable/enable boot-up services?

service_name = ntpdate

I did every thing and got my Boot-Up manager, However, when I try to edit the ntpdate it says that it can not be edited in a run level S. Anyone have any suggestions.
 ](*,)

---

### Post by joshmachine on 2005-09-23
My understanding is that the scripts in /etc/rcS.d are run before any of the other "runlevels".

Easiest thing is to
sudo rm /etc/rcS.d/S51nptdate

This just deletes the link to the script itself /etc/init.d/ntpdate

If you ever want to update your time just run
sudo /etc/init.d/ntpdate restart

Cheers

---

### Post by mlomker on 2005-09-23
> 
I did every thing and got my Boot-Up manager, However, when I try to edit the ntpdate it says that it can not be edited in a run level S. Anyone have any suggestions.
 ](*,)

```

sudo update-rc.d -f ntpdate remove

```

---

### Post by cigarette_burn on 2005-09-24
Thank you. I am trying to get this old notebook running at least enough to be semi-usable. So far not so bad. Thanks again

---

### Post by drogoh on 2005-09-24
An even better suggestion is merely to edit /etc/defaults/ntpdate

Remove the # from NTPSERVERS="pool.ntp.org" and place one in front of NTPSERVERS="ntp.ubuntulinux.org"

In my opinion the NTP pool should be used by default to keep the load distributed due to all of the Ubuntu computers that are updating on boot.

You don't need to remove ntpdate from your default runlevel, it's bad juju to let a clock stray very far (big ntpd fan, myself)

---

### Post by mlomker on 2005-09-24
> You don't need to remove ntpdate from your default runlevel, it's bad juju to let a clock stray very far (big ntpd fan, myself)

The problem is that it runs out of rcS.d prior to networking fully starting and sits and times out.  That's especially a problem for people that don't start wireless until rc2.d or start networking manually after going graphical.

I've reordered all of my scripts and run ntpdate at the end of /etc/init.d/bootmisc.sh instead.

---

### Post by newbie2 on 2005-11-26
[QUOTE=mlomker]I've reordered all of my scripts and run ntpdate at the end of /etc/init.d/bootmisc.sh instead.[/QUOTE]
i had the same problem...my server went down because of electricity net was down...so i started my desktop not knowing the server was out...my desktop kept hanging on the synchronizing clock issue at bootup....should be default at the end of bootup ...?

---

