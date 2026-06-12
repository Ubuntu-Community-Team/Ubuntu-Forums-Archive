---
title: "Script Help"
date: 2013-03-25
forum: General Help
---

### Post by stinkeye on 2013-03-25
I have a downloaded perl script that I use with conky to access gmail, that needs you to set your username and password within the script.
ie
```
$user="*[COLOR="#808080"]username[/COLOR]*"; #username for gmail account 
$pass="*[COLOR="#808080"]password[/COLOR]*";
```

I want the perl script to retrieve my password from gnome keyring instead of having it in the script.
I have a python script which can retrieve a password from gnome keyring.
The [**_[COLOR="#B22222"]python script[/COLOR]_**]("https://github.com/kparal/gkeyring#installation") is in my PATH and can be run in terminal to output my password with...
```
gkeyring --id 13 -1
```

So in the perl script I tried
$pass="*[COLOR="#808080"]`gkeyring --id 13 -1`[/COLOR]*";
but doesn't work.

What do I need to use so the $pass variable in the perl script uses the output of **gkeyring --id 13 -1**

PS I know nothing about perl or python.

---

### Post by schragge on 2013-03-25
Remove excessive quoting:
```
$pass=`gkeyring --id 13 -1`;
```

---

### Post by stinkeye on 2013-03-25
Aha... worked.
Thankyou.

---

