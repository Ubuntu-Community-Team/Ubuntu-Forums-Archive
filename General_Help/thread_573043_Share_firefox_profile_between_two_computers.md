---
title: "Share firefox profile between two computers?"
date: 2007-10-11
forum: General Help
---

### Post by DannyW on 2007-10-11
I have a desktop computer and a laptop, both running Kubuntu (7.04 and 7.10b)

I would like to be able to share my firefox and thunderbird profiles between the two, so that if I add a bookmark in firefox on my laptop, it is automatically added on my desktop pc.

Same goes for email with thunderbird. Receiving an email whilst on the laptop would add the email to my desktop configuration.

How could I share the profiles between two computers?

Thanks,
Danny

---

### Post by Forlong on 2007-10-11
You would need to have access to the same harddrive from both computers.

---

### Post by Matthaeus on 2007-10-11
I have never done it with firefox, but i always share my thunderbird account between my xp and ubuntu installations.
I believe it would be the same, except perhaps mount the shared folder....though you could probably just type in the network name.

I don't know what would happen if both computers accessed the one profile at the same time?

/home/insert.user.name/.mozilla-thunderbird

You need to edit the profile.ini

"IsRelative" - Is the profile is in the defult directory? Change this to 0.

[PHP][General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/Windows C Drive/Documents and Settings/M & M/Application Data/Thunderbird/Profiles/u12345q.default[/PHP]

You could do a similar thing with firefox - check out the mozilla site and search for profiles, it has more information there.

Cheers, Matt.

---

### Post by DannyW on 2007-10-11
So maybe setup ssh access to my desktop computer (and leave my desktop permanently on) and access the profile via sshfs? This could be a problem as my internet access is restricted, I cannot forward ports to my computer.

Maybe there is some internet file synchronising software?

Thanks,
Danny

---

### Post by DannyW on 2007-10-11
I have had a quick look at [Unison]("http://www.cis.upenn.edu/~bcpierce/unison/"). It keeps two remote folders synchronised via ssh, rsh, or socket. Would I have to forward port 22 (ssh) to my desktop and to my laptop wherever I happen to be connecting to the internet from?

---

### Post by jaygo on 2007-10-14
google has a nice browser-sync plugin for firefox that can sync most everything there.

Thunderbird will be a bit more of a challenge. I believe that sharing access to the *same* profile files is asking for trouble. A few other options:
[LIST=1][*]A third-party app might do the trick
[*]use imap
[*]if you have enough storage, you can just share your inbox between the two PCs by choosing to "leave messages on server"
[*]contacts can be shared with a tbird plugin -- addresses backup, or something like that -- it copies the files to a custom location everytime you close tbird
[*]I'm sure there's more but I can't think of them atm.
[/LIST]

GL. Let us know how it works out.

---

### Post by DannyW on 2007-10-14
Thanks for the info.

It seems my email provider supported imap and so I have switched to that, which is great! Just the sort of thing I needed really.

I have used the Foxmarks extension to sync my bookmarks with other computers. That plugin works great, but I would have liked to share my saved passwords and cookies.

I'll check out this google plugin you mention.

Thanks again!

Danny

---

