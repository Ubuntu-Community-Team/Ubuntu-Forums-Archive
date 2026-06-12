---
title: "Authentication is required to update SMART data from..."
date: 2015-04-18
forum: General Help
---

### Post by ytandogan2 on 2015-04-18
On ubuntu 14.04, when switch account is used ubuntu asks password for SMART data update for sda.
This is kind of annoying to enter password 2 times when switching between users.

Any solution?

Thanks in advance.

---

### Post by yatsenkoanton on 2015-05-02
I started to have the same problem ufter updating to 15.04. Don't know how to fix it though.

---

### Post by jonnylinuxnerd on 2015-05-05
Bump. I've also been getting this a lot since upgrading to 15.04! Does anyone know what's causing it? Any bugs filed about this?

---

### Post by jonnylinuxnerd on 2015-05-05
The only reference I've found so far is this: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=776029](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=776029)

---

### Post by jonnylinuxnerd on 2015-05-05
I've searched on Launchpad and can't find any existing bug report for this issue. @ytandogan2 , @yatsenkoanton if I created a bug report for this would you be willing to contribute so we can figure out what the causation of this bug is? It's only started affecting me on upgrade 15.04 but if it affects 14.04 as well then it is probably the result of a strange condition in the configuration somewhere! The drive it's asking me about is the primary boot disk drive as opposed to external storage etc. (2Gb Seagate drive). Is this the case for you guys as well?

Also @yatsenkoanton can you confirm that this is occurring because of a switch of user for you too?

---

### Post by jonnylinuxnerd on 2015-05-05
Also can you look check in your auth.log files? I'm seeing things like this in mine just after a user switch:

```
May  5 20:17:25 system-name polkitd(authority=local): Operator of unix-session:c2 FAILED to authenticate to gain authorization for action org.freedesktop.udisks2.ata-smart-update for system-bus-name::1.96 [psensor] (owned by unix-user:user)
May  5 20:18:37 system-name polkitd(authority=local): Operator of unix-session:c4 FAILED to authenticate to gain authorization for action org.freedesktop.udisks2.ata-smart-update for system-bus-name::1.167 [psensor] (owned by unix-user:user2)
```

The unix-session:c2 suggests this may have something to do with systemd as I believe this is the referencing it uses for sessions and would explain the occurrence in the upgrade to 15.04. I'm still learning more about how systemd works though as it's new. It also doesn't explain why @ytandogan2 is having issues either and it may be that your issue is caused by something else other than what me and @yatsenkoanton are experiencing.

---

### Post by ytandogan2 on 2015-05-20
@jonnylinuxnerd, sorry for late answer. Yes I am willing to contribute.

---

### Post by jonnylinuxnerd on 2015-06-18
@ytandogan2 Hey I resolved this issue ages ago. It's caused by lm-sensors. Click on the thermometer indicator (which is lm-sensors) -> Preferences -> Providers -> Then untick 'Enable support of udisks2'. That seems to make it go away. It probably is still a configuration type bug, but I'm not sure if I really need the udisks2 reading for what I use lm-sensors for. Hope this helps!

---

### Post by ytandogan2 on 2015-06-19
@jonnylinuxnerd, thanks for the update. Actually I happen to solve the issue exactly as you described some time ago but did not had time to write.

---

### Post by sancelot on 2015-11-02
This problem is related to polkit you have to edit /usr/share/polkit-1/actions files in order to change the behaviour

---

### Post by sancelot on 2015-11-02
edit org.freedesktop.udisks2.policy  , replace auth_admin with yes .

I know, it may be now possible to set it up  some persistant rules files in /etc folder. because this modification may be overriden in case of upgrade.
more details here [http://www.freedesktop.org/software/polkit/docs/latest/polkit.8.html](http://www.freedesktop.org/software/polkit/docs/latest/polkit.8.html)

---

### Post by crockabiscuit on 2016-07-25
I had to add the following file to authorize myself to udisks2's "org.freedesktop.udisks2.ata-smart-update" action.

/etc/polkit-1/rules.d/00_user_blah.rules

> 
polkit.addRule(function (action, subject) {
    var YES = polkit.Result.YES;
    var permission = {
        "org.freedesktop.udisks2.ata-smart-update": YES
    };


    if (subject.user == "blah") {
        return permission[action.id];
    }


    return polkit.Result.NOT_HANDLED;
});


---

### Post by evgen-veprickiy on 2016-11-10
> **jonnylinuxnerd said:**
> @ytandogan2 Hey I resolved this issue ages ago. It's caused by lm-sensors. Click on the thermometer indicator (which is lm-sensors) -> Preferences -> Providers -> Then untick 'Enable support of udisks2'. That seems to make it go away. It probably is still a configuration type bug, but I'm not sure if I really need the udisks2 reading for what I use lm-sensors for. Hope this helps!


OMG U really genius. Thanks, solved!

---

### Post by justen_m on 2017-02-13
> **jonnylinuxnerd said:**
> @ytandogan2 Hey I resolved this issue ages ago. It's caused by lm-sensors. Click on the thermometer indicator (which is lm-sensors) -> Preferences -> Providers -> Then untick 'Enable support of udisks2'. That seems to make it go away. It probably is still a configuration type bug, but I'm not sure if I really need the udisks2 reading for what I use lm-sensors for. Hope this helps!
Thanks! I know this is an almost two-year thread bump, but googling brought up this thread. Workaround works with 16.04.2LTS, 4.8 kernel, and Psensor 1.1.3. Like someone else mentioned, I really don't care about the disk temp, I just want to monitor the cpu temp, but udisks2 is checked by default.

---

### Post by oldos2er on 2017-02-13
Old thread closed.

---

