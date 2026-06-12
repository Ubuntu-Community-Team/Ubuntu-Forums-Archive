---
title: "Which hidden directories are vital to restore?"
date: 2020-05-21
forum: General Help
---

### Post by goemonburo on 2020-05-21
Hi.  I have a tar.gz backup of my old home directory and have now installed Lubuntu 20.04LTS (previously was running 18.04LTS).  It's a fresh install, as required, so I am about to restore most of my old home directory.  Obviously I'll restore all the NON hidden directories, but the backup took forever with countless hours of cached thumbnails and other stuff and I'd like to not restore stuff that I don't have to.

I am curious if there are any lists of hidden .something directories that I can safely NOT restore and still have a system that's again working.  Additionally, if I extract the tar file directly into my home directory, will I risk overwriting certain important hidden files or directories that 20.04 depends on with older 18.04 files?  

Am I best off excluding ANY of the hidden files from restore and then migrating them one by one?  If I do this for a file like .mozilla will I be able to get my passwords back?  (They've currently vanished, despite my copying the db and logins.json files into the current default profile...)

Any help would be fantastic.  Thank you in advance for sharing your expertise.

---

### Post by CatKiller on 2020-05-22
> **goemonburo said:**
> Am I best off excluding ANY of the hidden files from restore and then migrating them one by one?  If I do this for a file like .mozilla will I be able to get my passwords back?  (They've currently vanished, despite my copying the db and logins.json files into the current default profile...)

That's the way I would do it: only copy the ones I needed to when it turns out that I need to. My Firefox and Thunderbird folders have been moved across loads of systems: they started on Windows 2000. There's not a lot of order to the hidden files in your Home directory (some, but not a lot) but you shouldn't have much trouble working out which one is from which application should you find that you need it.

Edit: specifically to this point

> I am curious if there are any lists of hidden .something directories that I can safely NOT restore and still have a system that's again working. 

The hidden folders in your Home directory just store configuration files for your user. Any that need to exist that don't will just be created from the defaults whenever they're needed, so it will always work. It's just that you'll have whatever the default configuration is rather than whatever you'd configured it to.

---

### Post by lvm on 2020-05-22
Hidden directories usually contain application settings and temporary files. If you copy them, applications will work exactly as they did on the old system, if you don't, settings will be reset to defaults and you will have to reconfigure them from scratch so copying hidden directories is usually not only quite safe but recommended. It is safer to restore user data when this user is not logged in. If you are concerned about the amount of data being copied you may omit ~/.cache directory which contains temporary files and may review the list of folders and exclude applications you are no longer using. The modern trend is to store configuration data in ~/.config/<appname> and temporary files in ~/.cache/<appname>, older applications may store their data in ~/.<appname>, finally an application may switch from the old scheme to the new one but neglect to clean up old files.

---

### Post by goemonburo on 2020-05-22
Hi again, @CatKiller, thanks for your awesome help and suggestions.

I am finding it hard to figure out how I would construct a tar restore that excludes anything that's a hidden file.  Can I do that somehow?  Documentation is robust on how to exclude files when you're backing up.  But if I only want to restore non-hidden files and directories, what's the syntax for doing that?

Do I do something like:

    tar xzvf --exclude=/.* /path/to/my/tar/file.tar.gz .

Or does the exclude only work on the backup and for restore I'm kind of stuck?

---

### Post by CatKiller on 2020-05-23
I don't see any reason why you couldn't use exclude on extraction as well as when you're selecting files to put in. I don't have a lot of experience with command line tar, though.

---

