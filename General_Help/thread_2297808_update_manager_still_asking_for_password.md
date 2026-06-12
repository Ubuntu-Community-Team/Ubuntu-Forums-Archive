---
title: "update manager still asking for password"
date: 2015-10-06
forum: General Help
---

### Post by chopra on 2015-10-06
Hi guys,
When I first installed Ubuntu 14.05 on my current laptop, the update manager allowed updating already installed software without a password.  I had initially wanted to be prompted for a password, 
[http://askubuntu.com/questions/74439/how-to-make-authentication-required-to-install-updates](http://askubuntu.com/questions/74439/how-to-make-authentication-required-to-install-updates)
and changing ResultActive to be auth_admin_keep 
This worked, but then I got sick of typing in the password so I changed it back to "yes".  That had no effect.  As an experiment, I then added two unpriviledged accounts to the Identity, one as a user, the other as a group via the account's login group.
This also has no effect. It still asks only for the password of my primary account, which is the only administrator account.  Perhaps there are some updates that don't update already installed software, and I've just been unlucky recently?

[Update already installed software]
Identity=unix-group:admin;unix-group:sudo;unix-user:casual_user1;unix-group:casual_user2
Action=org.debian.apt.upgrade-packages
ResultActive=yes

Chopra

---

### Post by chopra on 2015-10-17
Got it fixed..sort of.  I just edited the file /usr/share/polkit-1/actions/org.debian.apt.policy, 

<action id="org.debian.apt.upgrade-packages">
    <description gettext-domain="aptdaemon">Upgrade packages</description>
    <message gettext-domain="aptdaemon">To install updated software, you need to authenticate.</message>
    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active> <-------------------------------------------------auth_admin to yes
    </defaults>
  </action>

I'm still not sure why the machine stopped looking at   /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla

Does anyone else see this behavior?

Chopra

---

