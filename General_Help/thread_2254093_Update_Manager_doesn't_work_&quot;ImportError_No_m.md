---
title: "Update Manager doesn't work &quot;ImportError: No module named 'codecs'&quot;"
date: 2014-11-25
forum: General Help
---

### Post by alghamedh on 2014-11-25
Hello,

Dear awesome community


Each time I try ```
sudo update-manager
``` it returns

 > Fatal Python error: Py_Initialize: Unable to get the locale encoding
Traceback (most recent call last):
  File "/usr/lib/python3.4/encodings/__init__.py", line 31, in <module>
ImportError: No module named 'codecs'



I tried the following with the help of my brother schultza  from the IRC boys.:
-sudo apt-get update                                                                                         [COLOR=#008000]// no errors[/COLOR]
-sudo apt-get clean                                                                                          [COLOR=#008000]// no errors[/COLOR]
-sudo apt-get install -fy                                                                                    [COLOR=#ff0000]// same error[/COLOR]
-sudo apt-get install --reinstall python3                                                           [COLOR=#ff0000]// same error                        [/COLOR]
-sudo apt-get install --reinstall dpkg apt update-manager python[COLOR=#ff0000]                         // same error[/COLOR] 
-sudo apt-get autoremove [COLOR=#ff0000]                        // same error[/COLOR]
-sudo apt-get upgrade[COLOR=#ff0000]                        // same error[/COLOR]
-sudo apt-get install --reinstall python3.4 [COLOR=#ff0000]//E: Internal Error, No file name for python3.4:amd64[/COLOR]
-sudo apt-get install  python3.4  [COLOR=#ff0000]// same error (Dependency problems )[/COLOR]
-python --version [COLOR=#008000]//Python 2.7.6[/COLOR]


And I didn't modify the "__init__.py" file .



Thanks for being Awesome
Your brother Majed

---

