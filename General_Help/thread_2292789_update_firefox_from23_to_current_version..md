---
title: "update firefox from23 to current version."
date: 2015-08-31
forum: General Help
---

### Post by jaxom98 on 2015-08-31
Dual boot ubuntu12.04 / windows 7ultimate
I want to update firefox but going to mozilla firefox website and clicking on the update button does not work. I had a friend disable the automatic update as the first thing that happened with an update was the bookmarks toolbar would get hidden. LIKE HELL!
Now it is time to update as I have lost sync(between firefox on different computers) and youtube needs activation on most clips.
Where do I find import/export? It seems to have vanished.
Can I update firefox from 23, or do I need to do a clean istall?
I really don't want loose my bookmarks as it would be impossible to get them back,even only getting the primary page would be a big job.

---

### Post by TheFu on 2015-08-31
Linux updates should only happen through the package manager - getting a file or source from the mozilla website should be the 5th or 6th solution in the list of solutions.

No need for a fresh install.  Programs are stored in a different place than user preferences. Please do a backup of your HOME, at a minimum.

I'm running Ubuntu 14.04 and it is running Firefox 40.0.3 using only the stock repositories.  Ubuntu systems need weekly maintenance. WEEKLY.  Lifehacker article: [http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint)

Also, [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) might explain some important things about how Linux and Windows are different.

---

### Post by monkeybrain20122 on 2015-08-31
Man How long have you not updated your system?? Fireox is now at version 40 and it is upgraded through the normal Ubuntu upgrade channel (so you don't download from Mozilla or use FF's update button) Didn't you ever see the upgrade manager popup??

In the terminal run
```

sudo apt-get update
sudo apt-get upgrade
```

I expect it to take a long while since it appears that you have not run any update since you got your OS.

Please run update regularly, it is important for security to keep your system up to date, either with the upgrade manager (which should popup periodically), use the commands above, the Software Centre or use synaptic (which you need to install with sudo apt-get install synaptic)

---

### Post by jaxom98 on 2015-09-02
monkeybrain20122 I see and ingnore the update avalible button.
The reason I have not used the get updates is because 12.04.1 is stable. 12.04.2 and later crash the system. ie, I burned 5 separate disks from 3 different mirror sites and in 8 attempts had 8 failures at 12.04.2. Going directly to 12.04.3 or 12.04.4 also failed so I just stayed with 12.04.1 (totally reliable)

---

### Post by TheFu on 2015-09-02
```
sudo apt-get update
sudo apt-get upgrade
```
is safe. The kernel will only get security patches.

You need to avoid sudo apt-get dist-upgrade, which will install newer kernel releases.
Neither will push you to any later Ubuntu release like 14.04 ... 

