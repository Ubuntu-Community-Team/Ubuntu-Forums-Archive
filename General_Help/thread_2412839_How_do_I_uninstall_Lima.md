---
title: "How do I uninstall Lima"
date: 2019-02-18
forum: General Help
---

### Post by Odense on 2019-02-18
I am running the latest LTS version of Ubuntu.
I have for the past couple of years been using "Lima personal cloud" but now they are stopping operations per 01-03-2019 so I cannot use Lima cloud storage after that date.

So I want to uninstall the Lima software from my Ubuntu laptop - how do I best do this?

---

### Post by again? on 2019-02-18
If you installed via a deb file look at the manual page...
```
man lima
```
> Uninstalling
To remove all user data created by the Lima application, run lima uninstall. Note that if you do this you will permanently lose all the files that have not been uploaded to your Lima yet.
Once this is done, you can uninstall Lima using your package manager if you have used one to install it.
You can find online manual here...[https://support.meetlima.com/hc/en-us/articles/115004950326-README-document](https://support.meetlima.com/hc/en-us/articles/115004950326-README-document)

I installed lima to check.
This shows the local files removed. So backup if needed.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] lima uninstall**
If you want to proceed with uninstall please type 'yes_i_am_sure': yes_i_am_sure
Note, you will lose all local files that are not yet stored on Lima. Continue? [y/n] : y
Removing /home/glen/.local/share/lima/db
Removing /home/glen/Lima
Removing /home/glen/.local/share/lima
Done

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] sudo apt remove lima**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  lima
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 49.8 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 286508 files and directories currently installed.)
Removing lima (1:1.3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...

```

---

### Post by Odense on 2019-02-18
Thank you guber2,

I cannot recall what I used to get it installed - the Linux help was certainly NOT as evolved as I can see it is now. 
I will try what you suggested.

Could I somehow just delete the files/ folders listed:

Removing /home/glen/.local/share/lima/db
Removing /home/glen/Lima
Removing /home/glen/.local/share/lima

or is it better to do the lima uninstall?

---

### Post by again? on 2019-02-18
Those files are just $USER created files.
If you used the package management system to install lima then
```
sudo apt remove lima
```
will remove the lima system files.

Removing a source installed application requires you to know how and where installed and depends on the developer making an uninstall rule.
FYI these are the system files installed by lima.
[http://paste.ubuntu.com/p/nSTvHVdPgN/](http://paste.ubuntu.com/p/nSTvHVdPgN/)

The main directories being 
```
/usr/lib/lima
/usr/bin/lima
```

---

### Post by Odense on 2019-02-19
Thanks again guber2,

I think it will do the trick :-)

---

