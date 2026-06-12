---
title: "Flash files not functioning"
date: 2008-02-09
forum: General Help
---

### Post by Kourosism on 2008-02-09
After the recent update for Firefox (coinciding with a Gnash and non-free Adobe player) Flash files are suddenly doing some very strange things.

Flash videos (such as through the BBC iPlayer, or YouTube) simply won't work at all - nothing on the screen whatsoever. Other files (say, Scrabulous) will go utterly haywire with large blocks of colour filling a portion of the allotted area.

Any ideas as to what may be the cause? What other information can I give to help narrow it down?

---

### Post by forrestcupp on 2008-02-09
Well, you could try this.  In Synaptic, go to Settings->Repositories.  Click the Updates tab and check the boxes that say 'Pre-released Updates (gutsy-proposed)' and 'Unsupported Updates (gutsy-backports)'.  Then click the reload button and see if there is an update for flashplugin-nonfree.

---

### Post by HappyFeet on 2008-02-09
is there a reason you need both gnash and flash? try removing gnash. there's probably a conflict.

---

### Post by jan quark on 2008-02-09
gnash and flash together are known to cause conflicts
remove gnash and reinstall flash with this code
```

sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

---

### Post by Kourosism on 2008-02-09
Thanks guys.

This is what I did in the end:-

I removed both Gnash and Flash, and then reinstalled Flash through apt get.

Everything appears hunky dorey again now. Thank you all... never let it be said that Ubuntu forumites aren't quick to respond about problems!

---

### Post by offchance on 2008-06-11
scrabulous/google video/youtube will not work with gnash on firefox. since I'm running a g4 ppc I can't use nspluginwrapper (weird C dependencies). 

hopefully the gnash team will find an opensource solution to flash9 (or adobe will loosen their closed-source reigns). sadly, this means the death of ubuntu on this particular machine. if the g4's owner can't use such common sites as youtube with certainty then the whole laptop is, in practical terms, bricked.

---

