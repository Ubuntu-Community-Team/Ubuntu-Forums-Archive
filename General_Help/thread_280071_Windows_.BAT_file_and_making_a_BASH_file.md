---
title: "Windows .BAT file and making a BASH file?"
date: 2006-10-18
forum: General Help
---

### Post by emarkay on 2006-10-18
*Strange, my post didn't show up in "Faqs, Howto, Tips & Tricks" - Apparently one needs 100 posts to post there???  I repost it here, then, for assistance.  :)*

Taking a Windows .BAT file and making a BASH file...  
The ".SAV" files are files I have as "known good" templates, FYI.)

********
ORIGINAL:
*05-20-06 - MRK
CD\WINDOWS\APPLIC~1\MOZILLA\PROFILES\DEFAULT\yqubrztk.slt
DEL localstore.rdf
COPY LOCALSTORE.SAV localstore.rdf
COPY LOCALSTORE.SAV \SAFE
COPY *.BAK \SAFE
CD\MOZCACHE\Cache
ECHO y | DEL *.*
CLS

TRANSITIONAL:

[Will start with:
 #!/bin/bash]
*05-20-06 - MRK
[This would be: ### 05-20-06 - MRK]
CD\WINDOWS\APPLIC~1\MOZILLA\PROFILES\DEFAULT\yqubrztk.slt
[I know to use the CD command to get to the appropriate directory]
DEL localstore.rdf
[this becomes:  rm "#localstore.rdf#" - correct?
COPY LOCALSTORE.SAV localstore.rdf
[This would be: cp  LOCALSTORE.SAV localstore.rdf - correct?]
COPY LOCALSTORE.SAV \SAFE
[This would be: cp  LOCALSTORE.SAV /HOME?USERDIR/SAFE - correct?]
COPY *.BAK \SAFE
[This would be: cp  *.BAK /home/userdir/SAFE - correct??]
CD\MOZCACHE\Cache
[CD of course]
ECHO y | DEL *.*
[this would become: rmdir *.* ??]
CLS
[clear - correct?]
[finish with: exit - correct?]

PROPOSED?:

#!/bin/bash
### 05-20-06 - MRK]
cd /home/userdir/.mozilla/default/yqubrztk.slt
rm "#localstore.rdf#" 
cp  LOCALSTORE.SAV localstore.rdf
cp  LOCALSTORE.SAV /home/userdir/SAFE
cp  *.BAK //home/userdir/SAFE
cd /home/userdir/.mozilla/default/cache
rmdir *.*
clear
exit

******
I can then just make an icon of this file on the desktop and click it and it will run?
Do I have to set it to go back to any specific directory to make sure it doesn't 'foul up' anything?

Apolly loggies for the noob-ness.  :)

MRK

---

### Post by po0f on 2006-10-18
emarkay,

I don't know about not being able to post in the HOWTO section, but this is more of a support question than a how-to anyway.

I don't know why you are using hashes around the filename in your rm command ("rm "#localstore.rdf#")?  And you can replace "/home/userdir/" with "~/".  You don't *have* to exit your script, but it's nice to.  You shouldn't need to cd to a different directory after it's done, because if something goes wrong, I don't think changing the directory as the last command will make it all better.  ;)

To run the script, make sure it is executable (`chmod u+x myscript.sh` from a terminal) and you should be able to double-click it on the desktop.

---

### Post by emarkay on 2006-10-18
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
was my primary reference.  

Thanks.  Other than that it looks OK?

Also - I forgot to ask - how can I make it PAUSE between lines and DISPLAY the result of the last operation?  (so if I see a boo-boo on first run I can cancel - oh yea what kills a running script?)

---

### Post by po0f on 2006-10-18
emarkay,

You can add `sleep 5` between commands to pause for 5 seconds.  To kill the script, press Ctrl-C.

---

