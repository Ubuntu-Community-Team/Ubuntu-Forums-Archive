---
title: "LibreOffice 4.0"
date: 2013-01-04
forum: General Help
---

### Post by Ron McIlvaine on 2013-01-04
Hi,

I've been using Ubuntu now for about 6 months and I'm still learning. I had a problem with Libreoffice (broken something or other) and read about using Synaptic to fix it. It did but now it loaded Libreoffice 4.0 Alpha. While it is nice, it is alo very buggy, especially when copy / pasting text from Writer to Impress, which I do a lot.

I've tried to remove Libreoffice 4.0 and re-install Libreoffice 3.6x but now, even the Ubuntu Software Center installs Libreoffice 4.0.

Can anyone help me with this problem. I'd like to make Libreoffice more usable before 4.0 Alpha is finally finalized.

---

### Post by Bucky Ball on 2013-01-04
Hi. You don't mention which Ubuntu release you are using.

Is this the problem you mean concerning Libreoffice?
> 
... _ very buggy, especially when copy / pasting text from Writer to Impress_ ...In future, please use descriptive thread titles. You will improve your chances of help considerably. 'Libreoffice 4.0' does not really describe the problem you are having. You can change the title of this thread by clicking 'Go Advanced'. ;)

---

### Post by Vaphell on 2013-01-04
what did you do? added some repository with daily version of libreoffice 4 or what?
if that's the case you need to uninstall and remove custom repository that overrides official one.

---

### Post by Ron McIlvaine on 2013-01-04
My bad. I'm using Ubuntu 12.10. What did I do? I don't know. Help!

---

### Post by ibjsb4 on 2013-01-04
> **Ron McIlvaine said:**
> My bad. I'm using Ubuntu 12.10. What did I do? I don't know. Help!

How did you install 4.0?

---

### Post by Vaphell on 2013-01-04
that alpha didn't install by itself. Which tutorial did you follow

---

### Post by Bucky Ball on 2013-01-04
> **ibjsb4 said:**
> How did you install 4.0?

I think that would be default in 12.10. The default office package used to be OpenOffice  then it changed, I think in 12.04 LTS. Annoying, at least for me.

You may need to find a repository (PPA) to install earlier versions of Libreoffice. Or you could try installing OpenOffice from Software Centre and see if it does the job ...

This might help:

[http://www.upubuntu.com/2012/08/install-libreoffice-36-final-from-ppa.html](http://www.upubuntu.com/2012/08/install-libreoffice-36-final-from-ppa.html)

... and if not, dig through this:

[http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=install+libreoffice+3+ubuntu+12.10&ql=](http://www.dogpile.com/info.dogpl/search/web?fcoid=417&fcop=topnav&fpid=27&q=install+libreoffice+3+ubuntu+12.10&ql=)

---

### Post by lykwydchykyn on 2013-01-04
> **Bucky Ball said:**
> I think that would be default in 12.10. 

LibreOffice 3.6.4 is default in 12.10.  4.0 Alpha would have had to come from a third-party source.

OP: can you post the output of this command?
```

ls /etc/apt/sources.list.d

```

That will show the names of PPAs installed on your system.

---

### Post by Bucky Ball on 2013-01-04
> **lykwydchykyn said:**
> 
OP: can you post the output of this command?
```

ls /etc/apt/sources.list.d

```That will show the names of PPAs installed on your system.

+1 and thanks for the info. My mistake (and yes, Vaphell, of course ... it's an alpha ... my mistake but same mistake). ;)

And Ron, give us the output from the command lykwydchykyn suggested ...

---

### Post by Ron McIlvaine on 2013-01-04
ron@ron-Aspire-5534:~$ ls /etc/apt/sources.list.d
google-musicmanager.list
google-musicmanager.list.save
google-talkplugin.list
google-talkplugin.list.save
libreoffice-libreoffice-prereleases-quantal.list
libreoffice-libreoffice-prereleases-quantal.list.save
myunity-ppa-quantal.list
myunity-ppa-quantal.list.save
nuvola-player-builders-stable-quantal.list
nuvola-player-builders-stable-quantal.list.save
nvbn-rm-ppa-precise.list
nvbn-rm-ppa-precise.list.distUpgrade
nvbn-rm-ppa-precise.list.save
precise-partner.list
precise-partner.list.distUpgrade
precise-partner.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-56_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-56_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-56_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-57_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-57_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-57_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-59_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-59_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-59_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-60_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-60_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-60_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-61_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-61_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-61_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-62_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-62_ubuntu.list.distUpgrade
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-62_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-63_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-63_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-64_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-64_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-65_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-65_ubuntu.list.save
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-66_ubuntu.list
private-ppa.launchpad.net_commercial-ppa-uploaders_fullcircle-issue-66_ubuntu.list.save
scopes-packagers-ppa-quantal.list
skype-wrapper-ppa-precise.list
skype-wrapper-ppa-precise.list.distUpgrade
skype-wrapper-ppa-precise.list.save
tualatrix-ppa-quantal.list
tualatrix-ppa-quantal.list.save
webapps-preview-quantal.list
webapps-preview-quantal.list.save
ron@ron-Aspire-5534:~$

---

### Post by Ron McIlvaine on 2013-01-04
Thank you all for your help. I saw:
libreoffice-libreoffice-prereleases-quantal.list
libreoffice-libreoffice-prereleases-quantal.list.save

I ent into System Settings | software Sources and removed them. Then I went to [http://www.upubuntu.com/2012/08/install-libreoffice-36-final-from-ppa.html](http://www.upubuntu.com/2012/08/install-libreoffice-36-final-from-ppa.html) and followed the directions to install Libreoffice. Now aI am using Libreoffice 3.6.4.3,

Thanks

---

### Post by Bucky Ball on 2013-01-04
Good news. Please mark thread as Solved from Thread Tools at top right to help others. Enjoy! ;)

---

