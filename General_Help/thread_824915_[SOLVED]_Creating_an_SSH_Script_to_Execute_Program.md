---
title: "[SOLVED] Creating an SSH Script to Execute Programs"
date: 2008-06-10
forum: General Help
---

### Post by azurepancake on 2008-06-10
I have a system running Ubuntu server and another running Ubuntu desktop. I am monitoring the server from my Ubuntu desktop system with Conky by tunneling X over SSH.

This means that every time I want to start up Conky remotely, I need to open up a terminal and type..

```

ssh -X 192.168.1.100
<enter password>
conky

```

Is there anyway to pull this off, so it is completely automated with no terminals? I am new to BASH scripts and wrote a very simple one, called "remote_script.sh" ..

```

#!/bin/bash
ssh -X 192.168.1.100
conky

```

I then made a launcher and put the file "remote_script.sh's" path in the command form.

When I click on the launcher, it prompts me for the password. I enter in the password and nothing happens. I was hoping it would go on to load Conky, but that doesn't seem to be whats happening. 

Am I doing something wrong? If anyone has any advice, I'd greatly appreciate it.

Thank you.

---

### Post by Gerlads Mod on 2008-06-10
Did you use ```
chmod u+x remote-script.sh
```

---

### Post by HalPomeranz on 2008-06-10
You simply want:

```

ssh -X 192.168.1.100 conky

```

This means "log into 192.168.1.100 (with X forwarding enabled) and run the command conky".

---

### Post by azurepancake on 2008-06-10
> **HalPomeranz said:**
> You simply want:

```

ssh -X 192.168.1.100 conky

```

This means "log into 192.168.1.100 (with X forwarding enabled) and run the command conky".

That does the trick! Thanks a lot.

---

