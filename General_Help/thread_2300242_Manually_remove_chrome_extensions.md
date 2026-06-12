---
title: "Manually remove chrome extensions"
date: 2015-10-24
forum: General Help
---

### Post by UncleMonty on 2015-10-24
How can I manually remove a chrome extension? I've installed an extension which locks you out of the 'settings' 'more extensions' etc. 

I'm using ubuntu 14.04 (64 bit). I'm using the latest version of Chrome (but obviously have no way of checking which one it is...)

---

### Post by howefield on 2015-10-24
The nuclear option would be to delete or rename your chrome profile in ~/.config/google-chrome (I think that's the path - I use chromium so am not completely sure).

If that is a bit strong for you, in the same folder find the preferences file and change the "state" for the extension to 0 - it should be set to 1 if currently active.

Alternatively, you will also find the extension folder (assuming the same path as chromium) in 

```
/Data/Data_Store/google-chrome/Default/Extensions
```

The folders in there will likely have "random" names such as "nmmhkkegccagdldgiimedpiccmgmieda" which you can marry up with info taken from the preferences file to help you locate which file is which extension. You could try copying the folder some place else. All this should be done with chrome closed.

---

