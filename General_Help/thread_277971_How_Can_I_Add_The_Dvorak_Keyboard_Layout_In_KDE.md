---
title: "How Can I Add The Dvorak Keyboard Layout In KDE?"
date: 2006-10-15
forum: General Help
---

### Post by dotancohen on 2006-10-15
How can I add the Dvorak keyboard layout to KDE? I see that there is a bugzilla entry on the subject, but I do not see how to add the files myself.

Thanks.

Dotan Cohen
[http://simplesniff.com/](http://simplesniff.com/)
[http://gmail-com.com/](http://gmail-com.com/)

---

### Post by roozbeh.daneshvar on 2008-02-12
To change the keyboard mapping on a per-session basis (it will revert once you logout), is by using the setxkbmap utility. To switch to dvorak using setxkbmap, you would type:

    ```
setxkbmap dvorak
```

To switch back to qwerty layout (try) type:

    ```
setxkbmap us
```

---

### Post by der_joachim on 2008-02-12
- Open System Settings from the menu
- Click Personal >> Regional & Language
- Click Keyboard Layout
- Choose 'U.S. English' from available layouts and click the Add button.
- Click the pulldown labeled 'layout variant' and choose 'Dvorak'. You can also choose to give your extra layout a label. That enables you to see your current layout. I labeled my layouts 'qw' and 'dv', meaning Qwerty and Dvorak. 
- Click 'Apply'. Your taskbar should show a flag or at least a label. Clicking it should switch layouts. You can configure the behaviour in the taw called 'Switching Options'.

Good luck.

---

### Post by spike9 on 2008-03-24
Thanks Joachim for your clear n00b friendly solution I have now adjusted my global key settings :guitar:

---

