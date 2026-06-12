---
title: "My pc is lagging a lot after updates?"
date: 2014-02-25
forum: General Help
---

### Post by TheUninvited on 2014-02-25
When i started up my computer it showed me up that it needs to make some updates i did the updates and after that my pc is whole lagging and the problem is i dont know how to unistall the updates.

here is the list of what it installed :
[http://i.imgur.com/695sFtx.png](http://i.imgur.com/695sFtx.png)

---

### Post by 23dornot23d on 2014-02-25
Was a time when I would remove ubuntuone as it caused lagging.

Its in that listing .......... but could not tell you for certain that it is ubuntuone ............

sudo synaptic 

Have a search on ubuntuone and see what you can do from that  .......... just a case of uninstalling by
ticking the box and then choosing to uninstall it ........ ( but that is only if you were not previously using it )

It can be re-installed again using the same method - if that is not the problem.

---

### Post by Mateusz Stachowski on 2014-02-25
First of all you are not using the development branch of Ubuntu and this part of the forums is strictly for development branches.

Secondly looking at your packages you have Unity 4.30 which is very old. The 12.04 LTS have Unity 5.20 and development branch have Unity 7.1.2.

You should always post the version of Ubuntu that you are using. You can check it in "About computer" or using terminal (Ctrl+Alt+T) and this command.

```
lsb_release -a
```

---

### Post by TheUninvited on 2014-02-25
> **Mateusz Stachowski said:**
> First of all you are not using the development branch of Ubuntu and this part of the forums is strictly for development branches.

Secondly looking at your packages you have Unity 4.30 which is very old. The 12.04 LTS have Unity 5.20 and development branch have Unity 7.1.2.

You should always post the version of Ubuntu that you are using. You can check it in "About computer" or using terminal (Ctrl+Alt+T) and this command.

```
lsb_release -a
```
I did as you told me it showed me up this:
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

```

So is there is any new version of it where can i get it?  

But now it works fine i did some upgrade on something but i still get support for my version has stopped.

---

### Post by Mateusz Stachowski on 2014-02-25
> **TheUninvited said:**
> 
So is there is any new version of it where can i get it?  

But now it works fine i did some upgrade on something but i still get support for my version has stopped.

Yes the version that you are using isn't supported anymore. Support for Ubuntu [Oneiric Ocelot]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_11.10_.28Oneiric_Ocelot.29") was officially ended on 9 May 2013.

If you have your system fully updated then it should offer you upgrade to 12.04 LTS which is a Long Term Support release (five years of support). 

There are settings in "Software & Updates" for actualizations by default it is set to display every new version of Ubuntu. You can also use this command in terminal to force the upgrade.

```
sudo update-manager -d
```

---

### Post by ventrical on 2014-02-25
Or. , if you want to experiment with development you can download the current development cycle here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)


 and you can use StartupDisk Creator to put the .iso on a bootable USB stick. (atually, the putting of the .iso on USB stick makes it bootable).

---

### Post by Elfy on 2014-02-25
*Thread moved to **General Help**.*

I'd not get involved in development versions unless you're really sure you want to.

---

### Post by deadflowr on 2014-02-25
> So is there is any new version of it where can i get it?  

Well, you shouldn't have to use the command line to get update manger to show you an upgrade release option.
If you simply launch update manager, you should have an option to upgrade to 12.04LTS up on top.
If you don't, then go down to where it says settings and click on that button.
This will open up the windows for the software sources.
In here, go to the tab for Updates.
Towards the bottom of updates is a selection for Notify for new release.
Make sure that is marked for either LTS releases or any releases.
When marked, close the software sources windows and back in Update Manager click on check.
This should reload the page, and hopefully an option for Release Upgrade across the top.

Of course, secondary( and probably a more common solution) would be to go to Ubuntu.com and download a fresh copy and do a reinstall/fresh install.

---

### Post by TheUninvited on 2014-02-25
alright thank you very much for your time for answering my questions i appreciate it!

---

