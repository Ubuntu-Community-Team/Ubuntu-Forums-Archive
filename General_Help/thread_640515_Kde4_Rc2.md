---
title: "Kde4 Rc2"
date: 2007-12-14
forum: General Help
---

### Post by Frodo232 on 2007-12-14
Yesterday ,using the instructions from the kubuntu page I installed kde4 RC2 on my Kubuntu system.

I log out, select KDE4 as the session log in and the screen goes blank for 5 seconds, and then returns to the login screen.

any ideas for how to troubleshoot this?

Frodo232

---

### Post by PmDematagoda on 2007-12-14
Did you follow the instructions to let KDE4 be run as a separate session properly?

---

### Post by Frodo232 on 2007-12-14
PmDematagoda

Thanks for you speedy reply

I followed the instruction except for the last bullet point as (tell me if im wrong) its only nessicary if launching KDE4 from within another KDE3 session

Frodo232

---

### Post by PmDematagoda on 2007-12-14
By rights KDE 4 should work on properly, I'm afraid I cannot help you further, hopefully someone else will come along and clear things up for you.

---

### Post by kc0eks on 2007-12-14
Mine does the same thing, unless I use a new user. For some reason my normal acount that works with KDE3 wont work with 4, I am on the hunt for a fix...

---

### Post by bmorency on 2007-12-14
the same thing happens to me too. kde 4 has never worked properly for me with every update that is released.

---

### Post by ben::zen on 2007-12-14
@ OP:
The absolute best thing to do is run the export commands, then Alt+F2 kdesu kate then edit the /usr/lib/kde4/bin/startkde to include those same lines after the first block of commented text (if it doesn't grey out the lines with #s in front of them, go to the Tools>Highlighting>Scripts>Bash command, it will show you what's commented by color, the faded grey is comments.)
Once you've done that, save the file, log out, and log in under the KDE4, and enjoy the oxygenated goodness ;)
Actually, after having read other posts, there seems to be something else... umm, are all the files absolutely installed properly?

---

### Post by PmDematagoda on 2007-12-14
Well, I do not know the real problem faced by the others, but KDE4 RC2 works on my Ubuntu 7.10 X64 system flawlessly and I did not do anything else other than just installing the necessary packages via apt-get.

---

### Post by der_joachim on 2007-12-15
I found a fix in [this thread]("http://ubuntuforums.org/showthread.php?t=638218&highlight=kde4"). Worked perfectly for me.

Apparently, KDE4 does not like your kde3 setting directory.

[Edit]: Since there is a new .kde settings directory, you will not be able to use your settings for KDE apps. If you still want to use them, you'll have to do the following things. Disclaimer: I tried these at home this morning, and although I have not run into any problems yet, I do not know whether  this is absolutely safe.

anyhoo, here goes:
* Open a konsole
* Go to the ~/.kde4/share subdirectory.
* Rename the subdirectories apps and config to apps_bak and config_bak. (Note:This is not really necessary. You can delete these subdirectories as well. It is safer though to keep a backup. )
* make symlinks to your kde3 apps and config subdirectories by issuing the following commands while in ~/.kde4/share:
```

ln -s ~/.kde/share/apps apps
ln -s ~/.kde/share/config config

```

[edit2] Typo d'oh!

---

### Post by Frodo232 on 2007-12-15
Thanks for that!

Now Working a Treat!!

---

### Post by Xbehave on 2007-12-15
wfm!
erm is there anyway to get the taskbar smaller, i managed to crash it but otherwise its perminantly taking up too much screen space (1st thing i do on an instal is set panels to tiny)

---

### Post by kc0eks on 2007-12-16
> **Xbehave said:**
> wfm!
erm is there anyway to get the taskbar smaller, i managed to crash it but otherwise its perminantly taking up too much screen space (1st thing i do on an instal is set panels to tiny)

I dont know if its just me and you, but I could not find a setting anywhere for this either. I think a ton of the settings GUI stuff is missing. And I have no desire to edit text files, so I guess I wait for the real release...

---

### Post by tghe-retford on 2007-12-16
I couldn't see anything either, the only customisation I could see with the Plasma workspace (which includes the panel) was to set the wallpaper on the desktop. So although I have RC2 installed, I will also wait, unless anyone has a solution that can set the panel to tiny. I have a preference to screen estate, and allowing the applications I use to take up as much of the screen as possible, something not possible with the current panel being customisable at the moment.

If I can't customise the panel come the release, then I shall stick with KDE3 until customisation for the panel comes along.

---

### Post by Frodo232 on 2007-12-16
It has to be said that KDE4 RC2 isen't really worth the effort of trying to get it to work.

Nice concept, but definatly in early beta not RC condition

---

### Post by kc0eks on 2007-12-16
> **tghe-retford said:**
> 

If I can't customise the panel come the release, then I shall stick with KDE3 until customisation for the panel comes along.

I agree with ya. From what I can see I hate the new menu system too, but maybe once I can customize it it wont annoy me so much. 

But I do agree this look early Beta, as I have managed to crash the plasma stuff a few times just doing basic things. 

I was excited with all the hype, but man it just doesnt impress me one bit. I hope things improve before the release...

---

