---
title: "Can't update Eclipse"
date: 2008-05-13
forum: General Help
---

### Post by revchris on 2008-05-13
I have this error when I go to manage configuration:

/usr/lib/eclipse/
[INDENT] Eclipse Project SDK 3.2.2.r322_v20070104-OlsEN15kdLend_i [/INDENT]

[INDENT][INDENT]Included feature "Eclipse Platform" version "3.2.2.r322_v20070119-CXMbUe9K_WF26uA" contains problems.

Included feature "org.eclipse.platform.source_3.2.2.r322_v20070119-CXMbUe9K_WF26uA" is missing.

Included feature "Eclipse Java Development Tools" version "3.2.2.r322_v20070104-R4CR0Znkvtfjv9-" contains problems.

Included feature "org.eclipse.jdt.source_3.2.2.r322_v20070104-R4CR0Znkvtfjv9-" is missing.

Included feature "Eclipse Plug-in Development Environment" version "3.2.1.r321_v20060823-6vYLLdQ3Nk8DrFG" contains problems.

Included feature "org.eclipse.pde.source_3.2.1.r321_v20060823-6vYLLdQ3Nk8DrFG" is missing.
[/INDENT][/INDENT]

anyone have any ideas on what I need to do?

Thanks

//Solved

---

### Post by revchris on 2008-05-15
Solved

---

### Post by AcidHawk on 2008-05-15
Would you mind telling us what you did to solve the problem?

Don't worry if it was user error, if it wasn't for user error I'd actually know what I was doing... ;)

---

### Post by ev45ive on 2008-05-27
Hate such threads...

If someones bothered to write "Solved", why couldn't he write even ONE SENTENCE HOW HE DID IT!?

:|

ps. Would be nice if someone could post here info How to solve it.

---

### Post by ev45ive on 2008-05-27
Seems to work :
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5054984](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=5054984)

Help > Software Updates > Find and Install... >
(*) Search for new features > Next >
[x] Europa Discovery Site

Select missing things and if you see error, that there is dependency missing press "Select Required", and eclipse will automaticly select dependent stuff.

Europa Discovery Site seems to have all missing stuff. If you do not have it in eclipse repos, then add this : [http://download.eclipse.org/releases/europa/](http://download.eclipse.org/releases/europa/)

Then it should work for you too. ;)

---

### Post by revchris on 2008-05-27
I downloaded it from Eclipse.org and extracted it into my home directory, instead of installing it from the repositories.

---

