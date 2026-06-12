---
title: "An issue with the Opera repository while trying to get updates"
date: 2016-09-21
forum: General Help
---

### Post by thewire2 on 2016-09-21
I've got Opera beta installed. Today, I ran sudo apt-get update, and this is what I got:

```
sudo apt-get update
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease         
Hit:4 http://ca.archive.ubuntu.com/ubuntu xenial InRelease                     
Ign:5 http://deb.opera.com/opera-stable stable InRelease                       
Hit:6 http://ppa.launchpad.net/canonical-chromium-builds/stage/ubuntu xenial InRelease
Hit:7 http://ca.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Ign:8 http://deb.opera.com/opera-stable stable Release                         
Hit:9 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:10 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease 
Hit:11 http://ca.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Ign:12 http://deb.opera.com/opera-stable stable/non-free amd64 Packages  
Ign:13 http://deb.opera.com/opera-stable stable/non-free i386 Packages
Ign:14 http://deb.opera.com/opera-stable stable/non-free all Packages
Ign:15 https://deb.opera.com/opera-beta stable InRelease
Ign:16 http://deb.opera.com/opera-stable stable/non-free Translation-en_CA
Ign:17 https://deb.opera.com/opera-beta stable Release
Ign:18 http://deb.opera.com/opera-stable stable/non-free Translation-en
Ign:19 https://deb.opera.com/opera-beta stable/non-free amd64 Packages
Ign:20 http://deb.opera.com/opera-stable stable/non-free amd64 DEP-11 Metadata
Ign:21 https://deb.opera.com/opera-beta stable/non-free i386 Packages
Ign:23 http://deb.opera.com/opera-stable stable/non-free DEP-11 64x64 Icons
Ign:24 https://deb.opera.com/opera-beta stable/non-free all Packages
Ign:12 http://deb.opera.com/opera-stable stable/non-free amd64 Packages
Ign:25 https://deb.opera.com/opera-beta stable/non-free Translation-en_CA
Ign:13 http://deb.opera.com/opera-stable stable/non-free i386 Packages
Ign:26 https://deb.opera.com/opera-beta stable/non-free Translation-en
Ign:14 http://deb.opera.com/opera-stable stable/non-free all Packages
Ign:27 https://deb.opera.com/opera-beta stable/non-free amd64 DEP-11 Metadata
Ign:16 http://deb.opera.com/opera-stable stable/non-free Translation-en_CA
Ign:28 https://deb.opera.com/opera-beta stable/non-free DEP-11 64x64 Icons
Ign:18 http://deb.opera.com/opera-stable stable/non-free Translation-en
Ign:19 https://deb.opera.com/opera-beta stable/non-free amd64 Packages
Ign:20 http://deb.opera.com/opera-stable stable/non-free amd64 DEP-11 Metadata
Ign:21 https://deb.opera.com/opera-beta stable/non-free i386 Packages
Ign:23 http://deb.opera.com/opera-stable stable/non-free DEP-11 64x64 Icons
Ign:24 https://deb.opera.com/opera-beta stable/non-free all Packages
Ign:12 http://deb.opera.com/opera-stable stable/non-free amd64 Packages
Ign:25 https://deb.opera.com/opera-beta stable/non-free Translation-en_CA
Ign:13 http://deb.opera.com/opera-stable stable/non-free i386 Packages
Ign:26 https://deb.opera.com/opera-beta stable/non-free Translation-en
Ign:14 http://deb.opera.com/opera-stable stable/non-free all Packages
Ign:27 https://deb.opera.com/opera-beta stable/non-free amd64 DEP-11 Metadata
Ign:16 http://deb.opera.com/opera-stable stable/non-free Translation-en_CA
Ign:28 https://deb.opera.com/opera-beta stable/non-free DEP-11 64x64 Icons
Ign:18 http://deb.opera.com/opera-stable stable/non-free Translation-en
Ign:19 https://deb.opera.com/opera-beta stable/non-free amd64 Packages
Ign:20 http://deb.opera.com/opera-stable stable/non-free amd64 DEP-11 Metadata
Ign:21 https://deb.opera.com/opera-beta stable/non-free i386 Packages
Ign:23 http://deb.opera.com/opera-stable stable/non-free DEP-11 64x64 Icons
Ign:24 https://deb.opera.com/opera-beta stable/non-free all Packages
Ign:12 http://deb.opera.com/opera-stable stable/non-free amd64 Packages
Ign:25 https://deb.opera.com/opera-beta stable/non-free Translation-en_CA
Ign:26 https://deb.opera.com/opera-beta stable/non-free Translation-en
Ign:13 http://deb.opera.com/opera-stable stable/non-free i386 Packages
Ign:27 https://deb.opera.com/opera-beta stable/non-free amd64 DEP-11 Metadata
Ign:14 http://deb.opera.com/opera-stable stable/non-free all Packages
Ign:28 https://deb.opera.com/opera-beta stable/non-free DEP-11 64x64 Icons
Ign:16 http://deb.opera.com/opera-stable stable/non-free Translation-en_CA
Ign:19 https://deb.opera.com/opera-beta stable/non-free amd64 Packages
Ign:18 http://deb.opera.com/opera-stable stable/non-free Translation-en
Ign:21 https://deb.opera.com/opera-beta stable/non-free i386 Packages
Ign:20 http://deb.opera.com/opera-stable stable/non-free amd64 DEP-11 Metadata
Ign:24 https://deb.opera.com/opera-beta stable/non-free all Packages
Ign:23 http://deb.opera.com/opera-stable stable/non-free DEP-11 64x64 Icons
Ign:25 https://deb.opera.com/opera-beta stable/non-free Translation-en_CA
Ign:12 http://deb.opera.com/opera-stable stable/non-free amd64 Packages
Ign:26 https://deb.opera.com/opera-beta stable/non-free Translation-en
Ign:13 http://deb.opera.com/opera-stable stable/non-free i386 Packages
Ign:27 https://deb.opera.com/opera-beta stable/non-free amd64 DEP-11 Metadata
Ign:14 http://deb.opera.com/opera-stable stable/non-free all Packages
Ign:28 https://deb.opera.com/opera-beta stable/non-free DEP-11 64x64 Icons
Ign:16 http://deb.opera.com/opera-stable stable/non-free Translation-en_CA
Ign:19 https://deb.opera.com/opera-beta stable/non-free amd64 Packages
Ign:18 http://deb.opera.com/opera-stable stable/non-free Translation-en
Ign:21 https://deb.opera.com/opera-beta stable/non-free i386 Packages
Ign:20 http://deb.opera.com/opera-stable stable/non-free amd64 DEP-11 Metadata
Ign:24 https://deb.opera.com/opera-beta stable/non-free all Packages
Ign:23 http://deb.opera.com/opera-stable stable/non-free DEP-11 64x64 Icons
Err:12 http://deb.opera.com/opera-stable stable/non-free amd64 Packages
  404  Not Found
Ign:25 https://deb.opera.com/opera-beta stable/non-free Translation-en_CA
Ign:13 http://deb.opera.com/opera-stable stable/non-free i386 Packages
Ign:26 https://deb.opera.com/opera-beta stable/non-free Translation-en
Ign:14 http://deb.opera.com/opera-stable stable/non-free all Packages
Ign:27 https://deb.opera.com/opera-beta stable/non-free amd64 DEP-11 Metadata
Ign:16 http://deb.opera.com/opera-stable stable/non-free Translation-en_CA
Ign:28 https://deb.opera.com/opera-beta stable/non-free DEP-11 64x64 Icons
Ign:18 http://deb.opera.com/opera-stable stable/non-free Translation-en
Err:19 https://deb.opera.com/opera-beta stable/non-free amd64 Packages
  404  Not Found
Ign:20 http://deb.opera.com/opera-stable stable/non-free amd64 DEP-11 Metadata
Ign:21 https://deb.opera.com/opera-beta stable/non-free i386 Packages
Ign:23 http://deb.opera.com/opera-stable stable/non-free DEP-11 64x64 Icons
Ign:24 https://deb.opera.com/opera-beta stable/non-free all Packages
Ign:25 https://deb.opera.com/opera-beta stable/non-free Translation-en_CA
Ign:26 https://deb.opera.com/opera-beta stable/non-free Translation-en
Ign:27 https://deb.opera.com/opera-beta stable/non-free amd64 DEP-11 Metadata
Ign:28 https://deb.opera.com/opera-beta stable/non-free DEP-11 64x64 Icons
Fetched 94.5 kB in 5s (17.5 kB/s)
Reading package lists... Done
W: The repository 'http://deb.opera.com/opera-stable stable Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'https://deb.opera.com/opera-beta stable Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://deb.opera.com/opera-stable/dists/stable/non-free/binary-amd64/Packages  404  Not Found
E: Failed to fetch https://deb.opera.com/opera-beta/dists/stable/non-free/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.



```

