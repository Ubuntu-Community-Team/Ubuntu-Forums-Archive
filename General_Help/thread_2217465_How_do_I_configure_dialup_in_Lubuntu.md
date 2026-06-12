---
title: "How do I configure dialup in Lubuntu"
date: 2014-04-17
forum: General Help
---

### Post by jacatone on 2014-04-17
Seems Lubuntu and Puppy Linux are the only distros left that'll install on older P4 hardware. Puppy Linux has an app (Pupdial) for using dialup but don't see anything in Lubuntu. I have a Linux compliant 56k hardware modem. Anyone know how to configure this thing? Thanks.

---

### Post by SeijiSensei on 2014-04-17
If you're trying to connect to a server running PPP to set up an Internet connection, start with  [this](http://www.cyberciti.biz/tips/linux-configure-modem-to-connect-to-the-internet-using-a-ppp-dialup-account.html).  For more details: [http://www.tldp.org/HOWTO/PPP-HOWTO/](http://www.tldp.org/HOWTO/PPP-HOWTO/).

For a dialup shell connection, I used [Minicom](http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html) back in the day.

---

### Post by monkeybrain20122 on 2014-04-17
run 
```
sudo pppoeconf
```

Enter crendentials and connect.

---

