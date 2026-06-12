---
title: "Running root crontab commands at different user levels"
date: 2015-02-26
forum: General Help
---

### Post by diyhouse on 2015-02-26
Ok,.. my dilemma is this,..

I am running a ubuntu apt-get update, followed by a apt-get -y upgrade. this works fine.

But then I need to run some additional commands within a script as a user,.. so as to take on that users environment,.. but to also run some commands as root from that user eg make install,..

Do I need to split the script up and run "su - username" prior to running commands,.... I'm not quite sure how to do this bit...

Thanks

---

### Post by ian-weisser on 2015-02-26
apt has a fantastic daily cron job already. See /etc/cron.daily/apt . Why duplicate it? You can simply change the settings to match your needs.

cron, and scripts started by cron won't take on the user's entire environment.
Classic Example: A cron-started script won't have a DISPLAY environment variable.
You can test this by running a cron job that outputs 'printenv' to a tempfile.

"run some commands as root from that user" seems confusing. Either it's run by a user, or as root. Not sure what you are trying to do.

I wouldn't run make or make install from a cron job without a really good reason. Seems like a great way to execute arbitrary code...you are placing a lot of trust on the author of that makefile.

---

### Post by kjohri on 2015-02-27
If you execute the command "su - username", you effectively become that user. Now to do some privileged work while effectively being that user, you can execute the command as "sudo command". The requirement is that that user must have the permission to execute commands as superuser. You can add that user in the sudo group with the command, "sudo adduser *that_user* sudo".

---

### Post by diyhouse on 2015-02-27
> [COLOR=#000000]the command "su - username", you effectively become that user. Now to do some privileged work while effectively being that user, you can execute the command as "sudo command"[/COLOR]

So will the system know that I have come from root,. and NOT prompt me for a passwd if I run this within a cron job.........

> [COLOR=#000000]"run some commands as root from that user" seems confusing. Either it's run by a user, or as root. Not sure what you are trying to do.[/COLOR]

To clarify this a bit for folks,... this is a media centre (Mythbuntu 14.04),.. and every couple of weeks I do a s/w update,... now,.. if one of these updates is a kernel update,.. the drivers for my tuner cards are blown away.... necessitating a reinstall of the previously installed tune card drivers,.. I understand DISPLAY may not be reset,.. but this *should *not matter for this scenario. 

So what I am attempting to do,.. is run the s/w update,...followed by a reinstall of the tuner card drivers,... thus IF a kernel update has taken place,.. system functionality will not be lost following a reboot...  

or am I barking up the wrong tree.................

---

