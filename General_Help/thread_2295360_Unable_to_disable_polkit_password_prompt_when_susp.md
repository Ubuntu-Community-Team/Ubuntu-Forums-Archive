---
title: "Unable to disable polkit password prompt when suspending laptop"
date: 2015-09-18
forum: General Help
---

### Post by amukher on 2015-09-18
I Iam using 14.04 minimal installation and trying to configure things on my own.

I am using pm-suspend to suspend my laptop. I do not want to be prompted for admin password by polkit while trying to suspend my laptop. To achieve this, I have created a file with the following path **/etc/polkit-1/rules.d/10-disable-suspend.rules** with the following content:

[HTML]/* Allow members of the adm group to execute the defined actions 
 * without password authentication, similar to "sudo NOPASSWD:"
 */
polkit.addRule(function(action, subject) {
    if ((action.id == "org.freedesktop.login1.suspend") &&
        subject.isInGroup("adm"))
    {
        return polkit.Result.YES;
    }
});
[/HTML]

However, this does not seem to have any effect and I am still prompted for the admin password. Does anyone know what could be wrong?

Thanks

---

### Post by bart2pub on 2015-11-29
Ubuntu 14.04 is still using the old version of polkit, where there are no .rules files but only .pkla and .conf files. 

on the command prompt, do
  pkaction --version

if it says < 0.106, then you can only use the the old syntax

you can create a .pkla file in /etc/polkit-1/localauthority/

Good luck !

---

