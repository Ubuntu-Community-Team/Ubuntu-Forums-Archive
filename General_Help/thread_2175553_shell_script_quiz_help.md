---
title: "shell script quiz help"
date: 2013-09-19
forum: General Help
---

### Post by vonvic on 2013-09-19
Hi. I'm trying to make a shell script that will quiz the user. But I need a way to continue to a the next part of a test.
Here it is:
```
#!/bin/bash
clear
read -p "Hi $USER! Today, you'll be taking a test. Enter G to continue" response

if ( $response = "G" ); then

else
echo please enter G

fi
```

---

### Post by Vaphell on 2013-09-19
conditions use square brackets not parentheses
when you use *if *you have to have something in the *then *block, even if it's a do-nothing command :
*If* is a one time use, so once you have proper syntax you will get past *fi *either way

---

