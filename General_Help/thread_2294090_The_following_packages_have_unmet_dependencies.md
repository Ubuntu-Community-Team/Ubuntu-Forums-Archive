---
title: "The following packages have unmet dependencies"
date: 2015-09-09
forum: General Help
---

### Post by Sky_Dog on 2015-09-09
Hi all,  I already installed npm some days ago, but when I execute ```
sudo apt-get install npm
``` then I geth the message "The following packages have unmet dependencies"  [http://paste.ubuntu.com/12323202/](http://paste.ubuntu.com/12323202/)  Why does it happen?  My npm current version is 2.11.3  Regards SkyDog

---

### Post by XBNCPRk on 2015-09-09
After getting that message run ```
sudo apt-get install -f
```  

This will get and install the needed dependencies for you.  You recieved the initial error message because npm was looking for, and didnt find, a component that it needed.

---

### Post by Sky_Dog on 2015-09-09
Hi [**[COLOR=#000000]XBNCPRk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1863065")

thanks for the info, but it doesn't work, I am getting the same errors:

[http://paste.ubuntu.com/12323408/](http://paste.ubuntu.com/12323408/)

Regards
SkyDog

---

### Post by XBNCPRk on 2015-09-09
There was a similar problem on stackoverflow a while back. The consensus solution was to remove node_modules  ```
sudo rm -rf node_modules/
``` clear the npm cache ```
sudo npm cache clean
```and then try the install again.  More info can be found on [http://stackoverflow.com/questions/20764881/why-does-npm-install-say-i-have-unmet-dependencies](http://stackoverflow.com/questions/20764881/why-does-npm-install-say-i-have-unmet-dependencies)

---

### Post by Sky_Dog on 2015-09-09
If I remove the node_modules, do I have to install node again? I am afraid to perform such action and that the packages, which use node, don't work anymore.

After "sudo rm -rf node_modules/", do I only have to perform "sudo npm cache clean"? 
Or do I have to reinstall node again?

Sorry for the questions :D

---

### Post by Sky_Dog on 2015-09-12
> **XBNCPRk said:**
> There was a similar problem on stackoverflow a while back. The consensus solution was to remove node_modules  ```
sudo rm -rf node_modules/
``` clear the npm cache ```
sudo npm cache clean
```and then try the install again.  More info can be found on [http://stackoverflow.com/questions/20764881/why-does-npm-install-say-i-have-unmet-dependencies](http://stackoverflow.com/questions/20764881/why-does-npm-install-say-i-have-unmet-dependencies)


Hi,

I did first "[COLOR=#000000][FONT=Ubuntu Mono]sudo rm -rf node_modules/[/FONT][/COLOR]" and then "[COLOR=#000000][FONT=Ubuntu Mono]sudo npm cache clean[/FONT][/COLOR]", but still having the same problem :-(

[http://paste.ubuntu.com/12377492/](http://paste.ubuntu.com/12377492/)

And the "npm list" is empty:

skydog@Merlin:~$ npm list
/home/skydog
&#9492;&#9472;&#9472; (empty)

---

### Post by mc4man on 2015-09-12
what does this report?
```
apt-cache policy npm nodejs node-abbrev
```

---

### Post by Sky_Dog on 2015-09-12
> **mc4man said:**
> what does this report?
```
apt-cache policy npm nodejs node-abbrev
```

"[COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy npm nodejs node-abbrev[/FONT][/COLOR]" _returns the following information_:

[http://paste.ubuntu.com/12379332/](http://paste.ubuntu.com/12379332/)

---

### Post by mc4man on 2015-09-12
Well you're using here as a source for nodejs,  - 
[https://github.com/nodesource/distributions](https://github.com/nodesource/distributions)
doesn't seem to be working out too well, maybe file an issue there or get rid of & either use the vivid package(s) or find a more suitable ppa.

---

### Post by Sky_Dog on 2015-09-12
> **mc4man said:**
> Well you're using here as a source for nodejs,  - 
[https://github.com/nodesource/distributions](https://github.com/nodesource/distributions)
doesn't seem to be working out too well, maybe file an issue there or get rid of & either use the vivid package(s) or find a more suitable ppa.

what do you mean with "use vivid packages" or "more suitable ppa"? Do you mean another source to install npm? I have started with Ubuntu shortly, sorry for the newbie question :D

---

### Post by mc4man on 2015-09-12
You likely used a setup script that added the repo, then you installed nodejs from that repo. (0.12.7-1nodesource1~vivid1
That nodejs package includes npm so no use trying to install the Ubuntu vivid package of npm.
(-screen shows some of the contents of nodejs from that repo, note /usr/bin/npm

As far as npm i've no interest in, you've already got it installed. Maybe you should post a thread on using npm...

---

### Post by Sky_Dog on 2015-09-13
> **mc4man said:**
> You likely used a setup script that added the repo, then you installed nodejs from that repo. (0.12.7-1nodesource1~vivid1
That nodejs package includes npm so no use trying to install the Ubuntu vivid package of npm.
(-screen shows some of the contents of nodejs from that repo, note /usr/bin/npm

As far as npm i've no interest in, you've already got it installed. Maybe you should post a thread on using npm...

Thanks a lot for the information :-)

---

