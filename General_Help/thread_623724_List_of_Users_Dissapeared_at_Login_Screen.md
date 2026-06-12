---
title: "List of Users Dissapeared at Login Screen"
date: 2007-11-26
forum: General Help
---

### Post by simonfiction on 2007-11-26
Hi,
I recently played about with installing theme's in Ubuntu but hadn't changed or played with the login screen theme at all. On restart my usual standard Ubuntu login screen popped up where there would normally be a list of users to select from. Except this time the list of 2 users had disappeared and I was left with the empty white box which normally contained these users, completely blank. I could still login fine by manually entering my user name but I want to get my old user list back. I can't seem to find anyone else on the forums who have experienced this. Can anyone help? 

Also, as a side note, is the fast user switching functionality in Gutsy full of bugs or is it just my own experience? I can switch once but when I switch back to the other user my screen goes completely white and stays like it. If I hit Ctrl+Alt+Backspace it seems to come out of it.

Thanks,
Si

---

### Post by simonfiction on 2007-11-27
*bump*

Anyone? Really struggling with this issue.

---

### Post by gits83 on 2007-11-28
same situation here after installing ubuntustudio theme. Any help would be appreciated

edit: same experience about fast user switch here, too.

edit2: solved! in the login preferences window under system->administration you have to change the "style" option in the second tab.
maybe you have only "theme" selected, change to "theme + user list" or something like that.

---

### Post by simonfiction on 2007-11-29
I can't believe it was that simple. I'm quite embarrassed. 

Thanks!

---

### Post by Anubis on 2007-12-13
> **simonfiction said:**
> 
Also, as a side note, is the fast user switching functionality in Gutsy full of bugs or is it just my own experience? I can switch once but when I switch back to the other user my screen goes completely white and stays like it. If I hit Ctrl+Alt+Backspace it seems to come out of it.

Thanks,
Si

I still get the white screen after the switch. At the white screen I type my PW and the desktop reappears, but whats with the white screen?

---

### Post by Sukarn on 2007-12-17
> **Anubis said:**
> I still get the white screen after the switch. At the white screen I type my PW and the desktop reappears, but whats with the white screen?

I think it might be related to the visual effects. Anyway, you can recover from it by going into first terminal (or any other, for that matter), and then switch back to your X-Session.

Default keys for these should be -

[LIST=1]
[*]Press CTRL+ALT+F1 for going into first terminal
[*]Press CTRL+ALT+F7 to go back to first x-session
[/LIST]

---