How do I fix this?

---

### Post by howefield on 2016-09-21
Can you post the output of..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by thewire2 on 2016-09-21
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*

/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://ca.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list:deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list.save:deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/canonical-chromium-builds-ubuntu-stage-xenial.list:deb http://ppa.launchpad.net/canonical-chromium-builds/stage/ubuntu xenial main
/etc/apt/sources.list.d/canonical-chromium-builds-ubuntu-stage-xenial.list.save:deb http://ppa.launchpad.net/canonical-chromium-builds/stage/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/opera-beta.list:deb https://deb.opera.com/opera-beta/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera-beta.list.save:deb https://deb.opera.com/opera-beta/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera.list:deb http://deb.opera.com/opera-stable/ stable non-free
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list.save:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial main
```

---

### Post by howefield on 2016-09-21
Open up the *Software & Updates* application and uncheck the opera-stable repository from the "*Other Software*" tab.

Close out and then try a sudo apt-get update again.

---

### Post by thewire2 on 2016-09-21
> **howefield said:**
> Open up the *Software & Updates* application and uncheck the opera-stable repository from the "*Other Software*" tab.

Close out and then try a sudo apt-get update again.

Yeah, that works. But if I do that, I won't receive updates for Opera beta, correct?

What could be the issue?

---

### Post by howefield on 2016-09-21
> **thewire2 said:**
> ...correct?

No, you will still have the opera-beta repository enabled so will continue to receive updates for it, it is only the opera-stable repository that you want to disable.

---

### Post by thewire2 on 2016-09-21
> **howefield said:**
> No, you will still have the opera-beta repository enabled so will continue to receive updates for it, it is only the opera-stable repository that you want to disable.

Sorry, I forgot to mention that I had to disable the Opera beta repo as well for sudo apt-get update to work. With opera-stable disabled and opera-beta enabled, it still did not work.

---

### Post by sampayu on 2016-09-21
I've just installed Opera on my 64-bit XUbuntu Linux version 16.04.1 and got this same error message when I executed [B]sudo apt-get update

[/B]The solution for this is pretty simple. Pay attention to the error messages that APT output on your screen. One of them states this:
[I]
The repository 'http://deb.opera.com/**opera-stable stable** Release' does not have a Release file.

[/I]That ...***opera-stable stable**... *means that inside the directory **opera-stable** there's a **dists** directory and that inside **dists** there will be a **stable** directory. Now open a new browser tab or window and then access [http://deb.opera.com/opera-stable](http://deb.opera.com/opera-stable)

You'll notice that after (inside) the directory **opera-stable** there's actually the **opera** directory, and only then (_inside of the **opera** directory_) you'll get the **dists** directory (and the **stable** directory inside of it).

:KS So, in a nutshell, the correct path is **[http://deb.opera.com/opera-stable/opera](http://deb.opera.com/opera-stable/opera)**

Now take a look into your local **opera-stable.list** file (open a shell terminal window and run the command below):

```
cat /etc/apt/sources.list.d/opera-stable.list
```

You'll find this line:

```
deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
```

See the error? Yes: the official Opera Browser DEB package is coming with an error that causes it to create that **opera-stable.list** file with the _wrong path_ to the repository (because _the **opera** directory is missing_).

You can fix this file with a single command, executed at the shell terminal:

```
sudo sed -i -e 's,opera-stable/ stable,opera-stable/opera/ stable,' "/etc/apt/sources.list.d/opera-stable.list"
```

The **sed** command will then make the **opera-stable/ stable** string be replaced by the **opera-stable/opera/ stable** string, thus fixing your **opera-stable.list** file.:)

[HR][/HR]
Because you also have Opera Beta, your system has a second repository configuration file: **opera-beta.list**

This file also needs a fix, because if you look into **/etc/apt/sources.list.d/opera-beta.list** you'll find a line with the code "deb [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) stable", but if you browse [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) you'll find that this repository also has a **opera** directory between the parent directory **opera-beta** and the child directory **dists**.

So, here's the command you'll have to execute in order to fix the Opera Beta repo config file:

```
sudo sed -i -e 's,opera-beta/ stable,opera-beta/opera/ stable,' "/etc/apt/sources.list.d/opera-beta.list"
```

[HR][/HR]
After you fix both repo config files, just run:

```
sudo apt-get update ; sudo apt-get check
```

...and notice how the problem is gone, now.:popcorn:

---

### Post by thewire2 on 2016-09-21
> **sampayu said:**
> I've just installed Opera on my 64-bit XUbuntu Linux version 16.04.1 and got this same error message when I executed [B]sudo apt-get update

[/B]The solution for this is pretty simple. Pay attention to the error messages that APT output on your screen. One of them states this:
[I]
The repository 'http://deb.opera.com/**opera-stable stable** Release' does not have a Release file.

[/I]That ...***opera-stable stable**... *means that inside the directory **opera-stable** there's a **dists** directory and that inside **dists** there will be a **stable** directory. Now open a new browser tab or window and then access [http://deb.opera.com/opera-stable](http://deb.opera.com/opera-stable)

You'll notice that after (inside) the directory **opera-stable** there's actually the **opera** directory, and only then (_inside of the **opera** directory_) you'll get the **dists** directory (and the **stable** directory inside of it).

:KS So, in a nutshell, the correct path is **[http://deb.opera.com/opera-stable/opera](http://deb.opera.com/opera-stable/opera)**

Now take a look into your local **opera-stable.list** file (open a shell terminal window and run the command below):

```
cat /etc/apt/sources.list.d/opera-stable.list
```

You'll find this line:

```
deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases)
```

See the error? Yes: the official Opera Browser DEB package is coming with an error that causes it to create that **opera-stable.list** file with the _wrong path_ to the repository (because _the **opera** directory is missing_).

You can fix this file with a single command, executed at the shell terminal:

```
sudo sed -i -e 's,opera-stable/ stable,opera-stable/opera/ stable,' "/etc/apt/sources.list.d/opera-stable.list"
```

The **sed** command will then make the **opera-stable/ stable** string be replaced by the **opera-stable/opera/ stable** string, thus fixing your **opera-stable.list** file.:)

[HR][/HR]
Because you also have Opera Beta, your system has a second repository configuration file: **opera-beta.list**

This file also needs a fix, because if you look into **/etc/apt/sources.list.d/opera-beta.list** you'll find a line with the code "deb [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) stable", but if you browse [https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/) you'll find that this repository also has a **opera** directory between the parent directory **opera-beta** and the child directory **dists**.

So, here's the command you'll have to execute in order to fix the Opera Beta repo config file:

```
sudo sed -i -e 's,opera-beta/ stable,opera-beta/opera/ stable,' "/etc/apt/sources.list.d/opera-beta.list"
```

[HR][/HR]
After you fix both repo config files, just run:

```
sudo apt-get update ; sudo apt-get check
```

...and notice how the problem is gone, now.:popcorn:

This worked. Thanks!

---

### Post by thewire2 on 2016-09-22
Well, today I get the exact same errors again. Yesterday it worked after entering the above command, but now it doesn't.

Edit: I had to change the repo config file to what it was initially. Works now.

---

### Post by sampayu on 2016-09-22
> **thewire2 said:**
> Well, today I get the exact same errors again. Yesterday it worked after entering the above command, but now it doesn't.

Edit: I had to change the repo config file to what it was initially. Works now.

Yesterday I sent an e-mail to the Opera business contact, reporting this issue (the wrong configuration inside the DEB packages). I was expecting the company to fix _the packages_ (by adding the **opera** directory to the repository path inside of each DEB package), but instead the company decided to fix _the directory hierarchy_ (by removing the **opera** directory from both repositories). This is why my solution above stopped working. :-(

Well, I've just accessed **[https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/)** and **[https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/)** and noticed that the **opera** folder is gone and the **dists** folder is now in its place. So, well, in such case just run:

```
sudo sed -i -e 's,opera-stable/opera/ stable,opera-stable/ stable,' "/etc/apt/sources.list.d/opera-stable.list" ; sudo sed -i -e 's,opera-beta/opera/ stable,opera-beta/ stable,' "/etc/apt/sources.list.d/opera-beta.list" ; sudo apt-get update ; sudo apt-get check
```

...and the repo config files will return to their original setting.

---

### Post by thewire2 on 2016-09-23
> **sampayu said:**
> Yesterday I sent an e-mail to the Opera business contact, reporting this issue (the wrong configuration inside the DEB packages). I was expecting the company to fix _the packages_ (by adding the **opera** directory to the repository path inside of each DEB package), but instead the company decided to fix _the directory hierarchy_ (by removing the **opera** directory from both repositories). This is why my solution above stopped working. :-(

Well, I've just accessed **[https://deb.opera.com/opera-stable/](https://deb.opera.com/opera-stable/)** and **[https://deb.opera.com/opera-beta/](https://deb.opera.com/opera-beta/)** and noticed that the **opera** folder is gone and the **dists** folder is now in its place. So, well, in such case just run:

```
sudo sed -i -e 's,opera-stable/opera/ stable,opera-stable/ stable,' "/etc/apt/sources.list.d/opera-stable.list" ; sudo sed -i -e 's,opera-beta/opera/ stable,opera-beta/ stable,' "/etc/apt/sources.list.d/opera-beta.list" ; sudo apt-get update ; sudo apt-get check
```

...and the repo config files will return to their original setting.

Yeah, I figured they had fixed the directory hierarchy. I changed it back to what it was before after I realized that and it worked. 

Thanks again.

---

