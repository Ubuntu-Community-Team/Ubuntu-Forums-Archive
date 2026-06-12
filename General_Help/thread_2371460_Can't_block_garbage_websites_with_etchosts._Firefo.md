---
title: "Can't block garbage websites with /etc/hosts. Firefox and chrome ignore it."
date: 2017-09-14
forum: General Help
---

### Post by link626 on 2017-09-14
my /etc/hosts file looks like

127.0.0.1 garbage1.com
127.0.0.1 toomanypopups.com


but both firefox and chrome ignore the file, so they still open the garbage websites.

How do I make the browsers obey the hosts file before anything else?


I'm using 16.04

---

### Post by SeijiSensei on 2017-09-14
Are you entering "garbage1.com" or "www.garbage1.com"?  They're not the same; the latter won't match the /etc/hosts file above.  For that you need to use aliases
```

127.0.0.1     garbage1.com      www.garbage1.com something-else.garbage1.com
```

In fact, you can combine all your redirections into one line
```

127.0.0.1     garbage1.com      www.garbage1.com toomanypopups.com www.toomanypopups.com
```

Note that pop-ups often don't come from the server which displays the main page.

To make sure things are working correctly, open a Terminal and type the command "ping garbage1.com".  It should report it's trying to connect to 127.0.0.1.  Then try the other names.

If you really want to control stuff like this, take a look at Ghostery, an add-on for Firefox and, I believe, some other browsers as well.

---

### Post by &amp;KyT$0P# on 2017-09-14
> **link626 said:**
> How do I make the browsers obey the hosts file before anything else?
See my posts [here]("https://ubuntuforums.org/showthread.php?t=2330221") for a better way to achieve this.

---

