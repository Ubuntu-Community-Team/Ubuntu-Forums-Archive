---
title: "[SOLVED] Firefox 3 beta is a joke"
date: 2008-04-27
forum: General Help
---

### Post by poliltimmy on 2008-04-27
Can someone tell me how to get rid of the firefox beta and install the regular release on Hardy? There is simply not enough add-ons

---

### Post by tribaal on 2008-04-27
One command:
"sudo aptitude install firefox2"

Hope this helps.

-Trib'

---

### Post by Fatal Equinox on 2008-04-27
go to applications> add/remove >   type in firefox... uncheck firefox 3 and check Firefox 2


i agree firefox 3 needs a little more tunning...

---

### Post by tseliot on 2008-04-27
I have moved this thread since it doesn't belong to the "programming talk" section.

Furthermore the title of this thread should be different e.g. "how can I install firefox 2?". Saying that something is a joke or that it sucks doesn't help at all.

---

### Post by poliltimmy on 2008-04-27
i get a message that says

 Cannot remove 'firefox-3.0'

One or more applications depend on firefox-3.0. To remove firefox-3.0 and the dependent applications, use the Synaptic package manager. will it automaticly uninstall the dependicies

---

### Post by sternkanz on 2008-04-27
so go into the Synaptic Package Manager (located under System -> Administration), click search, type in "firefox" and once it completes searching, find the firefox entry which has the version: "3.0~b5+nobinonly-", click on the green box beside it, and click "Mark for Removal". Then click the box beside firefox-2 (which should be directly underneath the firefox entry you just marked for removal) and select "Mark for Installation"

Then click apply at the top.

Enjoy.

P.S. I do like firefox 3, but releasing an operating system with a beta version of anything is not a good idea in my opinion.

---

### Post by poliltimmy on 2008-04-27
Great guys! Thanks!!!! I'm not sure why one way or the other would not work. I had to uninstall using SPM and had to install FF2 in Add and Remove. Kinda wierd. Anyway it's done. Whooo hooo!!! And I apologize for the negative title.

---

### Post by sternkanz on 2008-04-27
Glad you got it working!

You could always edit the title ;)

Edit your first post iirc. ;)

---

### Post by poliltimmy on 2008-04-27
I spoke too soon. This link (off another thread)is how it must be done. Otherwise you will not be able to install aded-ons  
[http://ubuntuforums.org/showpost.php?p=4745743&postcount=1](http://ubuntuforums.org/showpost.php?p=4745743&postcount=1)

                                                    Timmy

---

