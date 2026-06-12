---
title: "apturl not working"
date: 2021-07-21
forum: General Help
---

### Post by guybrushthreepwoods on 2021-07-21
Hi,
I know the subject has already been treated multiple times but none of the fixes worked in my case so...
I'm on Ubuntu 21.04 and use Firefox 89.0.2.

When I click on an apturl link such as : apt://gimp, and choose to open it with /bin/apturl, then nothing happens...

In Firefox about:config, I have set the recommended entries :
[LIST]
[*]**network.protocol-handler.app.apt** as string to **/usr/bin/apturl** 
[*]   **network.protocol-handler.app.apt+http** as string to **/usr/bin/apturl** 
[*]   **network.protocol-handler.warn-external.apt** as boolean to **false** 
[*]   **network.protocol-handler.warn-external.apt+http** as boolean to **false** 
[*]   **network.protocol-handler.expose.apt** as boolean to **false** 
[/LIST]

What I already tried :

[LIST]
[*]Purge/Reinstall apturl and apturl-common 
[*]Purge/Reinstall Firefox 
[*]Try with another browser (Chrome and Chromium) 
[/LIST]

None of this make apturl link work in the browser. However, when I use apturl in a terminal, it works fine. Such as :
```

apturl apt://gimp

```

I don't know what else can I check/fix...

Thanks

---

