---
title: "Logout Dialog Missing"
date: 2007-08-26
forum: General Help
---

### Post by bunnyfly on 2007-08-26
Hello - my logout/restart/shutdown dialog is missing! Every time I click Quit in the menu or panel it simply logs out without asking me. I think a setting must have been corrupted somehow.

I think I MIGHT know what it is. Could somebody please run gconf-editor and tell me what command is at /apps/panel/objects/session_dialog_screen0/action_type

I have "logout" as my key, and I think it maybe is supposed to be the command for the logout dialog. If not, does anybody have any other suggestions? Thank you so much,
[bunnyfly]

---

### Post by jamvegan on 2007-08-26
I have "logout" there, too.  But I did find something else: /apps/gnome-session/options/logout_prompt is checked for me.  How about you?

---

