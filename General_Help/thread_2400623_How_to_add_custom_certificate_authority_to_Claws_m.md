---
title: "How to add custom certificate authority to Claws mail?"
date: 2018-09-07
forum: General Help
---

### Post by &amp;KyT$0P# on 2018-09-07
I would like to experiment with Claws mail a bit.  I have a local testing server for exactly this sort of purpose.  My server's security certificate is signed with a custom CA, which I need to import into Claws.  But I can't find where to do this.

How to add a custom certificate authority to Claws mail?

---

### Post by &amp;KyT$0P# on 2018-09-09
I figured it out.  Turns out you don't do this inside Claws mail.  It uses the OS certificates.  So the solution is to add my CA to the system.

1) Copy the (.pem) CA certificate into [FONT=Courier New]/usr/local/share/ca-certificates[/FONT] , changing the .pem extension to .crt -
```
sudo cp -v [COLOR="#FF0000"]mycert[/COLOR].pem /usr/local/share/ca-certificates/[COLOR="#FF0000"]mycert[/COLOR].crt
```

2) run
```
sudo update-ca-certificates
```

Now Claws says my server's certificate has "Signature status: Correct".

---

