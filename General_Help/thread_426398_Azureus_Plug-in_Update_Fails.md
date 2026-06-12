---
title: "Azureus Plug-in Update Fails"
date: 2007-04-28
forum: General Help
---

### Post by skoalman88 on 2007-04-28
When I start Azureus, I am prompted to download the "tracker web templates" jar update. The file downloads successfully, but the install is canceled because "permission denied." What do I have to do to have the file install?

Thanks

---

### Post by kalpik on 2007-04-28
How did you install azureus? From the repos, or manually?

---

### Post by golovan on 2007-04-28
[EDIT]
OOPS!!
I did this myself and I belive it messed up my torrents?
Can't seem to get them back in the download window.
But if you have no current downloads it should work for you.
(and maybe it is easy to get them back, but I have no idea how)
[/EDIT]

I believe you can do it like this:

fire up your terminal.
type: sudo azureus and your password

azureus then starts in sudo-mode and you have the right to download and install the update.
do exactly that.
it prompts for a restart. do it. close it. open your "regular" azureus (without sudo)

then your set

---

### Post by skoalman88 on 2007-04-28
Thanks for the tips, but I am switching to KTorrent which will be used to download linux distros and ONLY LINUX DISTROS.


: )

SM-88

---

### Post by JebusWankel on 2007-04-30
golovan: I believe you lost all your torrents because when you ran sudo azureus it ran azureus as root user, so it looked for your .azureus file in /root directory and all your torrents were in the .azureus in you /home/username/ directory. It shouldn't have deleted anything though. I did the same thing but when I ran not as root I got all my torrents back.

I am in the same situation. It may be because I had azureus installed with automatix from my Edgy install and when I installed Feisty I used the same /home partition but reformatted my root partition. That's why apt didn't see it was installed.

My solution was to just install the version from the repos, which was a lot more recent: version 2.5.0.0 versus ~2.1.4. I didn't bother uninstalling the old version, I just got rid of its launchers.

---

### Post by Metallinut on 2007-05-16
I'm having a similar issue.  I've been able to install updates by running it with sudo from the CLI, but there seem to be some updates that get installed per user.  So after installing the update as root, if I run it as regular user, it still wants to do the update.  

Is there a way to change the permissions to allow my regular user account to do these updates?

I've tried doing:
```
sudo chown -R jp:jp /opt/azureus
```

But I'm still getting permission denied...

Any help would be awesome...thanks

---

