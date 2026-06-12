---
title: "Ubuntu 24.04.1 - lost permissions on user login after recent updates"
date: 2024-11-30
forum: General Help
---

### Post by ballem on 2024-11-30
Hello, am not a new user and have been using Ubuntu Gnome for several years, but after some system updates  a few days ago, I seem to have lost all user permissions on logging in. This is manifested by the options to restart or shutdown missing completely from the shell menu, and pressing the power button is ignored.

I still have sudo permissions and can shutdown from the CLI, but attempting to do anything that requires admin permissions in the gui is either missing, does nothing, or gives an error similar to the following:. in Users and Groups, my user account type is shown as Custom and attempting to change it or manage groups gives the following error:

**You are not allowed to modify the system configuration:**

**An error occurred whilst checking for authorisations:**
**GDBus.Error: org.freedesktop.PolicyKit1.Error.Failed:Action org.freedesktop.systemtoolsbackends.set is not registered.**
**You may report this as a bug.**

Not sure if this issue is related to the following Systemd UNIT errors I see in the logs:

**Failed to start app-gnome-ubuntu\x2dreport\x2don\x2dupgrade-3928.scope**
**Failed to start app-gnome-xdg\x2duser\x2ddirs-3737.scope**
**Failed to start app-gnome-gnome\x2dkeyring\x2dsecrets-3818.scope**
**Failed to start app-gnome-gnome\x2dkeyring\x2dpkcs11-3819.scope**

Grateful for any suggestions as other than waiting to see if this gets reported as a bug and fixed in due course, I am at a loss on how to resolve this apart from restoring a backup and trying the upgrades again?

---

### Post by TheFu on 2024-11-30
Any chance you caused root to take over ownership of files in your HOME?
I don't use PolicyKit nor gnome, so know idea how that might be impacted, but you can take ownership of all files in your HOME with this exact command:
```
sudo chown -R $USER $HOME
```
After, logout and login again.  That should be sufficient, but it may not be if you use too many systemd things.  Once in a while systemd will cache things that are unexpected so the only way to force a re-read is a full reboot/reset.

The chown command shouldn't do any harm at all. After all, all files in your HOME should be owned by that userid.

---

### Post by ballem on 2024-12-01
> **TheFu said:**
> Any chance you caused root to take over ownership of files in your HOME?

Thanks for the suggestion, however that isn't the case as my home permissions are still fine.

As I mentioned, this occurred after some recent updates, one of which was Systemd, so I suspect that could be the cause? Have tried reinstalling that and Polkit, etc, but to no effect. Everything runs fine otherwise, and I can do everything I need to on a day to day basis as a standard user, I just can't do anything (in the gui) that requires admin permissions!

---

### Post by TheFu on 2024-12-01
I don't have 24.04, but I do have LM 22 (based on 24.04) and a number of other systems.  Patched them all yesterday and haven't seen any issues like this.

You can create a new userid, login with it, and see if the problem is for a specific user or all users on the system. Plus, it is handy to have another user to try out things without risking your main user.

There was a snapd update this week, so if you use lots of snap packages, could that be related?  I know it screwed my Nextcloud install, which uses a snap package, but in a way that was easily fixed.

I don't use Polkit.  Thought it was deprecated years ago due to security issues.  [https://gitlab.freedesktop.org/polkit/polkit/](https://gitlab.freedesktop.org/polkit/polkit/) is an "archived project" whatever that means.

---

### Post by ballem on 2024-12-01
> **TheFu said:**
> You can create a new userid, login with it, and see if the problem is for a specific user or all users on the system

Thanks @TheFu, appreciate your help. I already tried creating a new user, but it wasn't that.

Decided to bite the bullet today and restore a backup of the root partition. This resolved the issue until I re-applied all the updates, when the problem re-occurred. So I restored the backup again and selectively re-applied updates until I isolated the offending package. Turned out it was a recent PolKit update after all, but I'd forgotten that I had enabled proposed some time ago, and the update was in fact from that repo. So turning off the proposed repo resolved the issue. Will have to be careful to check in future, but I am happy that is now resolved.

Thanks again.

---

### Post by TheFu on 2024-12-01
Great job thinking of that.  

Nobody knows your systems like you know your systems.

---

### Post by ajgreeny on 2024-12-02
And for any other users, it's a very good reason not to enable the proposed repos as a default for your system.

I have very occasionally used them for a specific package but after adding that proposed version package I immediately disable the proposed repos; working this way hs never caused me any problems!

---

