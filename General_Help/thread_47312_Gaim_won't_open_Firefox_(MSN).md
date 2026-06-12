---
title: "Gaim won't open Firefox (MSN)"
date: 2005-07-08
forum: General Help
---

### Post by darkmatter on 2005-07-08
I have gaim set up to notify me of new mail for my Hotmail account, and it had work perfectly until I upgraded Firefox.

Now when I click 'Open Mail', nothing happens. I've googled for a solution (and searched the forums) to no avail.

Does anyone know the solution to this problem?

Thanks.

---

### Post by cvmostert on 2005-09-23
[QUOTE=darkmatter]I have gaim set up to notify me of new mail for my Hotmail account, and it had work perfectly until I upgraded Firefox.

Now when I click 'Open Mail', nothing happens. I've googled for a solution (and searched the forums) to no avail.

Does anyone know the solution to this problem?

Thanks.[/QUOTE]
 I have no idea what your problem could be... but my firefox opens and does not log into hotmail... some .net problems... you wouldnt know what might be wrong?

all the best

---

### Post by phex on 2005-09-23
Perhaps the upgrade has overwritten your preferences or the firefox command has been changed. 
Go in the menu to "System", "Pereferences", "Preferred Applications". Then look what is standing in the Web Browser tabs textfield and try if the given command there can be executed in the terminal. if not try to find the command to start firefox and write the appropriate command in the textfield of the Web Browser tab.
gl

---

### Post by bountonw on 2006-02-16
Using this thread I got gaim to open firefox. (I use yahoo messenger.)  But it just opens my home page in firefox instead of opening my yahoo mail.  Any ideas?

---

### Post by bountonw on 2006-02-19
In the old world of yahoo messenger on Windows XP, when I received a new message and clicked on the box, it would open my yahoo mail in a new firefox tab, automatically.

Now, with gaim, I click on the new mail message and it opens a new firefox window with my home page.  Where do I go to adjust the setting for this?

---

### Post by bountonw on 2006-03-01
Still in the dark on this.  It is not only gaim, but e-mails in evolution also.  If I click on a link, it opens the firefox home page but will not force the link.  I then have to copy/paste in order to open the web page.

Help!!:)

---

### Post by Mustard on 2006-03-01
Are you using the Firefox from the repositories or Firefox 1.5.x (installed manually) ?

Do you have the custom command selected in System>>Preferences>>Preferred Applications?
If so what have you got in that field?

I'm using Firefox 1.5.x and I have this in the custom field..

```
firefox %s
```

---

### Post by bountonw on 2006-03-01
Thank you.

I just had

```
firefox
```
in preferred applications.

Changing to 

```
firefox %s
```

Fixed the problem.

Thank you.

---

