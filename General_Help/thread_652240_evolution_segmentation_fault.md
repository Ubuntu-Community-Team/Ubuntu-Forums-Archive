---
title: "evolution segmentation fault"
date: 2007-12-28
forum: General Help
---

### Post by kefurd06 on 2007-12-28
evolution opens and then immediately disappears. when i run it from terminal, i get:

```

kevin@dv9000:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:6264): DEBUG: mailto URL command: evolution %s
** (evolution:6264): DEBUG: mailto URL program: evolution
(evolution:6264): e-data-server-DEBUG: Loading categories from "/home/kevin/.evolution/categories.xml"
(evolution:6264): e-data-server-DEBUG: Loaded 29 categories
Segmentation fault (core dumped)
kevin@dv9000:~$ 

```

I read a related thread that listed some commands to fix it, including reinstalling, but i can't lose my calendars!! can anyone help? thanks. i don't know if it matters, but the first time evolution started doing this was when i added it as a launcher to my avant window navigator.

---

### Post by p_quarles on 2007-12-28
Reinstalling Evolution shouldn't cause any data loss. The vast majority of programs store data in your home folder, and these files don't get removed by the package manager. 

If you're not 100% confident about this, you can use your file manager to look for your calendar files. You will need to click on "show hidden files", and then go to the directory marked .evolution. Chances are, you will find the calendar files, and you'll then be able to make backups.

Also, I haven't used Evolution much, but it should have an "Export" function that would allow you to backup your e-mail, calendars, etc.

---

### Post by kefurd06 on 2007-12-29
fixed it. here's basically what i did:

1. backed up .evolution folder from home
2. first time i tried i couldn't uninstall evolution from add/remove. so i reinstalled from synaptic, which didn't work.
3. i uninstalled and reinstalled from synaptic. didn't work.
4. uninstalled from add/remove and this time it worked. i then reinstalled from add/remove.
5. evolution came up fine. closed it, deleted .evolution folder, put my old .evolution folder in its place, started it and everything is back to normal.

weird. thanks guy.

---

### Post by castironpants on 2008-01-10
I have the same problem, but you solution didn't work for me. Are there any other ideas?

---

### Post by stchman on 2008-01-10
> **castironpants said:**
> I have the same problem, but you solution didn't work for me. Are there any other ideas?

A friend of mine had this same problem.  Apparently there was an email that had a some weird characters in it.  He went to the web interface and deleted the offending email.

---

### Post by castironpants on 2008-01-10
I don't use it for mail, in fact I have the account disabled and no mail in my inbox.

---

