---
title: "Update Manager"
date: 2013-04-18
forum: General Help
---

### Post by arvadawest on 2013-04-18
Good day.  Recently, I have been recently some Updates that state that certain updates cannot be authenticated, then it states below that the exact updates are authentic.  I (we) are concerned about this.  Why would it say the same update is not authentic then below say it is?  Can anyone provide insight?  Thank you for your help.  -aw

---

### Post by blackbird34 on 2013-04-18
If you have installed any PPAs (personal package archives), they occasionnally cause this message to pop up. Some PPAs forget to authenticate themselves properly; this doesn't stop you installing stuff from them, but it is (quote) "at your own risk". If you read about the PPA on a reputable or well known site like webupd8.org it should be OK, but you have been warned, it is your problem if something goes wrong.

The contradiction just shows that different components of a given program get their information from different sources.

---

### Post by arvadawest on 2013-04-18
Thanks for replying Blackbird.  I'm sorry, but I am a newbie to this and I have no idea whether I installed a PPA or not.  Do you or anyone know how I can find this out and can it be removed?  Please keep in mind, I'm very weak on Linux/Ubuntu.  With serious health situations, I'm trying the best I can.  You have me concerned as I am not sure what is at risk and how to fix, find, or undo anything I might have done.  I only installed updates given to me. I appreciate any help.  Thanks.  -aw

---

### Post by papibe on 2013-04-18
Hi arvadawest.

Could you open a terminal, run this command and post back its results?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

