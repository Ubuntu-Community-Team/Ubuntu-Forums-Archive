---
title: "&quot;Simple&quot; sendmail ... with colon &quot;:&quot; in body"
date: 2018-11-17
forum: General Help
---

### Post by silverspr on 2018-11-17
HI, this is driving me to drink...I've googled high and low:

I want to include a colon after the word Ubuntu in a piped sendmail that is part of a script:

echo "Subject: The WAN IP has changed
The WAN IP on Ubuntu: $CURRENT_IP $(date +%F)" | sendmail -f ${FROM} ${TO}


I've tried escaping with \:, ":", "\:"  Nothing seems to work, is the only way to cat a txt file?

ubuntu 16.04.5

thanks for your help

---

### Post by SeijiSensei on 2018-11-18
What error does it throw?

You might try "\\\:" which escapes the slash as well as the colon. Sometimes that works.

---

### Post by silverspr on 2018-11-18
HI thanks for the help, that didn't work either!!
The code debugs OK, there is no error per say, but when live, only the subject is sent w/o the body. The colon is being read as something else... I'm thinking the only way around this is either to ignore having the colon in the body (it was purely for aesthetic appeal and then it became a "mission" to get it to work) or use "cat" to create the message via a file.

---

### Post by SeijiSensei on 2018-11-19
It's probably being treated as another message header like From:.

---

