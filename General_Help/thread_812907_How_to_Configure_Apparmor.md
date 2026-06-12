---
title: "How to Configure Apparmor?"
date: 2008-05-30
forum: General Help
---

### Post by ShinHadoken on 2008-05-30
Ok, those of you watching all my posts, I've decided to let go of SElinux for now. In the meantime, I know Apparmor is installed by default, but what do I need to know about setting it up?

Thanks,

SH

---

### Post by ShinHadoken on 2008-05-30
bump

---

### Post by ShinHadoken on 2008-05-30
bumpity bump

---

### Post by MythosLegend on 2008-05-30
You weren't able to find any information on apparmor?

Hopefully this can get you started. 
There are several commands you should get familiar with. (you will need sudo for these commands)
/etc/init.d/apparmor start
/etc/init.d/apparmor stop
/etc/init.d/apparmor status
/etc/init.d/apparmor reload

aa-complain NameOfProfile
aa-enforce NameOfProfile

autodep NameOfApplication
logprofile

There are other commands, but I don't use them. 

start - starts apparmor.
stop - stops apparmor.
status - tells you how many profiles you have and what mode they are in.
reload - reloads the profiles.
aa-complain - puts the profile into complain mode. If something doesn't work, put it in this mode. Complain mode is like learning mode. 
aa-enforce - puts the profile into enforce mode. After you are done with your settings, put the profile in this mode. 
autodep - creates a profile and puts it into complain mode.
logprofile - this is where you set the settings like inherit, glob, allow, deny. This is the most important part! It defines what your program can do and can't do. 

If you use the status command, it will show you that you have one profile called /usr/sbin/cupsd in enforce mode. 

What do you want to do first?
You need to make a profile for the application you want.
ex: autodep firefox
(Once firefox is created, the profile will be automatically put into complain mode. You can do a status command to check.)
Open firefox and start using firefox normally. 
Close forefox.
Now type in   sudo logprofile
This is where it will start asking you questions. Pay attention to what it asks you.
In the end, it will ask you to save. 
Your profile is still in complain mode. You need to test out your profile by putting it into enforce mode. 
Open up your application and try to use it. If you are able to open it up and use it normally, then its good. (You can still refine your settings - settings are stored in /etc/apparmor.d/) 
If it doesn't open or the application doesn't run well, you have 2 options:
1) Delete the profile and restart over. (I had to do this a few times)
2) Put the profile back into complain mode. Open up application and use it normally again. Close application. Do sudo logprofile. Put it back into enforce mode. Rinse and repeat.

Fellow apparmor users, please correct me if I'm wrong.

---

### Post by ShinHadoken on 2008-05-31
Thanks so much!!! You have no idea what I've been through trying to figure out how to make this work!!! Thank you!!
 
 
SH

---

### Post by ShinHadoken on 2008-05-31
Uhh, I just have one question... how can I set a default policy for all the other apps (beside stuff like firefox, my mail client, etc., which I'll set up myself) to follow? Is it enabled by default? If so, what are the rules it has?

Thank you infinitely, 

SH

---

### Post by MythosLegend on 2008-05-31
AFAIK I don't think there is a default policy for all programs. You have to customize each application. There are profiles online. I haven't used them myself.

---

### Post by ShinHadoken on 2008-05-31
Well, what apps do I need to customize. I can name Firefox, Pidgin, Thunderbird, and OpenSSH right off... others?

---

### Post by MythosLegend on 2008-05-31
It depends on what programs you have. The ones that you mentioned are pretty good. 
This link gives you an idea. It will probably help you better than I can. 
[http://developer.novell.com/wiki/index.php/Apparmor_FAQ#What_types_of_deployments.2Fapplications.2Fsystems.2C_etc._should_I_first_look_to_leverage_AppArmor_in.3F](http://developer.novell.com/wiki/index.php/Apparmor_FAQ#What_types_of_deployments.2Fapplications.2Fsystems.2C_etc._should_I_first_look_to_leverage_AppArmor_in.3F)

---

### Post by ShinHadoken on 2008-05-31
Thanks, that helps. I read at help.ubuntu.com that for hardy, I can download the apparmor-profiles package. Will that give me a default apparmor profile for all unspecified apps?

---

### Post by buntunub on 2008-05-31
SELinux, APParmor, and Policy Kit were included in Hardy mainly for Enterprise use. I.E., for those that already know well how to use/administer a huge network. You can use them on a small desktop system of course, but there really is not that big of a need because Linux is pretty secure in general; certainly secure enough for home desktop systems. You'll notice too that Hardy also includes preconfigured support for a large variety of networking systems - SSH, NFS, samba, and fuse to name a few. There's improved virtualization support and Pulse Audio to play with too. For all of these there is quite a lot of information available via Google.

---

### Post by ShinHadoken on 2008-06-01
Really though, what does "apparmor-profiles" do? What profiles are included? Does it have pre-installed profiles for all the apps I mentioned like Firefox, Pidgin, SSH, etc?

---

### Post by ShinHadoken on 2008-06-01
bump

---

### Post by ShinHadoken on 2008-06-01
bump

---

### Post by OliverW on 2008-06-01
I just had a short look and downloaded the package
From what I can see the following profiles are included for the following apps:

[LIST]
[*]ping
[*]klogd
[*]syslog-ng
[*]syslogd
[*]avahi-demon
[*]identd
[*]mdnsd
[*]nmbd
[*]nscd
[*]ntpd
[*]smbd
[*]traceroute
[/LIST]

So most of these are just daemons, not user apps.

---

### Post by ShinHadoken on 2008-06-01
Ok, so I need to download that package for those daemons, and make custom profiles for network apps like Firefox and etc. Cool, thanks everyone!

---

