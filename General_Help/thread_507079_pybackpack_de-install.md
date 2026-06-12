---
title: "pybackpack de-install"
date: 2007-07-22
forum: General Help
---

### Post by dennus on 2007-07-22
I have downloaded PyBackPack and extracted the files in a TMP directory. Then I've installed it using "python setup.py install". It all works fine, it is put in System -> Administration. But it won't start. When I run it in a terminal it says "ImportError: No module named rdiff_backup.Main". So, I don't know what to do with it now. I think I want to de-install it. But I don't know how to?

edit;
I've solved it!  Seems rdiff-backup was never properly installed.

```
sudo apt-get install rdiff-backup
```

did the trick...

---

