---
title: "Desable Dead Key"
date: 2006-11-15
forum: General Help
---

### Post by omiazad on 2006-11-15
In Keyboard layouts I added "[COLOR=Red]U.S. English International (With Dead Keys)[/COLOR]" and now I'm in problem.

When I press[COLOR=Red] ' " `~[/COLOR] buttons, the letter doesn't appear until I press space. Also if I press [COLOR=Red] 's[/COLOR] it becomes [COLOR=Red]&#347;[/COLOR] 

Who can I get rid of this stupid problem?

---

### Post by Arndt on 2006-11-15
> **omiazad said:**
> In Keyboard layouts I added "[COLOR=Red]U.S. English International (With Dead Keys)[/COLOR]" and now I'm in problem.

When I press[COLOR=Red] ' " `~[/COLOR] buttons, the letter doesn't appear until I press space. Also if I press [COLOR=Red] 's[/COLOR] it becomes [COLOR=Red]&#347;[/COLOR] 

Who can I get rid of this stupid problem?

I haven't used these things myself, but "man install-keymap" is perhaps relevant documentation. I found it by doing "apropos keyboard".

---

### Post by omiazad on 2006-11-15
Please do not suggest any command line, And there is no other layout available there. What should I do? Should I continue in that ougly way?

---

### Post by Zalbor on 2006-11-15
Wouldn't it work better if you used the simple US English layout instead? It does what you say because you chose international, and in some languages these symbols are used on letters.

---

### Post by Arndt on 2006-11-15
> **omiazad said:**
> Please do not suggest any command line, And there is no other layout available there. What should I do? Should I continue in that ougly way?

Then I won't suggest any command line.

But I do find for example these files:

/usr/share/keymaps/i386/qwerty/us-intl.iso01.kmap.gz
/usr/share/keymaps/i386/qwerty/us-intl.iso15.kmap.gz
/usr/share/keymaps/i386/qwerty/us.kmap.gz
/usr/share/keymaps/i386/qwerty/us-latin1.kmap.gz

---

### Post by kosack on 2006-11-15
You don't need any complicated command-line options...

From the "System" menu, choose "Preferences -> Keyboard"

In the "Layouts" tab, Push "Add" and add the "US English" layout. Move it to the top of the list, and the dead-keys will be disabled.

---

### Post by omiazad on 2006-11-16
> **kosack said:**
> You don't need any complicated command-line options...

From the "System" menu, choose "Preferences -> Keyboard"

In the "Layouts" tab, Push "Add" and add the "US English" layout. Move it to the top of the list, and the dead-keys will be disabled.

I only see US International. No other layout is available there.

---

