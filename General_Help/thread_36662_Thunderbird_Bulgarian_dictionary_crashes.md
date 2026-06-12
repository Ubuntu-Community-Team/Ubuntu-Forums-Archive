---
title: "Thunderbird Bulgarian dictionary crashes"
date: 2005-05-24
forum: General Help
---

### Post by brickbat on 2005-05-24
Hi, I tried installing the myspell dictionary for Thunderbird through the repository and it kept crashing thunderbird when selecting it.

For others with this problem, here is the temporary fix:

1. Uninstall the dictionary via synaptic

2. Go to the downloads page for Thunderbird dictionary files.

3. Download the dictionary you want and save it.  Don't try to install it.

4. Close any Thunderbird windows

5. Go to a terminal and type
sudo mozilla-thunderbird

If you try to install the extention with Thunderbird running normally, it will give you an "access denied" error.

6. Go to tools/extensions and select install

7. Find the file you downloaded and select it

8. When you restart Thunderbird, you should have a working dictionary.

ciao
bb

---

