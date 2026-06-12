---
title: "Jupyter Notebook crash because of ca certificate change?"
date: 2017-06-15
forum: General Help
---

### Post by ppong828 on 2017-06-15
[COLOR=#24292E][FONT=-apple-system]Hi all, I'm a novice Ubuntu/linux user and no problems installing and using jupyter notebook. However, after installing Citrix receiver and some certificate permissions, I get the below error when I try to launch Jupyter Notebook.:[/FONT][/COLOR]
```
[I 14:39:54.593 NotebookApp] Writing notebook server cookie secret to /run/user/1000/jupyter/notebook_cookie_secret


PermissionError: [Errno 13] Permission denied: '/usr/local/lib/netscape/mime.types'
```
[COLOR=#24292E][FONT=-apple-system]After installing Citrix, I ran the below commands to since I was getting certificate errors when launching citrix from chrome. Notebooks that I had open crashed after I ran the updates for the certificates and I get the error above when I try to launch new ones.[/FONT][/COLOR]
```
sudo update-ca-certificates 
sudo ln -s /usr/share/ca-certificates/mozilla/* /opt/Citrix/ICAClient/keystore/cacerts/
sudo c_rehash /opt/Citrix/ICAClient/keystore/cacerts/
/opt/Citrix/ICAClient/util/configmgr &
```
[COLOR=#24292E][FONT=-apple-system]Any help would be appreciated. Thanks.[/FONT][/COLOR]

---

