---
title: "home folder by default readable for all?"
date: 2017-02-11
forum: General Help
---

### Post by DB4711 on 2017-02-11
Hello,

I installed long time ago ubuntu with one user (systerm admin). Now I added another one (standard user) and noticed that both home folder are readable by default for everyone... is that common? I would assume I can only r/w my own home folder...

Thanks for help!

---

### Post by Dennis N on 2017-02-11
> I would assume I can only r/w my own home folder...
Other users don't by default have write permissions for those files, just read.

---

### Post by DB4711 on 2017-02-11
Hello Dennis N,

thanks for your answer.

OK, so reading other ones home is common in ubuntu?! That's weird and not really comprehensible to me. A user should only read his own files...

So every ubuntu user has to change his own home to "everyone -> nothing"?!

---

### Post by Impavidus on 2017-02-11
Yes, well, not necessarily. Sometimes you may want to give others read access to some parts of your home directory, but it's more common to use the group permissions for that.

---

### Post by Dennis N on 2017-02-11
Yes, If there is a file you don't want others to open and view, you can change the read permission for others on that file to 'none'. On a directory, no read permission means that you can't list the contents of the directory.

---

### Post by DB4711 on 2017-02-11
OK, thank you two for your help!

---

### Post by SeijiSensei on 2017-02-11
This is a "philosophical" decision by Canonical justified by a belief in the sharing ethic of open source.

Other distributions, especially those that target servers, do not follow the same belief.  On RedHat/CentOS systems, each user's $HOME folder has 700 permissions, which limit access only to the user that owns that folder.  Like you, I think that should be the norm, but Canonical thinks differently.

If you want to establish limited permissions by default, use the command "sudo nano /etc/login.defs" to edit that file, and change the line that reads
```
UMASK 022
```
to
```
UMASK 077
```
Now the home directory for any new users will have 700 permissions.  (The "umask" is the octal complement of the permissions mask, calculated by subtracting each digit from seven.  So a value of 022 translates to permissions of 755, while 077 results in 700 permissions.)

---

### Post by DB4711 on 2017-02-12
Hello SeijiSensei,

good to know... and intersting. Thanks for you help![**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=698195")

---

