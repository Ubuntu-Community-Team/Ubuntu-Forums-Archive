---
title: "Software Updater apparently locked into a loop..."
date: 2015-03-03
forum: General Help
---

### Post by Mike_Walsh on 2015-03-03
Afternoon, everybody.

Now, then; I appear to have a wee problem with the Software Updater. I've been using Ubuntu 14.04 since May last year, and never had the slightest problem with updating the system.....it's all gone like so much oiled silk; VERY smooth.

Today, however, it's 'playing up'. The usual weekly crop of updates have presented themselves for installation (actually, more like a fortnight's worth; haven't been on here much recently). I start the process; it loads the software list, and shows me what needs to be installed. (As you can see, there's quite a big old chunk):-

[ATTACH=CONFIG]260414[/ATTACH]

Accordingly, I click on 'Install Now'...and this is where things go awry. I authenticate, and then this pops up:-

[ATTACH=CONFIG]260415[/ATTACH]

Well, we ALL know the system doesn't like you installing anything that isn't officially checked & approved. I can't think of anything I've got on here that isn't 'official', with the exception of perhaps a number of themes & tweaks from noobslab.com.....and perhaps PSensor, Grive, f.lux, simple-audio-recorder, grub-customizer, and the Chrome PPA. But I can't say as I've heard of anybody having problems with ANY of these; they're all quite commonly used.

There's only two I can see that aren't coming via launchpad, and those are PlayonLinux (comes with Wine).....and the Chrome PPA. 

If I click on 'OK', the whole process just quits. If I go through it again, and click on 'Settings', naturally, up comes the 'Software & Updates' window.....but I'm HANGED if I know what it's asking me to do.

Would I be correct in assuming that it wants me to uninstall all my PPA's.....or uncheck them? I've not done this before, so I DON't know how awkward the process might be; it's the only conclusion I can arrive at, at this stage. There's SOMETHING there it DOESN'T like.....but until I can figure this one out, it looks like I won't be getting any more updates. Period.

Can anybody see anything in this list that LOOKS 'dodgy'? What will actually happen if I uncheck ALL PPAs (with the exception of the system ones, of course).....and update the cache? Will this 'break' any parts of the system, or is this stuff mainly to do with updates for the PPAs? Or do I need to completely clear the cache, and then re-populate it again with up-to-date stuff? I'm a wee bit lost with this stuff!

Any advice will, as always, be much appreciated.


Regards,

Mike.

---

### Post by oldos2er on 2015-03-03
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal, and post the output? Usually apt-get shows more explicit errors than you get in the GUI.

---

### Post by Bashing-om on 2015-03-03
Mike_Walsh; Hey, My friend.

What mirror are you using ?
I had ( now past tense) one system set up for the us.archive . I am aware that there have been reports of recent problems with this mirror and I too experienced real slow interaction with the update manager. a couple of times it did hang with me but did finally finish ( I do things from the CLI so I can see what is taking place) .. Anyway when the upgrade process finally did complete, I changed my mirror. - My bit to try and take the load off the us.archive mirror.

Changed the mirror and now things are back to moving along at the expected rate.

[INDENT][INDENT]working the mirror to hard
[INDENT][INDENT][INDENT]are we ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-03-03
Thanks for the replies, guys.

@Bashing-om:-

How's it going, bud? Nice to hear from you. To be honest, I don't quite know the location of the mirror I use. I guess it's in the UK, SOMEWHERE (as am I). I used to use the main UK mirror, but found I was getting regular 'drop-outs' with that one. I spent a little while getting the system to run 'ping' tests on the UK mirrors for me; I had three or four of them come up over about 2 dozen tries.....and the one I use ([http://ubuntu.datahop.net/ubuntu](http://ubuntu.datahop.net/ubuntu)) came up the most often, so.....that's the one I've been using since June last year. And it's been consistently reliable. I suspect that's not the issue here.

(I may not actually run my updates from the terminal, but I DO have the 'Details' tab checked while it's running; like you, I like to actually see what's going on.)

However, I believe I've tracked the problem down...stay tuned!

