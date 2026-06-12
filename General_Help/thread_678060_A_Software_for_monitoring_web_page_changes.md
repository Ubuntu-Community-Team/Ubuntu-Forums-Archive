---
title: "A Software for monitoring web page changes"
date: 2008-01-25
forum: General Help
---

### Post by megandy on 2008-01-25
Hi,

I'm looking for a gnome tool to monitor web pages. If the web page changes the tool should alert me. I've used a tool named "C4U" for Windows, which was great. Now, I'm searching something appropriate for my ubuntu :rolleyes:.

Requirements are:
- Highlighting the changes (diffs to last page)
- Navigation from one change to another
- Scheduled configuration
- customization for notification of changes. e.g. at least 2 blocks of text should differ or 3 images
- Residing in the notification (systray) area would be nice

Since not every page offers RSS, it's a very important tool to avoid manual polling of web pages.

Are there tools like that for gnome or kde?

Thanks in advance!

---

### Post by diaa on 2008-01-25
There's an extension for Firefox that does a subset of what you're asking for, I've used it for a while, it's called *Page Update Checker* and you can find it at [https://addons.mozilla.org/en-US/firefox/addon/920](https://addons.mozilla.org/en-US/firefox/addon/920)

---

### Post by megandy on 2008-01-26
Nice tool! Thank you. I miss only an integration with gnome without using firefox. Any other suggestions?

---

### Post by diaa on 2008-01-26
> **megandy said:**
> Nice too! Thank you. I miss only an integration with gnome without using firefox. Any other suggestions?
I don't know about others but I did a quick search via Synaptic and found *websec*
Here's its description:
> 
A visual Web page monitoring software. However, it goes
 beyond the normal functionalities offered by such software. Not only
does it detect changes based on content analysis (instead of date/time
stamp or simple textual comparison), it will email the changed page to
you with the new content highlighted.
You should be able to install it by running the command
```
sudo apt-get install websec
```

---

