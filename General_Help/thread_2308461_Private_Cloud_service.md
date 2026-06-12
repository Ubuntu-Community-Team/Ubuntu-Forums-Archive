---
title: "Private Cloud service ?"
date: 2016-01-03
forum: General Help
---

### Post by gordon16 on 2016-01-03
Hi,

I`m searching for a private cloud service I can isntall on my file server to access my personell files from other locations by using a web browser.
I have tested ownCloud, but i have removed it for security reason.

I have to use my exsisting /home/xxx dirs and I have also some exstra dir under /mnt/hd/ I want to access inside my cloud.

Your feedback highly appreciated.

---

### Post by vcbranco on 2016-01-03
Hi,

You can install from the [https://owncloud.org/]("https://owncloud.org/") repository

[https://download.owncloud.org/download/repositories/stable/owncloud/]("https://download.owncloud.org/download/repositories/stable/owncloud/")


After that you can find many addons to achive your goal

(Some time ago I saw an addon who does what you need)

---

### Post by gordon16 on 2016-01-03
> **vcbranco said:**
> Hi,

You can install from the [https://owncloud.org/](https://owncloud.org/) repository

[https://download.owncloud.org/download/repositories/stable/owncloud/](https://download.owncloud.org/download/repositories/stable/owncloud/)


After that you can find many addons to achive your goal

(Some time ago I saw an addon who does what you need)

Thank you for feedback, so I can manage what I want by using addons, thats cool.
I have been informed that owncloud is not safe, and have been removed from ubuntu package list?

---

### Post by pqwoerituytrueiwoq on 2016-01-03
The devs of owncloud had canonical remove it cause canonical was not pushing security updates, leaving users with a false sense of security (i have been lazy about updating it on my pi, just updated from 6 to 8)
here is the download page
[https://download.owncloud.org/download/repositories/stable/owncloud/](https://download.owncloud.org/download/repositories/stable/owncloud/)

---

### Post by 1clue on 2016-01-03
You could install a VPN on your network, and put owncloud behind that.

---

### Post by gordon16 on 2016-01-04
> **1clue said:**
> You could install a VPN on your network, and put owncloud behind that.

Yes, I can do that.
But the whole idea for me was to be abel to access private files from where i wanted.

Has it been many exploit to it?

---

### Post by vcbranco on 2016-01-04
> **pqwoerituytrueiwoq said:**
> The devs of owncloud had canonical remove it cause canonical was not pushing security updates, leaving users with a false sense of security (i have been lazy about updating it on my pi, just updated from 6 to 8)
here is the download page
[https://download.owncloud.org/download/repositories/stable/owncloud/](https://download.owncloud.org/download/repositories/stable/owncloud/)


This is correct.

The problem is only with the packages in the ubuntu repository (outdated).
Using the ownCloud repository you will have always the owncloud updated and you should be fine regarding security

If you use OpenVPN (installed in your server), you be able to access and/or syncronize files in your server from everywhere with windows, linux, osx, android, etc
With this you will have another layer of security

---

### Post by gordon16 on 2016-01-04
> **vcbranco said:**
> This is correct.

The problem is only with the packages in the ubuntu repository (outdated).
Using the ownCloud repository you will have always the owncloud updated and you should be fine regarding security

If you use OpenVPN (installed in your server), you be able to access and/or syncronize files in your server from everywhere with windows, linux, osx, android, etc
With this you will have another layer of security

I will think about these, but then i need to install a vpn software on the computer i want to use... so its not so flexible, but I say thank you for you tips.
Sad that they are not have enougf focus on saftey, like dropbox, box.com etc...

---

### Post by dragonfly41 on 2016-01-04
You could try [https://spideroak.com/opendownload](https://spideroak.com/opendownload) which encrypts your shared files and allows you to access shared files remotely (like dropbox .. which is not encrypted).

---

### Post by mastablasta on 2016-01-04
> **gordon16 said:**
> 
Sad that they are not have enougf focus on saftey, like dropbox, box.com etc...

obviously you haven't read what you were told - Owncloud was patching, Ubuntu wasn't. if you installed from Owncloud's repository you would have secure patched version, if you installed from Ubuntu repository you would have unpatched version for a time before patch would be available. the time between the patch and it's availability in Ubuntu repository was too long. Owncloud is focused on safety as well as other things. I am a bit disappointed that they have issue with user convenience. their insistence on everything must sync is a bit ridiculous, though they did make some changes to the policy and their client.

if you really found a security issue with Owncloud you should report it on their github bug reporting site rather than just uninstalling the program.

If you read some ***[FUD ]("https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt")***then nothing will work for you.

next - there is also:
SeaFile - [https://www.seafile.com/](https://www.seafile.com/)
Pydio - doesn't work on Ubuntu yet or people report some issue but works on CentOS7, RHEL7 & Debian 8 - [https://pydio.com/](https://pydio.com/)

a bit different is:
BtSync - *[https://getsync.com/](https://getsync.com/)*

---

### Post by gordon16 on 2016-01-04
> **mastablasta said:**
> obviously you haven't read what you were told - Owncloud was patching, Ubuntu wasn't. if you installed from Owncloud's repository you would have secure patched version, if you installed from Ubuntu repository you would have unpatched version for a time before patch would be available. the time between the patch and it's availability in Ubuntu repository was too long. Owncloud is focused on safety as well as other things. I am a bit disappointed that they have issue with user convenience. their insistence on everything must sync is a bit ridiculous, though they did make some changes to the policy and their client.

if you really found a security issue with Owncloud you should report it on their github bug reporting site rather than just uninstalling the program.

If you read some ***[FUD ]("https://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt")***then nothing will work for you.

next - there is also:
SeaFile - [https://www.seafile.com/](https://www.seafile.com/)
Pydio - doesn't work on Ubuntu yet or people report some issue but works on CentOS7, RHEL7 & Debian 8 - [https://pydio.com/](https://pydio.com/)

a bit different is:
BtSync - *[https://getsync.com/](https://getsync.com/)*

Thank you for your feedback, I will read through slow later today, and figure out what I will do.
ownCloud looks to be nice when it comes to interface etc... 
I need to read about patching it on my own etc...

---

### Post by gordon16 on 2016-01-05
I have now installed ownCloud and have installed a addon so Now have I the same unix user in owncloud also :)
I have also activated exernal storage support ([https://doc.owncloud.org/server/6.0/admin_manual/apps/files_external/index.html](https://doc.owncloud.org/server/6.0/admin_manual/apps/files_external/index.html)).

So when I logon with a unix user the home dir comes up and I can browse and download, but I have only READ ONLY access...
Somebody know how I can fix these?

Please seee the two attachment.

[ATTACH=CONFIG]266568[/ATTACH]

---

