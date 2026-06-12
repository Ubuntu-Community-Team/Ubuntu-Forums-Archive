---
title: "[SOLVED] Where does the Firefox executable hide?"
date: 2008-06-18
forum: General Help
---

### Post by Stolea on 2008-06-18
I have an old windows program called Powermarks I am very fond of and have as yet not found a Linux replacement for. It keeps track of my bookmarks. I have installed it under Wine and it starts and runs just fine. When you select a bookmarked address and click on it it is supposed to start Firefox. It did for the first couple of times but now doesn't. Its like it can't find the Firefox executable. There is a part in the Powermarks options that lets me define the location of the Firefox executable. Where would that executable live in Ubuntu, or what is its counterpart?
Sorry if this sounds strange, but I am still on learner plates

---

### Post by HalPomeranz on 2008-06-18
Generally, you can find out the path to an executable by running "which <programname>" at the command line.  For example:

```

$ **which firefox**
/usr/bin/firefox

```

---

### Post by Norwal on 2008-11-18
> **HalPomeranz said:**
> Generally, you can find out the path to an executable by running "which <programname>" at the command line.  For example:

```

$ **which firefox**
/usr/bin/firefox

```

Thanks

---

### Post by nrundy on 2011-07-19
I ran the "Which" command and it reported /usr/bin for my firefox program. All I see in the /usr/bin though is a firefox file labeled as type: "Link to shell script"

Shouldn't there be a type: "executable"

Where is the executable?

---

### Post by Grenage on 2011-07-19
> **nrundy said:**
> I ran the "Which" command and it reported /usr/bin for my firefox program. All I see in the /usr/bin though is a firefox file labeled as type: "Link to shell script"

Shouldn't there be a type: "executable"

Where is the executable?

It will probably be called firefox-bin, and be stored in /usr/lib/firefox-5.0/; the script references that executable file.

---

