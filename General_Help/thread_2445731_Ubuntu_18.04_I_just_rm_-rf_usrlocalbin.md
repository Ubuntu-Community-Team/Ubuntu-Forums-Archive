---
title: "Ubuntu 18.04: I just rm -rf /usr/local/bin"
date: 2020-06-18
forum: General Help
---

### Post by Dáire Fagan on 2020-06-18
I meant to deleted a directory I had just moved in there, and I was distracted and pressed enter on the command and accidentally deleted /usr/local/bin.

Is there anyway to recover this directory or regenerate it short of a fresh install?

My system is incredibly customised, Manual Full System Encryption dual booting with VeraCrypt Windows 10 - it would take a long time to set it up from the beginning :(

---

### Post by CatKiller on 2020-06-18
Nope.

---

### Post by &amp;KyT$0P# on 2020-06-18
> **dusf said:**
>  accidentally deleted /usr/local/bin.

Is there anyway to recover this directory or regenerate it short of a fresh install?

What did you have in there?
Do you have a backup?

A fresh install of the entire Ubuntu OS probably won't help you.  [FONT=Courier New]/usr/local/bin[/FONT] is just an empty directory in a fresh buntu install.

---

### Post by Dáire Fagan on 2020-06-18
> **CatKiller said:**
> Nope.

:-?

> **halogen2 said:**
> What did you have in there?
Do you have a backup?

A fresh install of the entire Ubuntu OS probably won't help you, this is just an empty directory in a fresh buntu install.

I am afraid the only backup I have is a directory somewhere else where I keep personal files, code, etc. and Insync syncs it to Google Drive.

I do not recall ever putting anything in that directory, unless install scripts have or I have at some point. I am reading up about /usr/local/bin - is it similar to opt? If so I normally place programs I install manually in opt...

---

### Post by Skaperen on 2020-06-18
do a fresh install onto a USB thumb drive (a 2nd one if using one to install from).  then copy its /usr/local/bin.  that will at least get your recovery started.  now you proceed to put your custom stuff back in there.

---

### Post by &amp;KyT$0P# on 2020-06-18
As a start, do
```
sudo mkdir /usr/local/bin
```

Then please post the output from running these commands in Terminal -
```
ls -la /usr/local/bin
find /usr/local -type f
```

---

### Post by Dáire Fagan on 2020-06-18
> **Skaperen said:**
> do a fresh install onto a USB thumb drive (a 2nd one if using one to install from).  then copy its /usr/local/bin.  that will at least get your recovery started.  now you proceed to put your custom stuff back in there.

Noted thanks.

---

### Post by Dáire Fagan on 2020-06-18
> **halogen2 said:**
> As a start, do
```
sudo mkdir /usr/local/bin
```

Then please post the output from running these commands in Terminal -
```
ls -la /usr/local/bin
find /usr/local -type f
```

```
runswithascript@contraption:~$ ls -la /usr/local/bintotal 8
drwxr-xr-x  2 root root 4096 Jun 18 23:31 .
drwxr-xr-x 10 root root 4096 Jun 18 23:31 ..
runswithascript@contraption:~$ find /usr/local -type f
/usr/local/sbin/refreshgrub
/usr/local/share/applications/mimeinfo.cache
/usr/local/share/applications/google-musicmanager.desktop

```

refreshgrub is very important, it's something the custom encryption setup uses to fix grub chain loading whenever there is a big update. What can you discern from the output?

---

### Post by &amp;KyT$0P# on 2020-06-18
Ok, now please do
```
echo "$PATH"
```
Make sure [FONT=Courier New]/usr/local/bin[/FONT] is listed.

How did you install refreshgrub?  I would suggest you now reinstall refreshgrub, if you think there's any chance any part of it could have been in [FONT=Courier New]/usr/local/bin[/FONT]

Can you please also post output of
```
cat /usr/local/share/applications/google-musicmanager.desktop
```

---

### Post by Skaperen on 2020-06-18
i have a script that does all my install customization.  i do a fresh install, reboot, and run my script.  it installs more packages.  a 2nd script adds my custom files which includes a setup script that runs each time i boot up.  one of the things i did was quit putting custom files in [COLOR=#0000ff][FONT=courier new]**/usr/local**[/FONT][/COLOR] and started putting them in [COLOR=#0000ff][FONT=courier new]**/usr/host**[/FONT][/COLOR] instead.  it is pure custom stuff, so that my custom build script can remove the whole thing and build it, again, totall from scratch, every time.  thus if my changes delete a file, the rebuild omits it and there is no old leftover copy, anymore.

---

### Post by Skaperen on 2020-06-18
@halogen2:  make a directory then list its contents?  hmmm.  intersting concept.

---

### Post by Dáire Fagan on 2020-06-18
> **halogen2 said:**
> Ok, now please do
```
echo "$PATH"
```

Make sure [FONT=&quot]/usr/local/bin[/FONT] is listed.

```
runswithascript@contraption:~$ echo "$PATH"
/home/runswithascript/.local/bin:/home/runswithascript/bin:/usr/local/sbin:**/usr/local/bin**:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/lib/jvm/java-13-oracle/bin:/usr/lib/jvm/java-13-oracle/db/bin:/home/runswithascript/.local/bin:/home/runswithascript/.local/bin

```

> **halogen2 said:**
> 


How did you install refreshgrub?  I would suggest you now reinstall refreshgrub, if you think there's any chance any part of it could have been in [FONT=Courier New]/usr/local/bin[/FONT]

it was part of a script that ran at the same time as the Ubuntu installer, I am trying to find it on the wiki.

> **halogen2 said:**
> 
Can you please also post output of
```
cat /usr/local/share/applications/google-musicmanager.desktop
```

```
runswithascript@contraption:~$ cat /usr/local/share/applications/google-musicmanager.desktop[Desktop Entry]
Version=1.0
Name=Google Music Manager
# Only KDE 4 seems to use GenericName.
GenericName=Google Music Manager
# Gnome and KDE 3 uses Comment.
Comment=Upload to Google Music
Exec=/opt/google/musicmanager/google-musicmanager
Terminal=false
Icon=google-musicmanager
Type=Application
Categories=AudioVideo;Audio;Network;

```

I do not use Google Music Manager as it did not fit my needs, so I am happy to uninstall it if that would help...

---

### Post by &amp;KyT$0P# on 2020-06-18
> **Skaperen said:**
> @halogen2:  make a directory then list its contents?  hmmm.  intersting concept.

The point was to see the permissions of the newly-created directory, to compare to a system where that directory had not been removed.  It's the same in this case.

---

### Post by Dáire Fagan on 2020-06-18
> **Skaperen said:**
> do a fresh install onto a USB thumb drive (a 2nd one if using one to install from).  then copy its /usr/local/bin.  that will at least get your recovery started.  now you proceed to put your custom stuff back in there.

Is /usr/local/bin not empty in a fresh install?

---

### Post by Dáire Fagan on 2020-06-18
[https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPrepareInstall](https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPrepareInstall)

The script linked on that page I think creates refreshgrub.

---

### Post by Dáire Fagan on 2020-06-18
So I just tested refreshgrub from terminal and it worked. I then rebooted and I was able to login :)

---

### Post by &amp;KyT$0P# on 2020-06-18
Quick look at that script indicates it doesn't put anything in [FONT=Courier New]/usr/local/bin[/FONT], but I didn't look through the whole script in detail.

> **dusf said:**
> So I just tested refreshgrub from terminal and it worked. I then rebooted and I was able to login :)