Perhaps this will help explain: [https://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade](https://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade)

Running an unpatched Ubuntu on the internet is dangerous. It isn't just about the browser. There are many other important fixes needed too.

---

### Post by vasa1 on 2015-09-02
> **jaxom98 said:**
> ...
I really don't want loose my bookmarks as it would be impossible to get them back ...
Press *Alt+B*, choose *Show All Bookmarks*, *Import and Backup*.

---

### Post by v3.xx on 2015-09-02
> **TheFu said:**
> ```
sudo apt-get update
sudo apt-get upgrade
```
is safe. The kernel will only get security patches.

You need to avoid sudo apt-get dist-upgrade, which will install newer kernel releases.


I'm confused.  I know, nothing new there, but..

My understanding is a "apt-get upgrade" will not touch the kernel and a "dist-upgrade" on v12.04.1 will only give you patches to the current kernel (3.2) and never gives a upgrade to a newer kernel.  By using the 12.04.1 installer you are locked in for the life of the install and a "dist-upgrade" will only provide patches to the 3.2 kernel.

---

### Post by speartip on 2015-09-02
> **v3.xx said:**
> I'm confused.  I know, nothing new there, but..

My understanding is a "apt-get upgrade" will not touch the kernel and a "dist-upgrade" on v12.04.1 will only give you patches to the current kernel (3.2) and never gives a upgrade to a newer kernel.  By using the 12.04.1 installer you are locked in for the life of the install and a "dist-upgrade" will only provide patches to the 3.2 kernel.

You are quite correct.
The op needs to update his system with:
```
sudo apt-get dist-upgrade
```
This will not change the kernel version, only bring the latest security patches & bug fixes to the kernel he is on.

jaxom98...
Your thinking on the updates is incorrect. The above command should bring your whole system, & Firefox upto date, without changing the version of Ubuntu you are running.
You really do need to regularly update your system, so as not to compromise your security.
If anything your system should be more stable after updating than it is now.
If you're insistent on not updating your system, then just use synaptic package manager to upgrade Firefox to the latest version.

---

### Post by monkeybrain20122 on 2015-09-02
I think  the only difference between dist-upgrade and ugrade is the former would try to resolve potential conflicts smartly while the latter simply aborts if conflicts are encountered. But there is no difference as to what is being upgraded. Neither will bring new kernel version or graphic stack.

Upgrading from 12.04.1 to 12.04.3 and installing  12.04.3 directly with a new ISO are different. The former would still have the same kernel version and graphic stack from 12.04.1, those won't get upgraded. The ISO would have something newer (the hardware enabling stack)

---

### Post by Geoffrey_Arndt on 2015-09-02
Bookmarks are the least of the issues . . . you can always save your current bookmarks to an html file.   and then import it to a new version.    Even better, register your Firefox browser for "Sync" . . . just like Google.   You get an ID name and password, and that's where the bookmarks are kept (but if you're sensitive about cloud based bookmarks sync, then just save the bookmarks file (it's called export I believe).

Re upgrade, your choice . . . I think each version of Ubuntu has improved upon the last.   I thought 14.10 was the best.   Now I think 15.04 is.    Not one issue . . . even minor.

---

### Post by jaxom98 on 2015-09-03
I ran sudo apt-get update and upgrade respectively. They worked text-book perfect. I now have firefox v40.0.3  .
Re the OS upgrade failures, I ran into a "recursive fault ********" .The number changed each time. Run time to first system lockup was about 2 minutes consistently ,with a pull-the-plug(literally) to get out and restart.You would have 4-6 restarts , each one with less runtime to lockup. By the last lockup/freeze you were locking up during password input. The only fix was a full reinstall at 12.04.1. When I tried a reinstall and online the install would not complete.The only way to get a viable install was to install offline and then get a friend to update the third party drivers for me.
Thank you for your help monkeybrain20122.

---

### Post by TheFu on 2015-09-03
Doing an OS upgrade (12.04 --> 14.04) to an unpatched and unmaintained system is bad.  For a system that is fully patched, the distro upgrades generally work.  However, nobody that I know suggests this is the best way. We always install a new release, then restore our old settings, use *dpkg --set-selections* to import the package list previously installed and go.

Using the "cloud" is crazy to me, but we each have to decide whether convenience or privacy is more important.  RMS said "Cloud computing is careless computing."  I agree.

---

### Post by monkeybrain20122 on 2015-09-03
For distro upgrade I never use the upgrade manager, it takes a very long time and can be risky (especially if system has been modified by installing third party software, drivers etc) To make the process easier next time create separate / and /home. When installing a new release choose "advanced" or "something else" and keep the same layout and only write over the / partition. That way your $HOME and all your settings (FF bookmarks, tabs etc) will be preserved and once finish installing (took 10 minutes last time I installed 15.04) you only have to reinstall the software. You can create a list to do it automatically (see TheFu's post above)

---

### Post by Geoffrey_Arndt on 2015-09-03
The more your install is customized from 3rd party software, and your official "sources" file is modified with PPA's, then the task of upgrading from let's say 14.10 to 15.04 becomes riskier. (much).

Before any upgrade to the latest version of Ubuntu, do as TheFu & monkeybrain suggest - - have an updated system and disable 3rd party ppa's - - and even consider uninstalling certain apps installed as stand alone debs and especially, custom scripts (python, bash, php, perl, ruby, yada yada yada).

As long as your key data is saved off-system, it's almost trivial to re-add ppa's and custom apps - - even system mods and settings.  (should be doable in less than about 90" post successful install).

Re Cloud Data . . . . most data is actually safer on the Cloud than not (imho) . . . but if anything is sensitive . . it can be encrypted pre-upload on users local machines.    (via 7zip, gpg/kgpg).

---

