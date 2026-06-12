---
title: "Copy and Paste Celestia Files From 12.04 to 16.04 Possible?"
date: 2016-06-06
forum: General Help
---

### Post by SciGuy1872 on 2016-06-06
Hi.  I want to upgrade from Precise to 16.04 by the DVD I made because I cannot upload new songs to Google Play anymore--I figure it's because the library from Precise is old.  I only want to upgrade because of this and want to know if I can copy/paste files from Celestia in 12.04 to a brand-new OS like 16.04, or will the process break things?
     If I upgrade, are there any tips as to what to copy to DVD?--I figure everything in Home, then the entire Celstia folder.
     Thanks,
            SciGuy

---

### Post by DuckHook on 2016-06-07
I only dabbled with Celestia and never downloaded any mappings or data. I understand that some people have reams of data and go exploring the universe like their private version of Star Trek. Therefore, take what follows with a grain of salt.

My understanding is that Celestia stores all of its data in /home. Therefore, a backup of /home will also backup all your Celestia data. You will need to be very careful that the backup is a good one. Make sure it can be read and restored. I also doubt that a DVD will have sufficient capacity, especially if you have other data too. You may prefer to back up to some sort of USB device, because you can get a ton of capacity for very little cost these days, but you are the only one who can tell.

From your description, you wish to wipe your Precise install and go for a fresh, clean Xenial install?

In your case, I would suggest the following:

[LIST=1]
[*]
[*]Try Xenial out as a LiveDVD first. Make sure everything works, especially video, but do ***not*** install.
[*]Keep your Xenial DVD as a plan "B", in case what follows doesn't work.
[*]Do a backup of your whole /home directory and make sure it is a good backup (i.e. it can be read and restored).
[*]Do a network upgrade of Precise to Trusty,
[*]If all goes well, do another network upgrade to Xenial
[/LIST]
When network upgrades work, they tend to automatically configure things properly and elegantly, replacing or getting rid of config files that are superseded/obsolete and installing the latest apps, yet keeping data intact. But they don't always work, hence the need for plan "B". Since you are already prepared to implement plan "B" now, it doesn't hurt you to try a network upgrade first. If it works, it saves you a lot of trouble trying to restore things.

A word of caution: Xenial is on its first go-round and still has lots of bugs (just look through these forums). You may be happy with Trusty, which is now very stable, and delay upgrading to Xenial until the first point release (16.04.1) in about two more months time. If you are intent on upgrading to Xenial right away, you must use the -d switch in your command line:```
sudo do-release-upgrade -d
```Last but not least, I would not be so sure that your problems with Google Play are due to Precise having libraries that are too old. Can you tell us where you came by this info? Precise is still in support and Google Play is accessed through your browser, not the OS. AFAIK, most browsers are up-to-date in Precise, so upgrading your OS is unlikely to change anything. Your upload problems may be due to something else, like reaching your quota maximum, etc.

---

### Post by SciGuy1872 on 2016-06-07
I thought that old libraries might be to blame because I tried to install Google Music Manager (google-musicmanager-beta), but the Software Center replies that "Dependency is not satisfiable: libc6 (>=2.16)"; also, I tried to install GoPanda and while troubleshooting with someone, I discovered that the library set was too old--I was told the only way to fix this is to install a new OS; I kept downloading the relevant file now-and-then and trying to install the program.  It eventually worked.  
   
I have only uploaded 153 songs; Google Play allows 50,000 songs--I have been able to upload songs with no problem, but now it doesn't work.  I tried emailing someone from Google about this and received an email about troubleshooting and did what was suggested.  Then I replied asking if Precise is too old and received no response.  I use Chromium and did not have to use Music Manager before--just thought the upload might work with Manager, since the method of using the website did not.  With the website, I see the upload arrow but there is no growing line that circles the arrow to show upload progress is occurring.  

If a new OS will not fix this issue, I will not upgrade (everything besides this works).  Thanks for the reply.

---

### Post by SciGuy1872 on 2016-06-09
I just want to make sure that this new information when trying to install Google Play Music Manager ([COLOR=#000000]Software Center replying that "Dependency is not satisfiable: libc6 (>=2.16)" means that if I want to upload other songs (either from the website or Music Manager), I need to upgrade to a newer OS?

I have a legacy Nvidia and that's the only reason I don't want to try an upgrade.  Just curious--how long does a network upgrade take?  

Thanks[/COLOR]

---

### Post by DuckHook on 2016-06-09
Apologies! Based on...> If a new OS will not fix this issue, I will not upgrade (everything besides this works). Thanks for the reply....I assumed that you were satisfied and not looking for any more guidance. My mistake for not reading your second posting more carefully.

The dependency alert very much indicates that your version may be too old. On my Xenial install, libc6 is version 2.23 which would satisfy the dependency requirement for google-musicmanager-beta. You do understand that Google Music Manager is beta software and may be buggy up to and including further dependency issues? If you are fine with that, then it's fair game.

If you are going to upgrade, try the simplest path first: see if your browser under Trusty is sufficient to get Google Music working. If so, then no further need for now to go all the way to Xenial, and no need for Google Music Manager.

To see if your legacy nVidia is supported, try running a LiveDVD/USB first (both Trusty and Xenial) before doing any sort of upgrade. If a Live session works, an upgrade should also work, or at least can be gotten to work. If you encounter problems, that's what these forums are here for. Upgrading to Trusty is simple and can be done from the graphical software manager. Upgrading to Xenial will require the special terminal command that I posted earlier.

A network upgrade is a major undertaking and the time is dependent on your bandwidth. On my 600kB/s connection, the download took about 40 minutes. The install then took another 40 min. Make sure that you disable all PPAs before upgrading. After disabling them, be sure to run:```
sudo apt-get update && sudo apt-get dist-upgrade
```...before doing the big version upgrade. This will give you the best chance of success. Also, make sure you have enough disk space before starting. 2GB of free space in your root directory ought to do it.

BE SURE TO BACKUP first.

---

### Post by DuckHook on 2016-06-09
Just rebooted into my Trusty install and checked: libc6 is version 2.19 in trusty, so should also satisfy your dependency. Since Trusty (14.04) is older and stabler than Xenial, I would suggest staying with it for now and not proceeding to Xenial whether the browser starts working again or you end up using G Music Manager.

---