----------------------------------------------------------------------------------------------------------

@oldos2er:-

Thanks for the suggestion. To be honest, I've been spending so much time in Puppy Linux the last 3-4 months, that I'd completely forgotten all about running this on a semi-regular basis! I've been logging-in once a week or so to keep on top of updates, but this one had totally escaped me.....

Now then; output of

```
sudo apt-get update && sudo apt-get upgrade
```

is as follows (I've skipped all the download stuff, and given you the bit we're interested in, toward the end):-

```
Reading package lists... Done
W: GPG error: http://deb.playonlinux.com trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  ca-certificates comerr-dev compiz compiz-core compiz-gnome
  compiz-plugins-default compizconfig-settings-manager cups cups-bsd
  cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common e2fslibs e2fsprogs firefox firefox-locale-en
  google-chrome-stable grive-tools language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base libc-bin libc-dev-bin
  libc6 libc6:i386 libc6-dbg libc6-dev libc6-i386 libcomerr2 libcomerr2:i386
  libcompizconfig0 libcups2 libcups2:i386 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdecoration0 libfreetype6 libfreetype6:i386
  libsmbclient libss2 libunity-core-6.0-9 libwbclient0 linux-libc-dev
  multiarch-support playonlinux python-compizconfig python-samba samba
  samba-common samba-common-bin samba-dsdb-modules samba-libs
  samba-vfs-modules smbclient thunderbird unattended-upgrades unity
  unity-services xfdesktop4 xfdesktop4-data
66 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
Need to get 157 MB of archives.
After this operation, 4,395 kB disk space will be freed.
Do you want to continue? [Y/n] 
WARNING: The following packages cannot be authenticated!
  playonlinux
Install these packages without verification? [y/N]
```


It rather looks like PlayOnLinux is the culprit. (Why am I NOT surprised...? :lol:) Well, of course, it was installed as part of the total Wine package, although I've never, ever used it. I use Wine to run one, solitary Windows graphics app which I've used for years. I would dispense with it completely, but for the fact that I would have to use 3 or 4 Linux alternatives to get the same combination of options it gives me.....which seems a wee bit silly. And it DOES have the coveted 'Platinum' rating; and RUNS flawlessly, too.....

(BTW: I'm not running the version from the repos (1.6, I believe); I'm running the 1.7.32 'beta', from the Ubuntu Wine Team's PPA.)

Obviously, I need to remove this from the PPA listings. Can this be done without disturbing the main Wine package? If so, what's the procedure; remove the PPA completely, then update the cache? And THEN, I presume, try the updates again.....? I won't take this any further yet until I get confirmation, one way or the other. I've got 'Trusty' set up just how I want her for the next couple of years; I REALLY don't want to do a re-install..!


Regards,

Mike. :)

---

### Post by oldos2er on 2015-03-03
You should be able to fix this by running ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E0F72778C4676186

sudo apt-get update
```

---

### Post by Mike_Walsh on 2015-03-03
@oldos2er:-

Thanks for the suggestion. If I'd  intended to keep PlayOnLinux, I would have followed the advice. However, I've decided that since I can do without PlayOnLinux (frankly, I'm NEVER going to use it!), I have, accordingly, removed the PPA for it. 

Having done that, I re-ran the updater, and it all went without a hitch.....as usual. Just for future reference, in case I want to try this with any other PPAs that decide to 'lose' their public keys (!), where do you get the keys from? I'm curious...!


Regards,

Mike. :)

---

### Post by oldos2er on 2015-03-03
The NO_PUBKEY error always contains the alphanumeric string you need for the apt-key command.

---

### Post by Mike_Walsh on 2015-03-04
Ah! 

I must remember that in future. Something like this is bound to crop up again at SOME point.....this is all part & parcel of my Linux tuition. Everyone ON the forums is helping with that..! :D

BTW, my graphics app (PhotoScape 3.7) still works fine; so I know I haven't broken anything. Thanks for the information, and your help. I'll mark this as solved.


Regards,

Mike.

---

### Post by oldos2er on 2015-03-04
Welcome.

---

