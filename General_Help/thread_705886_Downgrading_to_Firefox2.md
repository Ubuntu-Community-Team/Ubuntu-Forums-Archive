---
title: "Downgrading to Firefox2"
date: 2008-02-23
forum: General Help
---

### Post by zirtik on 2008-02-23
Hi,

I have asked this question on the Newbies section before but couldn't get an answer so I'm asking it here once again. I am on a Ubuntu Hardy 64 bit and I have been using out without any problems for quiet a while. Last week I upgraded to Firefox3 but didn't like it so I want to downgrade to Firefox2. When I remove it using Synaptic however, Firefox2 does not automatically install. When I try

```
sudo apt-get install Firefox
```

Firefox3 is installed again. I think I need to change some settings of the Software Sources but I am not sure. 

I'd really appreciate any help, thanks in advance.

---

### Post by hyperair on 2008-02-23
Could you try closing all Firefox 3.0 windows, then running "firefox" from the run dialog or terminal? And how did you install Firefox 3.0 in the first place? As far as I know, if you've installed the firefox-3.0 package, it co-exists with Firefox 2.0 peacefully.

---

### Post by zirtik on 2008-02-23
When I run "firefox" from the terminal, Firefox3 launches again. I installed it using Synaptic as an update.

---

### Post by hyperair on 2008-02-23
Huh, yeah you're right. Good lord, I never noticed. I've been using the daily build after all. I'll search around and see if I can find anything. I'll post back if I find anything.

EDIT: Found something: [http://ubuntuforums.org/showthread.php?p=4368577#post4368577](http://ubuntuforums.org/showthread.php?p=4368577#post4368577)

---

### Post by zirtik on 2008-02-23
Thank you, worked like a charm!

---

### Post by hyperair on 2008-02-23
Glad to be of help.

---

