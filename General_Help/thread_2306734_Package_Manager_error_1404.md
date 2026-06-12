---
title: "Package Manager error 14:04"
date: 2015-12-18
forum: General Help
---

### Post by greg73 on 2015-12-18
Hello,

I have gone through searching and can find similar ones which have been resolved but with older versions. I have had this error now for over 2 weeks....was kinda hoping it would correct itself..

I have a red "Stop" icon up top of screen which says the following;

An error occurred, please run Package Manager from menu or apt-get.. The error Message was; "Error: Opening the Cache (E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/Security.ubuntu.com_ubuntu_dists_Trusty-security_universe_i18n_Translation-en, E: The package lists or status file could not be parsed or opened.)

By reading some of the other problems relating to this I used Sudo to remove that item then used 

Sudo apt-get update

But am getting the following error;

Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
Cannot initiate the connection to security.ubuntu.com:80
connect (101: Network is unreacheable
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)


Any  help greatly appreciated

---

### Post by blackbird34 on 2015-12-18
have you tried 
```
sudo apt-get install -f
```

It's often used to repair situations like this where packages are installed wrong, corrupted or badly configured. ( -f for "fix" ;) )

---

### Post by ian-weisser on 2015-12-18
> **greg73 said:**
> connect (101: Network is unreacheable
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease)

apt uses plain old http/https. The error codes (101) are the same ones you see in a browser, and easily searchable.
If you have good network connectivity except for this sole error, try changing mirrors.

---

### Post by greg73 on 2015-12-19
Hiya Blackbird34, thank you. I tried that and it did not do anything.....

ian-weisser, Yes, I assumed that error is the same. But, you say try another mirror how do i get package manager or updater to use another mirror ??. Do they not do that themselves if first one fails try alternative??

---

### Post by deadflowr on 2015-12-19
[COLOR=#000000] > Do they not do that themselves if first one fails try alternative??[/COLOR]
No they don't.

But the simple solution is to open Software and Updates and in the first page go to the Download from: part and toggle it to Other.

From there you can try the Find Best Server option in the top right corner, or select a server from the list available.
Then press Choose server, it'll need your password at some point.
Then when you close out all the software and updates windows it'll ask to reload, which will then set the new mirror as the mirror to grab the packages from.

Hope it helps

---

### Post by greg73 on 2015-12-26
thank you, sorry for delay in replying. Have been rather busy with Christmas etc :( but yes that seemed to work. thank you very much for your assistance :).

---

