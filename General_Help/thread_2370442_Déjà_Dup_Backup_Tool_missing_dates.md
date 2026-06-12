---
title: "Déjà Dup Backup Tool missing dates?"
date: 2017-09-03
forum: General Help
---

### Post by Xubuntist on 2017-09-03
HI all,

I have an old PC that I turned into a Minecraft server for my boy, it's running Lubuntu 16.04 and Multicraft. I also installed Déjà Dup to carry out automated daily incremental backups because it's simple, gui-based and had a good rep wherever I looked. The server is never switched off and my son plays almost daily with his  pals so, theoretically, there should be a daily backup going back xx weeks in the Restore screen.

My boy reported the other day that something in Minecraft has been buggy, not only for him but for his pals who join him and he pinned it down to happening on or about Aug 15th. No problem, I told him, I'll just restore the server to the day/week before and he was delighted.

I Teamviewered onto the server today and ran Déjà Dup and went to Restore. As you can see, there are a bunch of backup dates, but it's not consistent:

[IMG]http://farm5.staticflickr.com/4355/37000637315_a08a185326_b.jpg[/IMG]

Déjà-Dup did backups from the date I installed it to 15th June. Then it skipped almost a week and has then hiccupped a few backups in a haphazardly fashion. I repeat that the boy plays daily, and if the server was down for any reason, I'd know about it immediately. Yet there's an ENTIRE month between 14 July and 14 Aug without backups. Etc, etc. I also checked the location of the backup files and the dates correspond to the dates shown in the screenshot.

I've checked the setup and it's definitely set up to do daily, incremental backups. Anyway, you can't change the "incremental" flag in Déjà-Dup (although I'm sure you can in Duplicity).

Could anybody offer an explanation for this behaviour? On this occasion I was lucky to find there was a backup for 14 Aug, but it was the first time for weeks that I checked it was doing daily backups which, in the beginning, it was.

Should I be looking for a more robust backup solution?

---

### Post by deadflowr on 2017-09-03
> Anyway, you can't change the "incremental" flag in Déjà-Dup 
The deja-dup settings gui is rather limited.
But you can tweak deja-dup settings, somewhat, in dconf-editor at org > gnome > deja-dup.

(And yes, duplicity is even more robust in regards of fine-tuning, though you need to set it up manually and most likely with a script (or two) or a cronjob)

---

### Post by untrustytahr on 2017-09-03
From gnome wiki: [https://wiki.gnome.org/Apps/DejaDup/HowItWorks](https://wiki.gnome.org/Apps/DejaDup/HowItWorks)

> Why Not Cron?
A monitoring program is used because access to the user session is useful for:


prompting for passwords
displaying status in the panel
watching for events like plugging in a remote disk or becoming connected to the Internet
**One disadvantage is that a backup can not be started while a user is not logged in.** [I]The primary use case for Déjà Dup is backing up user data, so this is not a large concern, as user data is unlikely to change while the user are not logged in.
[/I]
Deja dup is a rather interactive type of application (i.e. prompting for passwords and verifying backups periodically etc).

I suppose it could also be the backend location being unreachable/full or something along those lines, but I'm willing to bet that if you use 'last' to lookup when you were logged into the server, they would match those dates.

Duplicity on cli does give you much more flexibility and it's not particularly difficult to run from a cron job.   I use something like this:

```
@weekly duplicity --full-if-older-than 1M --encrypt-key <your-pub-key> --exclude-filelist <your-exclude-textfile> SOURCE DESTINATION >> /var/log/duplicity/duplicity.log 2>&1
```

The duplicity.log file is a file that you create in /var/log with write permissions for your user.  That way you can setup logrotate to maintain it.

---

### Post by Xubuntist on 2017-09-04
Many thanks for responding.
> **deadflowr said:**
> The deja-dup settings gui is rather limited.
Yes, it is. I'm used to a program called Cobian Backup which is perfect for my Windows needs and it's a shame and a surprise that there isn't such a user-friendly yet powerful gui-driven backup software for Ubuntu. Windows users are prettymuch spoilt for choice when it comes to free and paid backup apps.

> **untrustytahr said:**
> Deja dup is a rather interactive type of application (i.e. prompting for passwords and verifying backups periodically etc).
Not sure if I understand that. It is simple in the extreme and rather than being interactive I find it just sits there and does its job in the background. But, as you said later on, you have to be logged in for it to work.

> **untrustytahr said:**
> I suppose it could also be the backend location being unreachable/full or something along those lines, but I'm willing to bet that if you use 'last' to lookup when you were logged into the server, they would match those dates.
I'll check up on that, it's an interesting angle.

---