Then I think this might now be as recovered as it can get.

---

### Post by Dáire Fagan on 2020-06-18
> **halogen2 said:**
> Quick look at that script indicates it doesn't put anything in [FONT=Courier New]/usr/local/bin[/FONT], but I didn't look through the whole script in detail.

Then I think this might now be as recovered as it can get.

Thank you very much for your help :)

---

### Post by &amp;KyT$0P# on 2020-06-18
You're welcome :KS

---

### Post by TheFu on 2020-06-19
Nothing gets put into /usr/local/ using package or snap installs, unless YOU told the package to install their specifically. Only stuff you manually install, manually compile would end up there.

> Is there anyway to recover this directory 
Sure. Restore from the automatic, versioned, backups you made last night or last weekend.  Lacking that, nope.  Get backup religion.  My /usr/local/bin/ on my main VM host running 16.04 the last 18 months has ZERO files inside it. Actually, all the immediate subdirectories are empty of files.

Anything that happened to get under /usr/local/ isn't part of the core system, so relax.  Reinstall wouldn't help.

---

### Post by kneutron on 2020-06-20
> [COLOR=#000000]Restore from the automatic, versioned, backups you made last night or last weekend. Lacking that, nope. Get backup religion

--Amen to that.  I backup critical files AND do a full bare-metal backup with fsarchiver before doing any apt upgrades.  And I've tested my restores!


--Also, PROTIP: Use **midnight commander** ('mc' package) to SAFELY delete directories and subdirs.  I can count the number of times I've used ' rm -rf ' on one hand, and I've been a Linux admin for DECADES.  I took up using MC after learning that the two most deadly dangerous, misused commands on *nix systems are DD and RM.  And (years ago) I already mixed up /dev/fd0 and /dev/sda by accident with DD once.  ONCE.[/COLOR]

---

