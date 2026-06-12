---
title: "Ubuntu Virtualbox 5.2 Instillation Problem"
date: 2017-11-26
forum: General Help
---

### Post by deorez on 2017-11-26
Hi,

I would like to use genymotion and in order to do that I've installed virtualbox 5.2 but it has never worked and now I can't even install anything. I got this error message.

```
The following packages have unmet dependencies:
 vim : Depends: vim-runtime (= 2:7.4.1689-3ubuntu1.2) but it is not going to be installed
 virtualbox-ext-pack : Depends: virtualbox (>= 5.0.40-dfsg-0~) or
                                virtualbox-5.0 but it is not installable
                       Depends: virtualbox (< 5.0.40-dfsg-z) or
                                virtualbox-5.0 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

and when I try to remove virtualbox with the command: sudo aptitude purge virtualbox

```
Removing virtualbox-ext-pack (5.0.40-0ubuntu1.16.04.1) ...
/var/lib/dpkg/info/virtualbox-ext-pack.prerm: 4: /var/lib/dpkg/info/virtualbox-ext-pack.prerm: vboxmanage: not found
dpkg: error processing package virtualbox-ext-pack (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 virtualbox-ext-pack
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed to perform requested operation on package.  Trying to recover:
```

Thanks for help.

---

### Post by tachyon-01 on 2018-04-10
After trying


 [B]sudo apt-get update                                           

[/B]

 and


 **sudo dpkg --configure  -a**

 and
 [B]sudo apt-get install -f


[/B]

 If the problem of a broken package still exist , the solution is to **edit the dpkg status** file manually.


  
[LIST=1]
[*]$ **sudo gedit /var/lib/dpkg/status** 
[*]Locate the corrupt package, and remove the whole block of information about it and save the file. 
[/LIST]

then 
**sudo dpkg --configure  -a**

---

### Post by tachyon-01 on 2018-04-10
i had this problem ..... try the above solution of manually editing dpkg/status file  ..... after this it won't show any error in your terminal .

---

### Post by cruzer001 on 2018-04-10
You cannot use 5.0 extension pack with a 5.2 install.  They must match.

---

### Post by SeijiSensei on 2018-04-10
This thread was started last November.  I doubt the original poster is still waiting for an answer.

---

### Post by cruzer001 on 2018-04-10
Got me :) thanks

---

