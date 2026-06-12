---
title: "What happens if i overwrite just root partition"
date: 2018-02-03
forum: General Help
---

### Post by jacopastorius82 on 2018-02-03
I'm running xubuntu at the moment. What happens if I install ubuntu in my root partition, keeping my home partition? I mean, in term of desktop enviroment and in term of programs installed. For example i have wine and steam folder in my home partition. Do they keep all settings and games installed in those folders, and the software will run with no problems after the new installation?

---

### Post by oldfred on 2018-02-03
You still need to do good backup, just in case.

Almost all settings are in /home. But you must use Something Else and include the mount of /home partition. And you must be careful to NOT check the format box.
But the apps themselves will not be reinstalled unless a default app.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[URL="http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/"]http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/
[/URL]
 My backup includes dpkg list also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed. 

[URL="http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/"]
[/URL]

---

### Post by jacopastorius82 on 2018-02-03
Thank you for your reply. So, i need to reinstall apps like wine and steam after the new installation but, will the config files of these apps be overwrited or they just keep the old files in /home?

---

### Post by oldfred on 2018-02-03
Not sure about Steam. Never have used it.
Does it have a default with Linux on where it stores its data? Or is it like some Windows apps that like to store data in the application directory?
You need to know that even for backups.

But in /home is .wine with your Wine configurations.

---

