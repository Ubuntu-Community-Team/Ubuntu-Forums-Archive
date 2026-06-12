---
title: "How to Install Firefox 20 on Ubuntu 9.0.4"
date: 2013-04-15
forum: General Help
---

### Post by Victor43 on 2013-04-15
I know I am running an outdated copy of Ubuntu but I am unable to download and burn the latest version. So while I wait for the DVD copy to arrive I would like to know if anyone would be kind enough to provide any help with this issue. I have downloaded Firefox 20 and have no problems with the extraction of the tar file. But how do I either remove the old FF 3.08 and install version 20 or upgrade the old version to this new one. 

I read the following similar post but it would not work for me [http://ubuntuforums.org/showthread.php?t=2133583](http://ubuntuforums.org/showthread.php?t=2133583)

Any help would be apperciated

---

### Post by r.stiltskin on 2013-04-15
It depends on how you installed it in the first place.  Did you install FF 3.08 in Synaptic?  apt-get?  extracted a tarball?  dpkg from a .deb file?

By the way, do you have all the [libraries required by FF 20]("http://www.mozilla.org/en-US/firefox/20.0/system-requirements/")?  I don't know which versions of these libraries were included in Jaunty.

---

### Post by Impavidus on 2013-04-15
> **Victor43 said:**
> I read the following similar post but it would not work for me [http://ubuntuforums.org/showthread.php?t=2133583](http://ubuntuforums.org/showthread.php?t=2133583)
That thread doesn't really contain a solution, except for the suggestion to try an older firefox, like version 16. It may run.

And I think firefox 3.0 came by default on 9.04. OP has never updated his firefox to 3.6, which was offered by the automatic updates of 9.04.

---

### Post by Frogs Hair on 2013-04-15
I know 9.04 was before automatic updates for Firefox. Keep your old version because any dependencies you may need to install the new version would have to downloaded and installed manually. You would have to know exactly what you need package wise because the 9.04 repository is closed and there is  no way to pull the dependencies during the installation. You need specific instructions to compile Firefox and the ones I have found appear to be specific to a Ubuntu version and versions of Firefox available during the active life of the release.

---

### Post by Victor43 on 2013-04-16
> **r.stiltskin said:**
> It depends on how you installed it in the first place.  Did you install FF 3.08 in Synaptic?  apt-get?  extracted a tarball?  dpkg from a .deb file?

By the way, do you have all the [libraries required by FF 20]("http://www.mozilla.org/en-US/firefox/20.0/system-requirements/")?  I don't know which versions of these libraries were included in Jaunty.

Thanks for the reply.

Firefox came with the distribution. Yes and firefox is listed part of the list shown in Synaptic Package Manager. The items shown are as follows:

1. firefox
2. firefox-3.0
3. firefox-3.0-branding
4. firefox-gnome-support
5. firefox-3.0-gnome-support

With respect to your second question I downlaoded the tar ball from the firefox download site. If you tell what directory would contain the libraries I will then be able to determine whether they are there. I was able to extract the contents and the directories that exist there are Chrome Components Defaults Dictionaries Extensions Icons Modules and SearchPlugins and WebApprt.

Victor

---

### Post by Victor43 on 2013-04-16
> **Frogs Hair said:**
> I know 9.04 was before automatic updates for Firefox. Keep your old version because any dependencies you may need to install the new version would have to downloaded and installed manually. You would have to know exactly what you need package wise because the 9.04 repository is closed and there is  no way to pull the dependencies during the installation. You need specific instructions to compile Firefox and the ones I have found appear to be specific to a Ubuntu version and versions of Firefox available during the active life of the release.

Thanks for the tip. I will keep that mind. Victor.

---

### Post by Victor43 on 2013-04-16
Can anyone comment on whether this procedure will work for Forefox 20 instead of Firefox 3.5.5 as described in the article. I followed the exact instructions and everything went without a hitch except when I tried opening FF20. It showed in the taskbar at the bottom as opening but the window did not open. It looked like to close to opening but without showing any error messages. 

[http://chrisjean.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/](http://chrisjean.com/2009/07/01/upgrade-to-firefox-3-5-on-ubuntu-9-04-jaunty-jackalope/)

Thanks

Victor

---

### Post by Victor43 on 2013-04-16
> **Impavidus said:**
> That thread doesn't really contain a solution, except for the suggestion to try an older firefox, like version 16. It may run.

And I think firefox 3.0 came by default on 9.04. OP has never updated his firefox to 3.6, which was offered by the automatic updates of 9.04.

Thanks for the post. Yes your right FF3.0.8 did came with the distribution. Yes in my case I am unable to upgrade FF using Package Manager since I installed it just the other day and cannot upgrade because the repositories are no longer available for this version of Ubuntu.

---

### Post by Victor43 on 2013-04-16
Hello

I did have another question to ask. I am a newbie to Linux and Ubuntu and was wondering if anyone can tell me whether it is possible to install say Google Chrome on Ubuntu Desktop 9.0.4 ? If it is possible could someone point me in the direction of any step by step instructions on how to go about doing this ? My architecture is 64 bit.

Thanks in advance

---

### Post by r.stiltskin on 2013-04-16
The libraries listed by mozilla.org as Firefox20 requirements are not included in the tarball,  That's why they are listed as requirements. You can compare this list [Firefox20 System Requirements]("http://www.mozilla.org/en-US/firefox/20.0/system-requirements/") to the listings in your Synaptic package manager to see if you have all of them.  The fact that Firefox failed to open suggests that something in your system is incompatible.  The same probably applies to Google Chrome.  Google's system requirements lists says it needs Ubuntu 10.04 or newer.

---

### Post by Victor43 on 2013-04-16
> **r.stiltskin said:**
> The libraries listed by mozilla.org as Firefox20 requirements are not included in the tarball,  That's why they are listed as requirements. You can compare this list [Firefox20 System Requirements]("http://www.mozilla.org/en-US/firefox/20.0/system-requirements/") to the listings in your Synaptic package manager to see if you have all of them.  The fact that Firefox failed to open suggests that something in your system is incompatible.  The same probably applies to Google Chrome.  Google's system requirements lists says it needs Ubuntu 10.04 or newer.

Thanks for the reply. Your information at least helps me in determining whether FF20 can be installed on Ub untu 9.0.4 and if not at least what might be needed.

Victor

---

### Post by Victor43 on 2013-04-16
Thanks to everyone but I have found out from another Ubuntu member [**[COLOR=#000000]Dennis N[/COLOR]**]("http://ubuntuforums.org/member.php?u=321222") that FF20 will not install on Ubuntu 9.0.4 because of libraries which are not available for this version of Ubuntu. However this same member was able to assist me with installing FF16 on Ubuntu 9.0.4. I am able to use FF16 now**. **If anyone would like to know how to install FF16 on Ubuntu 9.0.4 please reply to this thread or send PM.

Thank you 

Victor

---

### Post by guido4 on 2014-03-07
Hi Victor!

Endeed, I am very interested to learn how I can install Firefox 16 on Ubuntu 9.04. Is that possible about Ubuntu 10.10 as well?

I eagerly await your response.

Thanks Victor!

Guido

---

### Post by QIII on 2014-03-07
Rest, old thread!

---

