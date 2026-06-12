---
title: "Help getting rid of (i think) saved searches in Thunderbird pop"
date: 2022-05-20
forum: General Help
---

### Post by Neon John on 2022-05-20
Ubuntu mate 21.1  
Kernel Linux 5.13.0-41-generic x86_64
MATE 1.26.0

In Thunderbird there are little arrowheads to the left of my "sent" directory and several more.  They are blocking the directory and there appears to be no way to get rid of them. 

[ATTACH=CONFIG]290494[/ATTACH]

I've spent a better part of a week on this so any help is greatly appreciated.
Thanks
John

---

### Post by norobro on 2022-05-21
Note: this will get rid of all of the folder icons.

First, you need to create a file named userChrome.css in the chrome directory of your default profile. Create the directory if it doesn't exist. Paste the following lines into the file:```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); 

treechildren::-moz-tree-image(folderNameCol) {
  list-style-image: none !important;
  margin-right: 0px;
  margin-left: -15px !important;
}

```In order for the css to work you have to modify a config setting. Select Edit->Preferences->Config Editor... 
Then in the search bar enter toolkit.legacy and change the setting to true.

My css file:```
$ cat ~/.thunderbird/ess986jy.default/chrome/userChrome.css 
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); 

treechildren::-moz-tree-image(folderNameCol) {
  list-style-image: none !important;
  margin-right: 0px;
  margin-left: -15px !important;
}

```

---

