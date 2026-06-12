---
title: "clipboard manager program doesnt work in 14.04"
date: 2014-04-19
forum: General Help
---

### Post by pretty_whistle on 2014-04-19
Its called Parcellite.  It's not working anymore.  I try to execute it but it doesnt come up. :(

I'd guess no one can help me fix it.  If that's the case does anyone know of a clipboard manager that does work with 14.04?

Thanks.

---

### Post by su:bhatta on 2014-04-20
Pretty_whistle,
I just downloaded Parcelite 1.1.7-1 from Synaptic to give it a try.
Seems to work fine here. What is your version?
Found, another program called Cliptit, as an alternative listed in Syanptic too.

What are the error messages you are getting when you try to run Parcellite from the terminal?
Also, since you upgraded from 13.10,you can try completely removing and then installing it fresh.

---

### Post by pretty_whistle on 2014-04-20
Thanks for your help.I have the update version, Parcelite 1.1.7-1, but it's not putting itself on the panel like it did before.  I tried reinstalling it but it didnt help.   Clipit did the same thing.

When I tried to run Parcellite from terminal here's what I got:

```
Unable to load pref 'history_pos'Unable to load pref 'history_x'
Unable to load pref 'history_y'
Unable to load pref 'data_size'
Unable to load pref 'automatic_paste'
Unable to load pref 'auto_key'
Unable to load pref 'auto_mouse'
Unable to load pref 'key_input'
Unable to load pref 'restore_empty'
Unable to load pref 'rc_edit'
Unable to load pref 'type_search'
Unable to load pref 'case_search'
Unable to load pref 'ignore_whiteonly'
Unable to load pref 'trim_wspace_begend'
Unable to load pref 'trim_newline'
Unable to load pref 'current_on_top'
Unable to load pref 'persistent_history'
Unable to load pref 'persistent_separate'
Unable to load pref 'persistent_on_top'
Unable to load pref 'persistent_delim'
Unable to load pref 'nonprint_disp'
Unable to load pref 'multi_user'
Unable to load pref 'phistory_key'



```

Plus a small window came up that said:

```
System program problem detected
Do you want to report the problem?
```

---

### Post by su:bhatta on 2014-04-20
pretty_whistle,
can you try another thing?
uninstall and purge parcellite.
Then remove the entire configuration folder of Parcellite from : ~/.local/share/parcellite.

Then reinstall again and see if that works.

ANd, did you try to report the problem, like raise a bug report?
What came up there?

---

### Post by pretty_whistle on 2014-04-20
I just did it.  Same problem as before. :(

---

### Post by su:bhatta on 2014-04-20
I believe you are booting Xfce, and I also booted to Xfce, strange but Parcelite is by default showing in the system tray on start up only.
Now I am clueless.

Sorry, no more help from me :(

---

### Post by pretty_whistle on 2014-04-20
Thanks anyway. :)

---

### Post by Toz on 2014-04-20
> **pretty_whistle said:**
> Thanks for your help.I have the update version, Parcelite 1.1.7-1, but it's not putting itself on the panel like it did before.  I tried reinstalling it but it didnt help.   Clipit did the same thing.

When I tried to run Parcellite from terminal here's what I got:

```
Unable to load pref 'history_pos'Unable to load pref 'history_x'
Unable to load pref 'history_y'
Unable to load pref 'data_size'
Unable to load pref 'automatic_paste'
Unable to load pref 'auto_key'
Unable to load pref 'auto_mouse'
Unable to load pref 'key_input'
Unable to load pref 'restore_empty'
Unable to load pref 'rc_edit'
Unable to load pref 'type_search'
Unable to load pref 'case_search'
Unable to load pref 'ignore_whiteonly'
Unable to load pref 'trim_wspace_begend'
Unable to load pref 'trim_newline'
Unable to load pref 'current_on_top'
Unable to load pref 'persistent_history'
Unable to load pref 'persistent_separate'
Unable to load pref 'persistent_on_top'
Unable to load pref 'persistent_delim'
Unable to load pref 'nonprint_disp'
Unable to load pref 'multi_user'
Unable to load pref 'phistory_key'



```

Plus a small window came up that said:

```
System program problem detected
Do you want to report the problem?
```

Perhaps there is a problem with the configuration file. Try deleting (or renaming if you want to save it) the ~/.config/parcellite folder before starting.

---

### Post by pretty_whistle on 2014-04-20
> **Toz said:**
> Perhaps there is a problem with the configuration file. Try deleting (or renaming if you want to save it) the ~/.config/parcellite folder before starting.
I deleted it and it worked.  Even works after I restart the computer!  Yay!

Thanks Toz!

---

