---
title: "seti boinc"
date: 2007-11-10
forum: General Help
---

### Post by mahiyar on 2007-11-10
In the last install of Fiesty I used folding@home, this time I decided to run Seti@home using Boinc. Install and everything else went fine, however I have just two questions 1) In the BOINC menu none of the browser buttons are working. Somewhere the enviroment variable needs to be fiddled, can any one tell me where? 2) There are conflicting reports on tne net, while some say that the graphics is on for linux some say other wise, for Ubuntu what is true?

---

### Post by HermanAB on 2007-11-10
Hmm, there are about 2 people in the world that runs boinc.  I once installed it just to answer some poor dude's question and back then it basically just worked.  You'll have to go to the boinc web site and ask there - look for a mailing list to subscribe to.

Cheers,

Herman

---

### Post by mahiyar on 2007-11-10
For the two people concerned here is how to start your browser links

In the Linux version of BOINC Manager, if you try to click on the links to the project web pages and you get an error message about not being able to find BROWSER or BROWSER not being set then you need to do the following - 
 edit /etc/profile to include the following -
  BROWSER="/path/to/browser"
 export BROWSER
  - where /path/to/browser is the executable path to your browser. To find out what this is open a terminal window and type whereis browser - so if your browser is firefox you would type whereis firefox. The result is your executable path, which maybe something like /usr/local/bin/firefox.
 In this case the exact code you would add to /etc/profile would be -
  BROWSER="/usr/local/bin/firefox"
 export BROWSER



I still wonder about the graphics.

---

### Post by mac.ryan on 2008-02-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/72192](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/72192) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				"2 people" is a bit of underestimation for the **1,272,113 ACTIVE** users... as of today and the around 1.100.000 at the time of the original post...:)
([http://www.boincsynergy.com/stats/index.php](http://www.boincsynergy.com/stats/index.php))

Anyhow. What it turned out to be true for me (boinc version 5.10.8 x86_64-pc-linux-gnu installed from the repos) is that **the graphics do work**, but require a little hack:

```
sudo xhost +si:localuser:boinc
```

Of course the graphics only work for those projects that provide such functionality (seti, rosetta, a few on "the world community grid"...), otherwise the button will remain grayed out.

More info in the link to bug I added to this post.
Cheers!

---

