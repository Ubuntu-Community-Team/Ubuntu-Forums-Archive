---
title: "aMSN auto strart 2 account"
date: 2008-05-03
forum: General Help
---

### Post by randomAccess on 2008-05-03
How can I autostart 2 aMSN accounts. I tried setting 2 aMSNs start with session but only the 1st one starts. I also tried the same with specifying the accounts such as 
```
amsn email_address
```
In this case, only the 1st amsn starts. 

Then I tried with console 
```
amsn email_address && amsn 2nd_email
```
but now the 1st amsn starts, and the 2nd one starts only if I close the 1st amsn. 

ps. Manual start is not an issue here

---

### Post by randomAccess on 2008-05-04
Ok I made a little console script that starts both account. It looks like this
```

echo "Starting 1st aMSN"
amsn xxxxxxx@hotmail.com &
echo "Starting 2nd aMSN"
amsn xxxxxxx@hotmail.com &
echo "Done."
```

It works flawlessly in console. But when I add it to start on boot (system->prefs->session) it starts 3 aMSNs. :confused::confused:

Anyone guesses why's this happening?

---

