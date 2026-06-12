---
title: "Memaid on hardy"
date: 2008-04-28
forum: General Help
---

### Post by acl123 on 2008-04-28
I know this app is outdated but I still like it.
Has anyone got it to work on Hardy? I get the following error:
```

  File "/usr/bin/memaid-pyqt", line 11, in <module>
    from pyqt_memaid.main_dlg import *
  File "/usr/lib/python2.5/site-packages/pyqt_memaid/main_dlg.py", line 10, in <module>
    from import_dlg import *
  File "/usr/lib/python2.5/site-packages/pyqt_memaid/import_dlg.py", line 9, in <module>
    from memaid_core import *
  File "/usr/lib/python2.5/site-packages/pyqt_memaid/memaid_core.py", line 653, in <module>
    class XML_Importer(saxutils.DefaultHandler):
AttributeError: 'module' object has no attribute 'DefaultHandler'

```

---

### Post by greg.hagen on 2008-04-30
Exact same thing here on Hardy 64-bit.

---

### Post by greg.hagen on 2008-04-30
Fixed it. There's something wrong with Hardy's python-xml package. I guess it doesn't support something that is in the much older pyxml package. Installing PyXML-0.84 from source will allow memaid-qt to start.

```

# install dependencies
sudo apt-get install python2.5-dev

# download and unzip pyxml
wget http://superb-west.dl.sourceforge.net/sourceforge/pyxml/PyXML-0.8.4.tar.gz
tar -xzf ./PyXML-0.8.4.tar.gz
cd PyXML-0.8.4

# build and install pyxml
python setup.py build
sudo python setup.py install

# remove temporary files, be careful where you point that loaded rm -rf!
cd ..
rm -rf ./PyXML-0.8.4

```

Memaid-qt should work fine after that.

---

### Post by acl123 on 2008-05-01
Great thanks, it works - excellent, clear instructions btw

---

### Post by Kaneda on 2008-06-28
Thanks!  This helped me too!  (Although I'm using it for Mnemosyne, not memaid)

---

### Post by bpont on 2008-07-04
Delete

---

