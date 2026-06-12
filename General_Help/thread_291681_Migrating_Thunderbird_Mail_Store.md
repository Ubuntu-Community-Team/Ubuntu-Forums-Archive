---
title: "Migrating Thunderbird Mail Store"
date: 2006-11-02
forum: General Help
---

### Post by marc_th on 2006-11-02
I'm trying really hard to migrate over to Linux. I got all the fun stuff working, but now I need to get down to business. Is there anyway for me to migrate my Thunderbird mail store under windows XP over to Ubuntu?  I have the store sitting here, but can't figure out how to bring it in. Google is being as useful at tits on a bull...Anyone ever try doing something like this?  Perhaps I should look for a Thunderbird forum out there....

---

### Post by marianom on 2006-11-02
Hi there. I too migrated my mail from xp to ubuntu. It is very easy.
TB is cross platform so you should have no problem. I know this page with instructions but it's not in english.
Give a few minutes and I traslate it for you.

---

### Post by marianom on 2006-11-02
Thanks to ChicoGeek for the original howto (I'm just traslating it: [http://www.ubuntu-es.org/node/972](http://www.ubuntu-es.org/node/972)). I added some tips.

1- Launch Ubuntu TB and create the same accounts you have in win TB (you know: name, user, pop3 server -possible-, the works). At the final part of the wizard it suggests downloading the emails from your mail server. Choose no and close TB.
2- Find and backup the following files: 
 2.1 /home/*youruser*/.mozilla-thunderbird/profiles.ini
 2.2 /home/*youruser*/.mozilla-thunderbird/XXXXXXXX.default/prefs.js
3- Delete the files in /home/*youruser*/.mozilla-thunderbird/XXXXXXXX.default/ (_the files inside, not the folder_).
4- Copy all files from w$ ...\Application Data\Thunderbird\Profiles\\XXXXXXXX.XXX\ to /home/*youruser*/.mozilla-thunderbird/XXXXXXXX.default/ (copy the files, not the folder).
5- move back profiles.ini and prefs.js you backed up in step 2 to their original folders (you'll be replacing the ones migrated from w$).
6- launch thunderbird and you should be ok.


Let me know if you need additional help.

---

### Post by marc_th on 2006-11-02
Marianom, Thanks for the translation. Tomorrow night I'll follow the instructions you translated and try to migrate my mail store. I'll post back detailed feedback either way. Awesome! Thanks again!

---

### Post by marc_th on 2006-11-03
Yes, using your instructions I was able to migrate my Windows Thunderbird mailstore over to Thunderbird under Ubuntu.  Actually, I only had my mail folders and not all the files you mentioned in your instructions, so I just deleted the folders and files under:

/home/{username}/.mozilla-thunderbird/719i8f4h.default/Mail/Local Folders

and pasted in the files and folders of my mailstore.  Fired up Thunderbird, and all my emails where there. Easy as 123.

I should of backed up more of the thunderbird files before I got rid of windows.  That way I would have been able to follow your instructions, and wouldn't have lost my TB configurations....Thanks for all your help!!!

---

### Post by eteran on 2007-01-14
The following worked for me migrating Thunderbird 1.5.0.9 from WindowsXP to Xubuntu 6.10.
Not only including the Mails, but also the Extensions, Message Filters, Account Settings and even Skins.

[SIZE="5"]1. Copy over the Profile(s) and profiles.ini[/SIZE]

On WinXP you find them usually in:
C:\[color=red]Dokumente und Einstellungen[/color]\[color=green]your_username[/color]\[color=red]Anwendungsdaten[/color]\Thunderbird\

(red=may vary depending on which language you've choosen, green=will vary depending on your username)

On Ubuntu copy them to 
/home/[color=green]username[/color]/.mozilla-thunderbird

If you're running a dual boot and have mounted the windows partitions, you could f.e.
```

cd ~/.mozilla-thunderbird
cp -Rp /media/sda1/Dokumente\ und\ Einstellungen/eteran/Anwendungsdaten/Thunderbird/* ./

```

[SIZE="5"]2. change file modes[/SIZE]

```

cd ~/.mozilla-thunderbird
chmod -R 750 ./
chmod 644 profiles.ini

```

[SIZE="5"]3. edit prefs.js[/SIZE]

open up ~/.mozilla-thunderbird/Profiles/{xxxxxxxx.profile}/prefs.js with your favorite editor
and delete every line that contains an absolute windows path.
Thunderbird will recreate those lines when necessary .
do **not** delete the relative paths (starting with [ProfD]).
If you've several profiles to migrate, you will have to do this for each profile.

[SIZE="4"]4. starting up Thunderbird[/SIZE]

When starting up Thunderbird, everything should be in place. You might get a warning from one or annother extension that you're using. Just uninstall it then. Everything else should work with no harm.


Hope this is useful for somebody.

---

### Post by marianom on 2007-01-14
Cool, you should consider to post it in the how-to subforum. I think this question aroses now and then.

---

### Post by discontentment68 on 2008-01-23
AWESOME.  Just what I needed.  I thought mozilla did things cross platform and now i'm sure.  I'm glad too... a few strokes of the keys and an errant 'rm -R' did some damage... Now, its back from my windows pc! Finally, windows is good for something.
thanks

---

